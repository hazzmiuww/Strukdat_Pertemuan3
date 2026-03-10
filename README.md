# 1. TIPE DATA
Terdapat 2 jenis tipe data di dalam C++, yaitu tipe data asli dan tipe data buatan. Tipe data asli
contohnya seperti: **integer**, **float**, **double**, **char**, **string**, dan **boolean**. Sedangkan
untuk tipe data buatan, contohnya adalah **Record**. **Record** merupakan tipe data buatan yang berisi kumpulan
variabel dengan tipe data asli.

## Deklarasi Record (C++)
untuk mendeklarasikan tipe data **record** di dalam C++, kita harus menggunakan `struct` dan diikuti dengan nama
variabel yang ingin kita buat. Contohnya:
```cpp
struct mahasiswa
{
  string nim, nama, prodi;
  float ipk;
};
```

```cpp
struct buku
{
  string judul, penulis;
  int jumlahHalaman;
  float harga;
};
```

Sedangkan untuk menggunakan **record** yang telah kita buat sebelumnya, maka kita harus memanggil variabel **record** itu sendiri 
diikuti dengan nama variabel penampung lainnya. Contohnya:

```cpp
struct mahasiswa
{
  string nim, nama, prodi;
  float ipk;
};

int main()
{
  //deklarasi variabel
  mahasiswa mhs1, mhs2;
}
```

```cpp
struct buku
{
  string judul, penulis;
  int jumlahHalaman;
  float harga;
};

int main()
{
  buku buku1, buku2;
}
```

## Mengakses Elemen Record
Untuk mengakses elemen **record**, kita perlu terlebih dahulu untuk mendeklarasikan variabel lain yang bertipe data
**record** seperti di atas, setelah itu, kita menggunakan titik `.` untuk mengakses variabel yang ada di dalam 
**record** itu sendiri. Contohnya:

```cpp
int main()
{
  mahasiswa mhs1, mhs2;
  mhs1.nim = "11223344";
  cin >> mhs1.nama;

  mhs2.nim = "11335577";
  cin >> mhs2.ipk;

  cout << "NIM mhs1: " << mhs1.nim << endl;
  cout << "IPK mhs2: " << mhs2.ipk;
} 
```

# 2. Array
Array merupakan tipe data di c++ yang dapat menyimpan banyak nilai di dalam satu variabel. Sesuai namanya, Array berfungsi
untuk menyimpan banyak nilai dengan tipe seragam ke dalam satu variabel. Untuk mendeklarasikan Array, kita
perlu menulis jenis tipe data yang ingin disimpan dan diikuti dengan nama variabel lalu diikuti dengan kurung siku `[]`. Contohnya:

```cpp
int deretNilai[100];
// jika nilainya belum diinput, maka perlu untuk menentukan ukuran array terlebih dahulu

float ipkMhs[4] = {3.2, 3.6, 2.9, 3.0};
// jika sudah menentukan ukuran array, maka hanya bisa diinput nilai sebanyak ukuran yang ditentukan

char namaMhs[] = {'b', 'u', 'd', 'i'};
// jika sudah memasukkan nilai ke dalam array, maka tidak perlu menentukan ukurannya
// c++ sudah tahu berapa ukuran array dari inputan yang sudah dimasukkan sebelumnya
```

Untuk mendapatkan nilai array, bisa dengan menulis nama variabel array dan diikuti dengan index dari 
nilai yang ingin diambil. Contohnya:

```cpp
float ipkMhs[4] = {3.2, 3.6, 2.9, 3.0};
cout << ipkMhs[0];
// Output: 3.2
```

Atau bisa juga dengan menggunakan `for` loop jika ingin melihat seluruh nilai yang ada di dalam array itu sendiri.
```cpp
#include <iostream>
using namespace std;
int main() {
  int nilai[5];
  for(int i = 0; i < 5; i++)
  {
    cout << "Masukkan nilai ke-" << i << " : ";
    cin >> nilai[i];
  }

  cout << "\nData yang dimasukkan:" << endl;
  for(int i = 0; i < 5; i++) {
  cout << nilai[i] << endl;
  }

  return 0;
}
```

Implementasi lain dari array bisa dilihat seperti contoh di bawah ini:
```cpp
#include <iostream>
using namespace std;

int main() 
{
  int nilai[5];
  int max;

  for(int i = 0; i < 5; i++)
  {
    cout << "Masukkan nilai ke-" << i+1 << " : ";
    cin >> nilai[i];
  }

  max = nilai[0];

  for(int i = 1; i < 5; i++ )
  {
    if(nilai[i] > max)
      {
        max = nilai[i];
      }
  }

  cout << "Nilai tertinggi adalah: " << max << endl;

  return 0;
}
```

Array yang telah disebutkan di atas merupakan contoh array 1 dimensi. Sedangkan untuk membuat array
dua dimensi, cukup dengan menambahkan kurung siku `[]` tambahan di sebelah kurung siku `[]` pertama.
Hasil dari array 2 dimensi merupakan sebuah tabel dengan baris dan kolom atau sebuah matriks.

```
int arr2dim[3][4];
// merupakan array dimensi dengan 3 baris dan 4 kolom

// untuk mengakses elemen di dalam array 2 dimensi juga mirip seperti array satu dimensi
cout << arr2dim[0][1];
// berarti kita ingin menampilkan nilai dari baris dengan index 0 dan kolom dengan index 1
```

# 3. Array of Record
Array of Record merupakan struktur data yang menyimpan kumpulan dari tipe data yang sejenis, yang dalam hal ini merupakan
tipe data **record**, yang mana **record** itu sendiri juga merupakan tipe data yang menyimpan berbagai
nilai dari tipe data yang berbeda. Untuk membuat array of record, cukup dengan mendeklarasikan terlebih dahulu
**record** itu sendiri dan diikuti dengan nama variabel lalu diikuti dengan kurung siku, yang menandakan bahwa
tipe data tersebut menggunakan array. Contohnya:

```cpp
struct mahasiswa {
  string nim, nama;
  float ipk;
};

mahasiswa daftarMhs[300];
```

Pada kode di atas, kita mendeklarasikan sebuah **record** dengan nama variabel mahasiswa lalu menjadikan variabel tersebut 
menjadi array yang memiliki ukuran 300. untuk melakukan input dan output dari array of record, kita perlu menentukan indeks
array mana yang akan diambil datanya, lalu dengan tanda titik `.`, kita mengambil data yang ingin kita tampilkan.
Contohnya:

```cpp
#include <iostream>
#include <string>
using namespace std;

struct mahasiswa{
  string npm, nama, jurusan;
  int umur;
  string hobi[3];
};

int main () {
  mahasiswa mhs[3];

  for(int i = 0; i < 3; i++) {
    cout << "Data Mahasiswa ke-" << i+1 << endl;
    cout << "NPM : ";
    cin >> mhs[i].npm;

    cout << "Nama : ";
    cin >> mhs[i].nama;

    cout << "Jurusan: ";
    cin >> mhs[i].jurusan;

    cout << "Umur : ";
    cin >> mhs[i].umur;

    cout << "Masukkan 3 Hobi:" << endl;
    for(int j = 0 ; j < 3; j++) {
      cout << "Hobi ke-" << j + 1 << " : " ;
      cin >> mhs[i].hobi[j];
    }

    cout << endl;
  }

  return 0;
}
```
