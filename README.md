#define RELAY1 2
#define RELAY2 3
#define RELAY3 4
#define RELAY4 5

char receivedChar;

void setup() {
    // Initialize relay pins as outputs
    pinMode(RELAY1, OUTPUT);
    pinMode(RELAY2, OUTPUT);
    pinMode(RELAY3, OUTPUT);
    pinMode(RELAY4, OUTPUT);

    // Turn off all relays initially
    digitalWrite(RELAY1, LOW);
    digitalWrite(RELAY2, LOW);
    digitalWrite(RELAY3, LOW);
    digitalWrite(RELAY4, LOW);

    // Start serial communication
    Serial.begin(9600);
}

void loop() {
    if (Serial.available() > 0) {
        receivedChar = Serial.read();

        switch (receivedChar) {
            case 'A': digitalWrite(RELAY1, HIGH); break; // Turn ON device 1
            case 'a': digitalWrite(RELAY1, LOW); break;  // Turn OFF device 1

            case 'B': digitalWrite(RELAY2, HIGH); break; // Turn ON device 2
            case 'b': digitalWrite(RELAY2, LOW); break;  // Turn OFF device 2

            case 'C': digitalWrite(RELAY3, HIGH); break; // Turn ON device 3
            case 'c': digitalWrite(RELAY3, LOW); break;  // Turn OFF device 3

            case 'D': digitalWrite(RELAY4, HIGH); break; // Turn ON device 4
            case 'd': digitalWrite(RELAY4, LOW); break;  // Turn OFF device 4

            default: break;
        }
    }
}
