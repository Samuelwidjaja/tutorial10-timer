# Advance Programming Tutorial 10
*Tutorial for Advanced Programming 2024 Module 10 - Faculty of Computer Science, Universitas Indonesia*

Reflection - Timer Future
1.2. Understanding How It Works

![image](https://github.com/Samuelwidjaja/tutorial10-timer/assets/119392779/1fa7c3d5-b398-41d1-b67c-89afd0b42c79)

Dalam kode Rust yang diberikan, terdapat implementasi executor sederhana untuk menjalankan tugas-tugas secara asinkron. Ini melibatkan penggunaan struktur data seperti Task, Spawner, dan Executor, yang berkomunikasi antara spawner dan executor. Urutan output yang dihasilkan adalah "hey hey", "howdy!", dan terakhir "done!". Ini dipengaruhi oleh cara executor menjalankan tugas-tugas asinkron.

Pertama-tama, output "hey hey" dicetak karena itu ada di dalam blok main() yang dieksekusi sebelum tugas-tugas asinkron. Kemudian, tugas asinkron "howdy!" dieksekusi, dan sebelum eksekusinya selesai, "done!" belum dicetak. Executor akan menunggu menggunakan TimerFuture (dalam contoh kode ini, 9 detik) sampai tugas asinkron selesai, baru kemudian mencetak "done!".


