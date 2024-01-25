# Batch

## Get Batch Overview
Get an overview of all batches.

```shell
curl https://grouphug.peachbitcoin.com/v1/batch/overview
```

> The above command returns JSON structured like this:

```json
[{
    "participants": 0,
    "maxParticipants": 30,
    "feeRange": [38, 0],
    "timeRemaining": 36907,
    "completed": false
  },
  {
    "participants": 3,
    "maxParticipants": 30,
    "feeRange": [31, 38],
    "timeRemaining": 36907,
    "completed": false
  },
  {
    "participants": 3,
    "maxParticipants": 30,
    "feeRange": [23, 31],
    "timeRemaining": 36907,
    "completed": false
  },
  {
    "participants": 0,
    "maxParticipants": 30,
    "feeRange": [16, 23],
    "timeRemaining": 36907,
    "completed": false
  },
  {
    "participants": 0,
    "maxParticipants": 30,
    "feeRange": [8, 16],
    "timeRemaining": 36907,
    "completed": false
  },
  {
    "participants": 0,
    "maxParticipants": 30,
    "feeRange": [1, 8],
    "timeRemaining": 36907,
    "completed": false
  }
]
```

### HTTP Request
`GET /v1/batch/overview`


## Get Batch Status
Get status of a batch.

```shell
curl https://grouphug.peachbitcoin.com/v1/batch?feeRate=38
```

> The above command returns JSON structured like this:

```json
// pending
{
  "participants": 3,
  "maxParticipants": 30,
  "feeRange": [23, 31],
  "timeRemaining": 37110,
  "completed": false
}
// completed
{
  "participants": 1,
  "maxParticipants": 1,
  "timeRemaining": 0,
  "completed": true,
  "txId": "c6a7...72"
}
```

### HTTP Request
`GET /v1/batch?batchId=BATCHID`

or

`GET /v1/batch?feeRate=FEERATE`
