## **Repositori ini dibuat untuk memenuhi UTS matakuliah pemrograman mobile 1**  
<br>Nama : Mohamad Adria Vanza 
<br>NIM : 312210171
<br>Kelas : TI.22.B1
<br>Mata Kuliah : Pemrograman Mobile  
**Tugas : Membuat tombol yang setiap diklik dapat bertambah angkanya, namun dengan urutan angka fibonacci, lalu lengkapi dengan fitur toast**  
berikut adalah link video aplikasi yang di jalankan : [tonton video](https://www.youtube.com/shorts/Fj5d-t8HxHg)  
<br>
Source Code:  
* activity_main.Xml

               package com.toast;
               
               import androidx.appcompat.app.AppCompatActivity;
               
               import android.annotation.SuppressLint;
               import android.os.Bundle;
               import android.view.View;
               import android.widget.Button;
               import android.widget.TextView;
               import android.widget.Toast;
               
               import org.w3c.dom.Text;
               
               public class MainActivity extends AppCompatActivity {
                   private int mCount = 0;
                   private int mCountFibo = 0;
                   private TextView mShowCount;
                   private TextView mShowCountFibo;
                   private Button buttonToast;
                   private Button buttonHitung;
                   private Button buttonReset;
               
                   @SuppressLint("MissingInflatedId")
                   @Override
                   protected void onCreate(Bundle savedInstanceState) {
                       super.onCreate(savedInstanceState);
                       setContentView(R.layout.toast_activity);
                       mShowCount = (TextView) findViewById(R.id.textViewNumber);
                       mShowCountFibo = (TextView) findViewById(R.id.textViewNumberFibo);
                       buttonToast = (Button) findViewById(R.id.button_toast);
                       buttonHitung = (Button) findViewById(R.id.button_hitung);
                       buttonReset = (Button) findViewById(R.id.button_reset);
               
                       buttonHitung.setOnClickListener(new View.OnClickListener() {
                           @Override
                           public void onClick(View view) {
                               hitungIncrement(view);
                           }
                       });
                       buttonToast.setOnClickListener(new View.OnClickListener() {
                           @Override
                           public void onClick(View view) {
                               showToast(view);
                           }
                       });
                       buttonReset.setOnClickListener(new View.OnClickListener() {
                           @Override
                           public void onClick(View view) {
                               resetCountDanFibo(view);
                           }
                       });
                   }
                   public void showToast(View view){
                       Toast toast = Toast.makeText(this, "Berhasil diklik", Toast.LENGTH_SHORT);
                       toast.show();
                   }
               
               
               
                   public void hitungIncrement(View view){
                       mCount++;
                       int Fibo = hitungFibonacci(mCount);
                       mCountFibo = Fibo;
                       if(mShowCount != null && mShowCountFibo != null){
                           mShowCount.setText(Integer.toString(mCount));
                           mShowCountFibo.setText(Integer.toString(mCountFibo));
                       }
               
                   }
                   public int hitungFibonacci(int n){
                       if(n <= 1){
                           return n;
                       }
                       int prev = 0;
                       int current = 1;
                       for(int i = 2; i<= n; i++){
                           int next = prev + current;
                           prev = current;
                           current = next;
                       }
                       return current;
                   }
                   public void resetCountDanFibo(View view){
                       mCount = 0;
                       mCountFibo = 0;
                       mShowCount.setText(Integer.toString(mCount));
                       mShowCountFibo.setText(Integer.toString(mCountFibo));
                   }
               }



Penjelasan :
1. linear layout1 diisi dengan 3 textview:
   * jumlah klik pada tombol hitung
   * angka fibonacci terakhir
2. linear layout 2 berisi :
   * button hitung
   * button reset
   * dan button toast


 * MainActivity.Java :

            <resources>
            <string name="app_name">BelajarAndroidToast</string>
            <string name="button_label_toast">Toast</string>
            <string name="button_label_hitung">Hitung</string>
            <string name="hitung_initial_value">0</string>
            <string name="toast_pesan">Berhasil diklik</string>
        </resources>
          <resources>
           <string name="app_name">BelajarAndroidToast</string>
           <string name="button_label_toast">Toast</string>
           <string name="button_label_hitung">Hitung</string>
           <string name="hitung_initial_value">0</string>
           <string name="toast_pesan">Berhasil diklik</string>
       </resources>
