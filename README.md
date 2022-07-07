# simox
## Installation on Ubuntu18.04 

### Get Simox from gitlab repository
Retrieve the sources with:

git clone https://gitlab.com/Simox/simox.git

### Install Dependencies
On Ubuntu 18.04 execute the following lines:

sudo apt-get install -y curl apt-file
sudo curl https://packages.humanoids.kit.edu/h2t-key.pub | sudo apt-key add - 
echo -e "deb http://packages.humanoids.kit.edu/bionic/main bionic main\ndeb http://packages.humanoids.kit.edu/bionic/testing bionic testing" | sudo tee /etc/apt/sources.list.d/armarx.list 
sudo apt-file update
#simox dependencies
sudo apt install -y git g++-8 libboost-all-dev cmake libeigen3-dev libnlopt-dev freeglut3-dev qtbase5-dev libqhull-dev  liburdfdom-dev libassimp-dev libtiff-dev
sudo apt-get install h2t-libbullet h2t-libsoqt5-dev h2t-libsimage-dev h2t-libcoin80-dev

### Compile Simox
On Ubuntu 18.04:

Create make files:

cd simox  
mkdir build  
cd build  
CXX=g++-8 cmake ..  
make -j4

You may need to adapt your bullet path.
