# AkimGame.github.io
C:\

DESKTOP\MySite.html
...............................................................................
<Code game>
.............
compilited
.............

// apples spawner
function spawnApple()
{
  var
    newApple = {
      x: ~~(Math.random() * canv.width),
      y: ~~(Math.random() * canv.height),
      color: 'red'
    };

  // forbid to spawn near the edges
  if(
    (newApple.x < aw || newApple.x > canv.width - aw)
    ||
    (newApple.y < ah || newApple.y > canv.height - ah)
  )
  {
    spawnApple();
    return;
  }

  // check for collisions with tail element, so no apple will be spawned in it
  for( var i = 0; i < tail.length; i++ )
  {
    if(
      newApple.x < (trail[i].x + pw)
      && newApple.x + aw > trail[i].x
      && newApple.y < (trail[i].y + ph)
      && newApple.y + ah > trail[i].y
    )
    {
      // got collision
      spawnApple();
      return;
    }
  }

  apples.push(newApple);

  if( apples.length < 3 && ~~(Math.random() * 1000) > 700 )
  {
    // 30% chance to spawn one more apple
    spawnApple();
  }
}

// random color generator (for debugging purpose or just 4fun)
function rc()
{
  return '#' + ((~~(Math.random() * 255)).toString(16)) + ((~~(Math.random() * 255)).toString(16)) + ((~~(Math.random() * 255)).toString(16));
}

// velocity changer (controls)
function changeDirection(evt)
{
  if( !fkp && [37,38,39,40].indexOf(evt.keyCode) > -1 )
  {
    setTimeout(function() {gs = true;}, 1000);
    fkp = true;
    spawnApple();
  }

  if( cooldown )
    {return false;}

  /*
    4 directional movement.
   */
  if( evt.keyCode == 37 && !(xv > 0) ) // left arrow
    {xv = -speed; yv = 0;}

  if( evt.keyCode == 38 && !(yv > 0) ) // top arrow
    {xv = 0; yv = -speed;}

  if( evt.keyCode == 39 && !(xv < 0) ) // right arrow
    {xv = speed; yv = 0;}

  if( evt.keyCode == 40 && !(yv < 0) ) // down arrow
    {xv = 0; yv = speed;}

  cooldown = true;
  

  setTimeout(function() {cooldown = false;}, 100);
}

</script>

<!-- JavaScript Bundle with Popper -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/js/bootstrap.bundle.min.js" integrity="sha384-b5kHyXgcpbZJO/tY9Ul7kGkf1S0CWuKcCD38l8YkeH8z8QjE0GmW1gYU5S9FOnJ0" crossorigin="anonymous"></script>
	
<div style="height: 2px; background-color:#008504;"></div>
<div>

<font style="padding-top:1px" size="6" color = "#008504" font = "verdana"><center>Rules</font>

<div style="height: 2px; background-color:#008504;"></div>
<div>
	<font size = "5" color = "#008504" font = "verdana">In this game you will play as a small snake that crawls around the map and collects fruits. You must avoid hurting your tail, which is lengthening due to the fact that you eat fruit.To start the game, press one of the < ^ > keys and control the snake with these keys</font>

</body>
</html>
