# Advance Programming Tutorial 10
*Tutorial for Advanced Programming 2024 Module 10 - Faculty of Computer Science, Universitas Indonesia*

Reflection - Timer Future
1.2. Understanding How It Works

![image](https://github.com/Samuelwidjaja/tutorial10-timer/assets/119392779/1fa7c3d5-b398-41d1-b67c-89afd0b42c79)

Dalam kode Rust yang diberikan, terdapat implementasi executor sederhana untuk menjalankan tugas-tugas secara asinkron. Ini melibatkan penggunaan struktur data seperti Task, Spawner, dan Executor, yang berkomunikasi antara spawner dan executor. Urutan output yang dihasilkan adalah "hey hey", "howdy!", dan terakhir "done!". Ini dipengaruhi oleh cara executor menjalankan tugas-tugas asinkron.

Pertama-tama, output "hey hey" dicetak karena itu ada di dalam blok main() yang dieksekusi sebelum tugas-tugas asinkron. Kemudian, tugas asinkron "howdy!" dieksekusi, dan sebelum eksekusinya selesai, "done!" belum dicetak. Executor akan menunggu menggunakan TimerFuture (dalam contoh kode ini, 9 detik) sampai tugas asinkron selesai, baru kemudian mencetak "done!".

1.3. Multiple Spawn and removing drop

Multiple Spawn and Removing Drop:

![image](https://github.com/Samuelwidjaja/tutorial10-timer/assets/119392779/524a6582-03b5-45e4-b0cf-5ee77b9cecb5)

Multiple Spawn and Put Drop:

![image](https://github.com/Samuelwidjaja/tutorial10-timer/assets/119392779/7ed2b0dc-094d-46d1-ab66-a092a01b4c7c)

Fungsi spawner.spawn(async { ... }) bertugas untuk menginisiasi tugas-tugas asinkron yang nantinya akan dieksekusi oleh Executor. Sementara itu, fungsi drop(spawner) bertugas untuk memberi tanda bahwa tidak akan ada lagi tugas yang akan dimasukkan ke dalam antrian tugas yang akan dieksekusi.

Output yang dihasilkan ketika ada drop(spawner) dan ketika tidak, berbeda. Perbedaan ini terjadi karena tanpa drop(spawner), executor akan terus menunggu tugas baru untuk dieksekusi, sehingga tugas-tugas yang telah siap akan langsung dieksekusi. Namun, dengan adanya drop(spawner), executor mengetahui bahwa tidak akan ada tugas baru yang masuk ke dalam antrian, sehingga akan menyelesaikan terlebih dahulu tugas-tugas yang masih ada di dalam antrian sebelum mengakhiri eksekusi. Inilah yang menyebabkan urutan output pada bagian "done" menjadi berbeda.

