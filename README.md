# Finding Aurora API

This is an Open API Specification (OAS) project.  The `Finding Aurora API` lets us find information about past and future northern lights in Manitoba by taking inputs such as location and time. The northern lights, aka Aurora, are mesmerizing waves of light that are known for their beauty that can be seen often during winter times. This API provides us information such as the KP index, which describes characteristics of the current aurora. 


## Endpoints

### By location
```auroraapi.org/location```

#### Parameters
* **lat** (float): The latitude of the location in Manitoba
* **long** (float): The longitude of the location in Manitoba

**NOTE:** `lat` and `long` must both be present, or neither present for current location.

#### Returns
Returns an array of [Aurora Events](#aurora-event) of length 1 denoting the next or current event for the given location.

### By time
```auroraapi.org/time```

#### Parameters
* **time** (string): The time an aurora occurred, formatted as an ISO 8601 Date Time string.

#### Returns
Returns an array of [Aurora Events](#aurora-event).

### Get photos
```auroraapi.org/photo```

#### Parameters
* **lat** (float): The latitude of the location in Manitoba
* **long** (float): The longitude of the location in Manitoba

**NOTE:** `lat` and `long` must both be present, or neither present for current location.

#### Returns
Returns a [Photo object](#photo).

## Resources
* time: ISO 8601 Date Time string in Central Time (UTC-6)
* length: Number of seconds, -1 if unknown
* kp: Integer ranging from 0-9

### Aurora Event
```json
[
    {
        "time": "2021-11-19T00:07:52-06:00",
        "location": {
            "lat": 49.8951,
            "long": 97.1384
        }
        "length": 20,
        "kp": 2
    },
]
```


### Photo
```json
{
    "url": "https://imagesite.com/image.png",
    "time": "2021-11-19T00:07:52-06:00",
    "location": {
        "lat": 49.8951,
        "long": 97.1384
    }
    "kp": 2
}
```

## Sample Requests

### Location
#### Request
`https://auroraapi.org/location?lat=49.8951&long=97.1384`

#### Response
```json
[
    {
        "time": "2021-11-19T00:07:52-06:00",
        "location": {
            "lat": 49.8951,
            "long": 97.1384
        }
        "length": 20,
        "kp": 2
    }
]
```

### Time
#### Request
`https://auroraapi.org/time?time="2021-11-19T00:07:52-06:00"`

#### Response
```json
[
    {
        "time": "2021-11-19T00:07:52-06:00",
        "location": {
            "lat": 49.8951,
            "long": 97.1384
        }
        "length": 20,
        "kp": 2
    }
]
```

### Photo
#### Request
`https://auroraapi.org/photo?lat=49.8951&long=97.1384`

#### Response
```json
{
    "url": "https://imagesite.com/image.png",
    "time": "2021-11-19T00:07:52-06:00",
    "location": {
        "lat": 49.8951,
        "long": 97.1384
    }
    "kp": 2
}
```