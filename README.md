# 360_Degree_Ultrasonic_Sensor
// Define the pins for the four ultrasonic sensors
const int trigPin1 = 2;
const int echoPin1 = 3;

const int trigPin2 = 4;
const int echoPin2 = 5;

const int trigPin3 = 6;
const int echoPin3 = 7;

const int trigPin4 = 8;
const int echoPin4 = 9;

// Function to measure distance
long measureDistance(int trigPin, int echoPin) {
  // Send a 10us pulse to trigger the ultrasonic sensor
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Read the echo pin and calculate distance
  long duration = pulseIn(echoPin, HIGH);
  long distance = duration * 0.034 / 2; // Convert to cm

  return distance;
}

void setup() {
  // Initialize serial communication
  Serial.begin(9600);

  // Set the trigger and echo pins as outputs and inputs respectively
  pinMode(trigPin1, OUTPUT);
  pinMode(echoPin1, INPUT);

  pinMode(trigPin2, OUTPUT);
  pinMode(echoPin2, INPUT);

  pinMode(trigPin3, OUTPUT);
  pinMode(echoPin3, INPUT);

  pinMode(trigPin4, OUTPUT);
  pinMode(echoPin4, INPUT);
}

void loop() {
  // Measure distances from each sensor
  long distance1 = measureDistance(trigPin1, echoPin1);
  long distance2 = measureDistance(trigPin2, echoPin2);
  long distance3 = measureDistance(trigPin3, echoPin3);
  long distance4 = measureDistance(trigPin4, echoPin4);

  // Print the distances to the Serial Monitor
  Serial.print("Distance 1: ");
  Serial.print(distance1);
  Serial.println(" cm");

  Serial.print("Distance 2: ");
  Serial.print(distance2);
  Serial.println(" cm");

  Serial.print("Distance 3: ");
  Serial.print(distance3);
  Serial.println(" cm");

  Serial.print("Distance 4: ");
  Serial.print(distance4);
  Serial.println(" cm");

  // Add a delay before the next measurement
  delay(1000);
}
