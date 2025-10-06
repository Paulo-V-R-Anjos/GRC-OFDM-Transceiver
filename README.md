To install through package managers and so on, follow the standard instructions: 

https://wiki.gnuradio.org/index.php/InstallingGR

While it is possible to install GNU Radio (and the companion) through package managers, I prefer to install into a custom preffix because I would like to work with SDR (Software Defined Radio) with my flowgraphs whenever possible.

The installation of GRC (tag v3.10.12.0) into a custom prefix (a custom folder) follows the procedure outlined in Ettus Research’s Knowledge Base:

https://kb.ettus.com/Building_and_Installing_UHD_and_GNU_Radio_to_a_Custom_Prefix

Be aware that it is a old tutorial, so you will have to install the Python 3 and Qt 5 equivalents of the legacy packages:

sudo apt install qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools python3-pyqt5 libqwt-qt5-dev python3-dev python3-numpy python3-scipy python3-docutils python3-mako python3-sphinx python3-lxml python3-requests python3-zmq gpsd-clients gpsd-tools libboost-all-dev python3-setuptools cmake g++ libusb-1.0-0-dev libfftw3-dev libgmp-dev libncurses5-dev libreadline-dev libcppunit-dev libqt5opengl5-dev qttools5-dev libqt5svg5-dev libspdlog-dev libvolk2-dev libsndfile1-dev libgsl-dev pybind11-dev

Follow the steps on the Knowledge Base link and, after cloning the repository, create a build directory and configure with CMake, explicitly pointing to the custom prefix and Python 3 interpreter:

cmake -DCMAKE_INSTALL_PREFIX=$HOME/workarea/installs \
-DENABLE_GR_QTGUI=ON \
-DPYTHON_EXECUTABLE=$(which python3) \
../
make -j4 && make install

Once installation completes, source a setup.env script to export the custom PATH, LD_LIBRARY_PATH, PYTHONPATH and PKG_CONFIG_PATH.
