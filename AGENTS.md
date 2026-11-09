# Repository guidance

This fork develops focused, upstreamable support for Dreo devices. Read
[CONTRIBUTING.md](CONTRIBUTING.md) for checks, evidence requirements, PR scope,
and approval boundaries. [README.md](README.md) covers installation and models.

## Source map

- [custom_components/dreo/](custom_components/dreo/) contains the entity platforms:
  `fan.py`, `humidifier.py`, `light.py`, `switch.py`, `number.py`, `sensor.py`,
  `select.py`, and `climate.py`.
- Shared state parsing and coordination are in
  [coordinator.py](custom_components/dreo/coordinator.py); entity behavior is in
  [entity.py](custom_components/dreo/entity.py), and shared keys and model
  exceptions are in [const.py](custom_components/dreo/const.py).
- User-facing strings live in [strings.json](custom_components/dreo/strings.json)
  and [translations/en.json](custom_components/dreo/translations/en.json).

Inspect the relevant platform and shared parsing before documenting model behavior.
