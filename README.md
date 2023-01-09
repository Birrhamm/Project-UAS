PDF [KLIK DISINI](https://drive.google.com/file/d/1B592hgFIhTPx2zmeHPPaCE1-gG92BFAb/view?usp=drivesdk)


## kode program daftar_nilai.py

```
def tambah_data(daftar, data):
    # function untuk menambahkan data ke daftar
    daftar.append(data)
    return daftar

def ubah_data(daftar, data_baru, data_lama):
    # function untuk mengubah data yang ada di daftar
    for i in range(len(daftar)):
        if daftar[i][0] == data_lama[0]:
            daftar[i] = data_baru
            break
    return daftar

def hapus_data(daftar, data):
    # function untuk menghapus data dari daftar
    daftar.remove(data)
    return daftar

def cari_data(daftar, data):
    # function untuk mencari data di daftar
    for i in range(len(daftar)):
        if daftar[i][0] == data[0]:
            return daftar[i]
    return "Data tidak ditemukan."
```

## kode program input_nilai.py

```
def input_data():
    # function untuk meminta input data dari pengguna
    nama = input("Masukkan nama mahasiswa: ")
    nim = input("Masukkan NIM: ")
    tugas = int(input("Masukkan nilai tugas: "))
    uts = int(input("Masukkan nilai UTS: "))
    uas = int(input("Masukkan nilai UAS: "))

    # hitung nilai akhir
    akhir = 0.3 * tugas + 0.35 * uts + 0.35 * uas

    data = (nama, nim, tugas, uts, uas, akhir)
    return data
```

## kode program view_nilai.py

```
def cetak_daftar_nilai(daftar):
    # function untuk mencetak daftar nilai
    print("Daftar Nilai Mahasiswa:")
    print("="*70)
    print("| No |     Nama     |    NIM    | Tugas |  UTS  | UAS  | Akhir |")
    print("="*70)
    for i in range(len(daftar)):
        print("| {no:2d} | {nama:14s} | {nim:9s} | {tugas:5d} | {uts:5d} | {uas:5d} | {akhir:6.2f} |"
              .format(no=i+1, nama=daftar[i][0], nim=daftar[i][1], tugas=daftar[i][2], uts=daftar[i][3], uas=daftar[i][4], akhir=daftar[i][5]))
    print("="*70)

def cetak_hasil_pencarian(data):
    # function untuk mencetak hasil pencarian data
    if data == "Data tidak ditemukan.":
        print(data)
    else:
        print("Data ditemukan:")
        print("="*70)
        print("|     Nama     |    NIM    | Tugas |  UTS  | UAS  | Akhir |")
        print("="*70)
        print("| {nama:14s} | {nim:9s} | {tugas:5d} | {uts:5d} | {uas:5d} | {akhir:6.2f} |"
              .format(nama=data[0], nim=data[1], tugas=data[2], uts=data[3], uas=data[4], akhir=data[5]))
        print("="*70)
```

## kode program main.py

```
import model.daftar_nilai as dn
import view.input_nilai as inp
import view.view_nilai as vi

def main():
    # inisialisasi daftar nilai
    daftar_nilai = []

    # menu pilihan
    while True:
        print("Menu:")
        print("1. Tambah data")
        print("2. Ubah data")
        print("3. Hapus data")
        print("4. Cari data")
        print("5. Lihat daftar nilai")
        print("6. Keluar")
        pilihan = input("Masukkan pilihan Anda (1-6): ")

        if pilihan == "1":
            # tambah data
            data = inp.input_data()
            daftar_nilai = dn.tambah_data(daftar_nilai, data)
        elif pilihan == "2":
            # ubah data
            data_lama = inp.input_data()
            data_baru = inp.input_data()
            daftar_nilai = dn.ubah_data(daftar_nilai, data_baru, data_lama)
        elif pilihan == "3":
            # hapus data
            data = inp.input_data()
            daftar_nilai = dn.hapus_data(daftar_nilai, data)
        elif pilihan == "4":
            # cari data
            data = inp.input_data()
            hasil_pencarian = dn.cari_data(daftar_nilai, data)
            vi.cetak_hasil_pencarian(hasil_pencarian)
        elif pilihan == "5":
            # lihat daftar nilai
            vi.cetak_daftar_nilai(daftar_nilai)
        elif pilihan == "6":
            # keluar
            break
        else:
            print("Pilihan tidak valid.")

if __name__ == "__main__":
    main()
```
