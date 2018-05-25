# ibus-table-tlim2

ibus table for Tâi-uân Bân-lâm-gí Lô-má-jī Phing-im Hong-àn (臺灣閩南語羅馬字拼音方案)

ibus table here was extracted/converted from binary formatted SCIM table module in [臺灣閩南語漢字輸入法](https://depart.moe.edu.tw/ed2400/cp.aspx?n=BB47AA61331DDAC8&s=5900082022C17E11).

## Install
### Build From Source
To build with traditional method: [![master](https://travis-ci.org/vicamo/ibus-table-tlim2.svg?branch=master)](https://travis-ci.org/vicamo/ibus-table-tlim2)
```
$ git clone -b master https://github.com/vicamo/ibus-table-tlim2.git
$ (cd ibus-table-tlim2; ./autogen.sh && make && make install)
```
To build debian package: [![debian](https://travis-ci.org/vicamo/ibus-table-tlim2.svg?branch=debian/unstable)](https://travis-ci.org/vicamo/ibus-table-tlim2)
```
$ git clone -b debian/unstable https://github.com/vicamo/ibus-table-tlim2.git
$ cd ibus-table-tlim2
$ sudo apt update
$ sudo apt install devscripts equivs
$ mk-build-deps --install --remove --root-cmd sudo
$ dpkg-buildpackage -i -us -uc -b
$ sudo dpkg -i ../ibus-table-tlim2_*.deb
```
### Debian
On debian you may use prebuilt binary deb available on [bintray](https://bintray.com/vicamo/ppa):
```
$ echo "deb [trusted=yes] http://dl.bintray.com/vicamo/ppa sid contrib" | sudo tee /etc/apt/sources.list.d/vicamo-ppa.list
$ sudo apt update && sudo apt install ibus-table-tlim2
```
