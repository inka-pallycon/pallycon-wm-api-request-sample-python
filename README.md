# pallycon-wm-api-request-sample

This sample is to get specification for PallyCon Watermark APIs for python 
<br><br>

## Prerequisites

### Language

This works on `PYTHON` version : 

- 3.7.6 and greater

<br>

### IDE

- PyCharm

<br><br>


## Quick Start

Clone this git repository and go to the `sample.py`. This code below is from `sample.py`.

```python
import json
from pallycon.sample.watermark.pallycon_wm_api import execute

"""
THIS IS A SAMPLE CODE FOR GENERATE PallyCon HTTP API specification.
"""


def generate(**kwargs):
    print('data requested', json.dumps(kwargs, indent=4))

    # set the parameters for generate.
    site_id = kwargs.get('site_id')
    access_key = kwargs.get('access_key')
    site_key = kwargs.get('site_key')
    json_req = kwargs.get('json_req')

    # get a result using execute function from module `pallycon_wm_api`
    result = execute(site_id, access_key, site_key, json_req)

    print('result', json.dumps({'pallycon-apidata': result}, indent=4))


json_str = {
    "storage_type": "S3",
    "region": "RG011"
}

# Sample Code
generate(site_id='TUTO',
         site_key='lU5D8s3PWoLls3PWFWkClULlFWk5D8oC',
         access_key='LT2FVJDp2Xr018zf4Di6lzvNOv3DKP20',
         json_req=json.dumps(json_str))

```
<br>

#### Result of quick start

```
data requested {
    "site_id": "TUTO",
    "site_key": "lU5D8s3PWoLls3PWFWkClULlFWk5D8oC",
    "access_key": "LT2FVJDp2Xr018zf4Di6lzvNOv3DKP20",
    "json_req": "{\"storage_type\": \"S3\", \"region\": \"RG011\"}"
}
result {
    "pallycon-apidata": "eyJkYXRhIjogIjFoY0crOUhMckR1ZWlJTjlDWXQ4SVNvekIzY0x6Zy9Db2VHNE5PKzY2cW9WRWo5eEJ1S2JzZkNUaVM3KzZrWWoiLCAidGltZXN0YW1wIjogIjIwMjAtMDctMTVUMTA6Mzg6MTdaIiwgImhhc2giOiAibVVyK1Y3S1JWYXVsVmRpNmRmekZCUERSZ1JHQnpnYWxIT1NCNitJdFh1VT0ifQ=="
}
```


<br><br>

### HOW IT WORKS ?

If want to see how it works, go to module  `pallycon.sample.watermark.pallycon_wm_api`. On the top of this module, there is a simple note how it works.

> 1. get `site_id`, `access_key`, `site_key`, and `json_req`
> 2. encrypt `json_req` with `_make_data()`.
> 3. make `timestamp` with `_make_timestamp()`.
> 4. make `hash` with `_make_hash()`.
> 5. return PallyCon Watermark API specificated String from the values `#2 ~ #4`

<br><br><br><br><br><br>

