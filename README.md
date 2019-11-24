# Machine Cycle

Machine Cycle is a live generative music framework utilizes Markov chains to melodically alter and playback phrases from a keyboard player in real time, creating a loop between the algorithm and performer.

## Dependencies

* This codebase is written in [Serpent](https://www.cs.cmu.edu/~music/serpent/doc/serpent.htm), a Pythonic language designed for real time systems
* [Max MSP](https://cycling74.com/) is used for parsing and routing MIDI data between Serpent and external sound system


## Repo Layout
### route_midi.maxpat
Max patch that creates virtual MIDI devices for routing MIDI between the Serpent code and external sound system. Also used for visualizing MIDI traffic throughout the pipeline.

### process_midi.srp
Main file that kicks off the system, runs the scheduler and interprets control messages

### Note, Node, Chain.srp
Abstraction for phrase markov chain. As input musician plays a phrase, a Chain is created for the phrase represented as a linked list

## How to Use
* Start up `route_midi.maxpat`. Currently the patch is set up to communicate with an external sound system over UDP, that the MIDI keyboardist is assumed to be hooked up to
* Run `serpent process_midi.srp` to kick off the system. You'll be prompted for input, output and control devices. The input should be set to the virtual Max MIDI out port, and the output should be set to the virtual Max MIDI in port. A control device is optional. Specifying one will allow you to control parameters of the markov chain with an external MIDI controller


