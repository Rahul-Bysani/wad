//PART A1

//activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical" tools:context=".MainActivity" >
    <TextView
        android:text="RED"
        android:textSize="25dp"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:background="#B11212"
        android:layout_weight=".14"
        android:gravity="center"
        android:textColor="#000"
        />

    <TextView
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:layout_weight=".14"
        android:background="#ffa500"
        android:gravity="center"
        android:text="ORANGE"
        android:textSize="25dp"
        android:textColor="#000" />
    <TextView
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:text="YELLOW"
        android:textSize="25dp"
        android:background="#ffff00"
        android:layout_weight=".14"
        android:gravity="center"
        android:textColor="#000"/>
    ﻿

    <TextView
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:text="GREEN"
        android:textSize="25dp"
        android:background="#0f0"
        android:layout_weight=".15"
        android:gravity="center"
        android:textColor="#000"/>
    <TextView
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:text="BLUE"
        android:textSize="25dp"
        android:background="#00f"
        android:layout_weight=".14"
        android:gravity="center"
        android:textColor="#000"/>
    <TextView
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:text="INDIGO"
        android:textSize="25dp"
        android:background="#4b0082"
        android:layout_weight=".15"
        android:gravity="center"
        android:textColor="#000"/>
    <TextView
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:text="VIOLET"
        android:textSize="25dp"
        android:background="#ee82ee"
        android:layout_weight=".14"
        android:gravity="center"
        android:textColor="#000"/>
</LinearLayout>

//MainActivity.java

package com.example.linearlayout_rainbow_1;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

    }
}



//PART A2
//activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/activity_main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#1AD6D0">

    <EditText
        android:id="@+id/text1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="18dp"
        android:layout_marginTop="150dp"
        android:layout_marginRight="18dp"
        android:background="#fff"
        android:hint="Username"
        android:padding="8dp" />

    <EditText
        android:id="@+id/text2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="18dp"
        android:layout_marginRight="18dp"
        android:padding="8dp"
        android:background="#fff"
        android:hint="Password"
        android:layout_marginTop="12dp"
        android:layout_below="@+id/text1" />
    <Button
        android:id="@+id/login"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Login"
        android:textColor="#FFF"
        android:layout_below="@+id/text2" android:layout_marginTop="17dp"
        android:layout_alignStart="@+id/text2"
        android:layout_alignEnd="@+id/text2" />
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/text3"
        android:textColor="#f00"
        android:text="Not a member?Sign up now"
        android:layout_below="@+id/login"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="30dp" />
</RelativeLayout>


//MainActivity.java

package com.example.relativelayout_loginscreen_2;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button b1 = (Button) findViewById(R.id.login);
        EditText e1 = (EditText) findViewById(R.id.text1);

        b1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                Toast.makeText(MainActivity.this, "You tried to login !!", Toast.LENGTH_SHORT).show();

            }
        });


    }
}


//PART A3
//activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="horizontal"
    tools:context=".MainActivity">


    <EditText
        android:id="@+id/et1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentEnd="false"
        android:layout_centerHorizontal="true"
        android:layout_marginStart="90dp"
        android:layout_marginTop="90dp"
        android:layout_marginEnd="90dp"
        android:layout_marginBottom="90dp"
        android:ems="10"
        android:hint="Enter First Number"
        android:inputType="number" />

    <EditText
        android:id="@+id/et2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentEnd="false"
        android:layout_alignParentBottom="true"
        android:layout_centerHorizontal="true"
        android:layout_marginEnd="201dp"
        android:layout_marginBottom="512dp"
        android:ems="10"
        android:hint="Enter Second Number"
        android:inputType="number" />

    <Button
        android:id="@+id/Add"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_alignParentBottom="true"
        android:layout_marginStart="162dp"
        android:layout_marginEnd="161dp"
        android:layout_marginBottom="386dp"
        android:text="Add +" />

    <Button
        android:id="@+id/Sub"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_alignParentBottom="true"
        android:layout_marginStart="162dp"
        android:layout_marginEnd="161dp"
        android:layout_marginBottom="312dp"
        android:text="Sub -" />

    <Button
        android:id="@+id/Div"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_alignParentBottom="true"
        android:layout_marginStart="162dp"
        android:layout_marginEnd="161dp"
        android:layout_marginBottom="232dp"
        android:text="Div /" />

    <Button
        android:id="@+id/Mul"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_alignParentBottom="true"
        android:layout_marginStart="162dp"
        android:layout_marginEnd="161dp"
        android:layout_marginBottom="149dp"
        android:text="Mul *" />

    <TextView
        android:id="@+id/t"
        android:layout_width="100dp"
        android:layout_height="40dp"
        android:layout_above="@+id/Add"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="160dp"
        android:layout_marginEnd="163dp"
        android:layout_marginBottom="18dp"
        android:hint="Answer"
        android:text=""
        android:textAlignment="center"
        android:textColor="#000000"
        android:textColorHint="#170D0D" />

</RelativeLayout>

//MainActivity.java
package com.example.calculator;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {


    EditText et1, et2;      Button Add,Sub,Div,Mul;     TextView t;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        et1 =  findViewById(R.id.et1);
        et2 =  findViewById(R.id.et2);

        Add = findViewById(R.id.Add);
        Sub = findViewById(R.id.Sub);
        Div = findViewById(R.id.Div);
        Mul = findViewById(R.id.Mul);

          t = findViewById(R.id.t);

        Add.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                int num1, num2;
                num1 = Integer.parseInt(et1.getText().toString());
                num2 = Integer.parseInt(et2.getText().toString());
                int a = num1 + num2;
                t.setText("Result = "+a);
            }

        });

        Sub.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                int num1, num2, a ;
                num1 = Integer.parseInt(et1.getText().toString());
                num2 = Integer.parseInt(et2.getText().toString());
                a = num1 - num2;
                t.setText("Result = "+a);
            }
        });


        Div.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                int num1, num2, a ;
                num1 = Integer.parseInt(et1.getText().toString());
                num2 = Integer.parseInt(et2.getText().toString());
                a = num1 / num2;
                t.setText("Result = "+a);
            }
        });


        Mul.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                int num1, num2, a ;
                num1 = Integer.parseInt(et1.getText().toString());
                num2 = Integer.parseInt(et2.getText().toString());
                a = num1 * num2;
                t.setText("Result = "+a);
            }
        });

    }
}



//PART A4
//activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <ImageView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/imageview"/>
</RelativeLayout>

//MainActivity.java

package com.example.graphical_design;

import androidx.appcompat.app.AppCompatActivity;
import android.app.Activity;
import android.graphics.*;
import android.graphics.drawable.BitmapDrawable;
import android.widget.ImageView;
import android.os.Bundle;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Bitmap bg = Bitmap.createBitmap(720,1280, Bitmap.Config.ARGB_8888);

        ImageView i = (ImageView) findViewById(R.id.imageview);
        i.setBackground(new BitmapDrawable(bg));

        Canvas canvas = new Canvas(bg);

        Paint paint = new Paint();
        paint.setTextSize(50);

        paint.setColor(Color.BLUE);
        canvas.drawText("Rectangle",420,150,paint);
        canvas.drawRect(400,200,650,700,paint);

        paint.setColor(Color.RED);
        canvas.drawText("Circle",120,150,paint);
        canvas.drawCircle(200,350,150,paint);


        paint.setColor(Color.BLACK);
        canvas.drawText("Line",480,800,paint);
        canvas.drawLine(520,850,520,1150,paint);

        paint.setColor(Color.GREEN);
        canvas.drawText("Square",120,800,paint);
        canvas.drawRect(50,850,350,1150,paint);



    }
}

//PART A6
//activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="Activity Lifecycle"
        android:textSize="50dp"
        android:textColor="@android:color/holo_blue_dark"/>

</RelativeLayout>

//MainActivity.java
package com.example.activity_lifecycle2;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.util.Log;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Log.d("Activity_Lifecycle","onCreate invoked");
        Toast.makeText(MainActivity.this, "Create", Toast.LENGTH_SHORT).show();
    }
    @Override
    protected void onStart() {
        super.onStart();
        Log.d("Activity_Lifecycle","onStart invoked");
        Toast.makeText(MainActivity.this, "Start", Toast.LENGTH_SHORT).show();
    }
    @Override
    protected void onResume() {
        super.onResume();
        Log.d("Activity_Lifecycle","onResume invoked");
        Toast.makeText(MainActivity.this, "Resume", Toast.LENGTH_SHORT).show();
    }
    @Override
    protected void onPause() {
        super.onPause();
        Log.d("Actiity_Lifecycle","onPause invoked");
        Toast.makeText(MainActivity.this, "Pause", Toast.LENGTH_SHORT).show();
    }
    @Override
    protected void onStop() {
        super.onStop();
        Log.d("Activity_Lifecycle","onStop invoked");
        Toast.makeText(MainActivity.this, "Stop", Toast.LENGTH_SHORT).show();
    }
    @Override
    protected void onRestart() {
        super.onRestart();
        Log.d("Activity_Lifecycle","onRestart invoked");
        Toast.makeText(MainActivity.this, "Restart", Toast.LENGTH_SHORT).show();
    }
    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.d("Activity_Lifecycle","onDestroy invoked");
        Toast.makeText(MainActivity.this, "Destroy", Toast.LENGTH_SHORT).show();
    }
}



//PART B2
//activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/button1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="136dp"
        android:layout_marginTop="326dp"
        android:layout_marginEnd="132dp"
        android:shadowColor="@color/cardview_light_background"
        android:text="call"
        android:textSize="30dp" />

    <EditText
        android:id="@+id/editText1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="102dp"
        android:layout_marginTop="209dp"
        android:layout_marginEnd="99dp"
        android:ems="10" />

</RelativeLayout>

//MainActivity.java
package com.example.implicity;

import android.net.Uri;
import android.os.Bundle;
import android.app.Activity;
import android.content.Intent;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.*;


public class MainActivity extends Activity {
    EditText editText1;
    Button button1;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState); setContentView(R.layout.activity_main); //Getting the edittext and button instance

        editText1= (EditText) findViewById(R.id.editText1);
        button1= (Button) findViewById(R.id.button1);
//Performing action on button click
        button1.setOnClickListener(new OnClickListener() {
            @Override
            public void onClick(View arg0) {
                String number=editText1.getText().toString();

                Intent callIntent = new Intent(Intent.ACTION_DIAL);
                callIntent.setData(Uri.parse("tel: "+number));
                startActivity(callIntent);
            }

        });

    }

}

//PART B3
//activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<AbsoluteLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_x="85dp"
        android:layout_y="22dp"
        android:text="Student Details"
        android:textSize="30sp" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_x="20dp"
        android:layout_y="110dp"
        android:text="Enter Rollno:"
        android:textSize="20sp" />
    <EditText
        android:id="@+id/Rollno"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="175dp"
        android:layout_y="100dp"
        android:inputType="number"
        android:textSize="20sp" />
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_x="20dp"
        android:layout_y="160dp"
        android:text="Enter Name:"
        android:textSize="20sp" />
    <EditText
        android:id="@+id/Name"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="175dp"
        android:layout_y="150dp"
        android:inputType="text"
        android:textSize="20sp" />
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_x="20dp"
        android:layout_y="210dp"
        android:text="Enter Marks:"
        android:textSize="20sp" />
    <EditText
        android:id="@+id/Marks"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="175dp"
        android:layout_y="200dp"
        android:inputType="number"
        android:textSize="20sp" />

    <Button
        android:id="@+id/Insert"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="34dp"
        android:layout_y="384dp"
        android:text="Insert"
        android:textSize="30dp" />

    <Button
        android:id="@+id/Delete"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="243dp"
        android:layout_y="368dp"
        android:text="Delete"
        android:textSize="30dp" />

    <Button
        android:id="@+id/Update"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="232dp"
        android:layout_y="502dp"
        android:text="Update"
        android:textSize="30dp" />

    <Button
        android:id="@+id/View"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="42dp"
        android:layout_y="528dp"
        android:text="View"
        android:textSize="30dp" />

</AbsoluteLayout>

//MainActivity.java

package com.example.part_b3;

import android.app.Activity;
import android.app.AlertDialog.Builder;
import android.content.Context;
import android.database.Cursor;
import android.database.sqlite.SQLiteDatabase;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;
public class MainActivity extends Activity implements OnClickListener
{
    EditText Rollno,Name,Marks;
    Button Insert,Delete,Update,View,ViewAll;
    SQLiteDatabase db;

    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Rollno=(EditText)findViewById(R.id.Rollno);
        Name=(EditText)findViewById(R.id.Name);
        Marks=(EditText)findViewById(R.id.Marks);
        Insert=(Button)findViewById(R.id.Insert);
        Delete=(Button)findViewById(R.id.Delete);
        Update=(Button)findViewById(R.id.Update);
        View=(Button)findViewById(R.id.View);

        Insert.setOnClickListener(this);
        Delete.setOnClickListener(this);
        Update.setOnClickListener(this);
        View.setOnClickListener(this);

        // Creating database and table
        db=openOrCreateDatabase("StudentDB", Context.MODE_PRIVATE, null);
        db.execSQL("CREATE TABLE IF NOT EXISTS student(rollno VARCHAR,name VARCHAR,marks VARCHAR);");
    }

    public void onClick(View view)
    {
        // Inserting a record to the Student table
        if(view==Insert)
        {
            // Checking for empty fields
            if(Rollno.getText().toString().trim().length()==0||
                    Name.getText().toString().trim().length()==0||
                    Marks.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter all values");
                return;
            }
            db.execSQL("INSERT INTO student VALUES('"+Rollno.getText()+"','"+Name.getText()+
                    "','"+Marks.getText()+"');");
            showMessage("Success", "Record added");
            clearText();
        }

// Deleting a record from the Student table
        if(view==Delete)
        {
            // Checking for empty roll number
            if(Rollno.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter Rollno");
                return;
            }

            Cursor c=db.rawQuery("SELECT * FROM student WHERE rollno='"+Rollno.getText()+"'", null);
            if(c.moveToFirst())
            {
                db.execSQL("DELETE FROM student WHERE rollno='"+Rollno.getText()+"'");
                showMessage("Success", "Record Deleted");
            }
            else
            {
                showMessage("Error", "Invalid Rollno");
            }
            clearText();
        }

        // Updating a record in the Student table
        if(view==Update)
        {
            // Checking for empty roll number
            if(Rollno.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter Rollno");
                return;
            }

            Cursor c=db.rawQuery("SELECT * FROM student WHERE rollno='"+Rollno.getText()+"'", null);
            if(c.moveToFirst()) {
                db.execSQL("UPDATE student SET name='" + Name.getText() + "',marks='" + Marks.getText() +
                        "' WHERE rollno='"+Rollno.getText()+"'");
                showMessage("Success", "Record Modified");
            }
            else {
                showMessage("Error", "Invalid Rollno");
            }
            clearText();
        }
        // Display a record from the Student table
        if(view==View)
        {
            // Checking for empty roll number
            if(Rollno.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter Rollno");
                return;
            }
            Cursor c=db.rawQuery("SELECT * FROM student WHERE rollno='"+Rollno.getText()+"'", null);
            if(c.moveToFirst())
            {
                Name.setText(c.getString(1));
                Marks.setText(c.getString(2));
            }
            else
            {
                showMessage("Error", "Invalid Rollno");
                clearText();
            }
        }

        // Displaying all the records
        if(view==ViewAll)
        {
            Cursor c=db.rawQuery("SELECT * FROM student", null);
            if(c.getCount()==0)
            {
                showMessage("Error", "No records found");
                return;
            }
            StringBuffer buffer=new StringBuffer();
            while(c.moveToNext())
            {
                buffer.append("Rollno: "+c.getString(0)+"\n");
                buffer.append("Name: "+c.getString(1)+"\n");
                buffer.append("Marks: "+c.getString(2)+"\n\n");
            }
            showMessage("Student Details", buffer.toString());
        }
    }


    public void showMessage(String title,String message)
    {
        Builder builder=new Builder(this);
        builder.setCancelable(true);
        builder.setTitle(title);
        builder.setMessage(message);
        builder.show();
    }


    public void clearText()
    {
        Rollno.setText("");
        Name.setText("");
        Marks.setText("");
        Rollno.requestFocus();
    }
}

//PART B4
//activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<AbsoluteLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_x="50dp"
        android:layout_y="20dp"
        android:text="Student Details"
        android:textSize="30sp" />
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_x="20dp"
        android:layout_y="110dp"
        android:text="Enter Rollno:"
        android:textSize="20sp" />
    <EditText
        android:id="@+id/Rollno"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="175dp"
        android:layout_y="100dp"
        android:inputType="number"
        android:textSize="20sp" />
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_x="20dp"
        android:layout_y="160dp"
        android:text="Enter Name:"
        android:textSize="20sp" />
    <EditText
        android:id="@+id/Name"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="175dp"
        android:layout_y="150dp"
        android:inputType="text"
        android:textSize="20sp" />
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_x="20dp"
        android:layout_y="210dp"
        android:text="Enter Marks:"
        android:textSize="20sp" />
    <EditText
        android:id="@+id/Marks"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="175dp"
        android:layout_y="200dp"
        android:inputType="number"
        android:textSize="20sp" />

    <Button
        android:id="@+id/Insert"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="125dp"
        android:layout_y="361dp"
        android:text="Insert"
        android:textSize="30dp" />

    <Button
        android:id="@+id/View"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_x="125dp"
        android:layout_y="468dp"
        android:text="View"
        android:textSize="30dp" />

    <Button
        android:id="@+id/ViewAll"
        android:layout_width="200dp"
        android:layout_height="wrap_content"
        android:layout_x="107dp"
        android:layout_y="578dp"
        android:text="View All"
        android:textSize="30dp" />
</AbsoluteLayout>


//MainActivity.java
package com.example.part_b4;
import android.app.Activity;
import android.app.AlertDialog.Builder;
import android.content.Context;
import android.database.Cursor;
import android.database.sqlite.SQLiteDatabase;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;
public class MainActivity extends Activity implements OnClickListener
{
    EditText Rollno,Name,Marks;
    Button Insert,Delete,Update,View,ViewAll;
    SQLiteDatabase db;

    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Rollno=(EditText)findViewById(R.id.Rollno);
        Name=(EditText)findViewById(R.id.Name);
        Marks=(EditText)findViewById(R.id.Marks);
        Insert=(Button)findViewById(R.id.Insert);
        /*Delete=(Button)findViewById(R.id.Delete);
        Update=(Button)findViewById(R.id.Update);*/
        View=(Button)findViewById(R.id.View);
        ViewAll=(Button)findViewById(R.id.ViewAll);
        Insert.setOnClickListener(this);

        View.setOnClickListener(this);
        ViewAll.setOnClickListener(this);
        // Creating database and table
        db=openOrCreateDatabase("StudentDB", Context.MODE_PRIVATE, null);
        db.execSQL("CREATE TABLE IF NOT EXISTS student(rollno VARCHAR,name VARCHAR,marks VARCHAR);");
    }

    public void onClick(View view)
    {
        // Inserting a record to the Student table
        if(view==Insert)
        {
            // Checking for empty fields
            if(Rollno.getText().toString().trim().length()==0||
                    Name.getText().toString().trim().length()==0||
                    Marks.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter all values");
                return;
            }
            db.execSQL("INSERT INTO student VALUES('"+Rollno.getText()+"','"+Name.getText()+
                    "','"+Marks.getText()+"');");
            showMessage("Success", "Record added");
            clearText();
        }
/*
// Deleting a record from the Student table
        if(view==Delete)
        {
            // Checking for empty roll number
            if(Rollno.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter Rollno");
                return;
            }

            Cursor c=db.rawQuery("SELECT * FROM student WHERE rollno='"+Rollno.getText()+"'", null);
            if(c.moveToFirst())
            {
                db.execSQL("DELETE FROM student WHERE rollno='"+Rollno.getText()+"'");
                showMessage("Success", "Record Deleted");
            }
            else
            {
                showMessage("Error", "Invalid Rollno");
            }
            clearText();
        }

        // Updating a record in the Student table
        if(view==Update)
        {
            // Checking for empty roll number
            if(Rollno.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter Rollno");
                return;
            }

            Cursor c=db.rawQuery("SELECT * FROM student WHERE rollno='"+Rollno.getText()+"'", null);
            if(c.moveToFirst()) {
                db.execSQL("UPDATE student SET name='" + Name.getText() + "',marks='" + Marks.getText() +
                        "' WHERE rollno='"+Rollno.getText()+"'");
                showMessage("Success", "Record Modified");
            }
            else {
                showMessage("Error", "Invalid Rollno");
            }
            clearText();
        }*/
        // Display a record from the Student table
        if(view==View)
        {
            // Checking for empty roll number
            if(Rollno.getText().toString().trim().length()==0)
            {
                showMessage("Error", "Please enter Rollno");
                return;
            }
            Cursor c=db.rawQuery("SELECT * FROM student WHERE rollno='"+Rollno.getText()+"'", null);
            if(c.moveToFirst())
            {
                Name.setText(c.getString(1));
                Marks.setText(c.getString(2));
            }
            else
            {
                showMessage("Error", "Invalid Rollno");
                clearText();
            }
        }

        // Displaying all the records
        if(view==ViewAll)
        {
            Cursor c=db.rawQuery("SELECT * FROM student", null);
            if(c.getCount()==0)
            {
                showMessage("Error", "No records found");
                return;
            }
            StringBuffer buffer=new StringBuffer();
            while(c.moveToNext())
            {
                buffer.append("Rollno: "+c.getString(0)+"\n");
                buffer.append("Name: "+c.getString(1)+"\n");
                buffer.append("Marks: "+c.getString(2)+"\n\n");
            }
            showMessage("Student Details", buffer.toString());
        }
    }


    public void showMessage(String title,String message)
    {
        Builder builder=new Builder(this);
        builder.setCancelable(true);
        builder.setTitle(title);
        builder.setMessage(message);
        builder.show();
    }


    public void clearText()
    {
        Rollno.setText("");
        Name.setText("");
        Marks.setText("");
        Rollno.requestFocus();
    }
}


