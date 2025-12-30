# FPGA Controlled Infrared Imaging System (Microbolometer-Based)


Project Overview:

This project implements a complete infrared (IR) imaging system using an uncooled LWIR microbolometer (ULIS 03-19-1, 384×288, 12-bit) interfaced with an Actel ProASIC3E FPGA. The system focuses on precise timing control, direct digital data acquisition, and offline image reconstruction, avoiding conventional frame buffers or high-level interfaces.The design demonstrates a memory-less, logic-analyzer-based acquisition approach, providing cycle-accurate visibility into detector readout and enabling reliable thermal image reconstruction using MATLAB.

System Architecture:

Detector: ULIS 03-19-1 uncooled microbolometer (384×288, 12-bit, multiplexed output)
FPGA: Actel ProASIC3E A3PE1500
Acquisition: Tektronix Logic Analyzer
Processing: MATLAB (offline image reconstruction)
The FPGA generates all required clocks and control signals (Master Clock, Reset, Integration, SERDAT), demultiplexes the detector’s 6-bit output into 12-bit pixel data, and tags each pixel with row and column counters for accurate frame reconstruction.

Key Features:

FPGA-generated deterministic timing control for detector readout
Direct parallel data capture using a logic analyzer (no RAM / USB bottlenecks)
Precise row–column indexed pixel acquisition
MATLAB-based thermal image reconstruction from raw digital waveforms
Custom biasing and signal-conditioning circuitry using space-grade components
Dedicated temperature control system (TEC + MAX1978) for detector stability

Hardware Design Highlights:

Nine precision bias voltages generated using RHFL4913A LDOs
Bidirectional buffering between detector and FPGA using 54AC164245
FPGA-based:

Clock dividers and FSMs
Pixel de-multiplexing (6-bit → 12-bit)
Row and column address counters
Standalone TEC controller PCB for microbolometer temperature regulation

Data Acquisition & Image Reconstruction:

FPGA outputs synchronized pixel data, counters, and control signals
Logic analyzer captures raw digital waveforms in real time
Captured data exported as CSV

MATLAB script:

Filters valid pixel samples
Maps pixels using row/column indices
Reconstructs full 384×288 thermal frames
Supports grayscale / false-color visualization

Tools & Technologies:

Cadence / FPGA tools: Libero SoC, QuestaSim
Hardware debugging: Tektronix Logic Analyzer

Image processing: MATLAB
Digital design: VHDL, FSMs, counters, clock management

Applications:

Thermal imaging and surveillance
Space and defense sensor prototyping
Embedded vision systems
FPGA-based sensor interfacing research

Key Learning Outcomes:

FPGA-controlled sensor interfacing
Timing-critical digital system design
Practical microbolometer readout techniques
Logic-analyzer-based system validation
End-to-end hardware-to-image reconstruction workflow
