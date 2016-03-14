# XHProf

*From: [PECL](https://pecl.php.net/package/xhprof)*

> A function-level hierarchical profiler for PHP and has a simple HTML based navigational interface. The raw data collection component is implemented in C (as a PHP extension). The reporting/UI layer is all in PHP. It is capable of reporting function-level inclusive and exclusive wall times, memory usage, CPU times and number of calls for each function. Additionally, it supports ability to compare two runs (hierarchical DIFF reports), or aggregate results from multiple runs.

*From: [PHP.net](http://php.net/manual/en/intro.xhprof.php)*

> XHProf is a light-weight hierarchical and instrumentation based profiler. During the data collection phase, it keeps track of call counts and inclusive metrics for arcs in the dynamic callgraph of a program. It computes exclusive metrics in the reporting/post processing phase, such as wall (elapsed) time, CPU time and memory usage. A functions profile can be broken down by callers or callees. XHProf handles recursive functions by detecting cycles in the callgraph at data collection time itself and avoiding the cycles by giving unique depth qualified names for the recursive invocations.

> XHProf includes a simple HTML based user interface (written in PHP). The browser based UI for viewing profiler results makes it easy to view results or to share results with peers. A callgraph image view is also supported.

> XHProf reports can often be helpful in understanding the structure of the code being executed. The hierarchical nature of the reports can be used to determine, for example, what chain of calls led to a particular function getting called.

> XHProf supports ability to compare two runs (a.k.a. "diff" reports) or aggregate data from multiple runs. Diff and aggregate reports, much like single run reports, offer "flat" as well as "hierarchical" views of the profile.

---

## Links

-   [Source](https://github.com/phacility/xhprof)
-   [Docs](https://pecl.php.net/package/xhprof)

---

## References

-   [EngineYard: Profiling PHP Part 1: Intro to Xhprof & Xhgui](https://blog.engineyard.com/2014/profiling-with-xhprof-xhgui-part-1)
-   [PECL: XHProf](https://pecl.php.net/package/xhprof)
-   [PHP.net: XHProf](http://php.net/manual/en/intro.xhprof.php)
