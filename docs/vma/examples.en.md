# Script Examples

## Auto Login

```vma
// Auto login example
// Assume login window is open

// Click username input
click(200, 150)
sleep(100)

// Type username
type("admin")

// Click password input
click(200, 200)
sleep(100)

// Type password
type("password123")

// Click login button
click(200, 250)

log("Login completed")
```

---

## Batch Processing

```vma
// Process 10 items
for i = 1 to 10
    // Click item
    click(100, 50 + i * 30)
    sleep(500)
    
    // Process
    click(300, 200)
    sleep(1000)
    
    // Confirm
    key("enter")
    sleep(500)
end

log("Batch processing completed")
```

---

## Scheduled Task

```vma
// Execute task every 5 minutes
loop 12  // Execute 12 times, total 1 hour
    // Execute task
    click(100, 100)
    sleep(500)
    type("Check completed")
    key("enter")
    
    // Wait 5 minutes
    sleep(300000)
endloop

log("Scheduled task completed")
```

---

## Window Management

```vma
// Check if window exists, open if not
if not windowExists("Notepad")
    // Open notepad (via Win+R)
    key("win+r")
    sleep(500)
    type("notepad")
    key("enter")
    sleep(1000)
end

// Activate window
activateWindow("Notepad")

// Type content
type("Hello, Vimina!")

// Save file
key("ctrl+s")
sleep(500)
type("test.txt")
key("enter")

log("Operation completed")
```

---

## Random Operations

```vma
// Random click positions (simulate human behavior)
loop 10
    var x = random(100, 500)
    var y = random(100, 400)
    
    click(x, y)
    
    // Random wait 0.5-2 seconds
    var delay = random(500, 2000)
    sleep(delay)
endloop

log("Random operations completed")
```

---

## Screenshot Monitoring

```vma
// Periodic screenshot monitoring
var count = 0

loop 60  // Monitor 1 hour (once per minute)
    count = count + 1
    
    // Save screenshot
    var filename = "screenshot_" + count + ".png"
    screenshot(filename)
    
    log("Saved: " + filename)
    
    // Wait 1 minute
    sleep(60000)
endloop

log("Monitoring completed")
```

---

## Drag Operation

```vma
// Drag file
// Drag from file list to target position

// Click to select file
click(100, 200)
sleep(100)

// Drag to target position
drag(100, 200, 500, 300)
sleep(200)

// Release
key("enter")

log("Drag completed")
```

---

## Form Filling

```vma
// Auto fill form

// Fill name
click(100, 100)
type("John Doe")

// Fill email
click(100, 150)
type("john@example.com")

// Fill phone
click(100, 200)
type("13800138000")

// Select gender (assume dropdown)
click(100, 250)
key("down")
key("enter")

// Check agree terms
click(100, 300)

// Submit form
click(100, 350)

log("Form filled")
```

---

## Integration with AI Assistant

```vma
// AI assistant generated automation script
// User request: "Help me organize desktop files"

// Open file manager
key("win+e")
sleep(1000)

// Navigate to desktop
key("ctrl+l")
sleep(200)
type("Desktop")
key("enter")
sleep(500)

// Select all files
key("ctrl+a")
sleep(200)

// Create new folder
key("ctrl+shift+n")
sleep(200)
type("Organized Files")
key("enter")
sleep(200)

// Move files
key("ctrl+x")
sleep(200)
dblclick(100, 100)  // Enter new folder
sleep(200)
key("ctrl+v")

log("Desktop files organized")
```
