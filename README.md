import tkinter as tk
from tkinter import messagebox

class SimpleGUIApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Gestor de Datos")
        self.root.geometry("400x300")
        
        # Etiqueta
        self.label = tk.Label(root, text="Ingrese un dato:")
        self.label.pack(pady=5)
        
        # Campo de entrada
        self.entry = tk.Entry(root, width=40)
        self.entry.pack(pady=5)
        
        # Botón Agregar
        self.add_button = tk.Button(root, text="Agregar", command=self.add_data)
        self.add_button.pack(pady=5)
        
        # Lista de datos
        self.listbox = tk.Listbox(root, width=50, height=10)
        self.listbox.pack(pady=5)
        
        # Botón Limpiar
        self.clear_button = tk.Button(root, text="Limpiar", command=self.clear_data)
        self.clear_button.pack(pady=5)
        
    def add_data(self):
        data = self.entry.get()
        if data:
            self.listbox.insert(tk.END, data)
            self.entry.delete(0, tk.END)
        else:
            messagebox.showwarning("Advertencia", "Ingrese un dato antes de agregar.")
    
    def clear_data(self):
        self.listbox.delete(0, tk.END)

if __name__ == "__main__":
    root = tk.Tk()
    app = SimpleGUIApp(root)
    root.mainloop()
