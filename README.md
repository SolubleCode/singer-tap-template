## singer-tap-template

A [cookiecutter](https://github.com/audreyr/cookiecutter) template for creating
[Singer](https://github.com/singer-io) taps.

1. Installing cookiecutter:
```bash
$ pip install cookiecutter
```

2. Bootstrap project using this template.
```bash
$ cookiecutter https://github.com/solublecode/singer-tap-template.git
```
3. Create project virtual environment
```bash
cd tap-foobar
python -m venv venv
source ./venv/bin/activate
```
4. Install the package:
```bash
$ pip install -e .
```

5. Invoke the tap in discovery mode to get the catalog:
```bash
$ tap-foobar -c sample_config.json --discover
```
The output should be a catalog with the single sample stream (from the schemas folder):
```bash
{
  "streams": [
    {
      "metadata": [],
      "schema": {
        "additionalProperties": false,
        "properties": {
          "string_field": {
            "type": [
              "null",
              "string"
            ]
          },
          "datetime_field": {
            "type": [
              "null",
              "string"
            ],
            "format": "date-time"
          },
          "double_field": {
            "type": [
              "null",
              "number"
            ]
          },
          "integer_field": {
            "type": [
              "null",
              "integer"
            ]
          }
        },
        "type": [
          "null",
          "object"
        ]
      },
      "stream": "sample_stream",
      "key_properties": [],
      "tap_stream_id": "sample_stream"
    }
  ]
}
```
You can save this catalog to a `catalog.json` file, to pass it back into the tap in sync mode:
```
tap-foobar -c sample_config.json --properties catalog.json
```

Now you build the tap!


Copyright &copy; 2018 Stitch
