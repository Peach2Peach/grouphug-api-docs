# Queue

## Add PSBT
Send a PSBT to the server with a desired fee rate.

Make sure that the PSBT fulfills all the criteria:

- 1 input & 1 output: the payouts are in full (i.e. no change output)
- the output amount must exclude the network fees
- output amounts can be smaller, any sats left over are considered a donation to the batching service
- the PSBT must have a valid signature: this includes that the PSBT is signed with the sighash `SINGLE|ANYONECANPAY`


```shell
curl -X POST  https://grouphug.peachbitcoin.com/v1/addPSBT
  -H 'Content-Type: application/json' \
  --data-raw '{
    "psbt": "cHNidP8BAFICAAAAATYf...EHXc5RJZlccqwAAA==",
    "feeRate": 40
}'
```

> The above command returns JSON structured like this:

```json
{
  "id": "0b8c1f997ecac4a2a88419e803cb86ed1662f087614f986b70bd0dd4fc688771",
  "revocationToken": "5d157eabd02448f4ba7b0d2b40f2051c",
}
```

### HTTP Request
`GET /v1/v1/addPSBT`

### Body Parameters

Name | Type | Required | Description
--------- | ----------- | ----------- | -----------
`psbt` | `string` | yes | base64 encoded PSBT (must fulfil the criteria)
`feeRate` | `number` | yes | The desired fee rate to be batched with, used to sort into a batching bucket
`index` | `number` | no | Used for multisig service. Only use if you need the batching service to co-sign.


## Revoke PSBT
Remove a PSBT from the batching service as long as it hasn't been included in a batch.


```shell
curl -X POST  https://grouphug.peachbitcoin.com/v1/revokePSBT
  -H 'Content-Type: application/json' \
  --data-raw '{
    "id": "0b8c1f997ecac4a2a88419e803cb86ed1662f087614f986b70bd0dd4fc688771",
    "revocationToken": "5d157eabd02448f4ba7b0d2b40f2051c",
}'
```

> The above command returns JSON structured like this:

```json
{
  "success": true
}
```

### HTTP Request
`GET /v1/v1/revokePSBT`

### Body Parameters

Name | Type | Required | Description
--------- | ----------- | ----------- | -----------
`id` | `string` | yes | The ID of the PSBT (it's a shae256 hash of the base64 encoded PSBT)
`revocationToken` | `string` | yes | The token provided by the server to recoke the PSBT