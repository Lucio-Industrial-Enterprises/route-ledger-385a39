# Warehouse tools

Small Python utilities for warehouse order and shipping workflows.

Run the tests with `python3 -m unittest discover -s tests -v`.

## Shipping

`shipping_quote(weight_kg, zone, service="standard")` returns a delivery quote
in US dollars.

| Parameter   | Values                      | Notes                              |
|-------------|-----------------------------|------------------------------------|
| `weight_kg` | any positive float          | weight of the parcel               |
| `zone`      | `"local"`, `"regional"`     | delivery zone                      |
| `service`   | `"standard"`, `"express"`   | express adds a flat $7 surcharge   |

A `ValueError` is raised for non-positive weights, unknown zones, or unknown
service levels.

### CLI

```
python -m warehouse.cli <weight_kg> <zone> [--service {standard,express}]
```

Examples:

```bash
python -m warehouse.cli 2 local                    # $8.00 (standard)
python -m warehouse.cli 2 local --service express  # $15.00 (express)
python -m warehouse.cli 2 regional --service express  # $18.00
```
