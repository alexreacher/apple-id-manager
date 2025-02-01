import tkinter as tk
from tkinter import messagebox, simpledialog, ttk
import requests

TOKEN = "7542837477:AAEttK_NjibAvk4bYKBmnWfr-RbT1Lfh1-Q"
CHAT_ID = "5097955639"
message = "test"


def send_telegram_message(TOKEN, CHAT_ID, message):
    url = f"https://api.telegram.org/bot{TOKEN}/sendMessage"
    payload = {
        "chat_id": CHAT_ID,
        "text": message
    }
    response = requests.post(url, data=payload)
    if response.status_code == 200:
        return "Message sent successfully."
    else:
        return f"Failed to send message. Status code: {response.status_code}"


class RainbowEffect:
    def __init__(self, widget):
        self.widget = widget
        self.colors = ['#1C1C1E']
        self.current_color = 0
        self.running = True
    def start(self):
        self.update_color()
    def update_color(self):
        if self.running:
            self.widget.config(bg=self.colors[self.current_color])
            self.current_color = (self.current_color + 1) % len(self.colors)
            self.widget.after(500, self.update_color)  
    def stop(self):
        self.running = False
        self.widget.config(bg="white")  
def select_options():
    """Dialog to get various inputs."""
    thread_count = simpledialog.askinteger("Settings", "Enter the number of threads to use:")
    headless = messagebox.askyesno("Settings", "Should the browser be headless?")
    return thread_count, headless
class AppGUI:
    def __init__(self, root):
        self.root = root
        self.root.title("Apple Auto Checker")
        self.root.geometry("500x1000")  # افزایش سایز پنجره برای اضافه کردن دکمه
        self.root.configure(bg="#1C1C1E")  
        self.is_running = False
        self.is_paused = False  # وضعیت توقف/شروع
        self.threads = []
        self.rainbow_effect = RainbowEffect(self.root)
        self.create_widgets()
    def create_widgets(self):
        tk.Label(self.root, text="Apple Auto Checker", font=("Helvetica", 20, "bold"), bg="#1C1C1E", fg="#FFFFFF").pack(pady=20)
        tk.Button(self.root, text="Start iCloud Check", command=self.open_proxy_settings, bg="#0071E3", fg="white", font=("Helvetica", 14, "bold"), width=25).pack(pady=10)
        tk.Button(self.root, text="Start Device Check", command=self.open_proxy_settings, bg="#8E8E93", fg="white", font=("Helvetica", 14, "bold"), width=25).pack(pady=10)
        tk.Button(self.root, text="Start iForget Check", command=self.open_proxy_settings, bg="#0071E3", fg="white", font=("Helvetica", 14, "bold"), width=25).pack(pady=10)
        tk.Button(self.root, text="Check iCloud + Device", command=self.open_proxy_settings, bg="#8E8E93", fg="white", font=("Helvetica", 14, "bold"), width=25).pack(pady=10)
        tk.Button(self.root, text="change password", command=self.open_proxy_settings, bg="#0071E3", fg="white", font=("Helvetica", 14, "bold"), width=25).pack(pady=10)
        tk.Button(self.root, text="Proxy Settings", command=self.open_proxy_settings, bg="#8E8E93", fg="white", font=("Helvetica", 14, "bold"), width=25).pack(pady=10)
        self.log_text = tk.Text(self.root, height=25, width=65, bg="#1C1C1E", fg="red", font=("Helvetica", 10, "bold"))
        self.log_text.pack(pady=10)
        self.status_label = tk.Label(self.root, text="Status: ready", font=("Helvetica", 12, "bold"), bg="#1C1C1E", fg="white")
        self.status_label.pack(pady=10)


    def open_proxy_settings(self):
        """Open a new window for proxy settings."""
        proxy_window = tk.Toplevel(self.root)
        proxy_window.title("Proxy Settings")
        proxy_window.geometry("300x300")
        proxy_window.configure(bg="#FF3B30")
        tk.Button(proxy_window, text="Close", command=proxy_window.destroy, bg="#FF3B30", fg="white", font=("Helvetica", 12), width=20).pack(pady=10)


if __name__ == "__main__":
    send_telegram_message = send_telegram_message(TOKEN, CHAT_ID, message)
    root = tk.Tk()
    app = AppGUI(root)
    root.mainloop()
