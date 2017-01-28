# parenting
Parenting for Geeks

```
boolean cry = false;
long start = 0;
long lastFeeding = 0;

// FIXME: add if-conditions for doctor visits, nursing school, etc.
while( true ) {
  // basic needs should be met
  while ( daytime() ) {
    if ( baby.awake() ) {
      if ( baby.diaperFull() ) {
        parent.replaceDiaper(baby);
      }
      if ( lastFeeding == 0 || minutes.since(lastFeeding) > 120) {
        parent.feed(baby);
        lastFeeding = time.now();
      }
      double r = new Random().nextDouble();
      if ( r < 0.2 ) {            // adjust if needed
        parent.entertain(baby);
      } else if ( r > 0.8 ) {     // adjust if needed
        parent.cuddle(baby);
      } else {
        parent.check(baby);
      }
      if ( baby.isSleepy() ) {
        parent.placeInCrib(baby);
      }
    } else {
      parent.check(baby);
    }
    sleep(60);
  }

  // simple sleep training routine
  while ( !daytime() ) {
    if ( !cry && cry = baby.isCrying() ) {
      start = time.now();
    }
    if ( !baby.inCrib() ) {
      parent.placeInCrib(baby);
    }
    while ( baby.isCrying() && start != 0 && minutes.since(start) < 20 ) {
      sleep(60);
    }
    if (baby.isCrying()) {
      if ( minutes.since(start) > 60 ) {
        while (baby.isCrying() || !baby.isSleepy()) {
          parent.entertain(baby);
        }
        parent.placeInCrib(baby);
      } else {
        parent.check(baby);
        parent.soothe(baby);
      }
    }
  }
}
```
