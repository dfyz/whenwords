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

Here's the yaml with the tests your implementation should pass:

```yaml
- name: "compact hours minutes"
  input: "2h30m"
  output: 9000

- name: "compact with space"
  input: "2h 30m"
  output: 9000

- name: "compact with comma"
  input: "2h, 30m"
  output: 9000

- name: "verbose"
  input: "2 hours 30 minutes"
  output: 9000

- name: "verbose with and"
  input: "2 hours and 30 minutes"
  output: 9000

- name: "verbose with comma and"
  input: "2 hours, and 30 minutes"
  output: 9000

- name: "decimal hours"
  input: "2.5 hours"
  output: 9000

- name: "decimal compact"
  input: "1.5h"
  output: 5400

- name: "single unit minutes verbose"
  input: "90 minutes"
  output: 5400

- name: "single unit minutes compact"
  input: "90m"
  output: 5400

- name: "single unit min"
  input: "90min"
  output: 5400

- name: "colon notation h:mm"
  input: "2:30"
  output: 9000

- name: "colon notation h:mm:ss"
  input: "1:30:00"
  output: 5400

- name: "colon notation with seconds"
  input: "0:05:30"
  output: 330

- name: "days verbose"
  input: "2 days"
  output: 172800

- name: "days compact"
  input: "2d"
  output: 172800

- name: "weeks verbose"
  input: "1 week"
  output: 604800

- name: "weeks compact"
  input: "1w"
  output: 604800

- name: "mixed verbose"
  input: "1 day, 2 hours, and 30 minutes"
  output: 95400

- name: "mixed compact"
  input: "1d 2h 30m"
  output: 95400

- name: "seconds only verbose"
  input: "45 seconds"
  output: 45

- name: "seconds compact s"
  input: "45s"
  output: 45

- name: "seconds compact sec"
  input: "45sec"
  output: 45

- name: "hours hr"
  input: "2hr"
  output: 7200

- name: "hours hrs"
  input: "2hrs"
  output: 7200

- name: "minutes mins"
  input: "30mins"
  output: 1800

- name: "case insensitive"
  input: "2H 30M"
  output: 9000

- name: "whitespace tolerance"
  input: "  2 hours   30 minutes  "
  output: 9000

- name: "error - empty string"
  input: ""
  error: true

- name: "error - no units"
  input: "hello world"
  error: true

- name: "error - negative"
  input: "-5 hours"
  error: true

- name: "error - just number"
  input: "42"
  error: true
```