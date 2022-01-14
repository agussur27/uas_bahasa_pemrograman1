# UAS

# Membuat package dan modul dengan struktur

* ✓ daftar_nilai.py berisi modul untuk: tambah_data, ubah_data, hapus_data, dan cari_data

* ✓ view_nilai.py berisi modul untuk: cetak_daftar_nilai, cetak_hasil_pencarian

* ✓ input_nilai.py berisi modul untuk: input_data yang meminta pengguna memasukkan data.

* ✓ main.py berisi program utama (menu pilihan yang memanggil semua menu yang ada)

### Tampilan package dan modul

![package](https://user-images.githubusercontent.com/92660371/149573218-2d6ca9e2-7eef-4a9e-986c-5c59dd193ef1.jpg)


### Berikut tampilan programnya


    from view.input_nilai import *


    dataMahasiswa = {}


    def tambah_data():

        global dataMahasiswa
        nama = input_nama()
        nim = input_nim()
        nilaiTugas = input_nilaiTugas()
        nilaiUts = input_nilaiUts()
        nilaiUas = input_nilaiUas()
        nilaiAkhir = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
        dataMahasiswa[nama] = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
        print("\nData Berhasil Ditambahkan!")
        return dataMahasiswa

    def ubah_data():
        nama = input("Masukkan Nama: ")
        if nama in dataMahasiswa.keys():
            nim = input_nim()
            nilaitugas = input_nilaiTugas()
            nilaiUts = input_nilaiUts()
            nilaiUas = input_nilaiUas()
            nilaiAkhir = (0.30 * nilaiTugas) + (0.35 * nilaiUts) + (0.35 * nilaiUas)
            dataMahasiswa[nama] = nim, nilaiTugas, nilaiUts, nilaiUas, nilaiAkhir
            print("\nData Berhasil Di Update!")
        else:
            print("Data tidak ditemukan!")

    
    def hapus_data():
        nama = input("Masukkan Nama:  ")
        if nama in dataMahasiswa.keys():
            del dataMahasiswa[nama]
            print("Data",nama, "Telah dihapus!")
        else:
            print("Data Mahasiswa Tidak Ada".format(nama))   

* diatas adalah program pada modul daftar_nilai.py


    from model.daftar_nilai import *


    def cetak_daftar_nilai():
    
    
        if dataMahasiswa.items():
        
        
            print("\n                      DAFTAR NILAI MAHASISWA                    ")
            print("==================================================================")
            print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
            print("==================================================================")
            i = 0
            for x in dataMahasiswa.items():
            i += 1
            print("| {6:2} | {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6} |".format(x[0], x[1][0], x[1][1], x[1][2], x[1][3], x[1][4], i))
            print("==================================================================")
        else:
            print("\n                      DAFTAR NILAI MAHASISWA                    ")
            print("==================================================================")
            print("| No |     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir |")
            print("==================================================================")
            print("|                          TIDAK ADA DATA!                       |")
            print("==================================================================")


    def cetak_hasil_pencarian():
    
        nama = input("Masukkan Nama : ")
        
        if nama in dataMahasiswa.keys():
           print("\n                   DAFTAR NILAI MAHASISWA                   ")
           print("==============================================================")
           print("|     Nama     |    NIM    | Tugas |  UTS  |  UAS  |  Akhir  |")
           print("==============================================================")
           print("| {0:12s} | {1:9s} | {2:5} | {3:5} | {4:5} | {5:6}  |".format(nama, dataMahasiswa[nama][0], dataMahasiswa[nama][1], dataMahasiswa[nama][2], dataMahasiswa[nama][3], dataMahasiswa[nama][4]))
        print("==============================================================")
        else:
            print("Datanya {0} Tidak Ada ".format(nama))
        
* diatas adalah program pada modul cetak_nilai.py



    def input_nama():
    
    
        global nama
        
        nama = input("Masukkan Nama        : ")
        
        return nama


    def input_nim():
    
        global nim
        
        nim = input("Masukkan NIM         : ")
        
        return nim


    def input_nilaiTugas():
    
        global nilaiTugas
        
        nilaiTugas = int(input("Masukkan Nilai Tugas : "))
        
        return nilaiTugas
        

    def input_nilaiUts():
    
        global nilaiUts
        
        nilaiUts = int(input("Masukkan Nilai UTS   : "))
        
        return nilaiUts
        

    def input_nilaiUas():
    
        global nilaiUas
        
        nilaiUas = int(input("Masukkan Nilai UAS   : "))
        
        return nilaiUas
    
* diatas adalah program pada modul input_nilai.py


    from view.cetak_nilai import *
    while True:
        c = input("\nT)ambah, U)bah, C)ari, H)apus, L)ihat, K)eluar: ")

        if c.lower() == 't':
            tambah_data()

        elif c.lower() == 'u':
            ubah_data()

        elif c.lower() == 'c':
            cetak_hasil_pencarian()

        elif c.lower() == 'h':
            hapus_data()

        elif c.lower() == 'l':
            cetak_daftar_nilai()

        elif c.lower() == 'k':
            break

        else:
            print("Menu yang anda maksud tidak tersedia, Silahkan pilih menu yang tersedia")
   
* diatas adalah program untuk modul main.py

### Berilut tampilan hasil program ketika dijalankan





![tambah](https://user-images.githubusercontent.com/92660371/149573805-b31af9bb-fd36-448e-ada0-c0616307131d.png)
* diatas tampilan untuk menambahkan data dengan menginputkan huruf t

![lihat](https://user-images.githubusercontent.com/92660371/149573799-79013a1a-87c3-4175-9e85-d9c5da9e512b.png)
* diatas tampilan untuk menampilkan data yang telah ditambahkan dengan menginputkan hurup l

![hapus](https://user-images.githubusercontent.com/92660371/149573779-4f5c3ee3-2e43-441c-9618-8b6e15c59c81.png)
* diatas tampilan untuk menghapus salah satu data dengan menginputkan huruf h

![cari](https://user-images.githubusercontent.com/92660371/149573768-f5a3d99f-431a-45c6-9cd8-844a3ebfeb95.png)
* diatas tampilan untuk mencari data, dengan menginputkan huruf c dan dilanjutkan memasukan keywords nama

![keluar](https://user-images.githubusercontent.com/92660371/149573791-224ac606-570c-4395-9b1c-ae60523edfb6.png)
* diatas tampilan untuk keluar atau menutup program

## Selesai
# Terima kasih
