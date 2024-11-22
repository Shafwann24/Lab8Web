<h1>Lab8Web</h1>
<hr> <br>
<h2>1. Persiapan Untuk memulai membuat aplikasi CRUD sederhana, yang perlu disiapkan adalah database server menggunakan MySQL. Pastikan MySQL Server sudah dapat dijalankan melalui XAMPP. Menjalankan MySQL Server Untuk menjalankan MySQL Server dari menu XAMPP Contol. Mengakses MySQL Client menggunakan PHP MyAdmin Pastikan webserver Apache dan MySQL server sudah dijalankan. Kemudian buka melalui browser: http://localhost/phpmyadmin/ atau bisa di menekan tombol admin di XAMPP di colum MySQL</h2>

![image](https://github.com/user-attachments/assets/538b2dd6-c8b3-4eba-8664-e961b18b799a)

<h2>2. Membuat Database: Studi Kasus Data Barang</h2>

![image](https://github.com/user-attachments/assets/9095f1fe-c575-43c7-bbe9-65a0c0b15673)

<h2>3. Membuat Table data_barang</h2>

![image](https://github.com/user-attachments/assets/27416646-a0df-4055-9295-edc20ab3008a)

<h2>4. Kemudian Membuat Item data pada data_barang yang sebelumnya sudah dibuat Membuatnya bisa melalui phpMyAdmin dan juga bisa dibuat melalui terminal dibuatnya dengan perintah INSERT INTO
</h2>

![image](https://github.com/user-attachments/assets/7dd1c0a9-1c07-45b2-a9a1-b4360b42c06f)

<h2>5. Kemudian untuk Menjalankan database ini ke sebuah website local Pertama kita harus membuat folder di htdocs caranya
buka File Explorer -> xampp -> htdocs -. buat folder di dalam htdocs dengan lab8_php_database.</h2>

![image](https://github.com/user-attachments/assets/e4953f57-9087-478f-848e-3f6eeec57068)

<h2>6. ketika sudah membuat folder kemudian kita cek foldernya sudah bisa tersambung dengan localhost kita di broser Buka browser -> lalu ketik di colom pencarian -> localhost/lab8_php/database/</h2>

![image](https://github.com/user-attachments/assets/7d1a5fbd-e3e4-466b-be38-68983d714726)

<h2>7. Membuat file koneksi database</h2>

    <?php
    $host = "localhost";
    $user = "root";
    $pass = "";
    $db = "latihan1";
    $conn = mysqli_connect($host, $user, $pass, $db);
    if ($conn == false)
    {
    echo "Koneksi ke server gagal.";
    die();
    } #else echo "Koneksi berhasil";
    ?>

![image](https://github.com/user-attachments/assets/1f384462-268c-418a-a668-fa73237be82a)

Koneksi Database: Kode ini mencoba untuk menghubungkan aplikasi PHP ke database MySQL dengan menggunakan mysqli_connect(), yang membutuhkan parameter host, username, password, dan nama database.
Cek Koneksi: Jika koneksi gagal (misalnya server tidak tersedia atau kredensial salah), pesan "Koneksi ke server gagal." akan ditampilkan dan eksekusi script dihentikan menggunakan die(). Jika koneksi berhasil, pesan "Koneksi berhasil" akan ditampilkan.
Output dari kode ini adalah pesan yang menunjukkan apakah koneksi ke database berhasil atau gagal.


<h2>8. Membuat file index untuk menampilkan data (Read)</h2>

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Data Barang</title>
        <style>
            table {
                width: 100%;
                border-collapse: collapse;
            }
            table, th, td {
                border: 1px solid black;
            }
            th, td {
                padding: 10px;
                text-align: left;
            }
            a {
                text-decoration: none;
                color: blue;
            }
            a:hover {
                text-decoration: underline;
            }
        </style>
    </head>
    <body>
        <h1>Data Barang</h1>
        <a href="tambah_barang.php">Tambah Barang</a>
        <br><br>
        <table>
            <thead>
                <tr>
                    <th>Gambar</th>
                    <th>Nama Barang</th>
                    <th>Kategori</th>
                    <th>Harga Jual</th>
                    <th>Harga Beli</th>
                    <th>Stok</th>
                    <th>Aksi</th>
                </tr>
            </thead>
            <tbody>
                <?php
                // Sample data, you should replace it with a database query in a real application
                $data_barang = [
                    [
                        "id" => 1,
                        "gambar" => "HP Samsung Android",
                        "nama" => "HP Samsung Android",
                        "kategori" => "Elektronik",
                        "harga_jual" => 2000000,
                        "harga_beli" => 2400000,
                        "stok" => 5
                    ],
                    [
                        "id" => 2,
                        "gambar" => "HP Xiaomi Android",
                        "nama" => "HP Xiaomi Android",
                        "kategori" => "Elektronik",
                        "harga_jual" => 1000000,
                        "harga_beli" => 1400000,
                        "stok" => 5
                    ],
                    [
                        "id" => 3,
                        "gambar" => "HP OPPO Android",
                        "nama" => "HP OPPO Android",
                        "kategori" => "Elektronik",
                        "harga_jual" => 1800000,
                        "harga_beli" => 2300000,
                        "stok" => 5
                    ]
                ];
    
                foreach ($data_barang as $barang) {
                    echo "<tr>
                            <td>{$barang['gambar']}</td>
                            <td>{$barang['nama']}</td>
                            <td>{$barang['kategori']}</td>
                            <td>{$barang['harga_jual']}</td>
                            <td>{$barang['harga_beli']}</td>
                            <td>{$barang['stok']}</td>
                            <td>
                                <a href='ubah.php?id={$barang['id']}'>Ubah</a> | 
                                <a href='hapus.php?id={$barang['id']}'>Hapus</a>
                            </td>
                        </tr>";
                }
                ?>
            </tbody>
        </table>
    </body>
    </html>

![image](https://github.com/user-attachments/assets/619daf44-63e8-4212-9131-283e97b309e1)

Kode ini menampilkan tabel data barang dengan kolom untuk gambar, nama, kategori, harga jual, harga beli, stok, dan aksi (ubah/hapus). Data barang disimulasikan dalam array, dan setiap barang memiliki link untuk mengubah atau menghapusnya. Tabel dan link diformat dengan CSS untuk tampilan yang rapi.

<h2>9. Menambah Data (Create)</h2>

    <?php
    error_reporting(E_ALL);
    include_once 'koneksi.php';
    if (isset($_POST['submit']))
    {
        $nama = $_POST['nama'];
        $kategori = $_POST['kategori'];
        $harga_jual = $_POST['harga_jual'];
        $harga_beli = $_POST['harga_beli'];
        $stok = $_POST['stok'];
        $file_gambar = $_FILES['file_gambar'];
        $gambar = null;
        if ($file_gambar['error'] == 0)
        {
            $filename = str_replace(' ', '_',$file_gambar['name']);
            $destination = dirname(__FILE__) .'/gambar/' . $filename;
            if(move_uploaded_file($file_gambar['tmp_name'], $destination))
            {
                $gambar = 'gambar/' . $filename;;
            }
        }
        $sql = 'INSERT INTO data_barang (nama, kategori,harga_jual, harga_beli,
    stok, gambar) ';
        $sql .= "VALUE ('{$nama}', '{$kategori}','{$harga_jual}',
    '{$harga_beli}', '{$stok}', '{$gambar}')";
        $result = mysqli_query($conn, $sql);
        header('location: index.php');
    }
    ?>
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <link href="style.css" rel="stylesheet" type="text/css" />
        <title>Tambah Barang</title>
    </head>
    <body>
    <div class="container">
        <h1>Tambah Barang</h1>
        <div class="main">
            <form method="post" action="tambah.php"
    enctype="multipart/form-data">
                <div class="input">
                    <label>Nama Barang</label>
                    <input type="text" name="nama" />
                </div>
                <div class="input">
                    <label>Kategori</label>
                    <select name="kategori">
                        <option value="Komputer">Komputer</option>
                        <option value="Elektronik">Elektronik</option>
                        <option value="Hand Phone">Hand Phone</option>
                    </select>
                </div>
                <div class="input">
                    <label>Harga Jual</label>
                    <input type="text" name="harga_jual" />
                </div>
                    <div class="input">
                    <label>Harga Beli</label>
                    <input type="text" name="harga_beli" />
                </div>
                <div class="input">
                    <label>Stok</label>
                    <input type="text" name="stok" />
                </div>
                    <div class="input">
                    <label>File Gambar</label>
                    <input type="file" name="file_gambar" />
                </div>
                    <div class="submit">
                    <input type="submit" name="submit" value="Simpan" />
                </div>
            </form>
        </div>
    </div>
    </body>
    </html>

![image](https://github.com/user-attachments/assets/a17cf135-e519-4210-ae29-07814195d4ca)

Error Reporting: Perintah error_reporting(E_ALL); digunakan untuk menampilkan semua jenis error yang terjadi selama eksekusi kode PHP.

Proses Form Submit: Ketika tombol submit pada form ditekan, data yang diinputkan (seperti nama, kategori, harga jual, harga beli, stok, dan file gambar) akan diproses.

Pengelolaan File Gambar:

Jika file gambar diupload ($_FILES['file_gambar']), file tersebut dipindahkan ke direktori gambar/.
Nama file akan diubah dengan mengganti spasi menjadi underscore (_), lalu disalin ke folder tujuan.
Variabel $gambar akan menyimpan path file gambar yang telah berhasil diupload.
Query Insert: Data yang diterima dari form akan dimasukkan ke dalam database melalui perintah INSERT INTO, sehingga barang baru dapat disimpan dalam tabel data_barang.

Redirect: Setelah data berhasil ditambahkan, pengguna akan diarahkan kembali ke halaman index.php.

Form HTML: Formulir HTML disediakan untuk menambah data barang, termasuk input untuk nama, kategori, harga jual, harga beli, stok, dan gambar. Form ini menggunakan metode POST dengan tipe multipart/form-data untuk mengakomodasi pengunggahan file.










