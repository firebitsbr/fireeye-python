[![PyPI version](https://badge.fury.io/py/fireeyepy.svg)](https://badge.fury.io/py/fireeyepy)
[![Python versions supported](https://img.shields.io/pypi/pyversions/fireeyepy.svg)](https://pypi.python.org/pypi/fireeyepy)

# FireEye Client Library for Python
This is the Python client library for all things FireEye API. Currently it only supports FireEye's Detection On Demand but will have support for other FireEye API's soon.

For more API information, visit the [FireEye Developer Hub](https://fireeye.dev)

Installation
------------

To install the Python client library:
```
pip install fireeyepy
```

To upgrade your installed library:
```
pip install fireeyepy --upgrade
```

Alternatively, you can clone the repository via the command line:
```
git clone https://github.com/fireeye/fireeye-python.git
```

Usage
-----
Begin by importing the 'fireeye' module:
```python
import fireeyepy
```

## Detection On Demand
Construct a Detection object with your api key:
```python
detection = fireeyepy.Detection(key=api_key)
```
To obtain a free trial API key, subscribe on the [AWS Marketplace](https://aws.amazon.com/marketplace/pp/B07XSMKK41)

### Upload A File
```python
  import fireeyepy

  detection = fireeyepy.Detection(key="yourapikeyhere")

  result = detection.submit_file(
    files={
      "file": ('filename', open('./path/to/filename', 'rb'))
    }
  )
```
With configuration options:
```python
  result = detection.submit_file(
    body={
      "file_name": "different_name.txt",
      "screenshot": true
    },
    files={
      "file": ('filename', open('./path/to/filename', 'rb'))
    }
  )
```

### Submit URLs
```python
  import fireeyepy

  detection = fireeyepy.Detection(key="yourapikeyhere")

  result = detection.submit_urls(["url1","url2",...])
```

### Retrieve File or URL Report
```python
response = detection.get_report(report_id)
```
You may also provide the optional `extended=True` flag to get the full, in-depth report:
```python
response = detection.get_report(report_id, extended=True)
```

### Retrieve Presigned URL for Dashboard Report
```python
result = detection.get_presigned_url(report_id)
```

### Perform Hash Lookup
```python
response = detection.get_hash(hash)
```

### Get a report artifact
```python
artifact = detection.get_artifact(report_id="8d0aa90b-8bf3-4483-ae3b-0ded00d157ab", artifact_type="screenshot")
```

### Get the health of the Detection on Demand service
```python
health = detection.get_health()
```