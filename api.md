# BoxFleet hosted control plane (boxfleet.io) JavaScript API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImUzZmQ0Yzc0NGFlODkzM2MwZTBiZDBjMjFhNjkyODk3Nzk1YTE0NjU3ZTU3N2ZiODIxMDg1MDBkMzlmMmFjOGQiLCJvcGVyYXRpb25fY291bnQiOjU2LCJyZW5kZXJlciI6ImphdmFzY3JpcHQiLCJ2ZXJzaW9uIjoiMS41LjAifQ -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `e3fd4c744ae8933c0e0bd0c21a692897795a14657e577fb82108500d39f2ac8d`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **verified**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`new Client({ hooks })` registers four callbacks. Every attempt starts with `beforeRequest` and ends with exactly one of `onRetry` (another attempt follows), `afterResponse` (the success the call returns) or `onError` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. `beforeRequest` is the one hook that may change the request (the documented per-request credential contract, which also reads credentials masked); the other three receive frozen `HookContext` copies.

`new Client({ tracer })` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `HostedPersistentBoxClose`
- `HostedPersistentBoxRead`
- `HostedPersistentUsageMeter`
- `HostedPersistentUsageRead`
- `ObservedBox`

## Resource `accounts`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhY2NvdW50cy5nZXRDb25maWciLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRBY2NvdW50c0NvbmZpZyIsInBhdGgiOiIvdjEvYWNjb3VudHMvY29uZmlnIiwicmVzb3VyY2UiOiJhY2NvdW50cyIsInNlY3Rpb25fc2hhMjU2IjoiMTc2YWFhOWVkYmZkYzliYWE1MDFiYjM0NjUwNTdkN2ZlNzM3Y2FkMDIwZDE4ZTE2YzdiNDdlMDMxYzg2NjBkMyIsInNpZ25hdHVyZV9zaGEyNTYiOiIxNGQ0N2FmYjlmZWVmOTBlZDc1ZTY0MmU3OThlMmVkMDBiOTQxOWM4ODMyZGUwZWZlYWE2OGZlMmU3Yjc4OTcyIn0 -->
### `client.accounts.getConfig`

Operation ID: `getAccountsConfig`  
Route: `GET` `/v1/accounts/config`  
Equivalent member: `client.getAccountsConfig`  

#### Signature

```javascript
client.accounts.getConfig(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.accounts.getConfig();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBY2NvdW50c0NvbmZpZyJ9 -->

## Resource `admin`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi5jb250cm9sVXNlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjb250cm9sVXNlciIsInBhdGgiOiIvdjEvYWRtaW4vdXNlcnMiLCJyZXNvdXJjZSI6ImFkbWluIiwic2VjdGlvbl9zaGEyNTYiOiI5ZDRkZDk4OWFiNjUwZDg1MTg4ZTA4MWU5YmViMGE5M2NkZTJlZDMyOGYxZTI3ZDA3NWJhOTJhMzU0NDBkNGZkIiwic2lnbmF0dXJlX3NoYTI1NiI6ImI4ZTBhMDU2ZDcxYWM5MGQ1N2MzZGRhYzQyNzQ4MDQwZGQ5MTJmYTc5MjNiZmIxMzA4MGI0OTZmODgyNWRmMjEifQ -->
### `client.admin.controlUser`

Operation ID: `controlUser`  
Route: `POST` `/v1/admin/users`  
Equivalent member: `client.controlUser`  

#### Signature

```javascript
client.admin.controlUser(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Applied | none |
| `401` | Admin token required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.admin.controlUser({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb250cm9sVXNlciJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi5nZXRDb25zb2xlIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0QWRtaW5Db25zb2xlIiwicGF0aCI6Ii92MS9hZG1pbi9jb25zb2xlIiwicmVzb3VyY2UiOiJhZG1pbiIsInNlY3Rpb25fc2hhMjU2IjoiMWE5ZjhhMTdlMDg4NzMwMzIyYzY2N2RiMmY1M2U5OTBlMGJmZDNiYWEzNTBhMWJjMzA5OWFhNTQ1ZGE5YzM0YSIsInNpZ25hdHVyZV9zaGEyNTYiOiJlNDhiMTgxOTNhY2UxZjliYWNiNDNiOWI5M2FmNjA3YjA5Y2U1MTdkZDA3Y2NiNWNhZmFiNTJlNjIxODk0ZTM3In0 -->
### `client.admin.getConsole`

Operation ID: `getAdminConsole`  
Route: `GET` `/v1/admin/console`  
Equivalent member: `client.getAdminConsole`  

#### Signature

```javascript
client.admin.getConsole(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Console | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.admin.getConsole();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBZG1pbkNvbnNvbGUifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi5nZXRQbGFucyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEFkbWluUGxhbnMiLCJwYXRoIjoiL3YxL2FkbWluL3BsYW5zIiwicmVzb3VyY2UiOiJhZG1pbiIsInNlY3Rpb25fc2hhMjU2IjoiNGE2ODc3ZWQ1YzEyZTk1MTlhYzdlNGUzNzkwOWI1MjE1MTRmYWViYzM3NWMzY2Q2NTkzMTk4YTcwNWIyYjZjMyIsInNpZ25hdHVyZV9zaGEyNTYiOiI4ZmFkOGZkODgwYWU4MzQ1M2ZhZmVmNWVlOGNhNzhjMmE4MmUxZjNhMGI2Y2RmMzA0MjkyZDY0YjRkNjBjYzU2In0 -->
### `client.admin.getPlans`

Operation ID: `getAdminPlans`  
Route: `GET` `/v1/admin/plans`  
Equivalent member: `client.getAdminPlans`  

#### Signature

```javascript
client.admin.getPlans(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Plans | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.admin.getPlans();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBZG1pblBsYW5zIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi5saXN0VXNlcnMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0VXNlcnMiLCJwYXRoIjoiL3YxL2FkbWluL3VzZXJzIiwicmVzb3VyY2UiOiJhZG1pbiIsInNlY3Rpb25fc2hhMjU2IjoiNGYzNWFhOGNlNjVlOWU5NjdmZTk3OWI1YzY0ZDJmZGNmMDFhNTVmN2EyNzIyM2RiYjViYmJlYjNhZjgyMDQzYyIsInNpZ25hdHVyZV9zaGEyNTYiOiI3NDYzY2MyNzViZWY3ZjM0MDdiMDQwZDU0NmU2NzE0MTRhYTEyYjRhM2IwYzgzOGFjMzYxZWM1NGFhNWFjMDYzIn0 -->
### `client.admin.listUsers`

Operation ID: `listUsers`  
Route: `GET` `/v1/admin/users`  
Equivalent member: `client.listUsers`  

#### Signature

```javascript
client.admin.listUsers(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Users | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.admin.listUsers();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0VXNlcnMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi5yZWFkVGVsZW1ldHJ5IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoicmVhZFRlbGVtZXRyeSIsInBhdGgiOiIvdjEvYWRtaW4vdGVsZW1ldHJ5IiwicmVzb3VyY2UiOiJhZG1pbiIsInNlY3Rpb25fc2hhMjU2IjoiM2ZiNWE4NjE2OWU5ZjEzYmFlYjAzMDdlOWMzYjg0MmM0YzhhYzFhZGRjODYwY2M1N2I5YWFjZGMwYzBhZjBhOCIsInNpZ25hdHVyZV9zaGEyNTYiOiI5ZTY5MjQ0ODM0MTY5ZWJjZGVlYzQwMGUyYjdkY2MzMDlhM2Y4M2U1MjY4ZDU1NTA4YTZhZDBiYmNiYjc0ZjZkIn0 -->
### `client.admin.readTelemetry`

Operation ID: `readTelemetry`  
Route: `GET` `/v1/admin/telemetry`  
Equivalent member: `client.readTelemetry`  

#### Signature

```javascript
client.admin.readTelemetry(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Events | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.admin.readTelemetry();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWFkVGVsZW1ldHJ5In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi51cGRhdGVQbGFuIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InVwZGF0ZVBsYW4iLCJwYXRoIjoiL3YxL2FkbWluL3BsYW5zIiwicmVzb3VyY2UiOiJhZG1pbiIsInNlY3Rpb25fc2hhMjU2IjoiZDBkYTUzNDBlNzk3YTBjZmNjM2I3Zjk5NTEyZTVhN2Q1ZDZhYTViMmQ2NDFhMDczM2JkMzgxZjA0ZWU1YmRmMiIsInNpZ25hdHVyZV9zaGEyNTYiOiI0YjlkODBjNTM5YTZiMDBhYjk4NmYyMzBkODBlZTExZGQ4MDFkMjA3M2ZmYzlmZmQ1NDViNmNkNTljZjhkZjVlIn0 -->
### `client.admin.updatePlan`

Operation ID: `updatePlan`  
Route: `POST` `/v1/admin/plans`  
Equivalent member: `client.updatePlan`  

#### Signature

```javascript
client.admin.updatePlan(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Updated | none |
| `401` | Admin token required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.admin.updatePlan({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ1cGRhdGVQbGFuIn0 -->

## Resource `auth_`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhdXRoXy5nZXRHYXRlIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0QXV0aEdhdGUiLCJwYXRoIjoiL3YxL2F1dGgvZ2F0ZSIsInJlc291cmNlIjoiYXV0aF8iLCJzZWN0aW9uX3NoYTI1NiI6IjNmNTI2OGVkMWZhYmZhYjdiMzFmZmU3ZDJjZjVjMDdkMTc2MzczNjk3ZmNiNWUyYzAyNjljMTU4OWEyZTA1MWEiLCJzaWduYXR1cmVfc2hhMjU2IjoiMGQ2YjVhZWE3ZGUwNDJlZjY4NDQyNGMwNTI4MzM4NzlhNmVjODU5NDk3M2M5ZDJhN2Y0Mjk4YzJiYTI4NWE4ZCJ9 -->
### `client.auth_.getGate`

Operation ID: `getAuthGate`  
Route: `GET` `/v1/auth/gate`  
Equivalent member: `client.getAuthGate`  

#### Signature

```javascript
client.auth_.getGate(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.auth_.getGate();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBdXRoR2F0ZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhdXRoXy5yZWdpc3RlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJyZWdpc3RlciIsInBhdGgiOiIvdjEvYXV0aC9yZWdpc3RlciIsInJlc291cmNlIjoiYXV0aF8iLCJzZWN0aW9uX3NoYTI1NiI6ImYyZDkyZjhiYWYxMDhjYzkyNWNiNzA4MGVmYjRjMzUxZjE3YTk4NmE1ZThjNmI4ZmUzYmQ5ZjdiNTgwYTk4ZmYiLCJzaWduYXR1cmVfc2hhMjU2IjoiNzczNzhlZTM4YWNiYzU0OGU1N2E4NTgwYWM5YjE0NTE4NzYyZjI1NzhiZWM5NzI0MTJjYjlhMjdjODE4MGYxMyJ9 -->
### `client.auth_.register`

Operation ID: `register`  
Route: `POST` `/v1/auth/register`  
Equivalent member: `client.register`  

#### Signature

```javascript
client.auth_.register(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | License issued | none |
| `202` | Verification code sent (or withheld by the resend cooldown) | none |
| `400` | Invalid or expired code | none |
| `403` | Not invited or refused | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |
| `429` | Rate limited | none |
| `503` | Registration not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.auth_.register({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWdpc3RlciJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhdXRoXy51cGRhdGVHYXRlIiwibWV0aG9kIjoiUFVUIiwib3BlcmF0aW9uX2lkIjoidXBkYXRlQXV0aEdhdGUiLCJwYXRoIjoiL3YxL2F1dGgvZ2F0ZSIsInJlc291cmNlIjoiYXV0aF8iLCJzZWN0aW9uX3NoYTI1NiI6Ijk3OWZjZjcwMGE1Yjg4ZmFkYTI2MTM0ZTFmZWRmYWEyZTE2MTkwZGYxZTMzZDYxOWIwYTk1YTQ2ZDIyMzAyMjAiLCJzaWduYXR1cmVfc2hhMjU2IjoiOGRjNjEwM2Y5YmUzMjU3OTBhOTVhNDgzODM1N2YwNWZkYzI4MWM3ZGM2ODJmYTVjNDRjOWViMDdiYWRjYjlhYyJ9 -->
### `client.auth_.updateGate`

Operation ID: `updateAuthGate`  
Route: `PUT` `/v1/auth/gate`  
Equivalent member: `client.updateAuthGate`  

#### Signature

```javascript
client.auth_.updateGate(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Updated | none |
| `401` | Admin token required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.auth_.updateGate({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ1cGRhdGVBdXRoR2F0ZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhdXRoXy52ZXJpZnlMaWNlbnNlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InZlcmlmeUxpY2Vuc2UiLCJwYXRoIjoiL3YxL2F1dGgvdmVyaWZ5IiwicmVzb3VyY2UiOiJhdXRoXyIsInNlY3Rpb25fc2hhMjU2IjoiZmFiN2FiM2VjNjU3NjAyOTZlNWM1NTQxM2I1MzUwYmYyN2NlNTkzNTQ4ZWQzZjFhNDk3MWJjYTExMTc4NmYxOCIsInNpZ25hdHVyZV9zaGEyNTYiOiI4ODBiMmFiMjU2MGIwYzk3NTBkMWE2YzAyMTUwNThkMmVhMTMzNGY3M2Q0ZDA1MzgyMjNlMWFiOGI1YTlkNDM5In0 -->
### `client.auth_.verifyLicense`

Operation ID: `verifyLicense`  
Route: `POST` `/v1/auth/verify`  
Equivalent member: `client.verifyLicense`  

#### Signature

```javascript
client.auth_.verifyLicense(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Valid | none |
| `401` | Invalid license | none |
| `403` | Refused | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |
| `503` | Verification not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.auth_.verifyLicense({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ2ZXJpZnlMaWNlbnNlIn0 -->

## Resource `billing`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJiaWxsaW5nLnN0cmlwZVdlYmhvb2siLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoic3RyaXBlV2ViaG9vayIsInBhdGgiOiIvdjEvYmlsbGluZy9zdHJpcGUvd2ViaG9vayIsInJlc291cmNlIjoiYmlsbGluZyIsInNlY3Rpb25fc2hhMjU2IjoiMTc4YWFjMmRhZGVhOGJjN2YzMGEzYzc5MmNiZWRhOWZlYWFlN2I5ODI4YzYyY2Y4ZWRhZTM4NmY5YjcwNzFiNyIsInNpZ25hdHVyZV9zaGEyNTYiOiI5ZDNjZDU0MGNlNWE2Yzg1YmJlMTQ2MDg0MGFiMDQ0ZjkzNmM2ZjlmZDVhYTg1OGFhMTc4MzkxZTgzODM3YTZkIn0 -->
### `client.billing.stripeWebhook`

Operation ID: `stripeWebhook`  
Route: `POST` `/v1/billing/stripe/webhook`  
Equivalent member: `client.stripeWebhook`  

#### Signature

```javascript
client.billing.stripeWebhook(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Received | none |
| `400` | Invalid signature or payload | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.billing.stripeWebhook();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdHJpcGVXZWJob29rIn0 -->

## Resource `health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJoZWFsdGguZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SGVhbHRoIiwicGF0aCI6Ii9oZWFsdGgiLCJyZXNvdXJjZSI6ImhlYWx0aCIsInNlY3Rpb25fc2hhMjU2IjoiNmViZTQ2NDk3ZTJmMDA3MDI2YzJmOWZlNmRkMWQ3ZjEzYWE1NzM1NmY1ZDYwZTg4NDg5ZjZlYThjMWIyMzEzZCIsInNpZ25hdHVyZV9zaGEyNTYiOiIwMjQzZWEwOTU4OTg0OTI2YjYzNWU5NjU5MDVmYzE2ZWQ0OWE5OWVmMjY4ZDExM2ZiNWZhYzFhN2E2Mjk4MDVmIn0 -->
### `client.health.get`

Operation ID: `getHealth`  
Route: `GET` `/health`  
Equivalent member: `client.getHealth`  

#### Signature

```javascript
client.health.get(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.health.get();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgifQ -->

## Resource `jobs`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJqb2JzLmNhbmNlbCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjYW5jZWxKb2IiLCJwYXRoIjoiL3YxL2pvYnMve2pvYklkfS9jYW5jZWwiLCJyZXNvdXJjZSI6ImpvYnMiLCJzZWN0aW9uX3NoYTI1NiI6ImVlYjk2MGM5Y2Q1N2EyM2NlOTEyNTNjYjU1OTc0YmQ1ODE4MzdkODExOWRjZTkzYzU5MDdhYWY5NTkzODliOGMiLCJzaWduYXR1cmVfc2hhMjU2IjoiNzliZWJiNTI3M2Q4YThhNDk0YzY3ZDg4YzA2YzUwNTc2ZmQ3YWExYzRmMmQzMWExMWQ3ZGFlODBjMjY3NmM3ZSJ9 -->
### `client.jobs.cancel`

Operation ID: `cancelJob`  
Route: `POST` `/v1/jobs/{jobId}/cancel`  
Equivalent member: `client.cancelJob`  

#### Signature

```javascript
client.jobs.cancel(jobId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.jobs.cancel("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjYW5jZWxKb2IifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJqb2JzLmdldCIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEpvYiIsInBhdGgiOiIvdjEvam9icy97am9iSWR9IiwicmVzb3VyY2UiOiJqb2JzIiwic2VjdGlvbl9zaGEyNTYiOiI5YTdkODkzOTE0ZGU3YTczMmRhMjZkY2M5NGFjZjRiNmRiMmY2N2JhNDNmN2U1YjU5NzNjOTYzZTBlN2QxYWU1Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjY2MGRhOTI5OTI2NThmYzQwNTdhN2QxZDY3NTQ0NTIxMDhkM2RjNjk5Njc4M2U3N2E5MTcwOTNlNWQ5MzQ1ZjEifQ -->
### `client.jobs.get`

Operation ID: `getJob`  
Route: `GET` `/v1/jobs/{jobId}`  
Equivalent member: `client.getJob`  

#### Signature

```javascript
client.jobs.get(jobId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.jobs.get("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRKb2IifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJqb2JzLmxpc3RFdmVudHMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0Sm9iRXZlbnRzIiwicGF0aCI6Ii92MS9qb2JzL3tqb2JJZH0vZXZlbnRzIiwicmVzb3VyY2UiOiJqb2JzIiwic2VjdGlvbl9zaGEyNTYiOiI3ZjVkOWI2MDkzNmRlMWQwYjEyNDRkZDJjYzA2ZmQ3ODRhNGFiNDk3ZGQ3ZDNhZjZkOTk3OWVmZTFiNTBhM2RkIiwic2lnbmF0dXJlX3NoYTI1NiI6ImU2ZDU3NzIxNjUwMWYyZGE4YmZhNTk0NTBhOWZiZGE4NDkwMzQyNmRmY2JlMzJkOTIzNTMxNjQ5OTc4NTAxZDYifQ -->
### `client.jobs.listEvents`

Operation ID: `listJobEvents`  
Route: `GET` `/v1/jobs/{jobId}/events`  
Equivalent member: `client.listJobEvents`  

#### Signature

```javascript
client.jobs.listEvents(jobId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.jobs.listEvents("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Sm9iRXZlbnRzIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJqb2JzLmxpc3QiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0Sm9icyIsInBhdGgiOiIvdjEvam9icyIsInJlc291cmNlIjoiam9icyIsInNlY3Rpb25fc2hhMjU2IjoiMDAzMzVjYmUyNDliM2EzZDg4MzQ1NWY0MDQ2NWQzMmNjYWM1MzUwNDNmODc4MzgyZWViMDk5MDc0ODllMzVjYSIsInNpZ25hdHVyZV9zaGEyNTYiOiJjOWMyOTFlY2U5ZTk3YTgyYTlkODc3ZWUzNzMwZGU2ZTg1NDc5ZGZhZTZmMjZmOTc0ZDNjNjhhNjE5NTMyMGZmIn0 -->
### `client.jobs.list`

Operation ID: `listJobs`  
Route: `GET` `/v1/jobs`  
Equivalent member: `client.listJobs`  

#### Signature

```javascript
client.jobs.list(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Jobs | none |
| `401` | Session required | none |
| `503` | Storage not configured | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.jobs.list();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Sm9icyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJqb2JzLnN1Ym1pdCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJzdWJtaXRKb2IiLCJwYXRoIjoiL3YxL2pvYnMiLCJyZXNvdXJjZSI6ImpvYnMiLCJzZWN0aW9uX3NoYTI1NiI6ImYxNTFlN2I5NDYwYzlkNTlmNzcxZWFjMGE1MDU0ZWU0YmQzMGYyNjY2NTk2NjlkMjQ4OGVkNDlkZTU3YTMwOTkiLCJzaWduYXR1cmVfc2hhMjU2IjoiNzk0NzNmMjhhMTVmYTk0ODA4ZGI2YjVhYTEwYjMxYWNjNDllMjRhZTEzZjc2OGEwZjA0N2Q3MGNjMjNkNjAwNSJ9 -->
### `client.jobs.submit`

Operation ID: `submitJob`  
Route: `POST` `/v1/jobs`  
Equivalent member: `client.submitJob`  

#### Signature

```javascript
client.jobs.submit(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Replayed | none |
| `201` | Created | none |
| `401` | Session required | none |
| `503` | Storage not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.jobs.submit({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdWJtaXRKb2IifQ -->

## Resource `organizations`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmNsb3NlUGVyc2lzdGVudEJveCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjbG9zZVBlcnNpc3RlbnRCb3giLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9wZXJzaXN0ZW50LWJveGVzL3tib3hJZH0vY2xvc2UiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjIyYWIxNjYwYzYyOWVkNDAxNzZmOGQ3NWY3NjU1YWEwNGM3ZDAzMzlhNjMzMGZlZjc0OWYzNjAwZmU4YjdhNmYiLCJzaWduYXR1cmVfc2hhMjU2IjoiOTJkMzYwZDliMGI2ODgyMjVjMmExOTM0ZjVlMGVlOTg5YzU0NDI2MDA3NWY4NGRkNWI3MDgwODQ5MjNhMjkyMiJ9 -->
### `client.organizations.closePersistentBox`

Operation ID: `closePersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/close`  
Equivalent member: `client.closePersistentBox`  

#### Signature

```javascript
client.organizations.closePersistentBox(organizationId, boxId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Closure is recorded; repeat requests return the same result without deleting again. | application/json (HostedPersistentBoxClose) |
| `202` | Closure is unconfirmed. Lost, late, negative or mismatched acknowledgements and failed receipt persistence retain reservations. Repeat requests never dispatch another deletion; operator reconciliation is required. | application/json (HostedPersistentBoxClose) |
| `400` | Invalid UUID, body or query parameters. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied cleanup or the organization/product/environment differs. | none |
| `404` | No durable box in this exact target scope. | none |
| `409` | Unconfirmed or changed provider allocation requires operator reconciliation. | none |
| `503` | Authority or storage unavailable, or no matching operator provider adapter. Missing configuration refuses before any close intention or deletion. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-c54d-988d0e4e7e77"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.closePersistentBox("example", "00000000-0000-0000-c54d-988d0e4e7e77");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjbG9zZVBlcnNpc3RlbnRCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmNyZWF0ZUJpbGxpbmdQb3J0YWwiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3JlYXRlQmlsbGluZ1BvcnRhbCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2JpbGxpbmcvcG9ydGFsIiwicmVzb3VyY2UiOiJvcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiJkMTFjMTI2M2IxNTNlYzg3OWViZDNmNTUxMTljZmIxOTQyNTg3MDBiNzk2ODc2MWI3NzgwNTFlZDQwMzE4Yzk0Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjI0Mzg1ODA3MTcxODMzOWQxYjljZjNjOWU1NTY1ZGQ1NjJiNzZhMTNkZmI1OTY0ZmNkMDQ0YzQ3ZDFmZmVlOGQifQ -->
### `client.organizations.createBillingPortal`

Operation ID: `createBillingPortal`  
Route: `POST` `/v1/organizations/{organizationId}/billing/portal`  
Equivalent member: `client.createBillingPortal`  

#### Signature

```javascript
client.organizations.createBillingPortal(organizationId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | portalUrl | none |
| `404` | No Stripe customer yet | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.createBillingPortal("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVCaWxsaW5nUG9ydGFsIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmNyZWF0ZUJveCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjcmVhdGVCb3giLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9ib3hlcyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiODIxYWUzYzg3Y2JiMjUxZTIyYTlhY2IwYjkzNmFlZDU3ODcwZTRmNDBhODVkY2NlMGIzNTBmYjhjZWRhY2I2ZiIsInNpZ25hdHVyZV9zaGEyNTYiOiJmZGQ3NTAzMDU0ZDZmZmMxYmRjZTJjYTMxZGQ1MWQ2ZGQxZWZlNzQwZWNjZWY1MmI2YWE0ZTkxNWM4NDZkOWI3In0 -->
### `client.organizations.createBox`

Operation ID: `createBox`  
Route: `POST` `/v1/organizations/{organizationId}/boxes`  
Equivalent member: `client.createBox`  

#### Signature

```javascript
client.organizations.createBox(organizationId, body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Box running at the provider | none |
| `402` | Concurrent-box limit reached | none |
| `502` | The provider refused; recorded as failed | none |
| `503` | No provider or no storage | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.createBox("example", {}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmNyZWF0ZUNoZWNrb3V0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNyZWF0ZUNoZWNrb3V0IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vYmlsbGluZy9jaGVja291dCIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiZWUwYjE3NzFhOWE5YzQ0YTk3NjVmMDU1YzQ3M2U0ODI4M2JkMzNiMWNiMWI2NjdiOTRiMzcwYjBmZTA4MDIwYyIsInNpZ25hdHVyZV9zaGEyNTYiOiI4MTdhM2JhZTZjNjQ3NmIyZDFiOWE0MTRlYjlmYmI5ODkxOTAyMDdjMTA1ZmEwYWM4MWVhMjQ1MmRlZjhmN2IzIn0 -->
### `client.organizations.createCheckout`

Operation ID: `createCheckout`  
Route: `POST` `/v1/organizations/{organizationId}/billing/checkout`  
Equivalent member: `client.createCheckout`  

#### Signature

```javascript
client.organizations.createCheckout(organizationId, body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | checkoutUrl of the Stripe Checkout Session | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. Autonomous mode: Plan not on sale or subscription exists | none |

#### Canonical required-input example

```json
{
  "body": {
    "planKey": "pro"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.createCheckout("example", {"planKey": "pro"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDaGVja291dCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldEJpbGxpbmciLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRCaWxsaW5nIiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vYmlsbGluZyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiODFkMTFiYmY1ZGE0NWIzZjRkYmU3YzVlZDhlNGFlYWMwNTY4OWQxMDdkNDllZmM2MzkzMWYxZmJkYTMxNTFhOSIsInNpZ25hdHVyZV9zaGEyNTYiOiI1MDQyNThjZDUxZDhhNDVhZWM4YzhkZDk3YTMxNTk1OWVhMDZlMjE0ZjJmMTc0YTVkZGIwZGU5YTVhZGQ3NTliIn0 -->
### `client.organizations.getBilling`

Operation ID: `getBilling`  
Route: `GET` `/v1/organizations/{organizationId}/billing`  
Equivalent member: `client.getBilling`  

#### Signature

```javascript
client.organizations.getBilling(organizationId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Billing status | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.getBilling("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRCaWxsaW5nIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldEJveCIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEJveCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2JveGVzL3tib3hJZH0iLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImNmYTBkMTU4MWY5YTM3ZDZlN2NiNWViNjQ1NDZjYjE5NDczN2QzYTU5YjBiZDlhYjYxZmJhZDNiNWQ4ZTMzY2IiLCJzaWduYXR1cmVfc2hhMjU2IjoiMjZkN2UxMzZkYmZkMDcyZjY4ZGIxOGU1N2E0NzEyNmQ3MGRmNTk5ZDgzYjJhNzAxNDA3YWUwMDMwNmI5YTExOSJ9 -->
### `client.organizations.getBox`

Operation ID: `getBox`  
Route: `GET` `/v1/organizations/{organizationId}/boxes/{boxId}`  
Equivalent member: `client.getBox`  

#### Signature

```javascript
client.organizations.getBox(organizationId, boxId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored box | none |
| `404` | Unknown box | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-d32a-0e84cb70d88a"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.getBox("example", "00000000-0000-0000-d32a-0e84cb70d88a");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldEVudGl0bGVtZW50cyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEVudGl0bGVtZW50cyIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2VudGl0bGVtZW50cyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiYWJlOGE4Y2E4ODI0MjEwOWNmN2I5NTAxNDFkYjUyYzE4ZWYzN2Y1Yjg4M2U2ZTk4ZTJhMGYzZGY3Y2JmYjg3MSIsInNpZ25hdHVyZV9zaGEyNTYiOiI0NDgwZDNhMzI4MWIxOTk4MzdjOTYyNTBlMzA1YzIyNmYyNGY3NGU3YTg2Zjk3OGRlM2JjNDhhODRiMTY0M2YyIn0 -->
### `client.organizations.getEntitlements`

Operation ID: `getEntitlements`  
Route: `GET` `/v1/organizations/{organizationId}/entitlements`  
Equivalent member: `client.getEntitlements`  

#### Signature

```javascript
client.organizations.getEntitlements(organizationId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Entitlements and usage | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.getEntitlements("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRFbnRpdGxlbWVudHMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldEZsZWV0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0RmxlZXQiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9mbGVldCIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiODljOTBmNjgwODNhYjMwZjM1ODY3NDVkZmMyMjFiNWMyNmQ2NjRhOWU1MWU0ZTM5ZDg0MTQ1NTIzMDg3ZGNjNSIsInNpZ25hdHVyZV9zaGEyNTYiOiI5YWU3YTg1OWI0OWU2OGU0ZmI5YjljZjU4MmQxYTFhYWU3MTI2ZmM5Yzc3YTAxZDA2ZGZjZjcwYWY3ZjFiMDJjIn0 -->
### `client.organizations.getFleet`

Operation ID: `getFleet`  
Route: `GET` `/v1/organizations/{organizationId}/fleet`  
Equivalent member: `client.getFleet`  

#### Signature

```javascript
client.organizations.getFleet(organizationId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored fleet | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.getFleet("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRGbGVldCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldEZsZWV0UG9saWN5IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0RmxlZXRQb2xpY3kiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9mbGVldC9wb2xpY3kiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImQ3YzNkN2U5YTU2YTZjM2ZmNWU1NzIzMDkyOWY2Y2I5MGY2M2FkMWVhOGMzMzdkYzUwOTEzM2E4N2IwNjZkNzMiLCJzaWduYXR1cmVfc2hhMjU2IjoiNjA3NDRjY2JhZWE4YzhkZDg2ZmQ1MDI3ODA0NjI5ZWRkNTQxYWE4OTQxMWRmY2VmOTJlNTM4NGNhZTNlNjRhMSJ9 -->
### `client.organizations.getFleetPolicy`

Operation ID: `getFleetPolicy`  
Route: `GET` `/v1/organizations/{organizationId}/fleet/policy`  
Equivalent member: `client.getFleetPolicy`  

#### Signature

```javascript
client.organizations.getFleetPolicy(organizationId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Effective policy | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.getFleetPolicy("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRGbGVldFBvbGljeSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldFBlcnNpc3RlbnRCb3giLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRQZXJzaXN0ZW50Qm94IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vcGVyc2lzdGVudC1ib3hlcy97Ym94SWR9IiwicmVzb3VyY2UiOiJvcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiJlODFlYmU0ZGUzNTY2YjQ3YTI3ZWIwMzEzYTQxZTY2OWNhY2U3Y2E2YjQ0ZWRmYTFlMTYyNGU3ZDRlYzdlZjRkIiwic2lnbmF0dXJlX3NoYTI1NiI6IjhmZDg1NjE3ZDcxNmZkYmFjODU0MTljYjBjMmFlZWNkNTZiNGJkZjkxMDFhN2Q1NmQ3Mzg2ZWJmYzZmYzA5YzcifQ -->
### `client.organizations.getPersistentBox`

Operation ID: `getPersistentBox`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}`  
Equivalent member: `client.getPersistentBox`  

#### Signature

```javascript
client.organizations.getPersistentBox(organizationId, boxId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Private stored record and reserved budget; runtime status is not-metered. | application/json (object) |
| `400` | Invalid UUID or query parameters. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied access or the organization/product/environment differs. | none |
| `404` | No durable box in this exact target scope. | none |
| `503` | Authority or durable record storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-098c-d4f2b24057fb"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.getPersistentBox("example", "00000000-0000-0000-098c-d4f2b24057fb");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQZXJzaXN0ZW50Qm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldFBlcnNpc3RlbnRCb3hQcm92aWRlclVzYWdlIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0UGVyc2lzdGVudEJveFByb3ZpZGVyVXNhZ2UiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9wZXJzaXN0ZW50LWJveGVzL3tib3hJZH0vdXNhZ2UiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjhjMDQ3YjEwZGY1OWE4ZjYxM2FkYWM1ZjNmNThmYmE1YjVjN2Q2NGYyMGRkOWEwZTE5MzY2YjY1NjViMGY3OTQiLCJzaWduYXR1cmVfc2hhMjU2IjoiZmNhNTQ0NDA0ZjMxMDA5MjZjM2ZjZmZmMjFhYWNjMTFjMTQ5NGU0ODJlZjcyYTljNjU3NzliNTg2YzQ3MzQ0MiJ9 -->
### `client.organizations.getPersistentBoxProviderUsage`

Operation ID: `getPersistentBoxProviderUsage`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/usage`  
Equivalent member: `client.getPersistentBoxProviderUsage`  

#### Signature

```javascript
client.organizations.getPersistentBoxProviderUsage(organizationId, boxId, from, to, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `from` | `query` | yes | `string&lt;date-time&gt;` |  |
| `to` | `query` | yes | `string&lt;date-time&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Private provider evidence summary with explicit interval coverage. | application/json (object) |
| `400` | Invalid box ID or bounded UTC window. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied access or target scope differs. | none |
| `404` | No durable box in this exact target scope. | none |
| `413` | Stored evidence exceeds the per-read record bound; select a smaller window. | none |
| `503` | Authority or usage storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-0848-7a89fcbe4ab4"
    },
    {
      "in": "query",
      "name": "from",
      "value": "2026-01-01T00:00:00Z"
    },
    {
      "in": "query",
      "name": "to",
      "value": "2026-01-01T00:00:27Z"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.getPersistentBoxProviderUsage("example", "00000000-0000-0000-0848-7a89fcbe4ab4", "2026-01-01T00:00:00Z", "2026-01-01T00:00:27Z");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQZXJzaXN0ZW50Qm94UHJvdmlkZXJVc2FnZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RCb3hlcyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RCb3hlcyIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2JveGVzIiwicmVzb3VyY2UiOiJvcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiJlYTRlOGUxNzVlMjljNWQwOTMxYThkMzY4NTI4MGQxZDk2Y2JlMDU0NWNhMjExNDQxYjNiNmFiMGI3YjQxZDQ3Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjY4NjRiNjRjNDI0ZDg2NmQ2YjdhMGI3ZmZlNmNhOTgzNWVkNmY0NTU0Nzg2YjM1OGFjN2NkYzIzOTc3ZDU0MDkifQ -->
### `client.organizations.listBoxes`

Operation ID: `listBoxes`  
Route: `GET` `/v1/organizations/{organizationId}/boxes`  
Equivalent member: `client.listBoxes`  

#### Signature

```javascript
client.organizations.listBoxes(organizationId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored boxes with their provider state | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.listBoxes("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Qm94ZXMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RJbnZvaWNlcyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RJbnZvaWNlcyIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2JpbGxpbmcvaW52b2ljZXMiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjkzY2UxZDI0NDkzYTdhMGJkMjdlMWI3OTVhODUwYTNlYmZhNjA4YWM2MDBhODJjNWQwYmMzY2JjZWJmZmIzM2EiLCJzaWduYXR1cmVfc2hhMjU2IjoiMDg5NjU2YzMzYjg1YzljOGE4ZGU1MWEwYTU4YjM3MjhjOTY3MDk2ZGRkY2Y4MGExYTU0NzQ4NzY3ZjhhMDhjMiJ9 -->
### `client.organizations.listInvoices`

Operation ID: `listInvoices`  
Route: `GET` `/v1/organizations/{organizationId}/billing/invoices`  
Equivalent member: `client.listInvoices`  

#### Signature

```javascript
client.organizations.listInvoices(organizationId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Invoices | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.listInvoices("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0SW52b2ljZXMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RNZW1iZXJzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdE1lbWJlcnMiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9tZW1iZXJzIiwicmVzb3VyY2UiOiJvcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiIyZWRmOThjOWM3NmZmYTZlODAwNDEyNmU2MGIxNzI1OGMzOTNkY2UzNDYxY2YzYTFjZWZlNTg1ZWQ4YTIyYzEwIiwic2lnbmF0dXJlX3NoYTI1NiI6ImM5MzU1OWQyNTYxOTkwYjE3MGYzNDUzNjY4YzZjOTQxM2I2YTJmNmFhZGZhYjM1NDU4OTJiYjIwYzVjMWI1MmIifQ -->
### `client.organizations.listMembers`

Operation ID: `listMembers`  
Route: `GET` `/v1/organizations/{organizationId}/members`  
Equivalent member: `client.listMembers`  

#### Signature

```javascript
client.organizations.listMembers(organizationId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored members and the plan seat limit | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.listMembers("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0TWVtYmVycyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RPYnNlcnZlZEJveGVzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdE9ic2VydmVkQm94ZXMiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9vYnNlcnZlZC1ib3hlcyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiZmRjYjJmZWIzNTVkNDI3ZTM4MWY5YmQyMWNkZGNjNzU3NDQxMDc4NDcwMzhkNzFkNWQyOTQ4MTY4OTU0Mzc4NyIsInNpZ25hdHVyZV9zaGEyNTYiOiI1OWU0MTg3YzcxYTI1NGI5ZjFiMTliZjk2ODc5MmQ1ZGNkYzcyZTQ3YTFjNDNiNGMzNjk0OTlhNmI2NGQ0OTY3In0 -->
### `client.organizations.listObservedBoxes`

Operation ID: `listObservedBoxes`  
Route: `GET` `/v1/organizations/{organizationId}/observed-boxes`  
Equivalent member: `client.listObservedBoxes`  

#### Signature

```javascript
client.organizations.listObservedBoxes(organizationId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Up to 100 non-expired client snapshots, private and not cacheable. | application/json (object) |
| `401` | No valid product session. | none |
| `403` | Organization or scope denied. | none |
| `503` | Inventory storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.listObservedBoxes("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0T2JzZXJ2ZWRCb3hlcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RQZXJzaXN0ZW50Qm94T2ZmZXJzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFBlcnNpc3RlbnRCb3hPZmZlcnMiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9wZXJzaXN0ZW50LWJveGVzL29mZmVycyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiMjMzZDNhMjUzNTA5ZjM0ZGNiN2Y1OGRjMDdjMjIyNzgxMjk1ZGU2YTI0MTY5MWI2NDQxZjI3MGY2M2NiMDQ2MyIsInNpZ25hdHVyZV9zaGEyNTYiOiJmMjIxMDNhZDI3NWEzODIwNzlhMmM0ZGM4NjkzNThmN2VkZWI2Y2M2YjcwOGZkNDgxNDJkMjNjNzhlNjBlMWFmIn0 -->
### `client.organizations.listPersistentBoxOffers`

Operation ID: `listPersistentBoxOffers`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes/offers`  
Equivalent member: `client.listPersistentBoxOffers`  

#### Signature

```javascript
client.organizations.listPersistentBoxOffers(organizationId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Private configured offers. | application/json (object) |
| `401` | Product session required. | none |
| `403` | Current read authority denied. | none |
| `503` | Storage or operator offer configuration unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.listPersistentBoxOffers("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0UGVyc2lzdGVudEJveE9mZmVycyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RQZXJzaXN0ZW50Qm94ZXMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0UGVyc2lzdGVudEJveGVzIiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vcGVyc2lzdGVudC1ib3hlcyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiODY5OTBjZTM0YjUyNGRlMTRjZGUwMWQ3MzM4MWRiOTUyMDcyNzRhZTU0NjE2NTJkODFlNDE4MTVjZGEyOWU4NyIsInNpZ25hdHVyZV9zaGEyNTYiOiI3OGE4NmIwMjIxZGIxNzgxZmVhOGVkOTA0ZjRmMDlkZjNlMWIzNjU1OTNjMTVmOGY2MTRmODM3YzNiODRlNmYxIn0 -->
### `client.organizations.listPersistentBoxes`

Operation ID: `listPersistentBoxes`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes`  
Equivalent member: `client.listPersistentBoxes`  

#### Signature

```javascript
client.organizations.listPersistentBoxes(organizationId, limit?, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `limit` | `query` | no | `integer` | Maximum recent records; duplicates and other query parameters are rejected. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Bounded stored records, private and not cacheable. limitReached indicates the requested bound was filled, not an exact total or proof that more records exist. | application/json (object) |
| `400` | Invalid query parameters. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied access or the organization/product/environment differs. | none |
| `503` | Authority or durable record storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.listPersistentBoxes("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0UGVyc2lzdGVudEJveGVzIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnByb3Zpc2lvblBlcnNpc3RlbnRCb3giLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicHJvdmlzaW9uUGVyc2lzdGVudEJveCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L3BlcnNpc3RlbnQtYm94ZXMiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6Ijc3YWIxZmVkN2NlNmM3MDc1ZGY4ZGViZjM1Y2UzNTgyNGQ4NWExYjQxZDVjM2FlYjUzMjFhZTVmMGI3ODc3YTMiLCJzaWduYXR1cmVfc2hhMjU2IjoiZDUyZDM4ZTAyMDQxMmQ3ZjFlMmRlMzg4MzQzYmY5NDdjN2ViYzllYWI4OGViODY4ZjE3N2M0YmQ2MTU2YWFlOCJ9 -->
### `client.organizations.provisionPersistentBox`

Operation ID: `provisionPersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes`  
Equivalent member: `client.provisionPersistentBox`  

#### Signature

```javascript
client.organizations.provisionPersistentBox(organizationId, body, Idempotency_Key?, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `Idempotency-Key` | `header` | no | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Previously recorded running or closed allocation; replayed is true. | none |
| `201` | Provider allocation confirmed and recorded as running. Runtime remains reserved, not measured. | application/json (object) |
| `202` | The reservation is held and the allocation remains unconfirmed. Repeated requests never dispatch create again; operator reconciliation is required. | none |
| `400` | Invalid body, unsupported fields, query parameters or idempotency key. | none |
| `401` | Missing or rejected product session. | none |
| `402` | Missing durable entitlement, bounded allowance or available capacity. | none |
| `403` | Current authority denied the operation or target scope. | none |
| `409` | Idempotency conflict, unresolved prior budget or UTC month boundary. | none |
| `413` | Request body exceeds 4 KiB. | none |
| `503` | Authority, storage, operator offer or independent runtime enforcement unavailable. Missing configuration is refused before reservation. | none |

#### Canonical required-input example

```json
{
  "body": {
    "offer": "example",
    "reserveMinutes": 1
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.provisionPersistentBox("example", {"offer": "example", "reserveMinutes": 1}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwcm92aXNpb25QZXJzaXN0ZW50Qm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnB1dEZsZWV0UG9saWN5IiwibWV0aG9kIjoiUFVUIiwib3BlcmF0aW9uX2lkIjoicHV0RmxlZXRQb2xpY3kiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9mbGVldC9wb2xpY3kiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjNiMzI1ODY5MGJlOTM3NDY3MzE2NDkxMGNiZjgyNWFmNWE2ZTQxMTkzZTM1YTUyNzEzYTViYWU5YWUzOWFjMjgiLCJzaWduYXR1cmVfc2hhMjU2IjoiMmZmMGMxNTRlYTQ2MDEyMWU0NzIxZGMzZDQwY2QzNTAwMWJjMjg2NjJmZDJjYTEwMGQyZjllZjY5Mjk1MGY2ZSJ9 -->
### `client.organizations.putFleetPolicy`

Operation ID: `putFleetPolicy`  
Route: `PUT` `/v1/organizations/{organizationId}/fleet/policy`  
Equivalent member: `client.putFleetPolicy`  

#### Signature

```javascript
client.organizations.putFleetPolicy(organizationId, body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored policy | none |
| `400` | Invalid or unenforced field | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.putFleetPolicy("example", {}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwdXRGbGVldFBvbGljeSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnJlY29uY2lsZVBlcnNpc3RlbnRCb3giLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicmVjb25jaWxlUGVyc2lzdGVudEJveCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L3BlcnNpc3RlbnQtYm94ZXMve2JveElkfS9yZWNvbmNpbGUiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjFhNWMzYmQ0ZjhlNDc3YWUwNGY5YzBmZTU3MWY3NjlhNzEwMmUzNDc1MzM4ZDY5MDI0ZTI0YzE1ZTkwZGYzNzgiLCJzaWduYXR1cmVfc2hhMjU2IjoiOWNhYjUzMjc2ZTRkMjJmODY3YjdiOTYyZWFlOGE4Y2E5YjVjNjdmNmE1N2Y4YTg4ZGQ2YmU0ZDljMjRhOTZiNyJ9 -->
### `client.organizations.reconcilePersistentBox`

Operation ID: `reconcilePersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/reconcile`  
Equivalent member: `client.reconcilePersistentBox`  

#### Signature

```javascript
client.organizations.reconcilePersistentBox(organizationId, boxId, body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Confirmed operation or replayed receipt. | application/json (object) |
| `202` | Operation remains unconfirmed; reconcile its operation ID without repeating the mutation. | application/json (object) |
| `400` | Invalid bounded lifecycle request. | none |
| `401` | Product session required. | none |
| `402` | Durable feature or quota denied. | none |
| `403` | Fresh operation authority denied. | none |
| `404` | Box or operation missing in the exact organization and deployment. | none |
| `409` | Conflicting operation, unresolved evidence or unavailable runtime budget. | none |
| `503` | Authority, storage or matching operator adapter unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {
    "operationId": "00000000-0000-0000-f735-3d332872b96e"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-a264-3ce9cdfbbeff"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.reconcilePersistentBox("example", "00000000-0000-0000-a264-3ce9cdfbbeff", {"operationId": "00000000-0000-0000-f735-3d332872b96e"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWNvbmNpbGVQZXJzaXN0ZW50Qm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnJlbW92ZU1lbWJlciIsIm1ldGhvZCI6IkRFTEVURSIsIm9wZXJhdGlvbl9pZCI6InJlbW92ZU1lbWJlciIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L21lbWJlcnMve3VzZXJJZH0iLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImMzOTI2YTZkNTY1Y2NhZmMwOGFjYTYzNzdjYTQ1Yjg0N2YzZDY5ZTc0Yjg5NjcwMDQ1ZDNlNzc3YmUyZDU3NDYiLCJzaWduYXR1cmVfc2hhMjU2IjoiMjgxMzA3OTVjZmZhMDljZmY4ZWI1ZmQ3MDBjMDYzMDk5ZWRiZGVjMzc0NzZkMDZlYWJkNzExMjQ5Y2ZhZmQ0MCJ9 -->
### `client.organizations.removeMember`

Operation ID: `removeMember`  
Route: `DELETE` `/v1/organizations/{organizationId}/members/{userId}`  
Equivalent member: `client.removeMember`  

#### Signature

```javascript
client.organizations.removeMember(organizationId, userId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `userId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Removed | none |
| `404` | Unknown member | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "userId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.removeMember("example", "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZW1vdmVNZW1iZXIifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnN0YXJ0UGVyc2lzdGVudEJveCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJzdGFydFBlcnNpc3RlbnRCb3giLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9wZXJzaXN0ZW50LWJveGVzL3tib3hJZH0vc3RhcnQiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjAyMDI0ODU1ZGI5ZTRiYTYyZWRkNjgwZDEyYWJkNGMxMDgxODk1OGIxYTkwMzg4MWY2MWQwMjhkMmYyMGE5ZGIiLCJzaWduYXR1cmVfc2hhMjU2IjoiNGUzZTgxNWM2ZDNmZjY3NmQ3NGEyZjljNWUxNDc1MmJiNjFiZjU3MzAwMTAwNjIzN2NjYmNiM2M1OTA1NzQyYiJ9 -->
### `client.organizations.startPersistentBox`

Operation ID: `startPersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/start`  
Equivalent member: `client.startPersistentBox`  

#### Signature

```javascript
client.organizations.startPersistentBox(organizationId, boxId, body, Idempotency_Key?, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `Idempotency-Key` | `header` | no | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Confirmed operation or replayed receipt. | application/json (object) |
| `202` | Operation remains unconfirmed; reconcile its operation ID without repeating the mutation. | application/json (object) |
| `400` | Invalid bounded lifecycle request. | none |
| `401` | Product session required. | none |
| `402` | Durable feature or quota denied. | none |
| `403` | Fresh operation authority denied. | none |
| `404` | Box or operation missing in the exact organization and deployment. | none |
| `409` | Conflicting operation, unresolved evidence or unavailable runtime budget. | none |
| `503` | Authority, storage or matching operator adapter unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {
    "reserveMinutes": 1
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-d7e8-d81c5e30ed9a"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.startPersistentBox("example", "00000000-0000-0000-d7e8-d81c5e30ed9a", {"reserveMinutes": 1}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdGFydFBlcnNpc3RlbnRCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnN0b3BCb3giLCJtZXRob2QiOiJERUxFVEUiLCJvcGVyYXRpb25faWQiOiJzdG9wQm94IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vYm94ZXMve2JveElkfSIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiZThiOTY2YzYxMzQ2NmNiMzM2MjNkZGNhZDQyYzIxMWJjOTUxMDU2OGNlZjg2MDc2ZjYxY2I2NjBkY2YyNjE0YyIsInNpZ25hdHVyZV9zaGEyNTYiOiJmZWI5M2Y2NjAyYzQxN2IyNzhiOWJhOTE2NTU1NWJjOTNjYjY0NTk4NTM2NTEzZDM1M2NmZTM5MTA3MTBhNTllIn0 -->
### `client.organizations.stopBox`

Operation ID: `stopBox`  
Route: `DELETE` `/v1/organizations/{organizationId}/boxes/{boxId}`  
Equivalent member: `client.stopBox`  

#### Signature

```javascript
client.organizations.stopBox(organizationId, boxId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stopped | none |
| `502` | The provider refused; state unchanged | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-265e-7c895c60153e"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.stopBox("example", "00000000-0000-0000-265e-7c895c60153e");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdG9wQm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnN0b3BQZXJzaXN0ZW50Qm94IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InN0b3BQZXJzaXN0ZW50Qm94IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vcGVyc2lzdGVudC1ib3hlcy97Ym94SWR9L3N0b3AiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImUwZThkNDRlYWM1NTg3YzNhOWY0YTRkZmMyNTJmMzYxOGFiODdlM2Q4YTdlMGY4NGE3ZTRmYWFmYTk5Y2VjYjgiLCJzaWduYXR1cmVfc2hhMjU2IjoiM2ExNDY1MzVhMDU0ZTEwNzY3MDYzOGJhNzRkNzlkMTVlNDk5ZTJkMDMxNWMyODg0MWUxMGE0NTIwMDMxMGM4NSJ9 -->
### `client.organizations.stopPersistentBox`

Operation ID: `stopPersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/stop`  
Equivalent member: `client.stopPersistentBox`  

#### Signature

```javascript
client.organizations.stopPersistentBox(organizationId, boxId, body, Idempotency_Key?, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `Idempotency-Key` | `header` | no | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Confirmed operation or replayed receipt. | application/json (object) |
| `202` | Operation remains unconfirmed; reconcile its operation ID without repeating the mutation. | application/json (object) |
| `400` | Invalid bounded lifecycle request. | none |
| `401` | Product session required. | none |
| `402` | Durable feature or quota denied. | none |
| `403` | Fresh operation authority denied. | none |
| `404` | Box or operation missing in the exact organization and deployment. | none |
| `409` | Conflicting operation, unresolved evidence or unavailable runtime budget. | none |
| `503` | Authority, storage or matching operator adapter unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-978f-a93165cf6579"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.stopPersistentBox("example", "00000000-0000-0000-978f-a93165cf6579", {}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdG9wUGVyc2lzdGVudEJveCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnN5bmNPYnNlcnZlZEJveGVzIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InN5bmNPYnNlcnZlZEJveGVzIiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vb2JzZXJ2ZWQtYm94ZXMvc3luYyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiNDc1MDBlYzFjMzFkZDU4YzM3YmY1OTQwYjBiMWIzNDIxOTY0Mzk4MWI5NWQ5ODQ2NmVlNjcyZDE0ODE3YzJjMiIsInNpZ25hdHVyZV9zaGEyNTYiOiIzNzExYWNjNzk3YTY0ZmJkMjRkNmQyOGNhYjg3M2E3MTU1NGQwNzA5MTkzNTNmZDYwMjY3OGM1N2FmMDA4OTBmIn0 -->
### `client.organizations.syncObservedBoxes`

Operation ID: `syncObservedBoxes`  
Route: `POST` `/v1/organizations/{organizationId}/observed-boxes/sync`  
Equivalent member: `client.syncObservedBoxes`  

#### Signature

```javascript
client.organizations.syncObservedBoxes(organizationId, body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Snapshot accepted; private and not cacheable. | application/json (object) |
| `400` | Invalid observation snapshot. | none |
| `401` | No valid product session. | none |
| `403` | Organization or scope denied. | none |
| `413` | Snapshot exceeds 64 KiB. | none |
| `503` | Inventory storage unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {
    "boxes": [
      {
        "boxId": "example",
        "kind": "provider-list",
        "provider": "example",
        "state": "running"
      }
    ],
    "sourceId": "00000000-0000-0000-ae61-93cfab8e5e4b"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.syncObservedBoxes("example", {"boxes": [{"boxId": "example", "kind": "provider-list", "provider": "example", "state": "running"}], "sourceId": "00000000-0000-0000-ae61-93cfab8e5e4b"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzeW5jT2JzZXJ2ZWRCb3hlcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnVwc2VydE1lbWJlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJ1cHNlcnRNZW1iZXIiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9tZW1iZXJzIiwicmVzb3VyY2UiOiJvcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiIzNzQwYjg3YjQ2MzI5NTc3ZGYxN2U0M2MzYzNiZDkyMDdiY2U0YTkzYWE0MDQzZGY5YTA1YjJlYTU5ZDg5YmRlIiwic2lnbmF0dXJlX3NoYTI1NiI6ImFkMTVmYTUxMGI5NjNlMjVhOTRhZTc3YWQ1MTlhYjk5YWM4ZWY2ZDFhZTFlZTJjNWFjZjhmMGFkZjJjZTRjNWQifQ -->
### `client.organizations.upsertMember`

Operation ID: `upsertMember`  
Route: `POST` `/v1/organizations/{organizationId}/members`  
Equivalent member: `client.upsertMember`  

#### Signature

```javascript
client.organizations.upsertMember(organizationId, body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Member updated | none |
| `201` | Member added | none |
| `402` | Seat limit reached or entitlement missing | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example-f35c@example.test",
    "role": "owner"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.organizations.upsertMember("example", {"email": "example-f35c@example.test", "role": "owner"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ1cHNlcnRNZW1iZXIifQ -->

## Resource `plans`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJwbGFucy5nZXQiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRQbGFucyIsInBhdGgiOiIvdjEvcGxhbnMiLCJyZXNvdXJjZSI6InBsYW5zIiwic2VjdGlvbl9zaGEyNTYiOiI2YzhjNGM3YmFlZmZlMzc3NDIyY2EwNGI5YmVmNGFmNzdkNDIzZGIzYjBmZjA3Mzc3ZDY4Y2NlODk2ODRjODJiIiwic2lnbmF0dXJlX3NoYTI1NiI6IjM1NmE3YzZmZWMzOTI1YmViMzdjNzllNzA2YmUyYzYwZTQyN2Q3YTdmYWNmYzA3NDgwNDU2N2FkM2U0YTZjOWMifQ -->
### `client.plans.get`

Operation ID: `getPlans`  
Route: `GET` `/v1/plans`  
Equivalent member: `client.getPlans`  

#### Signature

```javascript
client.plans.get(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.plans.get();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQbGFucyJ9 -->

## Resource `telemetry`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0ZWxlbWV0cnkuaW5nZXN0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImluZ2VzdFRlbGVtZXRyeSIsInBhdGgiOiIvdjEvdGVsZW1ldHJ5L2luZ2VzdCIsInJlc291cmNlIjoidGVsZW1ldHJ5Iiwic2VjdGlvbl9zaGEyNTYiOiI1MDU0OTlmNjU4NmY5ODI4YmIyNGI2NmQ3NzRhM2E0OGZlMWNhNTVmZGQ4ZjM0NTk0Nzk2ZGFmN2ExOGNmNzViIiwic2lnbmF0dXJlX3NoYTI1NiI6IjEyYjdjMjI3MTY3NDQ2OTUwMTU2ZDhjYTAxOTkwNDk4N2EwZTdlNDlkNDRiY2JlOTdjZjdhYjU1YTM0ZTNmNDcifQ -->
### `client.telemetry.ingest`

Operation ID: `ingestTelemetry`  
Route: `POST` `/v1/telemetry/ingest`  
Equivalent member: `client.ingestTelemetry`  

#### Signature

```javascript
client.telemetry.ingest(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Stored | none |
| `400` | Invalid event | none |
| `401` | License required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |
| `413` | Body too large | none |
| `503` | Ingestion not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.telemetry.ingest({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJpbmdlc3RUZWxlbWV0cnkifQ -->

## Resource `waitlist`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5saXN0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFdhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6IjU5MjIyODc5YTQ0NjEyYjQ1YjVhNjBkYjY3MWIwNjI4ZTgzNzNlNjY5YTQ4MTFhMDBjZTU1ZTM0MWM0MDUyOWQiLCJzaWduYXR1cmVfc2hhMjU2IjoiNTJlNDhjMmNlNGEzZGU4YzYxOWJlZWY0MDJjMzFhYjIzYTI5ZDRiYjBjZDczMzRmMjNhNzdkZTg3MjZhMWE2MyJ9 -->
### `client.waitlist.list`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  
Equivalent member: `client.listWaitlist`  

#### Signature

```javascript
client.waitlist.list(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Requests | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.waitlist.list();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5yZXF1ZXN0QWNjZXNzIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InJlcXVlc3RBY2Nlc3MiLCJwYXRoIjoiL3YxL3dhaXRsaXN0IiwicmVzb3VyY2UiOiJ3YWl0bGlzdCIsInNlY3Rpb25fc2hhMjU2IjoiYzI1NWZhZTZkNGMxZmYwMDFmYTAxYzhkYTdkMmQxYjk0YTFhNTRkYWQwYjU1ZTk0MDllYTA4MWUyZmQwYjIwYSIsInNpZ25hdHVyZV9zaGEyNTYiOiI0YTljMDQ3NjlmY2VhNTgyZDc4YjllZTczYjBiNDY3ZmUzZWE5OWM3ZjdiZDc3ZTQ3OGU4M2YzMTQ3MWY3MTdjIn0 -->
### `client.waitlist.requestAccess`

Operation ID: `requestAccess`  
Route: `POST` `/v1/waitlist`  
Equivalent member: `client.requestAccess`  

#### Signature

```javascript
client.waitlist.requestAccess(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `202` | Received | none |
| `400` | Invalid email | none |
| `413` | Body too large | none |
| `429` | Rate limited | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.waitlist.requestAccess({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZXF1ZXN0QWNjZXNzIn0 -->

## Resource `workspaces`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLmNsb3NlSG9zdGVkIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNsb3NlSG9zdGVkV29ya3NwYWNlIiwicGF0aCI6Ii92MS93b3Jrc3BhY2VzL3t3b3Jrc3BhY2VJZH0vY2xvc2UiLCJyZXNvdXJjZSI6IndvcmtzcGFjZXMiLCJzZWN0aW9uX3NoYTI1NiI6IjRlZDA2MzNmY2QyMzcwY2UxNTJiYTY3NzVlMjRmMDZhZmU0YTJkMDY2ZGViN2NiYzc0Mjc5Mjc3ZTkxMGRjMmYiLCJzaWduYXR1cmVfc2hhMjU2IjoiN2RlMDIyMGI2ZDdhYmQzZWZiOWZlMWJkNGJjMjBmNDk4OTUzMDI5MGViNzkxNWVkZDhlMmYxYmVlNTA5YjA2YyJ9 -->
### `client.workspaces.closeHosted`

Operation ID: `closeHostedWorkspace`  
Route: `POST` `/v1/workspaces/{workspaceId}/close`  
Equivalent member: `client.closeHostedWorkspace`  

#### Signature

```javascript
client.workspaces.closeHosted(workspaceId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-6658-e129a559a4dd"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.workspaces.closeHosted("00000000-0000-0000-6658-e129a559a4dd");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjbG9zZUhvc3RlZFdvcmtzcGFjZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLmdldEhvc3RlZCIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEhvc3RlZFdvcmtzcGFjZSIsInBhdGgiOiIvdjEvd29ya3NwYWNlcy97d29ya3NwYWNlSWR9IiwicmVzb3VyY2UiOiJ3b3Jrc3BhY2VzIiwic2VjdGlvbl9zaGEyNTYiOiI0OTg2NjhhZmU1NmE1ZGQ5OGNkOWNlYTY4NTFkMWIyNjhjM2ZiMGJmZGE5NzBiOTNjNmRlYWI3MWNhMTVmZjA4Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImM1NTY3MzFkYjI0ZjBjZWFmMWRhYjkwZDRkYThjMDA0MmQ2MTFkODU2MjQ2OTk5YzQ5ZjA1NmFjYTBkMWNmZDIifQ -->
### `client.workspaces.getHosted`

Operation ID: `getHostedWorkspace`  
Route: `GET` `/v1/workspaces/{workspaceId}`  
Equivalent member: `client.getHostedWorkspace`  

#### Signature

```javascript
client.workspaces.getHosted(workspaceId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-dd2f-cd2edd1eeb24"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.workspaces.getHosted("00000000-0000-0000-dd2f-cd2edd1eeb24");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIb3N0ZWRXb3Jrc3BhY2UifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLmdldEhvc3RlZE9wZXJhdGlvbiIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEhvc3RlZFdvcmtzcGFjZU9wZXJhdGlvbiIsInBhdGgiOiIvdjEvd29ya3NwYWNlcy97d29ya3NwYWNlSWR9L29wZXJhdGlvbnMve29wZXJhdGlvbklkfSIsInJlc291cmNlIjoid29ya3NwYWNlcyIsInNlY3Rpb25fc2hhMjU2IjoiMzdiODk0OGVjYWYxZDBkN2I4ODZlY2E0YzcwNDZiZTg4MjhmNzZlMDZjNDgyMTZmNWNlZWE2NWU0OWE2MjJiNSIsInNpZ25hdHVyZV9zaGEyNTYiOiI3MTZjZTEyMmU5NjU4NjUyNDZkYTFhY2QwNjhiNzVhMDMxZGMxYmFlODIxY2E2ZmQ4YWE0MzY1NjY2MGEwNDhkIn0 -->
### `client.workspaces.getHostedOperation`

Operation ID: `getHostedWorkspaceOperation`  
Route: `GET` `/v1/workspaces/{workspaceId}/operations/{operationId}`  
Equivalent member: `client.getHostedWorkspaceOperation`  

#### Signature

```javascript
client.workspaces.getHostedOperation(workspaceId, operationId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `operationId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-7261-284a8b699ebd"
    },
    {
      "in": "path",
      "name": "operationId",
      "value": "00000000-0000-0000-5ba1-19fa55640b6d"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.workspaces.getHostedOperation("00000000-0000-0000-7261-284a8b699ebd", "00000000-0000-0000-5ba1-19fa55640b6d");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIb3N0ZWRXb3Jrc3BhY2VPcGVyYXRpb24ifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLmdldEhvc3RlZFNvdXJjZSIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEhvc3RlZFdvcmtzcGFjZVNvdXJjZSIsInBhdGgiOiIvdjEvd29ya3NwYWNlcy97d29ya3NwYWNlSWR9L3NvdXJjZSIsInJlc291cmNlIjoid29ya3NwYWNlcyIsInNlY3Rpb25fc2hhMjU2IjoiMGI4NzQ3ODg0YmY1ZWM4N2MxZmVmZGIwMTA4MjUzMDQzNDMwYzA3NDFjZmJlYTUzN2FiOTNkMzgwM2ZjZDViMSIsInNpZ25hdHVyZV9zaGEyNTYiOiIxZjY3MGQxMDRkZmNhNjZiN2QwODY0Y2ZlODhiNTViZTBmMzY5OTFhYzZiNzFmMTA2ZGM2NTlhMjAyYTE4NDYyIn0 -->
### `client.workspaces.getHostedSource`

Operation ID: `getHostedWorkspaceSource`  
Route: `GET` `/v1/workspaces/{workspaceId}/source`  
Equivalent member: `client.getHostedWorkspaceSource`  

#### Signature

```javascript
client.workspaces.getHostedSource(workspaceId, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-43c8-d895a22336ed"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.workspaces.getHostedSource("00000000-0000-0000-43c8-d895a22336ed");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIb3N0ZWRXb3Jrc3BhY2VTb3VyY2UifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLmxpc3RIb3N0ZWQiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0SG9zdGVkV29ya3NwYWNlcyIsInBhdGgiOiIvdjEvd29ya3NwYWNlcyIsInJlc291cmNlIjoid29ya3NwYWNlcyIsInNlY3Rpb25fc2hhMjU2IjoiNDA3NjIyZGVlZWE2MTA1M2M2NzRlNDcyNzg4NjI3MmNjYzcyYTc0ZmI3YWZmMjE5ZDQ4ZTgyMjY1NDk2NjJmNCIsInNpZ25hdHVyZV9zaGEyNTYiOiJkMTlhZWJhZDM4OWQ5ZGYzOTRkMWE3YTVhNWNiMDA3MjQyZDExMzg5NDczNWVkZGMyOGJiMTliYjE0MjgxMGJiIn0 -->
### `client.workspaces.listHosted`

Operation ID: `listHostedWorkspaces`  
Route: `GET` `/v1/workspaces`  
Equivalent member: `client.listHostedWorkspaces`  

#### Signature

```javascript
client.workspaces.listHosted(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.workspaces.listHosted();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0SG9zdGVkV29ya3NwYWNlcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLm9wZW5Ib3N0ZWQiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoib3Blbkhvc3RlZFdvcmtzcGFjZSIsInBhdGgiOiIvdjEvd29ya3NwYWNlcyIsInJlc291cmNlIjoid29ya3NwYWNlcyIsInNlY3Rpb25fc2hhMjU2IjoiNTc3NjNkODMzOGNmMWRhZjhjNmZjMWM1MzJjYzg2MzZmZWU2Yzk1MDdlODUzYzM1NjJlZTljNGQ4YWM0ZDRhZSIsInNpZ25hdHVyZV9zaGEyNTYiOiJhZWE5YmMzZmU4YTMyYzBmMWY5NmFhZjU0ZWM1NWY5OWIxMTIzNTEyZTZmYmJlNWMzZTQyYzM4YTJjNTYxYTA0In0 -->
### `client.workspaces.openHosted`

Operation ID: `openHostedWorkspace`  
Route: `POST` `/v1/workspaces`  
Equivalent member: `client.openHostedWorkspace`  

#### Signature

```javascript
client.workspaces.openHosted(body, Idempotency_Key?, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `Idempotency-Key` | `header` | no | `string` | Required here or in the idempotencyKey body field. Replays never allocate or execute again. |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `201` | Prepared workspace; source and provider allocation recorded durably | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.workspaces.openHosted({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJvcGVuSG9zdGVkV29ya3NwYWNlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLnJlY292ZXJIb3N0ZWQiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicmVjb3Zlckhvc3RlZFdvcmtzcGFjZSIsInBhdGgiOiIvdjEvd29ya3NwYWNlcy97d29ya3NwYWNlSWR9L3JlY292ZXIiLCJyZXNvdXJjZSI6IndvcmtzcGFjZXMiLCJzZWN0aW9uX3NoYTI1NiI6IjY3OTIxMDlmMzVhZDhlMjU4YjRhOTQ4NGZjNmZiZjk4NDdiMDI2MWMxMjZiYzExMWYyOGNjOGJlOWEwZDI4MWQiLCJzaWduYXR1cmVfc2hhMjU2IjoiOGUxNGQ1Zjk2ZWJjMzEzNmE3MjE1ZjVkMGM3ZDNjZWIwMzM0ZTFkZGJmNGZjNDM4MTVlYzdlMTVmYWVhYTk2MyJ9 -->
### `client.workspaces.recoverHosted`

Operation ID: `recoverHostedWorkspace`  
Route: `POST` `/v1/workspaces/{workspaceId}/recover`  
Equivalent member: `client.recoverHostedWorkspace`  

#### Signature

```javascript
client.workspaces.recoverHosted(workspaceId, body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `202` | No verified terminal receipt yet; workspace remains unavailable for new commands | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "body": {
    "operationId": "00000000-0000-0000-d4ac-b0b84827b6d9"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-973a-c9ae0260973d"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.workspaces.recoverHosted("00000000-0000-0000-973a-c9ae0260973d", {"operationId": "00000000-0000-0000-d4ac-b0b84827b6d9"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWNvdmVySG9zdGVkV29ya3NwYWNlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLnJ1bkhvc3RlZCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJydW5Ib3N0ZWRXb3Jrc3BhY2UiLCJwYXRoIjoiL3YxL3dvcmtzcGFjZXMve3dvcmtzcGFjZUlkfS9ydW4iLCJyZXNvdXJjZSI6IndvcmtzcGFjZXMiLCJzZWN0aW9uX3NoYTI1NiI6IjcwMmVlOTQ3MGU2N2QzZDgxNWViNjYxNmEzYzdiNTJjZWQ3ZGQ2NDg4NmQ2NDc5NTlkMTU2Y2Q2YmIxNTQ2NjUiLCJzaWduYXR1cmVfc2hhMjU2IjoiNzQ4MDkwYjk1NzAyYzBiODcyODJhZTRjMTQ1ZGYxODAzN2E2MTI3ZDNkNGIxNGVhZmIxNTVhOGU3NGE4YmQzZSJ9 -->
### `client.workspaces.runHosted`

Operation ID: `runHostedWorkspace`  
Route: `POST` `/v1/workspaces/{workspaceId}/run`  
Equivalent member: `client.runHostedWorkspace`  

#### Signature

```javascript
client.workspaces.runHosted(workspaceId, body, Idempotency_Key?, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `Idempotency-Key` | `header` | no | `string` | Required here or in the idempotencyKey body field. Replays never allocate or execute again. |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `202` | Running or uncertain operation; inspect or explicitly recover, never resend with a new key | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "body": {
    "command": "example"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-4862-6c003dd1756b"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.workspaces.runHosted("00000000-0000-0000-4862-6c003dd1756b", {"command": "example"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJydW5Ib3N0ZWRXb3Jrc3BhY2UifQ -->

