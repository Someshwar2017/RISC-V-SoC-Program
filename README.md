# RISC-V SoC Program 
<details>
<summary> Week 0 - Tools Installation </summary>
  <br>
  <p>  In this step we are going to install all necessory Open Source tools which we are going to use in this program. Before that setup ubuntu in oracle virtualbox <br>
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
  <li>graywolf</li>
  <li>qrouter</li>
  
</ol>
 <h2></h2>
  <h2>Yosys – Yosys Open Synthesis Suite</h2>
<p>
 <pre> $ git clone https://github.com/YosysHQ/yosys.git 
       $ cd yosys 
       $ sudo apt install make # (If make is not installed please install it) 
       $ sudo apt-get install build-essential clang bison flex \ 
               libreadline-dev gawk tcl-dev libffi-dev git \ 
               graphviz xdot pkg-config python3 libboost-system-dev \ 
               libboost-python-dev libboost-filesystem-dev zlib1g-dev 
       $ make 
       $ sudo make install </pre>
  ( Note:- If code shows some error then remove "\" it from the code and keep it continue ) <br> <br>
  <p align="center">
  <img src="https://github.com/user-attachments/assets/1a0578b4-934a-47a3-82fc-036bb65a6bf0" alt="yosys" width="575">
</p>

  <h2></h2>
   <h2>Magic</h2>
  <p>
    <pre> 
    $ sudo apt-get install m4
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
    <pre>
      sudo apt-get update
      sudo apt-get upgrade
      sudo apt install -y build-essential python3 python3-venv python3-pip make git </pre>
    <pre>
      sudo apt install apt-transport-https ca-certificates curl software-properties-common
      curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o
      /usr/share/keyrings/docker-archive-keyring.gpg</pre>
    <pre>
      echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg]
      https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee
      /etc/apt/sources.list.d/docker.list > /dev/null  </pre>
      <pre>
        # After reboot
         docker run hello-world </pre><br>
         (<b>Note :-</b> You should install all the dependencies before installing OpenLANE)      
  </p>
  <h2></h2>
  <h2>OpenLANE</h2>
  <p>
    <pre>
      cd $HOME
      git clone https://github.com/The-OpenROAD-Project/OpenLane
      cd OpenLane
      make
      make test   </pre>
      <p align="center">
  <img src="https://github.com/user-attachments/assets/80845108-1ea8-4b45-936d-ad61391072ce" alt="yosys" width="575">
        <img src="https://github.com/user-attachments/assets/74d89146-c9bb-41ab-804d-59136c6b1d98" alt="yosys" width="575">
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
</details>

