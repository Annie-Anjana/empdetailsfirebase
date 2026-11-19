
# Ex.No:1 To create a employee details fields and to display the employee details using Firebase Database in Android Studio.

# Developed by: ANNIE ANJANA A
# Register number: 212224040025

## AIM:

To create and display the employee details using Firebase Database in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as HelloWorld and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Display the employee details in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
### java program:
```
package com.example.studentdatabase;

import android.os.Bundle;
import android.widget.EditText;
import android.widget.Button;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

import com.google.firebase.database.DatabaseReference;
import com.google.firebase.database.FirebaseDatabase;

public class MainActivity extends AppCompatActivity {

    EditText name, regno, department, year, marks;
    Button add;
    DatabaseReference database;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

        name = findViewById(R.id.name);
        regno = findViewById(R.id.regno);
        department = findViewById(R.id.department);
        year = findViewById(R.id.year);
        marks = findViewById(R.id.marks);
        add = findViewById(R.id.add);

        database = FirebaseDatabase.getInstance().getReference("Students");

        add.setOnClickListener(v -> {

            String n = name.getText().toString().trim();
            String r = regno.getText().toString().trim();
            String d = department.getText().toString().trim();
            String y = year.getText().toString().trim();
            String m = marks.getText().toString().trim();

            if (n.isEmpty() || r.isEmpty() || d.isEmpty()
                    || y.isEmpty() || m.isEmpty()) {

                Toast.makeText(this, "Please enter all details", Toast.LENGTH_SHORT).show();
                return;
            }

            Student student = new Student(n, r, d, y, m);

            database.child(r).setValue(student)
                    .addOnSuccessListener(unused -> {
                        Toast.makeText(this, "Student Added Successfully", Toast.LENGTH_SHORT).show();

                        name.setText("");
                        regno.setText("");
                        department.setText("");
                        year.setText("");
                        marks.setText("");
                    })
                    .addOnFailureListener(e ->
                            Toast.makeText(this, "Error: " + e.getMessage(), Toast.LENGTH_LONG).show());
        });
    }
}
```
### XML program:
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/student_database"
        android:textSize="25sp"
        android:textStyle="bold"
        android:gravity="center"
        android:padding="15dp"/>

    <EditText
        android:id="@+id/name"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/student_name"
        android:autofillHints="name"
        android:inputType="textPersonName"/>

    <EditText
        android:id="@+id/regno"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/register_number"
        android:inputType="number"
        android:importantForAutofill="no"/>

    <EditText
        android:id="@+id/department"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/department"
        android:inputType="text"
        android:importantForAutofill="no"/>

    <EditText
        android:id="@+id/year"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/year"
        android:inputType="number"
        android:importantForAutofill="no"/>

    <EditText
        android:id="@+id/marks"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/marks"
        android:inputType="numberDecimal"
        android:importantForAutofill="no"/>

    <Button
        android:id="@+id/add"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/add_student"/>

</LinearLayout>


```


## OUTPUT
<img width="1917" height="1088" alt="Screenshot 2026-11-19 124527" src="https://github.com/user-attachments/assets/5b786c45-30c9-410c-9981-dc07eda528f4" />

<img width="982" height="642" alt="Screenshot 2026-11-19 124517" src="https://github.com/user-attachments/assets/3f610f90-8910-4b8c-bbab-2f5e0d0ad8e7" />

<img width="381" height="836" alt="Screenshot 2026-11-19 124859" src="https://github.com/user-attachments/assets/eba71b04-f74f-419a-92e4-a96049a4034a" />


## RESULT
Thus a Simple Android Application create a firebase database and to display the employee details using Firbase Real Time Database in Android Studio is developed and executed successfully.
