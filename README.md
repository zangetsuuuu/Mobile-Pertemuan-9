Nama : Rafif Isdarufa Athallah

NIM : 312210299

Kelas : TI.22.A3

---

## Tugas 9

![Tugas](./images/Tugas%209.png)

## Launcher Splash Logo

### XML

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#ffffff">

    <ImageView
        android:id="@+id/logoImageView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:src="@drawable/launcher_logo" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/logoImageView"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="16dp"
        android:textSize="24sp"
        android:textColor="#000000" />
</RelativeLayout>
```

- `id (@+id/logoImageView)` digunakan untuk menetapkan ID unik untuk elemen `ImageView` ini. ID ini dapat digunakan dalam kode Java untuk merujuk ke `ImageView`.
- `layout_width` dan `layout_height` digunakan untuk menentukan lebar dan tinggi elemen `ImageView`.
- `layout_centerInParent` digunakan untuk menempatkan `ImageView` di tengah *parent* *(RelativeLayout)* baik secara horizontal maupun vertikal.
- `src (@drawable/launcher_logo)` digunakan untuk menetapkan sumber gambar untuk `ImageView`. Di sini, gambar diambil dari folder *res/drawable* dengan nama file **"launcher_logo"**.

---

### Java

```java
package id.co.myapplication;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;

import androidx.appcompat.app.AppCompatActivity;

public class SplashActivity extends AppCompatActivity {
    private static final int SPLASH_TIMEOUT = 5000;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_splash);

        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                Intent intent = new Intent(SplashActivity.this, MainActivity.class);
                startActivity(intent);
                finish();
            }
        }, SPLASH_TIMEOUT);
    }
}
```

- `SplashActivity` adalah kelas yang menggambarkan aktivitas pembukaan *(splash screen)* dalam aplikasi Android.
- `SPLASH_TIMEOUT` digunakan untuk menyimpan waktu penundaan sebelum aktivitas ini beralih ke aktivitas lain (dalam kasus ini, `MainActivity`).
- Metode `onCreate` dipanggil ketika aktivitas dibuat. Di sini, layout dari aktivitas ditetapkan menggunakan `setContentView` dengan referensi ke layout XML `activity_splash`.
- `Handler` digunakan untuk membuat penundaan selama `SPLASH_TIMEOUT` (5000 milidetik atau 5 detik).
- Setelah penundaan selesai, dijalankan `run()` yang berisi logika untuk beralih ke `MainActivity`.
- Buat objek `Intent` untuk memulai `MainActivity`, dilanjutkan dengan pemanggilan `startActivity(intent)` untuk memulai aktivitas berikutnya.
- Kemudian, menggunakan `finish()` untuk menutup `SplashActivity`, sehingga pengguna tidak dapat kembali ke aktivitas pembukaan setelah berhasil beralih ke `MainActivity`.

---

## Menampilkan Seluruh *Project*

### XML

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <Button
        android:id="@+id/button_main_hello"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="50dp"
        android:layout_marginTop="280dp"
        android:layout_marginEnd="50dp"
        android:backgroundTint="@color/btn_color"
        android:onClick="launchHelloActivity"
        android:text="@string/project_hello"
        android:textSize="12sp"
        android:textStyle="bold"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/button_main_toast"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="50dp"
        android:layout_marginEnd="50dp"
        android:backgroundTint="@color/btn_color"
        android:text="@string/project_count"
        android:onClick="launchToastActivity"
        android:textSize="12sp"
        android:textStyle="bold"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_main_hello" />

    <Button
        android:id="@+id/button_main_sianida"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="50dp"
        android:layout_marginEnd="50dp"
        android:backgroundTint="@color/btn_color"
        android:onClick="launchSianidaActivity"
        android:text="@string/project_sianida"
        android:textSize="12sp"
        android:textStyle="bold"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_main_toast" />

    <Button
        android:id="@+id/button_main_twoActivity"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="50dp"
        android:layout_marginEnd="50dp"
        android:backgroundTint="@color/btn_color"
        android:onClick="launchTwoActivity"
        android:text="@string/project_two_act"
        android:textSize="12sp"
        android:textStyle="bold"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_main_sianida" />

    <Button
        android:id="@+id/button_main_Alarm"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="50dp"
        android:layout_marginEnd="50dp"
        android:backgroundTint="@color/btn_color"
        android:onClick="createAlarm"
        android:text="@string/project_alarm"
        android:textSize="12sp"
        android:textStyle="bold"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_main_twoActivity" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

- Kode XML di atas merupakan antarmuka pengguna Android dengan konfigurasi yang serupa, tetapi memanggil metode yang berbeda ketika tombol tersebut diklik. Setiap tombol memiliki properti-properti seperti `android:id, android:layout_width, android:layout_height`, dan lainnya yang serupa, menciptakan konsistensi dalam tata letak dan penampilan.
- Namun, perbedaan terletak pada atribut `android:onClick`, di mana setiap tombol diprogram untuk masuk ke `activity` yang berbeda ketika tombol tersebut diklik. Yaitu:

    - Project Hello
    - Project Count
    - Project Sianida
    - Project Two Activity
    - Project Alarm

---

### Java

```java
package id.co.myapplication;

import android.content.Intent;
import android.os.Bundle;
import android.provider.AlarmClock;
import android.view.View;

import androidx.appcompat.app.AppCompatActivity;

import java.util.ArrayList;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstance) {
        super.onCreate(savedInstance);
        setContentView(R.layout.activity_main);
    }

    public void launchHelloActivity(View view) {
        Intent tampilHello = new Intent(MainActivity.this, MainHello.class);
        startActivity(tampilHello);
    }

    public void launchToastActivity(View view) {
        Intent tampilToast = new Intent(MainActivity.this, MainToast.class);
        startActivity(tampilToast);
    }

    public void launchSianidaActivity(View view) {
        Intent tampilSianida = new Intent(MainActivity.this, MainSianida.class);
        startActivity(tampilSianida);
    }

    public void launchTwoActivity(View view) {
        Intent tampilTwo = new Intent(MainActivity.this, MainFirstActivity.class);
        startActivity(tampilTwo);
    }

    public void createAlarm(View view) {
        ArrayList<Integer> alarmDays = new ArrayList<>();

        alarmDays.add(2);
        alarmDays.add(3);
        alarmDays.add(4);

        Intent intent = new Intent(AlarmClock.ACTION_SET_ALARM)

                .putExtra(AlarmClock.EXTRA_DAYS, alarmDays)

                .putExtra(AlarmClock.EXTRA_MESSAGE, "Wake up!")

                .putExtra(AlarmClock.EXTRA_HOUR, 7)

                .putExtra(AlarmClock.EXTRA_MINUTES, 30)

                .putExtra(AlarmClock.EXTRA_VIBRATE, false)

                .putExtra(AlarmClock.EXTRA_RINGTONE, "VALUE_RINGTONE_SILENT");

        if (intent.resolveActivity(getPackageManager()) != null) {

            startActivity(intent);
        }
    }
}
```

- Mendeklarasikan penggunaan pustaka `ArrayList` dari paket `java.util`.
- Mendeklarasikan kelas `MainActivity` yang merupakan aktivitas utama dalam aplikasi. Kelas ini meng-*extend* `AppCompatActivity`, yang merupakan kelas dasar untuk aktivitas di Android.
- Metode `onCreate()` dipanggil ketika aktivitas dibuat. Di sini, *layout* dari aktivitas ditetapkan menggunakan setContentView dengan referensi ke layout XML `activity_main`.
- Metode `launchHelloActivity()` dipanggil saat tombol dengan `android:onClick="launchHelloActivity"` diklik, dan membuat objek `Intent` untuk beralih ke aktivitas `MainHello` dan memulai aktivitas tersebut.
- Metode `launchToastActivity()` dipanggil saat tombol dengan `android:onClick="launchToastActivity"` diklik, dan membuat objek `Intent` untuk beralih ke aktivitas `MainToast` dan memulai aktivitas tersebut.
- Metode `launchSianidaActivity()` dipanggil saat tombol dengan `android:onClick="launchSianidaActivity"` diklik, dan membuat objek `Intent` untuk beralih ke aktivitas `MainSianida` dan memulai aktivitas tersebut.
- Metode `launchHelloActivity()` dipanggil saat tombol dengan `android:onClick="launchTwoActivity"` diklik, dan membuat objek `Intent` untuk beralih ke aktivitas `MainFirstActivity` dan memulai aktivitas tersebut.
- Metode `createAlarm()` dipanggil saat tombol dengan `android:onClick="createAlarm"` diklik.
- Inisiasi objek `ArrayList<Integer>` dengan tujuan menyimpan informasi mengenai hari-hari dimana alarm dijadwalkan akan berbunyi.
- Membuat objek `Intent` untuk mengatur alarm menggunakan `AlarmClock.ACTION_SET_ALARM`.
- Menambahkan beberapa ekstra seperti `EXTRA_DAYS`, `EXTRA_MESSAGE`, `EXTRA_HOUR`, dan lainnya ke dalam `intent`.

---

## Output

![Group 1](./images/Group%201.png)
![Group 2](./images//Group%202.png)

---

## Sekian, terimakasih.