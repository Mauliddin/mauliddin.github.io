---
date: '2025-04-23T14:13:58+08:00'
draft: false
title: 'Stopwatch Menggunakan Pyhton Dan Tkinter'
tags: ["python","tkinter"]
ShowToc: false
---
![stopwach](https://miro.medium.com/v2/resize:fit:640/format:webp/1*Jgb7wnYe4OhZPOiclNcipA.png)

Keterangan : 
- Display waktu : Berfungsi menunjukan waktu stopwatch, saat jam atau menitnya bernilai 0, jam atau menitnya tidak akan ditampilkan.
- Start Button : Untuk memulai waktu stopwatch.
- Pause Button: Untuk menjeda waktu Stopwatch.
- Reset Button: Untuk Mereset Waktu menjadi 0

Codenya:
```python
from tkinter import *
from tkinter import ttk

status_running =  False
seconds = 0
minutes = 0
hours = 0

def count():
    global seconds
    global minutes
    global hours
    global update_time
    
    seconds += 1
    if seconds == 60:
        minutes += 1
        seconds = 0
    if minutes == 60:
        hours += 1
        minutes = 0
        
    minutes_text = f"{minutes:02d}:" if minutes != 0 else ""
    hours_text = f"{hours:02d}:" if hours != 0 else ""
    times_text = f"{hours_text}{minutes_text}{seconds:02d}"

    number_canvas.itemconfig(stopwatch_text, text=times_text)

    update_time = number_canvas.after(1000, func=count)

def start_func():
    global status_running
    
    if not status_running:
        status_running = True
        count()

def pause_func():
    global status_running

    status_running = False
    number_canvas.after_cancel(update_time)


def reset_func():
    global seconds
    global minutes
    global hours
    global status_running
    
    status_running = False
  
    number_canvas.after_cancel(update_time)
    
    seconds = 0
    minutes = 0
    hours = 0

    number_canvas.itemconfig(stopwatch_text, text="00")
  
  
root = Tk()
root.title("Stopwach")
root.minsize(width=400, height=100)
root.config(padx=10, pady=10)

frm = ttk.Frame(root)

number_canvas = Canvas(background="white")
number_canvas.config(width=200, height=100)
stopwatch_text = number_canvas.create_text(100, 50, text="00", fill="black", font=("Helvetica",30,"bold"))
start_btn = ttk.Button(text="Start", width=20, command=start_func)
pause_btn = ttk.Button(text="Pause", width=20, command=pause_func)
reset_btn = ttk.Button(text="Reset", width=20, command=reset_func)
  
number_canvas.grid(row=0, column=0, columnspan=3)
pause_btn.grid(row=1, column=0)
start_btn.grid(row=1, column=1)
reset_btn.grid(row=1, column=2)
  
root.mainloop()
```