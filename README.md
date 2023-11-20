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
            android:src="@drawable/logo"
            android:gravity="center" />
    </item>
</layer-list>
```

- Lanjut, buka **themes.xml** yang letaknya ada di res>values>themes, dan tambahkan code ini didalam resourcesnya :

 ``` <style name="SplashScreen" parent="Theme.MaterialComponents.DayNight.NoActionBar">
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
        android:src="@drawable/background" />

    <Button
        android:id="@+id/btnHelloWorld"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="btnHelloWorld"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="200dp"
        android:text="@string/project_hello"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnProjectCount"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="btnCount"
        android:layout_below="@+id/btnHelloWorld"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="20dp"
        android:text="@string/project_count"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnProjectSianida"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="btnSianida"
        android:layout_below="@+id/btnProjectCount"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="20dp"
        android:text="@string/project_sianida"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnTwoActivity"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="btnTwoActivity"
        android:layout_below="@+id/btnProjectSianida"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="20dp"
        android:text="@string/project_twoactivity"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnSetAlarm"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="btnSetAlarm"
        android:layout_below="@+id/btnTwoActivity"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="20dp"
        android:text="@string/project_set_alarm"
        tools:ignore="UsingOnClickInXml" />

</RelativeLayout>
```
> **NOTE:** Background nya sesuaikan dengan keinginan kalian ya, dan ini aku memanggil nama fileku yaitu background `android:src="@drawable/background" ` nama file gambarnya sesuaikan dengan yang kalian buat yaa
