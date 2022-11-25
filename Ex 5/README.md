# Ex.No: 5 Develop a simple application for proximity sensor using Sensor Manager in android studio.

## AIM:

To develop a sensor application for proximity sensor using sensor manager in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Arctic Fox)

## ALGORITHM:

### Step 1:
Open Android Studio and then click on File -> New -> New project.

### Step 2: 
Then type the Application name as proximitysensor and click Next. 

### Step 3: 
Then select the Minimum SDK as shown below and click Next.

### Step 4: 
Then select the Empty Activity and click Next. Finally click Finish.

### Step 5: 
Design layout in activity_main.xml.

### Step 6: 
Display process of proximity sensor in android mobile devices.

### Step 7: 
Launch an emulator and run the application.


## PROGRAM:
```
Program to print the details of proximity sensor in android mobile devices.
Developed by        : S. Sanjna Priya
Registration Number : 212220230043
```
### MainActivity.java
```java
package com.example.proximitysensor;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Context;
import android.hardware.Sensor;
import android.hardware.SensorEvent;
import android.hardware.SensorEventListener;
import android.hardware.SensorManager;
import android.os.Bundle;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {
    TextView ProximitySensor, data;
    SensorManager mySensorManager;
    Sensor myProximitySensor;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        ProximitySensor = (TextView) findViewById(R.id.proximitySensor);
        data = (TextView) findViewById(R.id.data);
        mySensorManager = (SensorManager) getSystemService(
                Context.SENSOR_SERVICE);
        myProximitySensor = mySensorManager.getDefaultSensor(
                Sensor.TYPE_PROXIMITY);
        if (myProximitySensor == null) {
            ProximitySensor.setText("No Proximity Sensor!");
        } else {
            mySensorManager.registerListener(proximitySensorEventListener,
                    myProximitySensor,
                    SensorManager.SENSOR_DELAY_NORMAL);
        }
    }
    SensorEventListener proximitySensorEventListener
            = new SensorEventListener() {
        @Override
        public void onAccuracyChanged(Sensor sensor, int accuracy) {
            // TODO Auto-generated method stub
        }
        @Override
        public void onSensorChanged(SensorEvent event) {
            // TODO Auto-generated method stub
            if (event.sensor.getType() == Sensor.TYPE_PROXIMITY) {
                if (event.values[0] == 0) {
                    data.setText("Near");
                } else {
                    data.setText("Away");
                }
            }
        }
    };
}

```
### AndroidManifest.xml
```java
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">
    <uses-permission android:name="android.hardware.sensor.proximity"/>
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.ProximitySensor"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

            <meta-data
                android:name="android.app.lib_name"
                android:value="" />
        </activity>
    </application>

</manifest>
```
### activity_main.xml
```java
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:gravity="center"
    android:orientation="vertical">

    <TextView
        android:id="@+id/proximitySensor"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content" />

    <TextView
        android:id="@+id/data"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:textSize="50dp" />

</LinearLayout>
```

## OUTPUT:
![image](https://user-images.githubusercontent.com/65499285/200177179-43e70d7f-1834-4138-99df-cc8ce5120221.png)

![image](https://user-images.githubusercontent.com/65499285/200177206-bb7a4585-7948-499c-937a-e44ad2fe75fc.png)

## RESULT:
Thus, a Simple Android Application to display the process of proximity sensor using sensor manager in Android Studio is developed and executed successfully.
