# LED-blink-with-no-pushbutton-<img width="744" height="444" alt="no push button" src="https://github.com/user-attachments/assets/26a7fc94-dc4f-4ef9-9923-f367322b18ee" />
Here’s a simple Arduino code to control 2 LEDs and a buzzer using an LDR sensor (like in your circuit):

🔌 Pin Setup (based on your image)
LDR → A0
LED 1 (Green) → D8
LED 2 (Red) → D7
Buzzer → D6
Here’s a clear explanation of how an LDR sensor can control two LEDs and a buzzer using Arduino, based on the page you’re viewing:

🔌 Circuit Setup
LDR (Light Dependent Resistor) → Analog pin A0

Green LED → Digital pin D8

Red LED → Digital pin D7

Buzzer → Digital pin D6

💻 Arduino Code Example
cpp
int ldrPin = A0; 
int led1 = 8;   // Green LED
int led2 = 7;   // Red LED
int buzzer = 6; 
int threshold = 500; // Adjust depending on light level

void setup() {
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(buzzer, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int ldrValue = analogRead(ldrPin);
  Serial.println(ldrValue);

  if (ldrValue > threshold) { 
    // DARK condition
    digitalWrite(led1, LOW);
    digitalWrite(led2, HIGH);
    digitalWrite(buzzer, HIGH);
  } else { 
    // BRIGHT condition
    digitalWrite(led1, HIGH);
    digitalWrite(led2, LOW);
    digitalWrite(buzzer, LOW);
  }
  delay(200);
}
⚙️ How It Works
Dark environment (LDR value high) → Red LED ON + Buzzer ON

Bright environment (LDR value low) → Green LED ON

🔧 Tips
If the behavior is reversed, simply change the condition to:

cpp
if (ldrValue < threshold)
You can experiment with:

PWM control for smooth LED brightness

LCD display to show LDR values

Smart alarm system that triggers automatically at night
