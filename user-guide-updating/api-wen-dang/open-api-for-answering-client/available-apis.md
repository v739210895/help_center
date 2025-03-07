---
description: 'Request URL:  https://user.outweisurvey.com'
---

# Available APIs

## 1. **Get Answer Details by User ID**

Returns the latest answer record submitted by the user for the survey.

**API Endpoint**

`{URL}/open/api/answers/{sid}`

**Request method**

`GET`

**Parameter Description**

| Parameter | description                       | example                          |
| --------- | --------------------------------- | -------------------------------- |
| uid       | user id                           | xxx\_123                         |
| timestamp | current timestamp in milliseconds | 1741071430                       |
| sign      | Signature                         | e5688d43cc733f4ac82c553f313bff97 |

**CURL example**

```bash
curl --location '{URL}/open/api/answers/67c6a30e2797730bf50d0972?uid=xxx_123&timestamp=1741071430&sign=e5688d43cc733f4ac82c553f313bff97'
```

**Response Data:**

````json
```json
{
    "data": {
        "abnormal_end": false,
        "aid": "67c6a3b1582e38d11bd79368",
        "answer_consumed": 4,
        "answer_finished": true,
        "channel": "-",
        "effective": 0,
        "ended_at": 1741071281,
        "started_at": 1741071277,
        "uid": "xxx_123"
    }
}
```
````

**API Response Field Descriptions**

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top">Field</td><td valign="top">Description</td></tr><tr><td valign="top">abnormal_end</td><td valign="top">Indicates whether the survey ended abnormally </td></tr><tr><td valign="top">aid</td><td valign="top">Unique ID of the answer.</td></tr><tr><td valign="top">answer_consumed</td><td valign="top">Time spent answering the survey (in seconds).</td></tr><tr><td valign="top">answer_finished</td><td valign="top">Indicates whether the questionnaire was fully completed.</td></tr><tr><td valign="top">channel</td><td valign="top">Distribution channel of the survey.</td></tr><tr><td valign="top">effective</td><td valign="top">Indicates whether the answer is valid (0 means valid, non-0 means invalid).</td></tr><tr><td valign="top">ended_at</td><td valign="top">Timestamp when the survey was completed.</td></tr><tr><td valign="top">started_at</td><td valign="top">Timestamp when the survey started.</td></tr><tr><td valign="top">uid</td><td valign="top">User ID of the respondent.</td></tr></tbody></table>
