[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://www.webcomponents.org/element/andrewmiroshnichenko/se-timer)
# se-timer

Shows time in certain format and ticks it

## Install
```
$ bower install se-timer
```
Make sure you have the [Polymer CLI](https://www.npmjs.com/package/polymer-cli) installed. Then run `polymer serve` to serve your element locally.

## Viewing component

```
$ polymer serve
```

## Running tests

```
$ polymer test
```
## API
Component have four public properties.
1. Value

|                             |         |
| ---                         | ---     |
| **Property name**           | value   |
| **Property type**           | Number  |
| **Default value**           | 0       |
| **Can be set from html**    | Yes     |
| **Corresponding attribute** | value   |
|                             |         |

Number of milliseconds that should be reflected in the display. Value can’t exceed 359999999(which equivalents ‘99:59:59.999’). After reaching higher value component’s ‘state‘ will be explicitly set to ‘stop’.
```html
      <se-timer value="1234"></se-timer>
```
```javascript
      var customEl = document.querySelector('se-timer');
      customEl.value; // returns Number 1234
      customEl.value = 10000;
      customEl.value; // returns Number 10000
 ```
 ```html
      <se-timer>10:10:10</se-timer>
```
```javascript
      var customEl = document.querySelector('se-timer');
      customEl.value; // returns Number 36610000
 ```
2. timerStep

|                             |            |
| ---                         | ---        |
| **Property name**           | timerStep  |
| **Property type**           | Number     |
| **Default value**           | 500        |
| **Can be set from html**    | Yes        |
| **Corresponding attribute** | timer-step |
|                             |            |

Frequency of polling of current time and, subsequently, displayed time updating  in `count` state. Change of this property in `count` state won’t take effect. New value will be applied only after state will become `stop` at least once after change occurred. 

```html
      <se-timer timer-step="100"></se-timer>
```
```javascript
      var customEl = document.querySelector('se-timer');
      customEl.timerStep; // returns Number 100
      customEl.timerStep = 120;
      customEl.timerStep; // returns Number 120
 ```
3. State

|                             |            |
| ---                         | ---        |
| **Property name**           | state      |
| **Property type**           | String     |
| **Default value**           | 'stop'     |
| **Can be set from html**    | Yes        |
| **Corresponding attribute** | state      |
|                             |            |

State of the component. Two possible values are:
 - `count`. In this state value is increasing every `timerStep` milliseconds;
 - `stop`. In this state value isn’t changing.

```html
      <se-timer></se-timer>
```
```javascript
      var customEl = document.querySelector('se-timer');
      customEl.state; // returns String 'stop'
      customEl.state = 'count';
      customEl.state; // returns String 'count'
 ```
4. Format

|                             |            |
| ---                         | ---        |
| **Property name**           | format     |
| **Property type**           | String     |
| **Default value**           | 'hh:mm:ss' |
| **Can be set from html**    | Yes        |
| **Corresponding attribute** | format     |
|                             |            |

Format of output data. Seven formats are supported:
 - `hh`. Displays hours (value interval from 00 to 99);
 - `hh:mm`. Displays hours (value interval from 00 to 99) and minutes (value interval from 00 to 59);
 - `hh:mm:ss`. Displays hours (value interval from 00 to 99), minutes (value interval from 00 to 59) and seconds (value interval from 00 to 59);
 - `hh:mm:ss.ms`. Displays hours (value interval from 00 to 99), minutes (value interval from 00 to 59), seconds (value interval from 00 to 59) and milliseconds (value interval from 000 to 999);
 - `mm:ss`. Displays  minutes (value interval from 00 to 59) and seconds (value interval from 00 to 59);
 - `mm:ss.ms`. Displays  minutes (value interval from 00 to 59), seconds (value interval from 00 to 59) and milliseconds (value interval from 000 to 999);
 - `ss.ms`. Displays seconds (value interval from 00 to 59) and milliseconds (value interval from 000 to 999);

```html
      <se-timer format="hh"></se-timer>
```
```javascript
      var customEl = document.querySelector('se-timer');
      customEl.format; // returns String 'hh'
      customEl.format = 'hh:mm:ss:ms';
      customEl.format; // returns Number 'hh:mm:ss:ms'
 ```
## Styling

The following custom properties are available for styling:

| Custom property              | Description                                                        |         Default         |
| ---                          | ---                                                                |           ---           |
| `--setimer-number-color`     | Timer digits color                                                 | Browser-default(black)  |
| `--setimer-number-size`      | Font size of timer digits. This param changes component dimensions |          45px           |
| `--setimer-background-color` | Component's background color                                       |      `transparent`      |
| `--setimer-font-family`      | Font family of digits                                              |  `Roboto, sans-serif`   |

# Demo
Better view on [webcomponentsjs.org](https://www.webcomponents.org/element/andrewmiroshnichenko/se-timer)
 <!--
```
<custom-element-demo>
  <template>
    <script src="../webcomponentsjs/webcomponents-lite.js"></script>
    <link rel="import" href="se-timer.html">
    <next-code-block></next-code-block>
  </template>
</custom-element-demo>
```
-->
```html
<se-timer value="60000" state="count" timer-step="100" format="mm:ss.ms"></se-timer>
```