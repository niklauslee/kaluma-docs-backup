# Introduction

Kameleon is an open-source JavaScript platform for electronics prototyping. It consists of three main parts: [Kameleon runtime](./#kameleon-runtime), [Kameleon boards](./#kameleon-boards) and [Kameleon IDE](./#kameleon-ide-integrated-development-environment).

## Kameleon runtime

Kameleon runtime is a tiny and efficient JavaScript runtime for microcontrollers. The main features are:

* Small footprint \(Run on 300KB ROM, 64KB RAM\)
* ECMAScript 5.1/2015\(subset\) standard compliant \(Powered by [JerryScript](http://jerryscript.net/)\)
* Non-blocking I/O
* REPL mode support
* Portability \(No RTOS\)
* Native modules \(ADC, PWM, I2C, SPI, UART, Graphics, etc.\)

## Kameleon boards

Kameleon board is an open-source hardware board which has Kameleon runtime and can be programmed by JavaScript via Kameleon IDE. Currently supported Kameleon boards are:

* [Kameleon Core](boards/kameleon-core.md)

## Kameleon IDE \(Integrated Development Environment\)

Kameleon IDE is a cloud-based social coding environment provides free project repositories as well as web-based code editor and various tools. The main features are:

* Provide a web-based sophisticated code editor
* Provide cloud-based free public repositories
* Automatic code bundling with Webpack
* Support code linting based on ESLint
* Project release management \(publish and import reusable packages\)
* Support project fork



