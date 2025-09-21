# RISC-V SoC Program 
<details>
<summary> Week 0 - Tools Installation </summary>
  <br>
  <p>  In this step we are going to install all necessory Open Source tools which we are going to use in this program.<br> Before that, setup ubuntu in oracle virtualbox. <br>
    <h2>Tool includes:-</h2>
  </p>
<ol>
  <li>Yosys</li>
  <li>magic</li>
  <li>OpenLANE</li>
  <li>lverilog</li>
  <li>gtkwave</li>
  <li>ngspice</li>
  <li>OpenSTA</li>
  
</ol>
 <h2></h2>
  <h2>Yosys – Yosys Open Synthesis Suite</h2>
<p>
 <pre>$ git clone https://github.com/YosysHQ/yosys.git 
$ cd yosys 
$ sudo apt install make # (If make is not installed please install it) 
$ sudo apt-get install build-essential clang bison flex \ 
  libreadline-dev gawk tcl-dev libffi-dev git \ 
  graphviz xdot pkg-config python3 libboost-system-dev \ 
  libboost-python-dev libboost-filesystem-dev zlib1g-dev 
$ make 
$ sudo make install </pre>
  ( Note:- If code shows some error then remove "\" it from the code and keep it continue. ) <br> <br>
  <p align="center">
  <img src="https://github.com/user-attachments/assets/1a0578b4-934a-47a3-82fc-036bb65a6bf0" alt="yosys" width="575">
</p>

  <h2></h2>
   <h2>Magic</h2>
  <p>
    <pre>$ sudo apt-get install m4
$ sudo apt-get install tcsh
$ sudo apt-get install csh
$ sudo apt-get install libx11-dev
$ sudo apt-get install tcl-dev tk-dev
$ sudo apt-get install libcairo2-dev
$ sudo apt-get install mesa-common-dev libglu1-mesa-dev
$ sudo apt-get install libncurses-dev
git clone https://github.com/RTimothyEdwards/magic
cd magic
./configure
make
make install  </pre>
    <p align="center">
  <img src="https://github.com/user-attachments/assets/5e351991-6278-44fd-ab31-73c66cd9f34b" alt="yosys" width="575">
</p>
  </p>
  <h2></h2>
  <h2>Dependencies </h2>
    <pre>sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git </pre>
    <pre>sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o
/usr/share/keyrings/docker-archive-keyring.gpg</pre>
    <pre>echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg]
https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee
/etc/apt/sources.list.d/docker.list > /dev/null  </pre>
      <pre># After reboot
  docker run hello-world </pre><br>
         (<b>Note :-</b> You should install all the dependencies before installing OpenLANE.)      
  </p>
  <h2></h2>
  <h2>OpenLANE</h2>
  <p>
    <pre>cd $HOME
git clone https://github.com/The-OpenROAD-Project/OpenLane
cd OpenLane
make
make test   </pre>
      <p align="center">
  <img src="https://github.com/user-attachments/assets/80845108-1ea8-4b45-936d-ad61391072ce" alt="yosys" width="675">
        <img src="https://github.com/user-attachments/assets/74d89146-c9bb-41ab-804d-59136c6b1d98" alt="yosys" width="675"> </p>
      <details>
      <summary> OpenLane PDK Version Mismatch </summary><br>
      <p><b> Error encountered:</b></p>
        <p><i>While running make test in OpenLane:</i></p>
        <pre>[ERROR]: The version of open_pdks used in building the PDK does not match the version OpenLane was tested on
  (installed: a80ed405766c5d4f21c8bfca84552a7478fe75b2, tested: 0fe599b2afb6708d281543108caf8310912f54af)
  This may introduce some issues. You may want to re-install the PDK by invoking `make pdk`.</pre>
        <p> <i>Cause</i> <br>
                The installed Sky130 PDK version did not match the version OpenLane expects.</p>
        <p> <i>Solution</i> <br>
          <ol>
            <ln>Set up Python virtual environment:</ln><br>
            <pre>python3 -m venv venv
  source ./venv/bin/activate
  pip install volare</pre>
            <ln>Enable the tested PDK version:</ln>
            <pre>./venv/bin/ciel enable --pdk-family sky130 (hashes)</pre>
            <ln>Verify enabled PDK:</ln>
            <pre>./venv/bin/ciel ls-enabled --pdk-family sky130</pre>
            <ln>Run OpenLane flow:</ln>
            <pre>make test</pre>
          </ol>
      </details>
      <h2></h2>
  <h2>Iverilog</h2>
  Steps to install iverilog
  <p>
    <pre>sudo apt-get update
sudo apt-get install iverilog     </pre>
  </p>
  <h2></h2>
  <h2>gtkwave</h2>
  Steps to install gtkwave
  <p>
    <pre>sudo apt-get update
sudo apt-get install iverilog    </pre>
<h2></h2>
  <h2>ngspice</h2>
  <p>After downloading the tar file from https://sourceforge.net/projects/ngspice/files/ to a local
directory, unpack it using:</p>
    <pre>$ tar -zxvf ngspice-37.tar.gz
$ cd ngspice-37
$ mkdir release
$ cd release
$ ../configure --with-x --with-readline=yes --disable-debug
$ make
$ sudo make install  </pre>
<h2></h2>
  <h2>OpenSTA - Static Timing Analysis</h2>
  Reference :-  https://github.com/The-OpenROAD-Project/OpenSTA <br>
  <p>Build by using CMake.</p>
  Dependencies to download first.
    <pre>         Ubuntu   Macos
        22.04.2   14.5
cmake    3.24.2    3.29.2
clang             15.0.0
gcc      11.4.0
tcl       8.6      8.6.16
swig      4.1.0    4.1.1
bison     3.8.2    3.8.2
flex      2.6.4    2.6.4 <br>
<b>External Dependencies</b><br>
                 Ubuntu   Darwin  License
eigen       3.4.0   3.4.0   MPL2  required
cudd        3.0.0   3.0.0   BSD   required
tclreadline 2.3.8   2.3.8   BSD   optional
zLib        1.2.5   1.2.8   zlib  optional    </pre>
CUDD is available <a href="https://github.com/davidkebo/cudd/blob/main/cudd_versions/cudd-3.0.0.tar.gz">here.</a> download and follow the following steps.
<pre>tar xvfz cudd-3.0.0.tar.gz
cd cudd-3.0.0
./configure
make</pre>
<h2>Building with CMake</h2>
Use the following commands to checkout the git repository and build the OpenSTA library and excutable.
<pre>git clone https://github.com/parallaxsw/OpenSTA.git
cd OpenSTA
mkdir build
cd build
cmake -DCUDD_DIR=<CUDD_INSTALL_DIR> ..
make
</pre>
  If you find any difficulty then click <a href="https://github.com/The-OpenROAD-Project/OpenSTA?tab=readme-ov-file#building-with-cmake">here.</a><br>
  If you have any issues while performing setup please share it with me, I would love to solve it and I can update it on my repo.<br><br>
  <div align="center">
  <b><i>Thankyou for reading </i></b>
</div>
</details>
  <details>
<summary>
  Week 1 :- Introduction to Iverilog Design and Test Bench.
</summary>
    <br>
<h2>Day 1 :- Introduction to verilog RTL design and Synthesis.</h2>
    <p>
<ol><h3> <li>Introduction to open-source simulator Iverilog.</li></h3><h2></h2>
  <p>A simulator is a software tool that helps verify digital designs before they are implemented in hardware. It allows us to test the functionality of the design by executing it together with a testbench. </p>
  In Iverilog, the inputs are:
  <ul><li>Design file (RTL code)</li>
    <li>Testbench file</li></ul><br>
  Basic Simulation Flow:
  <ol><li>Write the RTL design and testbench.</li>
  <li>Compile using Iverilog.</li>
  <li>Run the simulation to generate a VCD file.</li>
  <li>Open the VCD file in GTKWave to visualize waveforms.</li></ol>
  <h2></h2>
 <h3><li>Labs using Iverilog and GTKWave.</li></h3><h2></h2>
  <p>To simulate a design and view its waveforms, the following steps were performed:
  <ol><li>Clone the workshop repository:</li>
    <pre>git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files</pre>
    <li>Compile the Verilog design using Iverilog:</li>
    <pre>cd verilog files
    iverilog good_latch.v</pre>This generates an output file named <b>"a.out."</b><br>
    <br><li>Run the simulation:</li>
    <pre>./a.out</pre>This produces the simulation result in a VCD file (e.g., tb_good_latch.vcd).<br>
    <br><li>Open the waveform in GTKWave:</li>
    <pre>gtkwave tb_good_latch.vcd</pre>At this stage, the signal transitions of the design can be visualized and analyzed in GTKWave to verify its functionality.</ol>
  <br>
  <p align="center">
  <img src="https://github.com/user-attachments/assets/b386e58c-8cc5-4927-86b4-9ff97209e914" width="45%"  valign="top"  />
  <img src="https://github.com/user-attachments/assets/b44e0958-5a2d-4659-8508-8e9a39685783" width="45%" />
</p>
  </p>
  <h2></h2>
 <h3> <li>Introduction to Yosys and Logic Synthesis</li></h3><h2></h2>
  <p>Yosys is an open-source logic synthesis tool used to convert RTL (Register Transfer Level) designs into a gate-level netlist. This netlist maps the design onto standard cells from a library, preparing it for further verification and eventual hardware implementation. Verification of Synthesis <br> After synthesis, the netlist is verified to ensure functional equivalence with the original RTL:
  <ol>
    <li>The netlist is simulated along with the same testbench used for RTL simulation.</li>
    <li>The simulator (e.g., Iverilog) generates a VCD file capturing signal transitions.</li>
    <li>This VCD file is viewed in GTKWave to compare waveforms and confirm that the synthesized design behaves identically to the RTL.</li>
  </ol>
  </p>
  <h2></h2>
 <h3> <li>Labs using Yosys and Sky130 PDKs</li></h3><h2></h2>
  <p>To synthesize a design using Yosys and the Sky130 PDK, the following steps were performed:
  <ol>
    <li>Navigate to the Verilog files directory:</li>
    <pre>cd verilog_files</pre>
    <li>Start Yosys and read the standard cell library:</li>
    <pre>yosys <br>read_liberty -lib ( relative_path_to_liberty_file ) </pre>
    <li>Read the Verilog design file:</li>
    <pre>read_verilog good_mux.v</pre>
    <li>Synthesize the design specifying the top module and library:</li>
    <pre>synth -top good_mux
abc -liberty ( relative_path_to_liberty_file )</pre>
  <li>Visualize the synthesized netlist:</li>
  <pre>show</pre>
  <li>Export the synthesized netlist to a Verilog file:</li>
  <pre>write_verilog -noattr good_netlist.v</pre>
  <li>(Optional) Open the file in a text editor for inspection:</li>
  <pre>!gvim ( file_name )</pre>
  </ol>
    <b>Explanation:</b>
    <ul>
      <li><code>read_liberty:</code> Loads the standard cell library for synthesis.</li>
      <li><code>read_verilog:</code> Loads the RTL design.</li>
      <li><code>synth</code> + <code>abc:</code> Performs logic synthesis and maps the design to the library cells.</li>
      <li><code>show:</code> Visualizes the netlist structure.</li>
      <li><code>write_verilog:</code> Saves the synthesized netlist for post-synthesis simulation or further processing.</li>
    </ul>
  </p>
</ol>
    </p>
  </details>
