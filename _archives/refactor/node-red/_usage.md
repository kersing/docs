# Usage
Here's how you can use the TTN node to receive messages and activations.

## Configure
To use the TTN node you need to configure it for your The Things Network Application.

### Lookup your application info

1.  Open [The Things Network Dashboard](https://preview.dashboard.thethingsnetwork.org/) a new window.
2.  Select the application you'd like to connect to.

### Edit the TTN node

1.  In Node-RED, drag a **ttn** node from the input category in the toolbox on the left to your workflow.
2.  Double click the node to edit it.

    Copy-paste the following information from the dashboard:

    * For **App ID**, copy **Application ID** from the **Application Overview** box.
    * For **Access Key**, scroll down to the **Access Keys**. For the key you'd like to use, click `👁` to show the key and then `📋` to copy it.
    * For **Region or Broker**, scroll back again to use **Handler Status** from the **Application Overview** box. Only copy the last bit following `ttn-handler-`.

    ![](node-red-ttn-edit.png)

4.  Click **Deploy** on the top right. The node should say it's connected:

    ![](node-red-ttn-connected.png)

    In the terminal you should see something like:

        8 Sep 11:53:41 - [info] [ttn:f2d6214.9aaa5e] Connected to TTN application hello-world

## Receive Messages
Messages sent by devices on the application can be received via the upper output of the **ttn** node.

1.  Drag a **debug** node from the output category of the toolbox.
2.  Drag the upper output of the **ttn** node to the input of the **debug** node.

    ![](node-red-debug.png)

3.  Click **Deploy**.
4.  In the right sidebar select the **debug** tab.
5.  Soon after a device sends a message to your application you should see it come in like this:
    
    ![](node-red-debug-message.png)

    By default the debug node only shows `msg.payload`, which is mapped to `msg.payload_fields` or `msg.payload_raw` of the original message received via MQTT. If you followed the [The Things Uno Quick Start](/uno/#quick-start) this would look like:

    ```json
    { 
      "led": true
    }
    ```
    
6.  Double click the **debug** node to edit it.
7.  Click the gray part of the **Output** value, select **complete msg object** and click **Done**:
    
    ![Output complete msg object](node-red-debug-edit.png)
    
8.  Click **Deploy** to see the next message in full, e.g.:

    ```json
    {
      "dev_id": "my-uno",
      "app_id": "hello-world",
      "port": 1,
      "counter": 19,
      "payload_raw": "AQ==",
      "payload_fields": {
        "led": true
      },
      "metadata": {
        "time": "2016-09-08T13:52:35.929159899Z",
        "frequency": 867.3,
        "modulation": "LORA",
        "data_rate": "SF7BW125",
        "coding_rate": "4/5",
        "gateways": [{
          "eui": "B827EBFFFE87BD22",
          "timestamp": 792136819,
          "time": "2016-09-08T13:52:35.912385Z",
          "channel": 4,
          "rssi": -55,
          "snr": 10.2
        }]
      },
      "payload": "[circular]",
      "_msgid": "f4fb1670.0b04e8"
    }
    ```

## Receive Activations
Device activations are sent from the lower node output.

1.  Drag the lower output to the input same **debug** node.
2.  Restart a device by briefly disconnecting power or upload a sketch.
3.  Soon, you should see the the activation message coming in like:

    ```json
    {
      "dev_id": "my-uno",
      "app_id": "hello-world",
      "app_eui": "70B3D57EF000001C",
      "dev_eui": "0004A30B001B7AD2",
      "dev_addr": "26012084",
      "metadata": {
        "time": "2016-09-08T14:04:52.755064047Z",
        "frequency": 868.5,
        "modulation": "LORA",
        "data_rate": "SF7BW125",
        "coding_rate": "4/5",
        "gateways": [{
          "eui": "B827EBFFFE87BD22",
          "timestamp": 1528942955,
          "time": "2016-09-08T14:04:52.716713Z",
          "channel": 2,
          "rssi": -57,
          "snr": 7.5,
          "rf_chain": 1
        }]
      },
      "payload": "my-uno",
      "_msgid": "10d6a2ba.ef295d"
    }
    ```
  
    Ask you can see the default `msg.payload` field is mapped to `msg.dev_id` which gives you the ID of the activated device.
