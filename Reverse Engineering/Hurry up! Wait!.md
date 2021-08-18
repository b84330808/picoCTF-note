## Description
[svchost.exe](https://mercury.picoctf.net/static/990a2760dfc64c33d04f0ee04803d69d/svchost.exe)

## Approach
1. Analyze the file by `ghidraRun`
2. We can find the code below:
```
void FUN_0010298a(void)
{
  ada__calendar__delays__delay_for(1000000000000000);
  FUN_00102616();
  FUN_001024aa();
  FUN_00102372();
  FUN_001025e2();
  FUN_00102852();
  FUN_00102886();
  FUN_001028ba();
  FUN_00102922();
  FUN_001023a6();
  FUN_00102136();
  FUN_00102206();
  FUN_0010230a();
  FUN_00102206();
  FUN_0010257a();
  FUN_001028ee();
  FUN_0010240e();
  FUN_001026e6();
  FUN_00102782();
  FUN_001028ee();
  FUN_0010226e();
  FUN_00102136();
  FUN_0010226e();
  FUN_0010233e();
  FUN_001023da();
  FUN_0010230a();
  FUN_001021d2();
  FUN_00102956();
  return;
}

```
3. The first line `ada__calendar__delays__delay_for(1000000000000000);` looks like a function to delay lots of time. And maybe the title of problem `Hurry up!` is a hint that wants us to check the function.
4. The next line `FUN_00102616`, we can find `p`
5. The next line `FUN_001024aa`, we can find `i`, so we can infer if we check every line, we can get the flag.