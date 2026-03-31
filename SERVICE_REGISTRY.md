# Service Registry

Maps each proto service to the microservice that implements it.

| Proto Service | Implemented By | Default Port | Source |
|---|---|---|---|
| `CardService` | `core-service` | 9090 | `com/cusp/v1/card/card_service.proto` |
| `UserCardService` | `core-service` | 9090 | `com/cusp/v1/card/user_card_service.proto` |
| `RewardService` | `core-service` | 9090 | `com/cusp/v1/reward/reward_service.proto` |

## Client Configuration

Each consumer should resolve service addresses via environment variables, not hardcoded values.

### Kotlin/Spring (grpc-spring-boot-starter)

```yaml
grpc:
  client:
    core-service:
      address: ${CORE_SERVICE_HOST:localhost}:${CORE_SERVICE_GRPC_PORT:9090}
      negotiation-type: plaintext  # use TLS in production
```

### Python (grpcio)

```python
import os
import grpc

host = os.environ.get("CORE_SERVICE_HOST", "localhost")
port = os.environ.get("CORE_SERVICE_GRPC_PORT", "9090")
channel = grpc.insecure_channel(f"{host}:{port}")
```

## Environments

| Environment | Host | gRPC Port |
|---|---|---|
| Local | `localhost` | `9090` |
| Staging | `13.127.47.166` | `9090` |
| Production | TBD | TBD |
