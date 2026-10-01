# Running Tests

## Prerequisites

You need a Box access token to run the tests against the live Box API. To run them against the bundled mock service, no credentials are needed.

## Test environments

Tests run against a local mock of the Box Platform API (`tests/mock_service.bal`, listening on port 9090) by default, and against `https://api.box.com/2.0` when `IS_LIVE_SERVER` is `true`.

| Variable | Description |
|---|---|
| `IS_LIVE_SERVER` | Set to `true` to run against the live Box API. Defaults to the mock service. |
| `BOX_ACCESS_TOKEN` | A Box access token or developer token. Read only when `IS_LIVE_SERVER` is `true`. |

The `live_tests` group contains only read-only calls. Tests that create or delete content run against the mock only.

## Running the tests

Run the mock tests:

```bash
bal test --groups mock_tests
```

Run the live tests:

```bash
export IS_LIVE_SERVER=true
export BOX_ACCESS_TOKEN=<access-token>
bal test --groups live_tests
```

## Test coverage

The suite covers 25 operations: file operations (get, update, copy), folder operations (get, create, update, delete, list items), comments (create, get, list), tasks (create, get), users (list, get current, create, get, delete), groups (create, get, remove), collaborations, webhooks, web links and search.
