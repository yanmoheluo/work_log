```
function get_microtime()

{

    list($usec, $sec) = explode(' ', microtime());

    return ((float) $usec + (float) $sec);

}

$php_run_time = get_microtime();

// 计算执行时间

function ptime()

{

    global $php_run_time;

    $time_end = get_microtime();

    $ptime = round($time_end - $php_run_time, 4);

    return substr($ptime, 0, 8);

}

function php_runtime()

{

    return ptime();

}
```