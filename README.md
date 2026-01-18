# Kiwix-Server-Using-a-Raspberry-PI
A guide on how to create and run an offline knowledge Kiwix Server running on a Raspberry PI 5 with 512 GB SSD storage.  

Hardware

  Raspberry Pi 5
  512GB SSD
  Synology NAS (for additional storage/backup)

Installed Content Options

  Wikipedia English w/ Images, Project Gutenberg, Khan Academy, TEDTalks, and more.



1. Install Kiwix Tools
bashsudo apt update
sudo apt install kiwix-tools
2. Create Directory
bashsudo mkdir -p /mnt/kiwix
cd /mnt/kiwix
3. Download ZIM Files
# Wikipedia English (all articles with images)
wget https://download.kiwix.org/zim/wikipedia/wikipedia_en_all_maxi_2025-08.zim

# Project Gutenberg (all books)
wget https://download.kiwix.org/zim/gutenberg/gutenberg_en_all_2023-08.zim

# Stack Exchange (all sites)
wget https://download.kiwix.org/zim/stack_exchange/stackexchange_en_all_2024-02.zim


4. Create Library File
bashcd /mnt/kiwix
kiwix-manage library.xml add wikipedia_en_all_maxi_2025-08.zim
kiwix-manage library.xml add gutenberg_en_all_2023-08.zim
kiwix-manage library.xml add stackexchange_en_all_*.zim


5. Start Server
bashkiwix-serve --port 8080 --library library.xml


Access
Navigate to http://<raspberry-pi-ip>:8080 from any device on your network.


Find Pi IP Address
bashhostname -I
Useful Commands
List ZIM Files
bashls -lh /mnt/kiwix/*.zim
Remove File
bashrm filename.zim
Check Running Status
bashps aux | grep kiwix
