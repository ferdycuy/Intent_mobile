# TUGAS PERTEMUAN 9

  Nama    : Ferdyana Eka Prasetya<br>
  NIM     : 312210121<br>
  Kelas   : TI.22.A.1</br>
  Dosen   : Donny Maulana, S.Kom., M.M.S.I.</br>

 ## Tugas 
  ![tugas 9 mobile](https://github.com/ferdycuy/Intent_mobile/assets/115714443/e1316f9f-b39e-41af-aa31-ea4408dd100d)

 ## 1.Launcher Splash Logo
Pertama, kita akan membuat Launcher Splash Logo, atau menampilkan logo saat kita pertama kali membuka aplikasi.<br>
caranya : <br>
- Membuat sebuah Drawable Resource File baru, untuk background logo launcher kita nanti. Buat file baru pada directory res/drawable
> Klik kanan drawable>new>new resource file>buat nama file>ok.
- Setelah file berhasil dibuat, kita tambahkan terlebih dahulu logo yang kita miliki ke dalam project kita.
> copy logonya>lalu paste di folder drawable tadi.
- Lanjut membuka backgroundlauncher.xml yang sudah kita buat tadi, dan masukan code ini :

```
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@color/grey"/>
    <item>
        <bitmap
            android:src="@drawable/bg_kp"
            android:gravity="center" />
    </item>

</layer-list>
```

- Lanjut, buka **themes.xml** yang letaknya ada di res>values>themes, dan tambahkan code ini didalam resourcesnya :

 ```
<style name="SplashScreen" parent="Theme.MaterialComponents.DayNight.NoActionBar">
        <item name="android:windowBackground">@drawable/backgroundlauncher</item>
        <item name="android:statusBarColor">?attr/colorOnPrimary</item>
  </style> 
  ```

- Lanjut, kita buat java class nya, supaya splashscreen bisa berjalan.
  > Klik File Java>klik kanan com.example yang paling atas>new>java class>buat nama file>enter.<br>

didalam **SplashScreen.java** , kita buat codenya, seperti ini :

```
 package com.example.tugassembilan;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;

import androidx.appcompat.app.AppCompatActivity;

public class SplashScreen extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                startActivity(new Intent(SplashScreen.this, MainActivity.class));
                finish();
            }
        }, 2500);
    }
}
```
- Lanjut, Buka **AndroidManifest.xml** dan tambahkan code berikut didalam `<application>` :

```
        <activity
            android:name=".SplashScreen"
            android:exported="true"
            android:theme="@style/SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
```
Sudah oke, perintah membuat Launcher Splash Logo sudah selesai, lanjut ke tahap berikutnya, membuat menu untuk menampilkan semua project yang sudah dibuat pada pertemuan sebelumnya.

# 2.Menu Utama
- Kita akan membuat tampilan menunya di **activity_main.xml**, berikut code nya:
  > **NOTE**: Jika awal waktu pembuatan project kita memilih template empty views activity, maka di layout otomatis terbuat file activity_main.xml dan di java akan terbuat MainActivity.java

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/bg_mainbutterfly" />

    <Button
        android:id="@+id/btnHelloWorld"
        android:layout_width="190dp"
        android:layout_height="wrap_content"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="200dp"
        android:onClick="btnHelloWorld"
        android:text="@string/project_hello"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnProjectCount"
        android:layout_width="190dp"
        android:layout_height="wrap_content"
        android:layout_below="@+id/btnHelloWorld"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="20dp"
        android:onClick="btnCount"
        android:text="@string/project_count"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnProjectSianida"
        android:layout_width="190dp"
        android:layout_height="wrap_content"
        android:layout_below="@+id/btnProjectCount"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="20dp"
        android:onClick="btnSianida"
        android:text="@string/project_sianida"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnPesanActivity"
        android:layout_width="190dp"
        android:layout_height="wrap_content"
        android:layout_below="@+id/btnProjectSianida"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="21dp"
        android:onClick="btnTwoActivity"
        android:text="@string/project_pesanactivity"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnSetAlarm"
        android:layout_width="190dp"
        android:layout_height="wrap_content"
        android:layout_below="@+id/btnPesanActivity"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="20dp"
        android:onClick="btnSetAlarm"
        android:text="@string/project_set_alarm"
        tools:ignore="UsingOnClickInXml" />

</RelativeLayout>
```
> **NOTE:** Background nya sesuaikan dengan keinginan kalian ya, dan ini aku memanggil nama fileku yaitu background `android:src="@drawable/background" ` nama file gambarnya sesuaikan dengan yang kalian buat yaa, caranya sama tinggal copy>paste di folder drawable.<br>
TAMPILAN DESAIN
![desain menu mobile](https://github.com/ferdycuy/Intent_mobile/assets/115714443/1a51527d-5a46-4d29-ab43-c773a852d518)

- Lanjut, kita buka **MainActivity.java** untuk menambahkan code intent untuk masing-masing tombol.

  ```
  package com.example.tugassembilan;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.btnSetAlarm).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Panggil metode untuk mengatur alarm
                setAlarm();
            }
        });
    }
    private void setAlarm() {
        Intent alarm = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
        startActivity(alarm);
    }

    public void btnHelloWorld(View view) {
        Intent helloworld = new Intent(MainActivity.this, HelloActivity.class);
        startActivity(helloworld);
    }

    public void btnCount(View view) {
        Intent count = new Intent(MainActivity.this, CountActivity.class);
        startActivity(count);
    }

    public void btnSianida(View view) {
        Intent sianida = new Intent(MainActivity.this, SianidaActivity.class);
        startActivity(sianida);
    }

    public void btnTwoActivity(View view) {
        Intent twoact = new Intent(MainActivity.this, PesanActivity.class);
        startActivity(twoact);
    }
}
```
> Dari semua button a - d menggunakan explicit intent, sedangkan button e. (Project Set Alarm) menggunakan implicit intent.

Menu Halaman Utama Sudah Selesai dibuat, lanjutt

# 3. AndroidManifest.xml
Didalam **AndroidManifest.xml** ini kita tambahkan semua .java dari semua project kita sebelumnya. Berikut nama .java dari berbagai project yang telah saya buat:

a. Project Hello World = **HelloActivity.java**
b. Project Count = **CountActivity.java**
c. Project Sianida = **SianidaActivity.java**
d. Project Pesan Activity = **PesanActivity.java** dan **Pesan2Activity.java**
e. Project Set Alarm = **MainActivity.java** (karena implicit intent, jadi sourc code untuk set alarm dibuat langsung disini)
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-permission
        android:name="com.android.alarm.permission.SET_ALARM" />
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Tugassembilan"
        tools:targetApi="31">

        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.SET_ALARM" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>

        <activity
            android:name=".HelloActivity"
            android:exported="true" />

        <activity
            android:name=".PesanActivity"
            android:exported="true" />

        <activity
            android:name=".Pesan2Activity"
            android:exported="true" />

        <activity
            android:name=".CountActivity"
            android:exported="true" />

        <activity
            android:name=".SianidaActivity"
            android:exported="true" />

        <activity
            android:name=".SplashScreen"
            android:exported="true"
            android:theme="@style/SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```
# HASIL RUN
Berikut Video Runnya :

https://github.com/ferdycuy/Intent_mobile/assets/115714443/9a54d15d-ee61-4c4a-af8b-22f87ad16d88


  


