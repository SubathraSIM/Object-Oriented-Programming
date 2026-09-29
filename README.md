# CM2005 Object Oriented Programming - University of London

Coursework for **CM2005 Object Oriented Programming** (BSc Computer Science, University of London). The module covers object-oriented design in C++ through a console-based data analysis toolkit and a GUI audio application built with JUCE.

| Assessment | Project | Key topics |
|---|---|---|
| Mid Term | Weather data analysis toolkit | CSV parsing, candlestick computation, text-based plotting, linear regression |
| End Term | Otodecks DJ application | JUCE, audio playback and mixing, custom GUI, event listeners |

**Tech:** C++ · JUCE framework · Visual Studio

---

## Midterm — Weather Data Analysis Toolkit

A C++ console application that analyses European temperature data from 1980 to 2019 using a stock-market-style **candlestick** approach.

**Task 1: Compute candlestick data**
- Parses the weather CSV and groups temperatures by year for a chosen country code
- Computes **Open** (previous year's average), **Close** (current year's average), **High**, and **Low** for each year

**Task 2: Text-based candlestick plot**
- Draws candlestick charts in the terminal using ASCII characters (`H`, `L`, `O`, `C`, `X`)
- Accepts multiple comma-separated country codes
- Colour-coded: **green** when the year closed warmer than it opened, **red** when it closed cooler

**Task 3: Filter and plot**
- Filters by **country** and **year range** (e.g. `AT,BE` for `2000-2003`) before plotting

**Task 4: Predict future temperatures**
- Fits a **linear regression** trendline to the 2015–2019 yearly averages to project future average temperatures
- Projects highs and lows from the average yearly change over the same period
- Plots historical and predicted candlesticks together, with predicted years in **blue/yellow** to set them apart from actual data

**Key classes:** `CSVReader`, `Candlestick`, `WeatherData`
---

## Endterm — Otodecks DJ Application

A two-deck DJ application built in C++ with the **JUCE** framework. It extends the basic Otodecks app from class with a fully redesigned interface and a drum pad sampler inspired by **Serato DJ Pro**.

**Core features**
- Load tracks three ways: the Load button (file chooser), drag and drop, or the playlist table
- Play two tracks at once, mixed through `juce::MixerAudioSource`
- Volume, speed, and position sliders on each deck
- Waveform display with a custom colour scheme

**Custom features**
1. **Drum pads:** six pads per deck triggering samples made in GarageBand, each with its own volume control and loop toggle. Active pads blink as visual feedback, driven by a 500 ms timer.
2. **Rotating disk:** a turntable animation whose spin speed follows the track's playback speed
3. **Playlist table:** search box, track durations, Load to Deck 1 / Deck 2 buttons, a delete button, and music import
4. **Track looping:** a loop button on each deck to repeat the current track

**OOP design**
- All drum pad behaviour is encapsulated in a reusable `DrumPadComponent` class
- JUCE's event-driven model is used throughout: `Button::Listener`, `Slider::Listener`, `ChangeListener`, `Timer`
- Main classes: `MainComponent`, `DeckGUI`, `DJAudioPlayer`, `WaveformDisplay`, `PlaylistComponent`, `DrumPadComponent`

---

## How to run

**Midterm**
1. Open the project in Visual Studio (or compile with `g++`)
2. Place `weather_data_EU_1980-2019_temp_only.csv` in the working directory
3. Build and run, then follow the menu prompts

**Endterm**
1. Install [JUCE](https://juce.com/) and open the `.jucer` file in Projucer
2. Export to your IDE (Visual Studio / Xcode) and build
3. Keep the `tracks` and `samples` folders alongside the executable
