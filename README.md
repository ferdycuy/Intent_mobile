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
TAMPILAN DESAIN<br>
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

a. Project Hello World = **HelloActivity.java**<br>
b. Project Count = **CountActivity.java**<br>
c. Project Sianida = **SianidaActivity.java**<br>
d. Project Pesan Activity = **PesanActivity.java** dan **Pesan2Activity.java**<br>
e. Project Set Alarm = **MainActivity.java** (karena implicit intent, jadi sourc code untuk set alarm dibuat langsung disini)<br>

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
# SOURCE CODE SEMUA PROJECT
## A. PROJECT HELLO WORD
- activity_hello.xml

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".HelloActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:background="@drawable/bg_bumi"
        android:scaleType="centerCrop"
        tools:layout_editor_absoluteX="0dp"
        tools:layout_editor_absoluteY="-53dp" />

    <TextView
        android:id="@+id/Texthello"
        android:layout_width="283dp"
        android:layout_height="45dp"
        android:fontFamily="courier"
        android:gravity="center"
        android:text="@string/hello_text"
        android:textColor="@color/white"
        android:textSize="15pt"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.496"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.436"
        tools:ignore="TextSizeCheck" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
- HelloActivity.java

```
package com.example.tugassembilan;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;

public class HelloActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_hello);
    }
}
```
## B. PROJECT COUNT
- activity_count.xml
  
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".CountActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@drawable/bg_count"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop" />

    <Button
        android:id="@+id/button_toast"
        android:layout_width="394dp"
        android:layout_height="58dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:background="@color/colorPrimary"
        android:onClick="showToast"
        android:text="@string/button_label_toast"
        android:textAlignment="center"
        android:textColor="@android:color/white"
        android:textSize="10pt"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.777"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/button_count"
        android:layout_width="390dp"
        android:layout_height="51dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="@color/colorPrimary"
        android:onClick="countUp"
        android:text="@string/button_label_count"
        android:textAlignment="center"
        android:textColor="@android:color/white"
        android:textSize="10pt"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <TextView
        android:id="@+id/show_count"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:text="@string/count_initial_value"
        android:textAlignment="center"
        android:textColor="@color/colorPrimary"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/button_toast"
        tools:ignore="RtlCompat" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
- CountActivity.java
  
```
package com.example.tugassembilan;

import android.annotation.SuppressLint;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class CountActivity extends AppCompatActivity {
    private int nCount = 0;

    private TextView nShowCount;

    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_count);
        nShowCount = findViewById(R.id.show_count);
    }

    public void showToast(View view){
        Toast toast = Toast.makeText(this, "Menghitung Bilangan",
                Toast.LENGTH_SHORT);
        toast.show();
    }

    @SuppressLint("SetTextI18n")
    public void countUp(View view){
        nCount++;
        if (nShowCount != null)
            nShowCount.setText(Integer.toString(nCount));
    }
}
```
## C. PROJECT SIANIDA
- activity_sianida.xml

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    tools:context=".SianidaActivity">

    <TextView
        android:id="@+id/article_heading"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@color/colorPrimary"
        android:padding="@dimen/padding_regular"
        android:text="@string/article_title"
        android:textAppearance="@android:style/TextAppearance.DeviceDefault.Large"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    <ScrollView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/article_heading">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">

            <TextView
                android:id="@+id/article_subheading"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:padding="@dimen/padding_regular"
                android:text="@string/article_subtitle"
                android:textAlignment="center"
                android:textAppearance="@android:style/TextAppearance.DeviceDefault"
                android:textColor="#BC7156" />

            <TextView
                android:id="@+id/article"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:autoLink="web"
                android:lineSpacingExtra="@dimen/line_spacing"
                android:padding="@dimen/padding_regular"
                android:text="@string/article_teks"
                tools:ignore="VisualLintLongText" />
        </LinearLayout>
    </ScrollView>
</RelativeLayout>
```
- SianidaActivity.java
```
  package com.example.tugassembilan;

import android.os.Bundle;

import androidx.appcompat.app.AppCompatActivity;

public class SianidaActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_sianida);
    }
}
```
## D. PROJECT PESAN ACTIVITY
- activity_pesan.xml

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".PesanActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/bg_pesan" />

    <TextView
        android:id="@+id/text_header_reply"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="@string/text_header_reply"
        android:textAppearance="@style/TextAppearance.AppCompat.Medium"
        android:textStyle="bold"
        android:visibility="invisible"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>

    <TextView
        android:id="@+id/text_message_reply"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        android:visibility="invisible"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text_header_reply" />

    <Button
        android:id="@+id/button_main"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:layout_marginRight="16dp"
        android:text="@string/button_main"
        android:onClick="LaunchSecondActivity"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        tools:ignore="UsingOnClickInXml"/>

    <EditText
        android:id="@+id/editText_main"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="@string/editText_main"
        android:inputType="textLongMessage"
        android:minHeight="48dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/button_main"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
- activity_pesan2.xml
  
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".Pesan2Activity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/bg_pesan" />

    <TextView
        android:id="@+id/text_header"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="@string/text_header"
        android:textAppearance="@style/TextAppearance.AppCompat.Medium"
        android:textStyle="bold"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/text_message"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text_header" />

    <Button
        android:id="@+id/button_second"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:layout_marginRight="16dp"
        android:text="@string/button_second"
        android:onClick="returnReply"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <EditText
        android:id="@+id/editText_second"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="@string/editText_second"
        android:inputType="textLongMessage"
        android:minHeight="48dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/button_second"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
- PesanActivity.java

```
package com.example.tugassembilan;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

public class PesanActivity extends AppCompatActivity {

    private static final String LOG_TAG = PesanActivity.class.getSimpleName();

    public static final String EXTRA_MESSAGE = "com.example.android.Pesan2Activity.extra.MESSAGE";

    public static final int TEXT_REQUEST = 1;

    private EditText mMessageEditText;

    private TextView mReplyHeadTextView;

    private TextView mReplyTextView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_pesan);

        mMessageEditText = findViewById(R.id.editText_main);
        mReplyHeadTextView = findViewById(R.id.text_header_reply);
        mReplyTextView = findViewById(R.id.text_message_reply);
    }

    public void LaunchSecondActivity(View view) {
        Log.d(LOG_TAG, "Button clicked!");
        Intent intent = new Intent(this, Pesan2Activity.class);
        String message = mMessageEditText.getText().toString();
        intent.putExtra(EXTRA_MESSAGE, message);
        startActivityForResult(intent, TEXT_REQUEST);
    }

    @Override
    public void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);

        if (resultCode == TEXT_REQUEST) {
            if (resultCode == RESULT_OK) {
                String reply = data.getStringExtra(Pesan2Activity.EXTRA_REPLY);

                mReplyHeadTextView.setVisibility(View.VISIBLE);

                mReplyHeadTextView.setText(reply);
                mReplyHeadTextView.setVisibility(View.VISIBLE);
            }
        }
    }
}
```
- Pesan2Activity.java

```
package com.example.tugassembilan;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class Pesan2Activity extends AppCompatActivity {

    public static final String EXTRA_REPLY ="com.example.android.Pesan2Activity.extra.REPLY";

    private EditText mReply;

    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_pesan2);

        mReply = findViewById(R.id.editText_second);

        Intent intent = getIntent();
        String message = intent.getStringExtra(PesanActivity.EXTRA_MESSAGE);

        TextView textView = findViewById(R.id.text_message);
        textView.setText(message);
    }
    public void returnReply(View view){
        String reply = mReply.getText().toString();
        Intent replyIntent = new Intent();
        setResult(RESULT_OK, replyIntent);
        finish();
    }
}
```
## E. PROJECT SET ALARM
- Kita buat buttonnya terlebih dahulu didalam sebuah activity.xml, kita buat di **activity_main.xml**, bersama dengan tombol lainnya.
```
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
```
- lalu tambahkan code implicit intent di **MainActivity.java nya**.
```
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
```
- Lanjut, buka **AndroidManifest.xml** dan tambahkan code berikut untuk izin membuka Alarm
```
<uses-permission android:name="com.android.alarm.permission.SET_ALARM" />
```
Tambahkan code berikut didalam `<application>` agar set alarm dapat berjalan:
```
    <activity
        android:name=".MainActivity"
        android:exported="true">
        <intent-filter>
            <action android:name="android.intent.action.SET_ALARM" />
            <category android:name="android.intent.category.DEFAULT" />
        </intent-filter>
    </activity>
```
## Colors, String, Dimens
- Colors
> Terdapat semua warna dari project

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="grey">#5E5A5A</color>
    <color name="blue">#0004FF</color>
    <color name="green">#6CF388</color>
    <color name="colorPrimary">#3F51B5</color>
    <color name="colorPrimaryDark">#DA883F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="hijautua">#0F500D</color>
</resources>
```
> **NOTE**: Bisa diubah warnanya sesuai selera teman-teman

- Strings
> Terdapat semua string dari project

```
<resources>
    <string name="app_name">Tugas Sembilan</string>

    <string name="project_hello">Project Hello World</string>
    <string name="project_count">Project Count</string>
    <string name="project_sianida">Project Sianida</string>
    <string name="project_pesanactivity">Project Pesan Activity</string>
    <string name="project_set_alarm">Project Set Alarm</string>

    <string name="hello_text">Hello World!</string>

    <string name="button_label_toast">Desk</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value">0</string>
    <string name="toast_message">Project Count</string>

    <string name="button_main">Send</string>
    <string name="text_header_reply">Message Received</string>
    <string name="editText_main">Enter Your Message Here</string>
    <string name="text_header">Reply Received</string>
    <string name="button_second">Reply</string>
    <string name="editText_second">Enter Your Reply Here</string>

    <string name="article_title">Kasus Sianida</string>
    <string name="article_subtitle">ICE COLD!</string>

    <string name="article_teks">
    In a vault deep inside Abbey Road Studios in London — protected by an unmarked, triple-locked, police-alarmed door — are something like 400 hours of unreleased Beatles recordings, starting from June 2, 1962 and ending with the very last tracks recorded for the Let It Be album. The best of the best were released by Apple Records in the form of the 3-volume Anthology series. For more information, see the Beatles Time Capsule at www.rockument.com. \n\n This volume starts with the first new Beatle song, “Free as a Bird” (based on a John Lennon demo, found only on The Lost Lennon Tapes Vol. 28, and covers the very earliest historical recordings, outtakes from the first albums, and live recordings from early concerts and BBC Radio sessions. \n\n
    </string>
</resources>
```
> **NOTE**: Teks Artikel nya saya ambil sedikit biar menghemat tempat

- Dimens
> Code dimens untuk project sianida

```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <dimen name="padding_regular">10dp</dimen>
    <dimen name="line_spacing">5sp</dimen>
</resources>
```

## FINISH
Alhamdulillah telah seslasai :)<br>
TERIMA KASIH





  


