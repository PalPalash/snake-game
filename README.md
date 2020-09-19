# About 
This a simple HTML , Javascript game made by me. This is he iconic snake game 
### The About The Game
Snake is the common name for a video game concept where the player maneuvers a line which grows in length, with the line itself being a primary obstacle. The concept originated in the 1976 arcade game Blockade, and the ease of implementing Snake has led to hundreds of versions (some of which have the word snake or worm in the title) for many platforms. After a variant was preloaded on Nokia mobile phones in 1998, there was a resurgence of interest in the snake concept as it found a larger audience. There are over 300 Snake-like games for iOS alone

## How To Play 
The player controls a dot, square, or object on a bordered plane. As it moves forward, it leaves a trail behind, resembling a moving snake. In some games, the end of the trail is in a fixed position, so the snake continually gets longer as it moves. In another common scheme, the snake has a specific length, so there is a moving tail a fixed number of units away from the head. The player loses when the snake runs into the screen border, a trail or other obstacle, or itself. a sole player attempts to eat items by running into them with the head of the snake. Each item eaten makes the snake longer, so controlling is progressively more difficult. 


## Where to play 

Either just download index.html and run it /  go to the [website](https://fast-and-curious-1910.github.io/snake-game/) / play it here if it works 
<hr>
<br>
<meta http-equiv="Content-Type" content="text/html; charset=windows-1252">
        <style>
        #g{background:teal;margin:auto;display:block;}</style></head><span id="warning-container"><i data-reactroot="">

        </i>
    </span>
    <body>
        <canvas id="g" width="640px" height="480px">
         </canvas>
        <script>
            const area_w = 640, area_h = 480, tile_sz = 32, area_tile_w = area_w / tile_sz, area_tile_h = area_h / tile_sz, padding = tile_sz / 4, food_padding = tile_sz / 8, max_snake = area_tile_w * area_tile_h, D_UP = 38, D_DOWN = 40, D_LEFT = 37, D_RIGHT = 39; var canvas = document.getElementById("g"), ctx = canvas.getContext("2d"), phys_timer = null, dir = 0, started = !1, pos = [{ x: Math.round(area_tile_w / 2), y: Math.round(area_tile_h / 2) }], food = null, ctrl_stack = [], forgive = !1; function pos_equal(e, a) { return e.x == a.x && e.y == a.y } function place_food() { var e; do { food = { x: Math.floor(Math.random() * area_tile_w), y: Math.floor(Math.random() * area_tile_h) }, e = !1; for (var a = 0; a < pos.length; a++)if (pos_equal(pos[a], food)) { e = !0; break } } while (e) } function draw_internal() { if (ctx.clearRect(0, 0, area_w, area_h), ctx.fillStyle = "white", pos.length > 1) for (var e = 1; e < pos.length; e++) { var a = pos[e], t = pos[e - 1], i = Math.min(a.x, t.x), _ = Math.max(a.x, t.x), o = Math.min(a.y, t.y), l = Math.max(a.y, t.y), r = i * tile_sz + padding, n = o * tile_sz + padding, s = (1 + _ - i) * tile_sz - 2 * padding, d = (1 + l - o) * tile_sz - 2 * padding; 0 == i && _ == area_tile_w - 1 ? (ctx.fillRect(0, n, tile_sz - padding, d), ctx.fillRect(area_w - tile_sz + padding, n, tile_sz - padding, d)) : 0 == o && l == area_tile_h - 1 ? (ctx.fillRect(r, 0, s, tile_sz - padding), ctx.fillRect(r, area_h - tile_sz + padding, s, tile_sz - padding)) : ctx.fillRect(r, n, s, d) } else { var c = pos[0]; ctx.fillRect(c.x * tile_sz + padding, c.y * tile_sz + padding, tile_sz - 2 * padding, tile_sz - 2 * padding) } food && (ctx.fillStyle = "lime", ctx.fillRect(food.x * tile_sz + food_padding, food.y * tile_sz + food_padding, tile_sz - 2 * food_padding, tile_sz - 2 * food_padding)) } function draw_loop() { draw_internal(), window.requestAnimationFrame(draw_loop) } function end_game(e) { clearInterval(phys_timer), setTimeout(function () { alert(e) }, 250) } function physics_loop() { for (var e = Object.assign({}, pos[pos.length - 1]); ctrl_stack.length > 0;) { var a = ctrl_stack[0]; if (ctrl_stack.shift(), !dir_is_opposing(dir, a)) { dir = a; break } } switch (dir) { case D_UP: e.y--; break; case D_DOWN: e.y++; break; case D_LEFT: e.x--; break; case D_RIGHT: e.x++ }e.x < 0 ? e.x = area_tile_w - 1 : e.x >= area_tile_w && (e.x = 0), e.y < 0 ? e.y = area_tile_h - 1 : e.y >= area_tile_h && (e.y = 0); var t = !1, i = pos_equal(e, food); if (!i) { for (var _ = 1; _ < pos.length; _++)if (pos_equal(pos[_], e)) { t = !0; break } t && (forgive ? end_game("Game over!") : forgive = !0) } t || (i || pos.shift(), pos.push(e), i && (pos.length == max_snake ? (food = null, end_game("YOU'RE WINNER !")) : place_food()), forgive = !1) } function start_game() { phys_timer = setInterval(physics_loop, 150), window.requestAnimationFrame(draw_loop) } function dir_is_opposing(e, a) { return e == D_DOWN && a == D_UP || a == D_DOWN && e == D_UP || e == D_LEFT && a == D_RIGHT || a == D_LEFT && e == D_RIGHT } document.addEventListener("keydown", function (e) { switch (e.keyCode) { case D_UP: case D_LEFT: case D_RIGHT: case D_DOWN: ctrl_stack.push(e.keyCode) }!started && ctrl_stack.length > 0 && (started = !0, start_game()) }), place_food(), draw_internal();
</script>

## Problems
I have noticed some times it won't work , then 
replace 
<br>
```
<script>
..................
</script>
```
with 

```
<script src="https://raw.githubusercontent.com/fast-and-curious-1910/snake-game/master/script.js">
```
or if that dosent work , go to 
https://raw.githubusercontent.com/fast-and-curious-1910/snake-game/master/script.js and copy it , then 
remove and everythong between them 
```
<script>
</script>
```
and write 
```
<script>
// CODE YOU COPIED
</script>
```
and if that dosent work , it is impossible

### Note : I Am A Begginer 

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## My Other Projects 
[Time Travel](https://github.com/fast-and-curious-1910/time-travel.git "Click Here!")
