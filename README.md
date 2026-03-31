# cusp-proto

Language-agnostic gRPC/Protobuf schema definitions for Cusp services.

## Structure

```
com/cusp/v1/
  card/
    card_service.proto        # Card listing and search
    user_card_service.proto   # User card management
  reward/
    reward_service.proto      # Reward calculation
```

## Usage

### As a Git Submodule

```bash
git submodule add https://github.com/cusp-core/cusp-proto.git proto
```

### Kotlin/Java (Gradle)

Point the protobuf plugin source set at the submodule directory:

```kotlin
sourceSets {
    main {
        proto { srcDir("proto") }
    }
}
```

### Python

```bash
pip install grpcio-tools
python -m grpc_tools.protoc \
  -I proto \
  --python_out=./generated \
  --grpc_python_out=./generated \
  proto/com/cusp/v1/card/card_service.proto
```

### Go

```bash
protoc -I proto \
  --go_out=./generated --go_opt=paths=source_relative \
  --go-grpc_out=./generated --go-grpc_opt=paths=source_relative \
  proto/com/cusp/v1/card/card_service.proto
```
