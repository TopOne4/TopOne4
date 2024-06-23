- 👋 Hi, I’m @TopOne4
- 👀 I’m interested in ... teamwork 
- 🌱 I’m currently learning ... to be awesome 
- 💞️ I’m looking to collaborate with... all the humans in the world 
- 📫 How to reach me ... by the README.md   
- 😄 Pronouns: ...ohhhhhh 
- ⚡ Fun fact: ... ha ha ha ha ha ha ha 

<!---
TopOne4/TopOne4 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
AccessRoot(-1) 
Onwer = #TopOne4----> LowAccess[[true]] = [[AccessRqst]]//99% open
htaccess***sessions¤exe*** c.o.T14 entries  
https://www.youtube.com/watch?v=iSvsf27wRns 
# python  
import tkinter as tk
from tkinter import ttk

class FunGameApp(tk.Tk):
    def __init__(self):
        super().__init__()
        self.title("Fun Game")
        self.geometry("400x400")

        # Skapar spelplansfält
        self.game_frame = ttk.Frame(self)
        self.game_frame.pack(pady=20)

        self.button_grid = []
        for row in range(3):
            row_buttons = []
            for col in range(3):
                button = ttk.Button(self.game_frame, text="", width=5, height=2, 
                                   command=lambda r=row, c=col: self.button_click(r, c))
                button.grid(row=row, column=col, padx=5, pady=5)
                row_buttons.append(button)
            self.button_grid.append(row_buttons)

        self.current_player = "X"
        self.game_over = False

    def button_click(self, row, col):
        if not self.game_over and self.button_grid[row][col]["text"] == "":
            self.button_grid[row][col]["text"] = self.current_player
            self.check_winner()
            self.switch_player()

    def check_winner(self):
        # Kontrollera rader, kolumner och diagonaler för att se om någon har vunnit
        for i in range(3):
            if (self.button_grid[i][0]["text"] == self.button_grid[i][1]["text"] == 
                self.button_grid[i][2]["text"] != ""):
                self.declare_winner(self.button_grid[i][0]["text"])
                return
            if (self.button_grid[0][i]["text"] == self.button_grid[1][i]["text"] == 
                self.button_grid[2][i]["text"] != ""):
                self.declare_winner(self.button_grid[0][i]["text"])
                return
        if (self.button_grid[0][0]["text"] == self.button_grid[1][1]["text"] == 
            self.button_grid[2][2]["text"] != ""):
            self.declare_winner(self.button_grid[0][0]["text"])
            return
        if (self.button_grid[0][2]["text"] == self.button_grid[1][1]["text"] == 
            self.button_grid[2][0]["text"] != ""):
            self.declare_winner(self.button_grid[0][2]["text"])
            return
        if all(button["text"] != "" for row_buttons in self.button_grid for button in row_buttons):
            self.declare_winner("Nobody")

    def declare_winner(self, winner):
        self.game_over = True
        if winner == "Nobody":
            messagebox.showinfo("Game Over", "It's a tie!")
        else:
            messagebox.showinfo("Game Over", f"Player {winner} wins!")

    def switch_player(self):
        self.current_player = "O" if self.current_player == "X" else "X"

if __name__ == "__main__":
    app = FunGameApp()
    app.mainloop()
