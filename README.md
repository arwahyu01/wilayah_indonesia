# wilayah_indonesia

Data Wilayah Seluruh Indonesia

## Deskripsi

**wilayah_indonesia** adalah kumpulan data wilayah administratif Indonesia yang tersedia dalam format JSON. Data ini mencakup seluruh provinsi, kota/kabupaten, kecamatan, serta kelurahan/desa yang ada di Indonesia.

## Format Data

Data wilayah Indonesia tersedia dalam format **JSON**, yang memudahkan pengguna dalam mengakses, mengolah, dan mengintegrasikan ke dalam berbagai aplikasi.

## Struktur Data

Data wilayah Indonesia ini terdiri dari 4 level, yaitu:

1. **Provinsi**
2. **Kota/Kabupaten**
3. **Kecamatan**
4. **Kelurahan/Desa**

Berikut adalah contoh struktur data untuk setiap level:

### Provinsi

```json
[
  {
    "nama": "ACEH",
    "id": 11,
    "kode": "11",
    "tingkat": 1
  }
]
```

### Kota/Kabupaten

```json
[
  {
    "nama": "ACEH BARAT",
    "id": 1105,
    "kode": "1105",
    "tingkat": 2
  }
]
```

### Kecamatan

```json
[
  {
    "nama": "BAKONGAN",
    "id": 110101,
    "kode": "110101",
    "tingkat": 3
  }
]
```

### Kelurahan/Desa

```json
[
  {
    "nama": "DARUL IKHSAN",
    "id": 1101012015,
    "kode": "1101012015",
    "tingkat": 4
  }
]
```

## API Endpoint

Pengguna dapat mengakses data wilayah Indonesia secara langsung melalui API berikut:

```
https://raw.githubusercontent.com/arwahyu01/wilayah_indonesia/main/data/
```

### Cara Mengakses Data Wilayah Secara Otomatis

Berikut adalah contoh kode dalam berbagai bahasa pemrograman untuk mengambil data wilayah berdasarkan tingkatannya secara otomatis.

#### Menggunakan JavaScript (Fetch API)

```js
async function fetchWilayah(level, id = "0") {
    const url = `https://raw.githubusercontent.com/arwahyu01/wilayah_indonesia/main/data/${id}.json`;
    try {
        const response = await fetch(url);
        const data = await response.json();
        console.log(`Data ${level}:`, data);
    } catch (error) {
        console.error("Gagal mengambil data", error);
    }
}

fetchWilayah("provinsi");
fetchWilayah("kota/kabupaten", "11");
fetchWilayah("kecamatan", "1105");
fetchWilayah("kelurahan/desa", "110101");
```

#### Menggunakan Python (Requests)

```python
import requests

def fetch_wilayah(level, id="0"):
    url = f"https://raw.githubusercontent.com/arwahyu01/wilayah_indonesia/main/data/{id}.json"
    try:
        response = requests.get(url)
        data = response.json()
        print(f"Data {level}:", data)
    except Exception as e:
        print("Gagal mengambil data", e)

fetch_wilayah("provinsi")
fetch_wilayah("kota/kabupaten", "11")
fetch_wilayah("kecamatan", "1105")
fetch_wilayah("kelurahan/desa", "110101")
```

#### Menggunakan PHP (cURL)

```php
function fetchWilayah($level, $id = "0") {
    $url = "https://raw.githubusercontent.com/arwahyu01/wilayah_indonesia/main/data/" . $id . ".json";
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, $url);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    $data = curl_exec($ch);
    curl_close($ch);
    
    echo "Data $level: " . $data . "\n";
}

fetchWilayah("provinsi");
fetchWilayah("kota/kabupaten", "11");
fetchWilayah("kecamatan", "1105");
fetchWilayah("kelurahan/desa", "110101");
```

#### Menggunakan Golang

```go
    package main
    
    import (
        "encoding/json"
        "fmt"
        "io"
        "net/http"
    )
    
    func fetchWilayah(level, id string) {
        url := "https://raw.githubusercontent.com/arwahyu01/wilayah_indonesia/main/data/" + id + ".json"
        resp, err := http.Get(url)
        if err != nil {
            fmt.Printf("Gagal mengambil data %s: %v\n", level, err)
            return
        }
        defer resp.Body.Close()
    
        body, err := io.ReadAll(resp.Body)
        if err != nil {
            fmt.Printf("Gagal membaca data %s: %v\n", level, err)
            return
        }
    
        var data any
        if err := json.Unmarshal(body, &data); err != nil {
            fmt.Printf("Gagal parsing JSON %s: %v\n", level, err)
            return
        }
    
        fmt.Printf("Data %s: %v\n", level, data)
    }
    
    func main() {
        for _, wilayah := range map[string]string{
            "provinsi":"0",
            "kota/kabupaten":"11",
            "kecamatan":"1105",
            "kelurahan/desa":"110101",
        } {
            fetchWilayah(wilayah, wilayah)
        }
    }
```

## Cara Menggunakan

1. **Akses data JSON** langsung dari API di atas.
2. **Gunakan dalam aplikasi** Anda untuk menampilkan daftar wilayah atau sebagai referensi data administratif.
3. **Filter dan manipulasi data** sesuai kebutuhan menggunakan kode pemrograman seperti JavaScript, Python, PHP, atau Golang.

## Lisensi

Proyek ini didistribusikan di bawah lisensi **MIT**, sehingga dapat digunakan untuk keperluan pribadi maupun komersial dengan tetap mencantumkan atribusi.

## Kontribusi

Kontribusi dari komunitas sangat dihargai! Jika Anda ingin menambahkan atau memperbarui data:

1. **Fork** repositori ini.
2. **Buat perubahan** yang diperlukan.
3. **Kirimkan Pull Request** untuk ditinjau.

## Kontak

Jika Anda memiliki pertanyaan atau masukan, silakan hubungi:

- **GitHub:** [@arwahyu01](https://github.com/arwahyu01)

Jika proyek ini bermanfaat bagi Anda, mohon untuk memberikan ⭐ di GitHub! 🚀

