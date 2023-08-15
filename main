import tkinter as tk
from tkinter import ttk
import cryptocode
#UI design of SecretNote 
window = tk.Tk()
window.minsize(width=350, height=650)
window.title("Secret Notes")

title_label = tk.Label(text="Enter your title", font=("Arial", 14))
title_label.pack()

title_entry = tk.Entry(width=40)
title_entry.pack()

secret_label = tk.Label(text="Enter your Secret", font=("Arial", 14))
secret_label.pack()

secret_text = tk.Text(width=35, height=20, padx=20, pady=20)
secret_text.pack()

masterkey_label = tk.Label(text="Enter master key", font=("Arial", 14))
masterkey_label.pack()

masterkey_entry = tk.Entry(width=40)
masterkey_entry.pack()

# Getting information from title and text section
def add_file():
    title_information = title_entry.get()
    text_information = secret_text.get(1.0, tk.END)
    return [title_information, text_information]

#encrycripting of text with cryptocode
def encrypting_file(file_text):
    password = masterkey_entry.get()
    encoded = cryptocode.encrypt(file_text, password)
    return [encoded, password]

#Creating secret.txt to add title and encrypted text
def write_file(title, text):
    path = "C:/Users/hakbas/Downloads/secret_file/secret.txt"
    with open(path, "a+") as f:
        f.write("{}\n{}".format(title, text))

#popup error mesage
def popupmsg(msg):
    popup = tk.Tk()
    popup.geometry("400x400")
    popup.wm_title("Error Message")
    label = tk.ttk.Label(popup, text=msg, font=("Arial", 16))
    label.pack(side="top", fill="x", pady=10, padx=70)
    B1 = tk.ttk.Button(popup, text="Okay", command=popup.destroy)
    B1.pack()
    popup.mainloop()

# button 1 design to save title, key and encrypted text
def button1():
    if title_entry.get() == "" or secret_text.get(1.0, tk.END) == "" or masterkey_entry.get() == "":
        popupmsg("Please fill all blanks")
    else:
        new_file = add_file()
        encrypted_file = encrypting_file(new_file[1])
        write_file(new_file[0], encrypted_file[0])
        secret_text.delete(1.0, tk.END)
        masterkey_entry.delete(0, tk.END)
        title_entry.delete(0, tk.END)

#button 2 design to decryting message
def button2():
    message = secret_text.get(1.0, tk.END)
    decrypt = masterkey_entry.get()
    decoded = cryptocode.decrypt(message, decrypt)
    if decoded:
        secret_text.delete(1.0, tk.END)
        secret_text.insert(tk.END, decoded)
    else:
        popupmsg("You have enter wrong password")


save_button = tk.Button(text="Save & Encrypt", font=("Arial", 12), padx=20, command=button1)
save_button.pack()

decrypt_button = tk.Button(text="Decrypt", font=("Arial", 12), padx=20, command=button2)
decrypt_button.pack()
window.mainloop()
