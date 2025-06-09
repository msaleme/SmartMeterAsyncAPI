# Smart Meter AsyncAPI

An AsyncAPI specification for real-time smart meter telemetry data consumption.

## Overview

This repository contains an AsyncAPI 2.6.0 specification that defines an event-driven API for consuming smart meter reading data. The API enables real-time monitoring and processing of utility meter readings through asynchronous messaging.

## API Specification

The API defines a single channel for smart meter data:

- **Channel**: `smartmeter/reading`
- **Operation**: Subscribe to meter readings
- **Content Type**: `application/json`

### Message Format

Each smart meter reading message contains:

```json
{
  "meterId": "string",
  "timestamp": "2024-01-01T12:00:00Z",
  "reading": 1234.56
}
```

| Field | Type | Description |
|-------|------|-------------|
| `meterId` | string | Unique identifier for the smart meter |
| `timestamp` | string (date-time) | ISO 8601 timestamp of the reading |
| `reading` | number | Meter reading value |

## Usage

1. **View the specification**: Open `smartmeterasynchapi.yaml` in an AsyncAPI viewer or editor
2. **Generate code**: Use AsyncAPI tools to generate client/server code
3. **Integration**: Implement the subscription pattern to receive meter readings

### AsyncAPI Tools

- [AsyncAPI Studio](https://studio.asyncapi.com/) - Online editor and viewer
- [AsyncAPI Generator](https://github.com/asyncapi/generator) - Code generation tool
- [AsyncAPI CLI](https://github.com/asyncapi/cli) - Command-line interface

## Example Implementation

```javascript
// Example Node.js subscriber using AsyncAPI generated code
const subscriber = new SmartMeterSubscriber();

subscriber.receiveSmartMeterReading((message) => {
  const { meterId, timestamp, reading } = message.payload;
  console.log(`Meter ${meterId}: ${reading} at ${timestamp}`);
  
  // Process meter reading data
  processReading(meterId, reading, timestamp);
});
```

## Use Cases

- **Real-time monitoring**: Track energy consumption patterns
- **Billing systems**: Automated meter reading for utility billing
- **Grid management**: Monitor electrical grid load and distribution
- **Analytics**: Collect data for energy usage analysis
- **Alerting**: Detect anomalies or threshold breaches

## Contributing

1. Fork the repository
2. Make your changes to the AsyncAPI specification
3. Submit a pull request with a clear description

## License

This project is open source. Please check the repository for license details.