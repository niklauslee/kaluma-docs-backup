# Getting Started

Welcome to Kameleon! To get started with Kameleon, we strongly recommend you to [code online with Kameleon IDE](getting_started.md#code-online-with-kameleon-ide) If you have reliable internet connection. Otherwise, you can also have alternative to [code in local with CLI \(Command Line Interface\)](getting_started.md#code-in-local-with-cli-command-line-interface).

## Code online with Kameleon IDE

To code online with Kameleon IDE ensure that you are signed up in the web \([https://kameleon.io](https://kameleon.io)\).

#### 1. Install Kameleon Agent

To code online you have to install [Kameleon Agent](https://kameleon.io/agent) first.

#### 2. Write your code

Open the Playground and write your code.

```javascript
var led = board.LED0;
setInterval(function () {
  led.toggle();
}, 1000);
```

#### 3. Connect the board

Connect the board to your computer using a USB cable. You can find connected Kameleon boards in Playground.

#### 4. Upload your code

Press upload button in Playground

## Code in local with CLI \(Command Line Interface\)

You can also code with your familiar editors \(e.g. Visual Studio Code, Atom, Sublime Text, etc.\) and then upload the code with [Kameleon CLI](https://github.com/kameleon-project/kameleon-cli).

#### 1. Install Kameleon CLI

Open a terminal and install Kameleon CLI. \(Ensure that [Node.js/NPM](https://nodejs.org/) is already installed. Sometimes you may need to use npm option `--unsafe-perm=true`\)

```bash
$ (sudo) npm install -g kameleon-cli
```

#### 2. Write you code

Write your code with your familiar code editor.

{% code title="index.js" %}
```javascript
var led = board.LED0;
setInterval(function () {
  led.toggle();
}, 1000);
```
{% endcode %}

#### 3. Connect the board

Connect the board to your computer using a USB cable and then check serial port where the board is connect.

```bash
$ kameleon -l  # list available serial ports
# e.g.) COM? (for Windows)
# e.g.) /dev/tty.usbmodem? (for MacOS)
# e.g.) /dev/ttyACM? (for Linux)
```

#### 4. Upload your code

Upload your code to the board using CLI.

```bash
$ kameleon write index.js -p <port> . # COM?, /dev/tty.usbmodem?, ttyACM?
```



