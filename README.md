# Ex.No:4 To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Step 1: Open Android Studio and then click on File -> New -> New project.

Step 2: Then type the Application name as “ExplicitIntent″ and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Write the logic to find factorial of a number in MainActivity file.

Step 7: Design layout in activity_main2.xml.

Step 8: Use Explicit intent in MainActivity2 file to get the result.

Step 9: Save and run the application.


## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: Sathiya Narayanan G
Registeration Number :212221220049
*/
```

activiity_main.xml:

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/maintxt"
        android:layout_width="317dp"
        android:layout_height="38dp"
        android:layout_marginTop="36dp"
        android:fontFamily="sans-serif-medium"
        android:text="@string/factorial_calculator"
        android:textAlignment="center"
        android:textColor="@color/purple_500"
        android:textSize="25sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/text1"
        android:layout_width="181dp"
        android:layout_height="48dp"
        android:layout_marginStart="64dp"
        android:layout_marginTop="240dp"
        android:fontFamily="sans-serif-light"
        android:text="@string/enter_a_number"
        android:textColor="@color/purple_500"
        android:textSize="24sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <EditText
        android:id="@+id/n1"
        android:layout_width="95dp"
        android:layout_height="50dp"
        android:layout_alignEnd="@+id/text1"
        android:layout_marginTop="236dp"
        android:layout_marginEnd="60dp"
        android:autofillHints=""
        android:textColor="#EA80FC"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/btn1"
        android:layout_width="142dp"
        android:layout_height="45dp"
        android:layout_marginBottom="360dp"
        android:background="#2C34CF"
        android:fontFamily="sans-serif-medium"
        android:text="@string/calculate"
        android:textColor="@color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent" />    

    <TextView
        android:id="@+id/resum"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="150dp"
        tools:ignore="MissingConstraints" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
MainActivity.java:

```
package com.example.explicitintent;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import com.example.explicitintent.MainActivity2;

public class MainActivity extends AppCompatActivity {

    public static String Send_Result;
    EditText num1;
    TextView txtrslt;
    Button btn;
    double n,i=1,fact=1;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        num1 = (EditText) findViewById(R.id.n1);
        txtrslt = (TextView) findViewById(R.id.resum);
        btn = (Button) findViewById(R.id.btn1);
        btn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                n = Double.parseDouble(num1.getText().toString());
                while (i<=n)
                {
                    fact=fact*i;
                    i++;
                }
                String message = Double.toString(fact);
                Intent myIntent = new Intent(MainActivity.this, MainActivity2.class);
                myIntent.putExtra(Send_Result, message);
                startActivity(myIntent);
            }
        });
    }
}
```
activity_main2.xml:

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/textView"
        android:layout_width="132dp"
        android:layout_height="40dp"
        android:fontFamily="sans-serif-smallcaps"
        android:text="@string/resulT"
        android:textColor="@color/purple_500"
        android:textSize="34sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.229"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.413" />

    <TextView
        android:id="@+id/reslt"
        android:layout_width="187dp"
        android:layout_height="47dp"
        android:text="@string/_00_00"
        android:textColor="@color/purple_500"
        android:textSize="38sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.928"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.407" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
MainActivity2.java:

```
package com.example.explicitintent;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;

public class MainActivity2 extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
        Intent intent = getIntent();
        String message = intent.getStringExtra(com.example.explicitintent.MainActivity.Send_Result);
        TextView textView = findViewById(R.id.reslt);
        textView.setText(message);
    }
}
```
## OUTPUT

![image](https://github.com/kannan0071/MAD-Ex.No-4/assets/119641638/59f0a848-5d51-43ec-97d8-e7ff2e886b0b)

![image](https://github.com/kannan0071/MAD-Ex.No-4/assets/119641638/c2bff05c-91f8-4e05-8654-634292e84e28)

![image](https://github.com/kannan0071/MAD-Ex.No-4/assets/119641638/351a90e1-3b66-4654-af78-235d0fbe16bf)

![image](https://github.com/kannan0071/MAD-Ex.No-4/assets/119641638/d4b12871-0621-4ada-af5c-8d724e676121)

![WhatsApp Image 2023-05-25 at 13 06 56](https://github.com/kannan0071/MAD-Ex.No-4/assets/119641638/ae9fc1a6-8344-4364-ba35-9cddcc690699)

![WhatsApp Image 2023-05-25 at 13 07 05](https://github.com/kannan0071/MAD-Ex.No-4/assets/119641638/ae89a2a5-f6d5-44d6-b61e-7b7e71b3221f)



## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.

