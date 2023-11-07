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

               package com.example.toast;
              
              import androidx.appcompat.app.AppCompatActivity;
              
              import android.annotation.SuppressLint;
              import android.os.Bundle;
              import android.view.View;
              import android.widget.Button;-
              import android.widget.TextView;
              import android.widget.Toast;
              
              import com.example.toast.R;
              
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
- linear layout1 diisi dengan textview:
   * jumlah klik pada tombol hitung
   * angka fibonacci terakhir


 *toast_activity.xml :

            <?xml version="1.0" encoding="utf-8"?>
      <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
          android:layout_width="match_parent"
          android:layout_height="match_parent">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@color/teal_200"
        android:gravity="center"
        android:orientation="vertical"
        android:paddingLeft="40dp"
        android:paddingRight="40dp">


        <TextView
            android:id="@+id/textView3"
            android:layout_marginBottom="100dp"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Belajar Toast!"
            android:textAlignment="center"
            android:textSize="30sp"/>

        <TextView
            android:id="@+id/textView2"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="Increment"
            android:textAlignment="center"
            android:textSize="24sp" />

        <TextView
            android:id="@+id/textViewNumber"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="0"
            android:textAlignment="center"
            android:textSize="24sp" />

        <TextView
            android:id="@+id/textView"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="Fibonacci"
            android:textAlignment="center"
            android:textSize="24sp" />

        <TextView
            android:id="@+id/textViewNumberFibo"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="0"
            android:textAlignment="center"
            android:textColor="@color/black"
            android:textFontWeight="600"
            android:textSize="24sp" />


    </LinearLayout>

    <Button
        android:id="@+id/button_toast"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentLeft="true"
        style="@style/Widget.AppCompat.Button"
        android:text="Toast"/>

    <Button
        android:id="@+id/button_reset"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_marginEnd="10dp"
        android:layout_marginBottom="10dp"
        android:backgroundTint="@color/red"
        android:text="Reset"
        android:textAlignment="center"
        android:textColor="@color/white" />

    <Button
        android:id="@+id/button_hitung"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentRight="true"
        android:backgroundTint="@color/teal_700"
        android:layout_marginRight="10dp"
        android:textColor="@color/white"
        android:text="Hitung"/>


    </RelativeLayout>


 linear layout berisi :
   * button hitung
   * button reset
   * dan button toast


 *colors.xml :
 
      <?xml version="1.0" encoding="utf-8"?>
      <resources>
          <color name="black">#FF000000</color>
          <color name="white">#FFFFFFFF</color>
          <color name="purple_200">#FFBB86FC</color>
          <color name="purple_500">#FF6200FE</color>
          <color name="purple_700">#FF370083</color>
          <color name="teal_200">#FF03DAC5</color>
          <color name="teal_700">#FFBB86FC</color>
          <color name="red">#D10000</color>
      </resources>


*strings.xml :
          
     <resources>
    <string name="app_name">BelajarAndroidToast</string>
    <string name="button_label_toast">Toast</string>
    <string name="button_label_hitung">Hitung</string>
    <string name="hitung_initial_value">0</string>
    <string name="toast_pesan">Berhasil diklik</string>
    </resources>


      
