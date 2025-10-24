# Home Assistant – Warmtepomp + Radiator Booster Fans (Lovelace tab)

Een Lovelace-tabblad (**Radiatorfans**) voor het aansturen van radiator booster fans, met:
- live **chips** voor PWM %, RPM, **Inlet**-temperatuur en **ΔT** (inlet − outlet) in dezelfde stijl als je warmtepomp chips;
- een **slider** (80% breed) voor handmatige PWM override;
- een compacte **Auto**-knop (20% breed) inline naast de slider, zonder icoon, met hoofdletter **A**;
- per ruimte eigen entiteiten (Tuinkamer, Keuken, Woonkamer, Eetkamer, Gang) en een voorbeeld **Kantoor** met generieke entiteiten.

> Voeg deze tab toe aan je bestaande `custom:simple-tabs` setup. Zie `snippets/radiatorfans_tab.yaml`.

## Screenshots
*(plaats hier je screenshots)*

## Vereisten (HACS custom cards)
Installeer en voeg als bron toe (Resources) in je dashboard:
- [button-card] – `custom:button-card`
- [paper-buttons-row] – `custom:paper-buttons-row`
- [mini-graph-card] – `custom:mini-graph-card` *(optioneel, elders in je dashboard)*
- [simple-tabs] – `custom:simple-tabs`
- [bubble-card] – `custom:bubble-card` *(optioneel, elders in je dashboard)*
- [plotly-graph] – `custom:plotly-graph` *(optioneel, elders in je dashboard)*
- [card-mod] – vereist voor de 80/20 layout in de slider/Auto rij

> Controleer in *Instellingen → Dashboards → Bronnen* of alle JS-resources goed geladen worden.

## Entity-namen (schema)
De tab verwacht onderstaande naamgeving. Pas ze aan in het YAML als jouw namen afwijken.

| Ruimte     | PWM sensor                                 | RPM sensor                                 | Inlet temp                                    | Outlet temp                                   | Number (slider)                                          | Auto button                                        |
|------------|--------------------------------------------|--------------------------------------------|-----------------------------------------------|-----------------------------------------------|----------------------------------------------------------|----------------------------------------------------|
| **Kantoor**| `sensor.radiator_booster_fan_pwm`          | `sensor.radiator_booster_fan_rpm`          | `sensor.radiator_booster_ntc1_temperature_inlet`  | `sensor.radiator_booster_ntc2_temperature_outlet` | `number.radiator_booster_manual_pwm_override`           | `button.radiator_booster_return_to_auto`          |
| Tuinkamer  | `sensor.radiator_booster_tuinkamer_fan_pwm`| `sensor.radiator_booster_tuinkamer_fan_rpm`| `sensor.radiator_booster_tuinkamer_ntc1_temperature_inlet` | `sensor.radiator_booster_tuinkamer_ntc2_temperature_outlet` | `number.radiator_booster_tuinkamer_manual_pwm_override` | `button.radiator_booster_tuinkamer_return_to_auto` |
| Keuken     | `sensor.radiator_booster_keuken_fan_pwm`   | `sensor.radiator_booster_keuken_fan_rpm`   | `sensor.radiator_booster_keuken_ntc1_temperature_inlet` | `sensor.radiator_booster_keuken_ntc2_temperature_outlet` | `number.radiator_booster_keuken_manual_pwm_override`    | `button.radiator_booster_keuken_return_to_auto`    |
| Woonkamer  | `sensor.radiator_booster_woonkamer_fan_pwm`| `sensor.radiator_booster_woonkamer_fan_rpm`| `sensor.radiator_booster_woonkamer_ntc1_temperature_inlet` | `sensor.radiator_booster_woonkamer_ntc2_temperature_outlet` | `number.radiator_booster_woonkamer_manual_pwm_override` | `button.radiator_booster_woonkamer_return_to_auto` |
| Eetkamer   | `sensor.radiator_booster_eetkamer_fan_pwm` | `sensor.radiator_booster_eetkamer_fan_rpm` | `sensor.radiator_booster_eetkamer_ntc1_temperature_inlet` | `sensor.radiator_booster_eetkamer_ntc2_temperature_outlet` | `number.radiator_booster_eetkamer_manual_pwm_override`  | `button.radiator_booster_eetkamer_return_to_auto`  |
| Gang       | `sensor.radiator_booster_gang_fan_pwm`     | `sensor.radiator_booster_gang_fan_rpm`     | `sensor.radiator_booster_gang_ntc1_temperature_inlet` | `sensor.radiator_booster_gang_ntc2_temperature_outlet` | `number.radiator_booster_gang_manual_pwm_override`      | `button.radiator_booster_gang_return_to_auto`      |

## Installatie
1. **Dependencies via HACS**: installeer de custom cards hierboven, herstart HA indien gevraagd.
2. **Kopieer** de inhoud van [`snippets/radiatorfans_tab.yaml`](snippets/radiatorfans_tab.yaml) naar je Lovelace view, **binnen** je `custom:simple-tabs > tabs:` lijst, als een tab met titel **Radiatorfans**.
3. **Pas** entiteiten aan waar nodig.
4. **Bewaar** en herlaad je dashboard.

## Styling/UX
- De “chips” (PWM, RPM, Inlet, ΔT) gebruiken dezelfde stijl als de warmtepomp-chip in je voorbeeld (`var(--active-big)`, hoogte 34px, ronde icon background).
- De slider/Auto rij gebruikt `card-mod` om een 80/20 flexverdeling af te dwingen.
- ΔT = `NTC1_inlet − NTC2_outlet`.

## Troubleshooting
- Werkt de slider niet? Controleer of je `number.*_manual_pwm_override` entiteit `set_value` ondersteunt en niet direct door een automation overschreven wordt.
- Zien de chips er anders uit? Controleer dat je kleuren/variabelen (`--active-big`, `--gray000`, `--gray800`) in je thema zijn gedefinieerd.

## Licentie
MIT — zie [LICENSE](LICENSE).
