# Bitcoin-Simulator-master

Clone the Bitcoin Simulator.
The Bitcoin Simulator is built on ns3 and it has been tested with versions 3.24 and 3.25. So, go to the official site and grab a suitable release. Detailed installation instructions for various platforms can be found here.
Untar it with the following command:

tar xvfj ns-allinone-3.25.tar.bz2

For exhanging block messages, rapidjson is used. Download it from here. https://github.com/miloyip/rapidjson.git

Create a new directory named rapidjson under ns-allinone-3.xx/ns-3.xx and copy the contents of the directory include/rapidjson (from the downloaded rapidjson project in step 4) to the newly created rapidjson folder (ns-allinone-3.xx/ns-3.xx/rapidjson). You also have to copy all the files from Bitcoin-Simulation to the respective folders under ns-allinone-3.xx/ns-3.xx/. All the above can be done automatically by the provided copy-to-ns3.sh script.

Update the ns-allinone-3.xx/ns-3.xx/src/applications/wscript.

Add the following lines in module.source:
'model/bitcoin.cc',
'model/bitcoin-node.cc',
'model/bitcoin-miner.cc',
'model/bitcoin-simple-attacker.cc',
'model/bitcoin-selfish-miner.cc',
'model/bitcoin-selfish-miner-trials.cc',
'helper/bitcoin-topology-helper.cc',
'helper/bitcoin-node-helper.cc',
'helper/bitcoin-miner-helper.cc',					

Add the following lines in headers.source:
'model/bitcoin.h',
'model/bitcoin-node.h',
'model/bitcoin-miner.h',
'model/bitcoin-simple-attacker.h',
'model/bitcoin-selfish-miner.h',
'model/bitcoin-selfish-miner-trials.h',
'helper/bitcoin-topology-helper.h',
'helper/bitcoin-node-helper.h',
'helper/bitcoin-miner-helper.h',					

Update the ns-allinone-3.xx/ns-3.xx/src/internet/wscript.

Add the following line in obj.source:
'helper/ipv4-address-helper-custom.cc',

Add the following line in headers.source:
'helper/ipv4-address-helper-custom.h',

Configure ns3 with the follow command to ensure compatibility and maximum performance.
CXXFLAGS="-std=c++11" ./waf configure --build-profile=optimized --out=build/optimized --with-pybindgen=/home/bill/Desktop/workspace/ns-allinone-3.24/pybindgen-0.17.0.post41+ngd10fa60 --enable-mpi --enable-static

Build ns3 using the ./waf command.
