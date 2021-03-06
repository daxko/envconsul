envconsul Changelog
===================

## v0.5.1.dev (Unreleased)

BUG FIXES:

  * Fix config merging (GH-49)

## v0.5.0 (February 19, 2015)

DEPRECATIONS:

  * Specifying the prefix before the command is deprecated, please use the
    `-prefix` key instead

FEATURES:

  * Add support for logging to syslog
  * Add `log_level` as a configuration file option and CLI option
  * Add support for basic HTTP authentication when connecting to Consul
  * Add support for connecting to Consul via SSL
  * Add support for specifying a custom retry interval when Consul is not
    available
  * Add support for specifying multiple prefixes using the new `-prefix` command
    line and configuration option (GH-27)
  * Add support for propagating select signals to the child process (GH-31)


IMPROVEMENTS:

  * Improve test coverage, specifically around command-line flag parsing
  * Use Consul Template's logging library for consistency (and get syslog
    logging for free)

BUG FIXES:

  * Fix a bug in the documentation where the environment would be reset
  * Raise an error when specifying a non-existent option in the configuration
    file

## v0.4.0 (February 5, 2015)

IMPROVEMENTS:

  * Allow `envconsul` to run when Consul is unavailable (GH-28)
  * Add `-max-stale` to specify envconsul may talk to non-leader Consul nodes
    if they are less than the maximum stale value (GH-36)

BUG FIXES:

  * Remove deprecated CLI and config options

## v0.3.0 (November 4, 2014)

FEATURES:

  * Watch and reload by default - previously you needed to specify the `-reload`
  flag for envconsul to poll, but this is now the default behavior - you can
  restore the old behavior using the new `-once` flag
  * Leverage watching libraries from Consul Template
  * Unified command interface with Consul Template
  * Added support for quiescene using the new `-wait` option
  * Added support for Consul ACLs using the new `-token` option
  * Added support for reading configuration from file using the new `-config`
  option - the config file is HCL

IMPROVEMENTS:

  * Added `-timeout` parameter for specifying the interval to wait for SIGTERM
  to return before sending SIGKILL
  * Added `-version` flag to print the current version of envconsul
  * Added a full debug log tracer which can be set using `ENV_CONSUL_LOG=debug`
  * Drastically improved documentation with usage examples and feature
  documentation
  * Add significantly more test coverage (still not 100%, but more more
  thoroughly tested)

DEPRECATIONS:

  * `-addr` is deprecated in favor of `-consul` and will be removed in the next
  major release
  * `-dc` is deprecated in favor of using the inline `@dc` syntax and will be
  removed in the next major release
  * `-errExit`, `-terminate`, and `-reload` are all deprecated in favor of
  `-once`. envconsul now intelligently exits where appropriate


## v0.2.0 (July 16, 2014)

FEATURES:

  * Sanitize and upcase by default
  * If `-reload` is not set, don't watch keys
  * Preserve the original process environment

BUG FIXES:

  * Fixed issue with prefix listing missing final forward slash
  * Fixed panic condition on error

## v0.1.0 (May 13, 2014)

  * Initial release
