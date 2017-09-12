## statements

- `array_map` is so much slower than `foreach` (even for just numbers).
    - It's ok to use `array_map` or `array_filter` when you have a small array, otherwise it's best to avoid its use.

- `foreach` is faster than a `for` loop


## optimizations

```php
// given a big array of randoms
for ($i = 0; $i < 999999; ++$i) {
  $rands[] = rand(0, 20);
}

// THIS
foreach ($rands as $r) {
    $arr1[$r] = null;
}
$uniques1 = array_keys($arr1);

// IS FASTER THAN THIS
foreach ($rands as $r) {
    $arr2[] = $r;
}
$uniques2 = array_unique($arr2);
```