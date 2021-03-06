# WiFiCrackPy

WiFiCrackPy demonstrates of some of the security flaws associated with WPA(2) networks by performing simple and efficient cracking. It captures the necessary Wi-Fi packets associated with with WPA(2) handshakes and then utilises [hashcat](https://github.com/hashcat/hashcat) to attempt to extract the hashed passkey. The script is for educational purposes and should not be misused.

WiFiCrackPy has been developed as the successor of [WiFiCrack](https://github.com/Tommrodrigues/WiFiCrack) which is written in bash. The script is much more streamlined and reliable than its predecessor with some additional functionality.

## Prerequisites

You must have Python 3 installed. You will need to install any other outstanding requirements:

| Command | Installation |
| --- | --- |
| `hashcat` | Install via [brew](https://brew.sh) by running `brew install hashcat`|
| `mergecap` | Comes with the [Wireshark](https://www.wireshark.org) application (v2.6.12) |
| `./hashcat-utils/src/cap2hccapx.bin` | Clone the [repository](https://github.com/hashcat/hashcat-utils) then run `make` from inside `src` |

## Usage

Download with:
```
git clone https://github.com/Tommrodrigues/WiFiCrackPy.git
pip3 install -r ~/WiFiCrackPy/requirements.txt
```

Run from same directory with:
```
python3 WiFiCrackPy.py
```

The script is fairly easy to use, simply run it using the command above and enter your `sudo` password when prompted. Here are some flags you can add:

| Flag | Description |
| --- | --- |
| `-w <wordlist>` | Wordlist: Define a wordlist path (script will prompt you otherwise) |
| `-i <interface>` | Interface: Set Wi-Fi interface (script can auto-detect default interface) |
| `-m <method>` | Method: Define the attack method (script will prompt you otherwise) |
| `-p <pattern>` | Pattern: Define a brute-force pattern in advance (script will prompt you if required otherwise) |

After running the script, you will be asked to choose a network to crack

Following the selection of a network, you may have to wait for a while until a handshake occurs on the target network (i.e. for a device to (re)connect to the network), but this can be hastened by performing a [deauthentication attack](https://en.wikipedia.org/wiki/Wi-Fi_deauthentication_attack).

Once a handshake is captured, WiFiCrackPy will initialise `hashcat` to extract the Wi-Fi password. This step may take a while depending on a number of factors including your processing power. If successful you will be presented with the password. WiFiCrackPy will retain the handshake in its directory if you would like to perform another type of attack against the capture.

## To-do list

- [ ] Integrate deauthentication attack into main script
