# notes-rileychou
All code linked in demo repo: https://github.com/allolib-s24/demo1-rileychou

# Simple Melody
This is a short transcript of a song called All The Pretty Little Horses. I transcribed the Tenor line of when I sang it in choir. 


To hear it, run `./run.sh tutorials/synthesis/01_SineEnv_Piano.cpp`. Once the app opens, select `test` in the list of synth sequences, and hit play. 

Video: 

https://github.com/allolib-s24/notes-rileychou/assets/61360955/d94dc16f-9518-455c-87d8-9a8159429593


# Sound Design Project: 
I explored synthesizing vibrato using additive synthesis, based off of `tutorials/synthesis/01_SineEnv.cpp`.

I made a new sine oscillator called mVib. I also added 2 parameters with sliders that the user could control: vibDepth to control the depth (variation of pitch) of the vibrato, and vibFreq to control the speed of the vibrato. 

Since the frequencies between each semitone vary by $\sqrt[12]{2}$, we need a scaledVibDepth multiplier that changes the sine wave by a certain ratio based on what frequency the pitch currently being played is at.

Then, we create a delta variable that multiplies the vibrato oscillator, mVib, by the scaledVibDepth minus 1. We do that because scaledVibDepth is a value between 1 and $\sqrt[12]{2}$. Subtracting by 1 gives us the amount of change.

Lastly, we set the frequency of mOsc, the original oscilator, to the note frequency * (delta + 1) to get the frequency + the pitch change at that moment.

One unexpected thing that I ran into while creating this project is that the vibFreq value that produces a perceivable vibrato is in the thousands, but the frequency should only differ by a few hertz. 

To hear it, run `./run.sh tutorials/synthesis/01_SineEnv_vib.cpp`. Once the app opens, play a note by hitting a key on the keyboard and hear the vibrato in action. You can adjust the vibDepth and vibFreq sliders to see how that affects the vibrato. 


# Final Project:
## Jaminator (Inspired by Phineas and Ferb)

For this project, I wanted to make an easy entry point for people to jam along to midi files by playing some beats and notes over it.

It features: Snare drum, bass drum, cymbal, and random pentatonic note in the key of A flat (same key as Phineas and Ferb). 

The randomly generated pentatonic scale sounds unmusical until I started trying to play along with the melody. After my demo, Professor Conrad introduced to me a composition technique called "Skip and Step" where certain notes are more likely to play after a certain note is played to make the music flow more naturally. 

To play, run `./run.sh experiments/jaminator.cpp`. Once the app opens, Once the app opens, select `phineasandferb` in the list of synth sequences, and hit play. Use the key 'd' for snare, 's' for bass, and 'c' for cymbal. Play the random pentatonic note using the key 'k'. 

## Final Project Demo Video

https://www.youtube.com/watch?v=rZaRl8dq51I
