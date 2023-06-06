# Ujian-Akhir-Semester---PBO
Ujian Akhir Semester matakuliah Pemrograman Berorientasi Objek ini membuat program sederhana yaitu Notepad menggunakan Tkinter dengan Python: Tkinter adalah paket GUI dari python. Kita dapat membuat notepad sederhana yang terdiri dari berbagai menu seperti cara menyimpan, membuka, dan mengedit file.

# Penjelasan mengenai kode program notepad
1. Kode program dibuat dengan mengimport modul tkinkter as tk dan from tkinkter import filedialog, messagebox. Modul tkinter adalah mdoul utama yang menyediakan antarmuka pengguna grafis (GUI) sehingga kita dapat membuat notepad ini menggunakan python. Selanjutnya filedialog merupakan submodul dari tkinkter yang menyediakan fungsi untuk berinteraksi dengan dialog kotak file dan messagebox merupakan submodul dari tkinter juga yang digunakan untuk menampilkan kotak dialog pesan kepada pengguna.  
2. Membuat kelas untuk notepad tersebut
    class Notepad:
    def __init__(self, master):
        self.master = master
        self.master.title("Notepad Kelompok 1")
        self.file_path = None

        self.text_area = tk.Text(self.master)
        self.text_area.pack(fill=tk.BOTH, expand=True)

        self.create_menu()
        
        # Mengganti warna background atau canvasnya
        self.set_background("#ECE5C7")
        
    def set_background(self, color):
        self.text_area.configure(bg=color)
Kelas ini digunakan untuk mengimplementasikan fitur-fitur aplikasi Notepad sederhana. Pada kelas Notepad ini terdapat parameter master yang menggunakan method self.master.title untuk membuat judul aplikasi notepad tersebut. Lalu terdapat method self.text_area.pack() agar kita dapat membuat teks pada area notepad dan mengganti warna dari canvasnya dengan menggunakan self.set_background.    

3. Membuat tombol menu pada notepad
def create_menu(self):
        menu_bar = tk.Menu(self.master)

        file_menu = tk.Menu(menu_bar, tearoff=0)
        file_menu.add_command(label="New", accelerator="Ctrl+N", command=self.new_file)
        file_menu.add_separator()
        file_menu.add_command(label="Open", accelerator="Ctrl+O", command=self.open_file)
        file_menu.add_separator()
        file_menu.add_command(label="Save", accelerator="Ctrl+S", command=self.save_file)
        file_menu.add_separator()
        file_menu.add_command(label="Save As", accelerator="Ctrl+Shift+S", command=self.save_file_as)
        file_menu.add_separator()
        file_menu.add_command(label="Exit", command=self.exit_app)
        menu_bar.add_cascade(label="File", menu=file_menu)

        edit_menu = tk.Menu(menu_bar, tearoff=0)
        edit_menu.add_command(label="Cut", accelerator="Ctrl+X", command=self.cut_text)
        edit_menu.add_command(label="Copy", accelerator="Ctrl+C", command=self.copy_text)
        edit_menu.add_command(label="Paste", accelerator="Ctrl+V", command=self.paste_text)
        edit_menu.add_command(label="Delete", accelerator="Del", command=self.delete_text)
        edit_menu.add_separator()
        edit_menu.add_command(label="Find", accelerator="Ctrl+F", command=self.find_text)
        edit_menu.add_command(label="Replace", accelerator="Ctrl+H", command=self.replace_text)
        menu_bar.add_cascade(label="Edit", menu=edit_menu)

        format_menu = tk.Menu(menu_bar, tearoff=0)
        format_menu.add_command(label="Font", command=self.change_font)
        format_menu.add_separator()
        format_menu.add_command(label="Arial", command=lambda: self.set_font("Arial"))
        format_menu.add_command(label="Times New Roman", command=lambda: self.set_font("Times New Roman"))
        format_menu.add_command(label="Courier New", command=lambda: self.set_font("Courier New"))
        format_menu.add_command(label="Verdana", command=lambda: self.set_font("Verdana"))
        menu_bar.add_cascade(label="Format", menu=format_menu)

        help_menu = tk.Menu(menu_bar, tearoff=0)
        help_menu.add_command(label="About", command=self.about)
        menu_bar.add_cascade(label="Help", menu=help_menu)

        self.master.config(menu=menu_bar)

        # pengikatan beberapa shortcut keyboard
        self.master.bind("<Control-n>", lambda event: self.new_file())
        self.master.bind("<Control-o>", lambda event: self.open_file())
        self.master.bind("<Control-s>", lambda event: self.save_file())
        self.master.bind("<Control-S>", lambda event: self.save_file_as())
        self.master.bind("<Control-x>", lambda event: self.cut_text())
        self.master.bind("<Control-c>", lambda event: self.copy_text())
        self.master.bind("<Control-v>", lambda event: self.paste_text())
        self.master.bind("<Delete>", lambda event: self.delete_text())
        self.master.bind("<Control-f>", lambda event: self.find_text())
        self.master.bind("<Control-h>", lambda event: self.replace_text())
        
Kode diatas merupakan pendefinisian untuk pembuatan tombol-tombol yang tertera pada program Notepad. Pada method create_menu terdapat 4 menu yang akan dibuat yaitu menu file, edit, format, dan help. Kemudian masing-masing dari menu tersebut terdapat submenu. Pada menu file terdapat submenu New, Open, Save, Save As, dan Exit. Selanjutnya pada menu edit terdapat submenu Cut, Copy, Paste, Delete, Find, dan Replace. Lalu pada menu format terdapat pilihan untuk mengganti font, font yang tersedia yaitu Arial, Times New Roman, Courier New, dan Verdana. Dan terkahir terdapat menu help untuk menampilkan tentang program notepad ini. 
Terdapat juga menggunakan method self.master.bind untuk membuat shortcut dari menu-menu tadi.

4. Pengimplementasian metode open file dalam kelas Notepad. Metode ini digunakan untuk membuka file teks dan menampilkan isinya di area teks pada aplikasi notepad.
5. Pengimplementasian metode save file dalam kelas Notepad. Metode ini digunakan untuk menyimpan konten yang ada di area teks ke dalam file.
6. Pengimplementasian metode save file as dalam kelas Notepad. Metode ini digunakan untuk menyimpan konten yang ada di area teks ke dalam file dengan meminta pengguna untuk memilih path dan nama file melalui dialog save as.
7. Pengimplementasian metode save file dalam kelas Motepad. Metode ini digunakan untuk menyimpan konten yang ada di area teks ke dalam file dengan path yang sudah ditentukan.
8. Pengimplementasian metode exit app dalam kelas Notepad. Metode ini digunakan untuk menampilkan kotakk dialog konfirmasi saat pengguna ingin keluar dari aplikasi.
9. Pengimplementasian metode cut teks dalam kelas Notepad. Metode ini digunakan untuk memotong teks yang dipilih di area teks.
10. Pengimplementasian metode copy dalam kelas notepad. Metode ini digunakan untuk menyalin teks yang dipilih di area teks. 
11. Pengimplementasian metode paste teks dalam kelas Notepad. Metode ini digunakan untuk melakukan operasi paste teks pada posisi kursor di area teks. 
12. Pengimplementasian metode delete teks. Metode ini digunakan untuk menghapus teks yang dipilih di area teks.
13. Pengimplementasian metode find text pada kelas Notepad. Metode ini digunakan untuk membuat jendela dialog "Find" yang memungkinkan pengguna mencari teks tertentu dalam area teks. 
14. Pengimplementasian metode find dengan parameter (self, search_text) pada kelas Notepad. Metode ini digunakan untuk melakukan pencarian teks dalam area teks.
15. Pengimplementasian metode replace text pada kelas Notepad. Metode ini digunakan untuk membuat jendela dialog "Replace" yang memungkinkan pengguna mencari dan mengganti teks dalam area teks.
16. Pengimplementasian metode replace dengan parameter (self, search_text, replace_text) pada kelas notepad. Metode ini digunakan untuk mencari teks yang cocok dengan search_text dalam area teks dan menggantinya dengan replace_teks.
17. Pengimplementasian metode change_font(self) digunakan untuk mengubah font yang digunakan saat mengetik di area teks.
18. Pengimplementasian metode change_font(self, font_name) digunakan untuk menetapkan font yang ingin digunakan dalam area teks.
19. Pengimplementasian metode about(self) digunakan untuk menampilkan dialog informasi "About" yang memberikan informaasi singkat tentang aplikasi Notepad. 
20. Dan pada bagian akhir program terdapat contoh dari kelas Notepad dibuat dengan menggunakan objek 'root' dari kelas 'Tk'. Hal ini membuat jendela aplikasi Notepad muncul saat aplikasi dijalankan. Perulangan mainloop() dipanggil pada objek root untuk menjalanlan aplikasi secara terus-menerus hingga jendela ditutup.
