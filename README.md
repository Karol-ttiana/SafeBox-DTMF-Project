# Safe Box Code Detection (DTMF)

## Overview
This project is designed to detect a 6-digit safe code embedded in a DTMF-based signal. It leverages a real-time operating system (RTOS) environment to continuously sample the input signal, apply IIR band-pass filtering, and identify which tones are present at any given time.

## Features
- Sampling at 10 kHz using a hardware timer.  
- IIR band-pass filtering (Elliptic 4th order) to isolate the known DTMF frequency ranges.  
- Automatic detection of the 6-digit code based on the strongest frequency pair.  
- Logging and displaying real-time filtering outputs and FFT Magnitude graphs for each stage.  
- Execution Graph and CPU/Task load visualization.

## Getting Started
1. Clone or download this repository.  
2. Include the provided header file (for example, `safe_code6.h`) that contains the sampled DTMF signal.  
3. Review or modify the filter coefficient files (if needed) which define the IIR band-pass filters for each frequency band.  
4. Build and load the project onto your target DSP/processor environment.  
5. Run the code to detect the 6-digit safe box code.

## Directory Structure
- **SHORT_DESCRIPTION.md**  
  A brief summary of the repository’s purpose.  
- **README.md**  
  Project overview, instructions, and feature list.  
- **images/**  
  Folder containing images or diagrams used in documentation.  
- **(Future Files)**  
  - Source code and filter design implementation.  
  - Header files with filter coefficients and DTMF signal arrays.  
  - Any additional scripts, configuration, or documentation.

## Usage
1. Ensure the timer interrupt (Hwi) is correctly configured for 10 kHz sampling.  
2. In the DSP code, the interrupt service routine (ISR) reads samples from the input array in a cyclic manner.  
3. The software interrupt(s) (Swi) then processes the samples through the band-pass filters.  
4. A task (Task) analyzes the filtered signals to determine which frequency pairs are present.  
5. On recognizing valid tone pairs, the corresponding code digit is logged and displayed.  
6. For debugging, monitor the FFT plots for both the raw and filtered signals, and observe CPU and Task loads via the RTOS tools.

## Additional Figures
Below are suggested points in the documentation where you may place images from the "images" folder:

1. **Block Diagram**  
   ![Block Diagram](images/block_diagram.png)

2. **System Flow Diagram**  
   ![System Flow](images/system_flow.png)

3. **Program Flowchart**  
   ![Program Flow](images/program_flow.png)

4. **Filter Outputs / FFT Graphs**  
   ![FFT Magnitude](images/fft_magnitude.png)  
   ![Filtered Signal](images/filtered_signal.png)

5. **Execution Graph, Task Load, CPU Load**  
   ![Execution Graph](images/execution_graph.png)  
   ![Load Graphs](images/load_graphs.png)

## Contributing
Feel free to open an issue or pull request for any bug reports or feature suggestions. This project is open to improvements and collaborative development.

## License
This project is provided as-is for educational and demonstration purposes. Please review the license details (if included) before use.
