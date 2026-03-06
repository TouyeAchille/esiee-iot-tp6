# TP6 – IoT System with MQTT + Raspberry Pico W + DHT22 + LCD + + Led + PIR + Cloud Integration

## Objective

In this practical lab, students will build a complete IoT system using:

- Raspberry Pico W
- DHT22 sensor (Temperature & Humidity)
- LCD 16x2 (I2C)
- LED
- PIR (Motion Sensor)
- MQTT Protocol
- Adafruit IO Cloud Dashboard

Students will:

* Read sensor data
* Display data locally on LCD
* Send data to cloud using MQTT 
* Visualize data on mobile dashboard
* Remotely control both the LED using a toggle button from:
  > - The Adafruit IO Dashboard (Web)
  > - The iOS mobile application (itsaSNAP)
  > - Functionality
  > - When the user changes the toggle button state:
  > - ON → The LED turns if Sensor PIR detected moving
  > - ON → The LED turns from cloud or app mobile
  > - Display Temperature , Humidity and Movement value
  > - This control works in real time using the MQTT protocol.


# System Architecture

```
DHT22
   ↓
Raspberry Pico W (MCU)
   ├── LCD Display (Local Monitoring)
   ├── LED, PIR
   └── MQTT → Adafruit IO Cloud
                ↓
            Mobile Dashboard
```

# Required Components (Student Task)

Students must:

1. Add **Raspberry Pico W board**
2. Add **DHT22 sensor**
3. Add **LCD1602 I2C**
4. Add **Breadboard, LED, PIR**
5. Connect all components properly
6. Configure WiFi connection
7. Configure MQTT connection
8. Write MicroPython program
9. Run simulation and test cloud publishing

---

# Software Requirements

Students must write a MicroPython program that:

### Connects to WiFi

### Connects to MQTT Broker (Adafruit IO)
send temperature, humidity and motion value to cloud
```
     add this step when connect to server to prevent automatic deconnection
     
     try:
        client.publish(MQTT_TOPIC1, str(temp))
        client.publish(MQTT_TOPIC2, str(hum))
        ...
    except:
        print("MQTT lost — reconnecting...")
        client.connect()
        ...
      
```
  
### Reads temperature & humidity from DHT22
  ```
   Add this inside the loop to add fluctuations:
   
   variation_temp = random.uniform(-0.5, 0.5)
   variation_hum = random.uniform(-1, 1)
   
   temp = sensor.temperature() + variation_temp
   hum = sensor.humidity() + variation_hum
 ```

### Displays data on LCD

### Publishes data to cloud using MQTT

## Example Output on LCD

```
T:24.5C M: 1
H:60%
```

# Cloud Visualization 

Students must:

1. Create a Dashboard
2. Add:

   * Gauge for Temperature and Humidity
   * Slider for Temperature and Humidity 
   * Line Chart for Temperature and Humidity

3. Link widgets to MQTT feeds
     
# Remote Control of LED and Buzzer via Cloud
1. add
   * toogle button for LED
     
2. Technical Behavior

> - The ESP32 subscribes to the MQTT feed (e.g., led-control)
> - When a new message is received:
> - If the message is "1" or "ON" → Activate LED 
> - If the message is "0" or "OFF" → Deactivate LED 
     
3. Link widgets to MQTT feeds

Mobile access:

```
https://io.adafruit.com Or Install `itsaSNAP` by adafruit for students with iOS phone only
```
# Helpful Resources

## LCD Library (MicroPython)

Students can use:

Library source:
[micropython-i2c-lcd](https://micropython-i2c-lcd.readthedocs.io/en/latest/readme_link.html)

## Wokwi Documentation

[https://docs.wokwi.com/](https://docs.wokwi.com/)

## Raspberry Pico W MicroPython Docs

[https://docs.micropython.org/](https://docs.micropython.org/)

# Submission Requirements

Students must submit:
* Wokwi project link OR project folder

---
# Helpful Resources

## LCD Library (MicroPython)

Students can use:

Library source:
[micropython-i2c-lcd](https://micropython-i2c-lcd.readthedocs.io/en/latest/readme_link.html)

## Wokwi Documentation

[https://docs.wokwi.com/](https://docs.wokwi.com/)
[https://learn.adafruit.com/welcome-to-adafruit-io](https://learn.adafruit.com/welcome-to-adafruit-io)


## MicroPython Docs

[https://docs.micropython.org/](https://docs.micropython.org/)

# Submission Requirements

Students must submit:
* Wokwi project link OR project folder



