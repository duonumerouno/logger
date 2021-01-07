# Logger class
Small and fast logging class.

## Tests

```cpp
  // [1 mln] nostdout && no fwrite && no input data                       - 0.03s
  logger(logflag::warn | logflag::unixtime | logflag::nostdout);

  // [1 mln] 10 bytes to file                                             - 0.30s
  logger("/log/file", logflag::warn | logflag::unixtime | logflag::nostdout) << "000000000";

  // [1 mln] 10 bytes to stdout(std::ios::sync_with_stdio(false))         - 1.25s
  logger(logflag::warn | logflag::unixtime | logflag::no_sync_with_stdio) << "000000000";

  // [1 mln] 10 bytes to stdout                                           - 2.15s
  logger(logflag::warn | logflag::unixtime) << "000000000";

  // [1 mln] 10 bytes to file && stdout(std::ios::sync_with_stdio(false)) - 1.36s
  logger("/log/file", logflag::warn | logflag::unixtime | logflag::no_sync_with_stdio) << "000000000";

  // [1 mln] 10 bytes to file && stdout                                   - 2.29s
  logger("/log/file", logflag::warn | logflag::unixtime) << "000000000";

```

## Example usage
```cpp
  logger(logflag::box_bracekts)   << "text" << 1 << 2;    // [2021-01-07 17:56:04]  [text][1][2]
  logger(logflag::curly_brackets) << "text" << 1 << 2;    // [2021-01-07 17:56:04]  {text}{1}{2}
  logger(logflag::round_brackets) << "text" << 1 << 2;    // [2021-01-07 17:56:04]  (text)(1)(2)
  logger(logflag::chevrons)       << "text" << 1 << 2;    // [2021-01-07 17:56:04]  [text][1][2]
  logger(logflag::debug)          << "text" << 1 << 2;    // [2021-01-07 17:56:04]  [ DEBUG  ] [text][1][2]
  logger(logflag::info)           << "text" << 1 << 2;    // [2021-01-07 17:56:04]  [ INFO   ] [text][1][2]
  logger(logflag::error)          << "text" << 1 << 2;    // [2021-01-07 17:56:04]  [ ERROR  ] [text][1][2]
  logger(logflag::warn)           << "text" << 1 << 2;    // [2021-01-07 17:56:04]  [ WARN   ] [text][1][2]
  logger(logflag::nostdout)       << "text" << 1 << 2;    //
  logger(logflag::unixtime)       << "text" << 1 << 2;    // [1610038819]  text12
  logger(logflag::unixtime | logflag::spaces) << "text" << 1 << 2;
                                                          // [1610038819]  text 1 2
```
