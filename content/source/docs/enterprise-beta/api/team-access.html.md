---
layout: enterprise2
page_title: "Team Acccess - API Docs - Terraform Enterprise Beta"
sidebar_current: "docs-enterprise2-api-team-access"
---

# Team access API

The Team access APIs are used to associates a Team to a Workspaces with permissions. A single `team-workspace` resource contains the relationship to the Team and Workspace, and it contains the privelege the Team has on the Workspace.

-> **Note**: These API Endpoints are not yet available on `https://atlas.hashicorp.com/api/v2/` and may be subject to change before they are made available.

## List Team access to Workspaces

| Method | Path           |
| :----- | :------------- |
| GET | /team_workspaces |

### Parameters

- `?filter[organization][username]` (`string: <required>`) - The organization username
- `?filter[workspace][name]` (`string: <required>`) - The worksapce name
- `?filter[team][id]` (`string: <required>`) - Team ID

### Sample Request

```shell
$ curl \
  --header "Authorization: Bearer $ATLAS_TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request GET \
  https://atlas.hashicorp.com/api/v2/team_workspaces?filter[organization][username]=hashicorp&filter[workspace][name]=example&filter[team][id]=1
```

### Sample Response

```json
{}
```

## Add Team access to a Workspace

| Method | Path           |
| :----- | :------------- |
| POST | /team_workspaces |

### Parameters

- `filter[organization][username]` (`string: <required>`) - The organization username
- `filter[workspace][name]` (`string: <required>`) - The worksapce name
- `filter[team][id]` (`string: <required>`) - Team ID
- `permission` (`string: <required>`) - ...

### Sample Payload

```json
{
  "data": {
    "type": "team-workspaces",
    "attributes": { "permission": "read" }
  }
}
```

### Sample Request

```shell
$ curl \
  --header "Authorization: Bearer $ATLAS_TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request POST \
  --data @payload.json \
  https://atlas.hashicorp.com/api/v2/team_workspaces?filter[organization][username]=hashicorp&filter[workspace][name]=example&filter[team][id]=1
```

### Sample Response

```json
{
  "data": {
    "type": "team-workspaces",
    "id": "1",
    "attributes": { "permission": "read" }
  }
}
```

## Show Team access to a Workspace

| Method | Path           |
| :----- | :------------- |
| GET | /team_workspaces/:id |

### Parameters

- `id` (`string: <required>`) - ...

### Sample Request

```shell
$ curl \
  --header "Authorization: Bearer $ATLAS_TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request GET \
  https://atlas.hashicorp.com/api/v2/team_workspaces/257525
```

### Sample Response

```json
{
  "data": {
    "type": "team-workspaces",
    "id": "1",
    "attributes": { "permission": "read" }
  }
}
```

## Update Team access to a Workspace

| Method | Path           |
| :----- | :------------- |
| PATCH | /team_workspaces/:id |

### Parameters

- `id` (`string: <required>`) - ...

### Sample Payload

```json
{
  "data": {
    "type": "team-workspaces",
    "id": "1",
    "attributes": { "permission": "read" }
  }
}
```

### Sample Request

```shell
$ curl \
  --header "Authorization: Bearer $ATLAS_TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request PATCH \
  --data @payload.json \
  https://atlas.hashicorp.com/api/v2/team_workspaces/257525
```

### Sample Response

```json
{
  "data": {
    "type": "team-workspaces",
    "id": "1",
    "attributes": { "permission": "read" }
  }
}
```

## Remove Team access to a Workspace

| Method | Path           |
| :----- | :------------- |
| DELETE | /team_workspaces/:id |

### Parameters

- `id` (`string: <required>`) - The ID of the Teams Access to a Workspace

### Sample Request

```shell
$ curl \
  --header "Authorization: Bearer $ATLAS_TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request DELETE \
  https://atlas.hashicorp.com/api/v2/team_workspaces/257525
```

