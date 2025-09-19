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
  <li>OpenSTA</li>
  <li>graywolf</li>
  <li>qrouter</li>
  <li>lverilog</li>
  <li>ngspice</li>
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
  <h2>OpenLANE</h2>
  <p>
    <pre>
      cd $HOME
      git clone https://github.com/The-OpenROAD-Project/OpenLane
      cd OpenLane
      make
      make test   </pre>
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
         docker run hello-world </pre>
  </p>
</details>

