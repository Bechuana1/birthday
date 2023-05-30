




## Code Description

The following code snippet demonstrates how to use the Web Audio API to play a sequence of musical notes.

### Prerequisites

Before running this code, make sure you have a compatible web browser that supports the Web Audio API.


### Resources

- [Web Audio API Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)




### Code Explanation

```javascript
let audioContext = new (window.AudioContext || window.webkitAudioContext)();
let i = 0;
([[0, 0.7], [0, 0.3], [2], [0], [5], [4, 2], [0, 0.7], [0, 0.3], [2], [0], [7], [5, 2], [0, 0.7], [0, 0.3], [12], [9], [5], [4], [2, 2], [10, 0.7], [10, 0.3], [9], [5], [7], [5, 2]])
  .map(([n, dur = 1]) => {
    let oscillator = audioContext.createOscillator();
    oscillator.start(i);
    oscillator.frequency.value *= Math.pow(1.06, n);
    let h = audioContext.createGain();
    i += dur / 1.5;
    h.gain.linearRampToValueAtTime(0, i);
    oscillator.connect(h);
    h.connect(audioContext.destination);
});


usage
Create an instance of the AudioContext object.
Initialize a variable i to keep track of the timing.
Use an array of note sequences [[pitch, duration], ...] to define the musical sequence.
Iterate over each note in the sequence and perform the following steps:
Create an oscillator node using createOscillator().
Start the oscillator at the specified timing.
Set the frequency of the oscillator using the pitch value and the multiplier 1.06.
Create a gain node using createGain() for controlling the volume.
Update the timing for the next note.
Connect the oscillator to the gain node and the gain node to the destination (audio output).
The code will play the sequence of notes using the Web Audio API.


` The value 1.06 is used as a multiplier to calculate the frequency of each note. It represents a musical interval called a "semitone" or "half step" in Western music.