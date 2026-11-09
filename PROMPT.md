Implement a `parse_duration()` function in Python.
It should parse a human-written duration into seconds,
or throw an exception if it can't be parsed.

**Accepted formats:**
- Compact: "2h30m", "2h 30m", "2h, 30m"
- Verbose: "2 hours 30 minutes", "2 hours and 30 minutes"
- Decimal: "2.5 hours", "1.5h"
- Single unit: "90 minutes", "90m", "90min"
- Colon notation: "2:30" (interpreted as h:mm), "2:30:00" (h:mm:ss)

**Unit aliases:**
- seconds: s, sec, secs, second, seconds
- minutes: m, min, mins, minute, minutes
- hours: h, hr, hrs, hour, hours
- days: d, day, days
- weeks: w, wk, wks, week, weeks

**Error conditions:**
- Empty string
- No parseable units
- Negative values

Be liberal in what you accept. Users type durations in many ways.

Place the result in `./parse_duration.py`.
`./tests.yaml` contains a lists of tests your implementation should pass.
