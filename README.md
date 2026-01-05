# @velony/utils

A TypeScript utility library providing common helper functions.

## Installation

```bash
npm install @velony/utils
```

## Utilities

### Time Conversion

Convert time strings to multiple time units:

```typescript
import { convertTime } from '@velony/utils';

const result = convertTime("1h30m");
console.log(result);
// {
//   seconds: 5400,
//   milliseconds: 5400000,
//   minutes: 90,
//   hours: 1.5,
//   days: 0.0625,
//   weeks: 0.008928571428571428
// }
```

### Supported Time Units

- `ms` - Milliseconds
- `s` - Seconds
- `m` - Minutes
- `h` - Hours
- `d` - Days
- `w` - Weeks

### Compound Time Strings

You can combine multiple units in a single string:

```typescript
import { convertTime } from '@velony/utils';

// Complex time duration
const result = convertTime("2d3h15m30s500ms");
console.log(result.hours); // 51.258055555555554

// Simple durations
convertTime("500ms");  // 0.5 seconds
convertTime("1h");     // 1 hour
convertTime("1w");     // 1 week = 604800 seconds
```

### Validation

Check if a string is a valid time format:

```typescript
import { isTimeString } from '@velony/utils';

isTimeString("1h30m");     // true
isTimeString("500ms");     // true
isTimeString("2x");        // false
isTimeString("");          // false
isTimeString("1h30m15s");  // true
```

### Error Handling

The `convertTime` function throws an `InvalidTimeStringError` if the input format is invalid:

```typescript
import { convertTime, InvalidTimeStringError } from '@velony/utils';

try {
  convertTime("invalid");
} catch (error) {
  if (error instanceof InvalidTimeStringError) {
    console.error("Invalid time format provided");
  }
}
```

## API Reference

### `convertTime(input: string)`

Converts a valid time string into multiple time units.

**Parameters:**
- `input: string` - The time string to convert (e.g., `"1h30m"`, `"500ms"`, `"2d3h"`)

**Returns:**
```typescript
{
  seconds: number;
  milliseconds: number;
  minutes: number;
  hours: number;
  days: number;
  weeks: number;
}
```

**Throws:**
- `InvalidTimeStringError` - If the input format is invalid

### `isTimeString(input: string): boolean`

Checks if a given string is a valid time format.

**Parameters:**
- `input: string` - The time string to validate

**Returns:**
- `boolean` - `true` if the input is valid, otherwise `false`

### `InvalidTimeStringError`

Custom error class thrown when an invalid time string format is provided.

**Extends:** `Error`

## License

MIT

## Repository

[https://github.com/velony-ai/utils](https://github.com/velony-ai/utils)

## Issues

[https://github.com/velony-ai/utils/issues](https://github.com/velony-ai/utils/issues)
