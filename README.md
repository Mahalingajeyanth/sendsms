
# Ex.No:6 Design an android application Send SMS using Intent.


## AIM:

To create and design an android application Send SMS using Intent using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as smsintent and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Send SMS and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to create and design an android application Send SMS using Intent.
Developed by: MAHALINGA JEYANTH V
Registeration Number : 212224220057
*/
```
ACTIVITY MAIN.XML
```
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/background"
    android:fillViewport="true">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical">

        <!-- Header -->
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:background="@drawable/bg_header"
            android:gravity="center"
            android:orientation="vertical"
            android:paddingTop="48dp"
            android:paddingBottom="56dp">

            <ImageView
                android:layout_width="72dp"
                android:layout_height="72dp"
                android:contentDescription="@string/sms_icon"
                android:src="@drawable/ic_message" />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginTop="12dp"
                android:text="@string/quick_sms"
                android:textColor="@color/white"
                android:textSize="26sp"
                android:textStyle="bold" />

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginTop="4dp"
                android:text="@string/send_a_message_using_intent"
                android:textColor="@color/text_light"
                android:textSize="14sp" />
        </LinearLayout>

        <!-- Card -->
        <com.google.android.material.card.MaterialCardView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginStart="20dp"
            android:layout_marginTop="-32dp"
            android:layout_marginEnd="20dp"
            app:cardBackgroundColor="@color/white"
            app:cardCornerRadius="20dp"
            app:cardElevation="8dp">

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="vertical"
                android:padding="20dp">

                <com.google.android.material.textfield.TextInputLayout
                    android:id="@+id/tilPhone"
                    style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:hint="@string/phone_number"
                    app:boxCornerRadiusBottomEnd="12dp"
                    app:boxCornerRadiusBottomStart="12dp"
                    app:boxCornerRadiusTopEnd="12dp"
                    app:boxCornerRadiusTopStart="12dp"
                    app:startIconDrawable="@android:drawable/ic_menu_call">

                    <com.google.android.material.textfield.TextInputEditText
                        android:id="@+id/etPhone"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:inputType="phone"
                        android:maxLength="15" />
                </com.google.android.material.textfield.TextInputLayout>

                <com.google.android.material.textfield.TextInputLayout
                    android:id="@+id/tilMessage"
                    style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:layout_marginTop="16dp"
                    android:hint="@string/type_your_message"
                    app:boxCornerRadiusBottomEnd="12dp"
                    app:boxCornerRadiusBottomStart="12dp"
                    app:boxCornerRadiusTopEnd="12dp"
                    app:boxCornerRadiusTopStart="12dp"
                    app:counterEnabled="true"
                    app:counterMaxLength="160">

                    <com.google.android.material.textfield.TextInputEditText
                        android:id="@+id/etMessage"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:gravity="top|start"
                        android:inputType="textMultiLine|textCapSentences"
                        android:lines="5"
                        android:maxLength="160" />
                </com.google.android.material.textfield.TextInputLayout>

                <com.google.android.material.button.MaterialButton
                    android:id="@+id/btnSend"
                    android:layout_width="match_parent"
                    android:layout_height="60dp"
                    android:layout_marginTop="24dp"
                    android:text="@string/send_sms"
                    android:textAllCaps="false"
                    android:textSize="17sp"
                    app:backgroundTint="@color/primary"
                    app:cornerRadius="14dp"
                    app:icon="@android:drawable/ic_menu_send"
                    app:iconGravity="textStart" />
            </LinearLayout>
        </com.google.android.material.card.MaterialCardView>

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_margin="24dp"
            android:gravity="center"
            android:text="@string/your_default_messaging_app_will_open_with_the_message_ready_to_send"
            android:textColor="#757575"
            android:textSize="13sp" />
    </LinearLayout>
</ScrollView>
```
ACTIVITY MAIN.JAVA
```
package com.example.sendsms;

import android.content.ActivityNotFoundException;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

import com.google.android.material.button.MaterialButton;
import com.google.android.material.textfield.TextInputEditText;
import com.google.android.material.textfield.TextInputLayout;

public class MainActivity extends AppCompatActivity {

    private TextInputLayout tilPhone, tilMessage;
    private TextInputEditText etPhone, etMessage;
    /**
     *
     */
    private MaterialButton btnSend;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        tilPhone = findViewById(R.id.tilPhone);
        tilMessage = findViewById(R.id.tilMessage);
        etPhone = findViewById(R.id.etPhone);
        etMessage = findViewById(R.id.etMessage);
        btnSend = findViewById(R.id.btnSend);

        btnSend.setOnClickListener(v -> sendSms());
    }

    private void sendSms() {
        String phone = etPhone.getText().toString().trim();
        String message = etMessage.getText().toString().trim();

        tilPhone.setError(null);
        tilMessage.setError(null);

        if (phone.isEmpty()) {
            tilPhone.setError("Enter a phone number");
            return;
        }
        if (phone.length() < 10) {
            tilPhone.setError("Enter a valid phone number");
            return;
        }
        if (message.isEmpty()) {
            tilMessage.setError("Message cannot be empty");
            return;
        }

        try {
            Intent smsIntent = new Intent(Intent.ACTION_SENDTO);
            smsIntent.setData(Uri.parse("smsto:" + Uri.encode(phone)));
            smsIntent.putExtra("sms_body", message);
            startActivity(smsIntent);
        } catch (ActivityNotFoundException e) {
            Toast.makeText(this, "No SMS app found on this device", Toast.LENGTH_LONG).show();
        }
    }
}
```
STRING.XML
```
<resources>
    <string name="app_name">Quick SMS</string>
    <string name="sms_icon">SMS icon</string>
    <string name="quick_sms">Quick SMS</string>
    <string name="send_a_message_using_intent">Send a message using Intent</string>
    <string name="phone_number">Phone Number</string>
    <string name="type_your_message">Type your message</string>
    <string name="send_sms">Send SMS</string>
    <string name="your_default_messaging_app_will_open_with_the_message_ready_to_send">Your default messaging app will open with the message ready to send.</string>
</resources>
```
COLOURS.XML
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="primary">#1976D2</color>
    <color name="primary_dark">#0D47A1</color>
    <color name="accent">#00BFA5</color>
    <color name="background">#F2F5FA</color>
    <color name="white">#FFFFFF</color>
    <color name="text_dark">#212121</color>
    <color name="text_light">#E3F2FD</color>
</resources>
```
THEMES.XML
```
<resources>
    <style name="Theme.SendSMS" parent="Theme.MaterialComponents.Light.NoActionBar">
        <item name="colorPrimary">@color/primary</item>
        <item name="colorPrimaryDark">@color/primary_dark</item>
        <item name="colorSecondary">@color/accent</item>
        <item name="android:statusBarColor">@color/primary_dark</item>
    </style>
</resources>
```

## OUTPUT
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/b178143f-4bac-4519-b7a7-ec680ee4e0d5" />

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/cf47010d-171b-4d72-a6c1-e5ee30155429" />


## RESULT
Thus a Simple Android Application create and design an android application Send SMS using Intent using Android Studio is developed and executed successfully.
