# Built-in Functions

## Mouse Functions

### click(x, y)

Left click at the specified coordinates.

```vma
click(100, 200)
```

---

### clickR(x, y)

Right click at the specified coordinates.

```vma
clickR(100, 200)
```

---

### dblclick(x, y)

Double click at the specified coordinates.

```vma
dblclick(100, 200)
```

---

### move(x, y)

Move mouse to the specified coordinates.

```vma
move(500, 300)
```

---

### drag(fromX, fromY, toX, toY)

Drag from start point to end point.

```vma
drag(100, 100, 300, 300)
```

---

### scroll(delta)

Scroll the mouse wheel.

```vma
scroll(1)    // Scroll up
scroll(-1)   // Scroll down
```

---

### getMousePos()

Get current mouse position.

```vma
var pos = getMousePos()
log(pos.x)   // X coordinate
log(pos.y)   // Y coordinate
```

---

## Keyboard Functions

### type(text)

Type text string.

```vma
type("Hello World")
```

---

### key(keyName)

Send keystroke or combination key.

```vma
key("enter")
key("ctrl+c")
key("alt+tab")
```

---

### keyDown(keyName)

Press key (don't release).

```vma
keyDown("ctrl")
```

---

### keyUp(keyName)

Release key.

```vma
keyUp("ctrl")
```

---

## Window Functions

### activateWindow(title)

Activate window with the specified title.

```vma
activateWindow("Notepad")
```

---

### closeWindow(title)

Close window with the specified title.

```vma
closeWindow("Notepad")
```

---

### minimizeWindow(title)

Minimize window with the specified title.

```vma
minimizeWindow("Notepad")
```

---

### maximizeWindow(title)

Maximize window with the specified title.

```vma
maximizeWindow("Notepad")
```

---

### windowExists(title)

Check if window exists.

```vma
if windowExists("Notepad")
    log("Window exists")
end
```

---

### getWindowList()

Get all windows list.

```vma
var windows = getWindowList()
for win in windows
    log(win.title)
end
```

---

## Control Functions

### clickTag(tag)

Click control with the specified tag.

```vma
clickTag("AB")
```

---

### getControlByTag(tag)

Get control info with the specified tag.

```vma
var ctrl = getControlByTag("AB")
log(ctrl.name)
log(ctrl.bounds.x)
```

---

### getControlList()

Get all controls in current window.

```vma
var controls = getControlList()
for ctrl in controls
    log(ctrl.tag + ": " + ctrl.name)
end
```

---

## Time Functions

### sleep(ms)

Pause execution for specified milliseconds.

```vma
sleep(1000)  // Pause 1 second
```

---

### getTimestamp()

Get current timestamp (milliseconds).

```vma
var ts = getTimestamp()
log(ts)
```

---

## Log Functions

### log(message)

Output log message.

```vma
log("Operation completed")
log("Count: " + count)
```

---

## Screenshot Functions

### screenshot()

Take fullscreen screenshot.

```vma
screenshot()
```

---

### screenshot(filename)

Take fullscreen screenshot and save to file.

```vma
screenshot("screen.png")
```

---

### screenshot(x, y, width, height)

Take screenshot of specified region.

```vma
screenshot(100, 100, 400, 300)
```

---

## Random Functions

### random(min, max)

Generate random integer in specified range.

```vma
var r = random(1, 100)
log(r)
```

---

### randomFloat()

Generate random float between 0-1.

```vma
var r = randomFloat()
log(r)
```

---

## Math Functions

### abs(x)

Absolute value.

```vma
var a = abs(-5)  // 5
```

---

### floor(x)

Round down.

```vma
var f = floor(3.7)  // 3
```

---

### ceil(x)

Round up.

```vma
var c = ceil(3.2)  // 4
```

---

### round(x)

Round to nearest.

```vma
var r = round(3.5)  // 4
```

---

### sqrt(x)

Square root.

```vma
var s = sqrt(16)  // 4
```

---

### pow(x, y)

Power operation.

```vma
var p = pow(2, 3)  // 8
```

---

## System Functions

### beep()

Play system beep.

```vma
beep()
```

---

### exit()

Terminate script execution.

```vma
if error
    exit()
end
```

---

### getVersion()

Get Vimina version.

```vma
var v = getVersion()
log(v)
```
