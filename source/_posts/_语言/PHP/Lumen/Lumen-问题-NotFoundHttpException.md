The problem was solved by changing the
```
$app->run();
```
in /public/index.php to

$request = Illuminate\Http\Request::capture();
```
$app->run($request);
```