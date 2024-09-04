import tkinter as tk
import pyaudio
import numpy as np

# Initialize PyAudio
p = pyaudio.PyAudio()
CHUNK = 1024
FORMAT = pyaudio.paInt16
CHANNELS = 1
RATE = 44100
stream = p.open(format=FORMAT, channels=CHANNELS, rate=RATE, input=True, frames_per_buffer=CHUNK)

# Create window
window = tk.Tk()
window.title("Interactive Candle")

# Create canvas
canvas = tk.Canvas(window, width=300, height=400, bg='white')
canvas.pack()

# Draw candle with light pink color
canvas.create_rectangle(120, 100, 180, 300, fill='light pink', outline='pink')

# Draw the letter
canvas.create_text(150, 350, text='A', font=('Arial', 40, 'bold'), fill='black')

# Draw a flame
flame = canvas.create_oval(135, 80, 165, 100, fill='yellow', outline='orange')

def update_candle():
    data = np.frombuffer(stream.read(CHUNK), dtype=np.int16)
    volume = np.linalg.norm(data)
    height = min(200, volume / 100)  # Adjust scaling factor as needed
    canvas.coords(flame, 135, 80 - height, 165, 100 - height)
    window.after(50, update_candle)

update_candle()
window.mainloop()- 👋 Hi, I’m @48236
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
48236/48236 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
