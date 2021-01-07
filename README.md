# Logger class
Small and fast logging class.

## Tests

```
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