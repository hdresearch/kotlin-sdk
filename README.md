# Orchestrator Control Plane API Kotlin SDK

> vers-sdk v0.1.8

It is generated with [Sterling](https://github.com/hdresearch/sterling).

## Installation

### Gradle (Kotlin DSL)

```kotlin
dependencies {
    implementation("sh.vers.sdk:vers-sdk:0.1.8")
}
```

### Gradle (Groovy)

```groovy
implementation 'sh.vers.sdk:vers-sdk:0.1.8'
```

## Usage

```kotlin
import sh.vers.sdk.VersSdkClient
import kotlinx.coroutines.runBlocking

fun main() = runBlocking {
    val client = VersSdkClient(
        apiKey = "your-api-key",
    )

    client.use {
        // Call API methods
        // val response = it.someOperation()
    }
}
```

## Configuration

| Parameter    | Environment Variable | Default         | Description                      |
|-------------|---------------------|-----------------|----------------------------------|
| `baseUrl`   | `VERS_BASE_URL`     | `https://api.vers.sh`  | API base URL                     |
| `apiKey`    | `VERS_API_KEY`      | —               | Bearer token for authentication  |
| `maxRetries`| —                   | `2`             | Maximum retry attempts           |
| `timeout`   | —                   | `30`            | Request timeout in seconds       |

## Error Handling

```kotlin
import sh.vers.sdk.*

try {
    val response = client.someOperation()
} catch (e: NotFoundError) {
    println("Resource not found: ${e.status}")
} catch (e: RateLimitError) {
    println("Rate limited, retry later")
} catch (e: APIError) {
    println("API error: ${e.status} - ${e.message}")
} catch (e: APIConnectionError) {
    println("Connection failed: ${e.message}")
}
```

## Logging

Set the `VERS_LOG` environment variable to control log verbosity:

- `debug` — all request/response details
- `info` — retries and important events
- `warn` — warnings (default)
- `error` — errors only
- `off` — no logging

## License

Apache-2.0
