# INNOVA
Tested innova install


Masternode Guide with cold-windows/mac wallet && hot linux vps
This is a guide to install masternode with your wallet in your home pc and Linux VPS The reason for this way of setting your masternode is security. You will have your coins in your PC and your masternode in VPS won’t have your coins. Your masternode will just do the earning rewards. For your home wallet you can use Windows, Mac or even Linux. But on VPS side you have to use Linux, Ubuntu 16.04 recommended.
STEP 1. Install wallet in your PC
1. Download wallet from releases here for your OS innovacoin wallets.
STEP 2. Pay 1000 INN to yourself
1. Make sure you have a little more than 1000 INN in your balance. It can just be 1001 INN. You can buy the coins here: https://www.cryptopia.co.nz/Exchange/?market=INN_BTC https://coinsmarkets.com/trade-BTC-INNOVA.htm
2. Pay exactly 1000 INN to yourself. When you make transaction you pay a small fee, this is the reason you need a little more than 1000 INN. To make the transaction: 1. Go to File -> Receiving Addresses 2. Click on “New” and give label name something like “For_my_masternode_1” and click Ok. Select the new created address and click copy. 3. On your main window go to “Send” tab. Paste the copied address to address box. Type 1000 for Amount box. Do not select “Subtract fee from amount” checkbox. Send the coin. Now it will take some time until this transaction is confirmed. Let’s move to your VPS.
STEP 3. Install Masternode
1. Login to your VPS server with root user. Make sure you are in root directory
cd /root 
2. Download installing script file
apt-get install wget -y wget https://github.com/innovacoin/sentinel/releases/download/linux_masternode_script/linux_masternode_setup_script.sh
3. Make the script executable
chmod 740 linux_masternode_setup_script.sh
4. Run the script to install
./linux_masternode_setup_script.sh
Now it will take some time. Wait until the following is printed to the console: “Job completed successfully”. It will also print masternode private key as: “Masternode private key:<generated private key>”. Save that somewhere, you will use it later. Note, if you happen to see nothing after Masternode private key: then it failed to generate private key. In that case follow these steps: (Skip to Step 4 if you see private key) a) Generate key:
innova-cli masternode genkey
b) Copy the printed key and open the config file:
nano /root/.innovacore/innova.conf
c) Paste the copied key after masternodeprivkey= d) Save and close the file
CTRL+X Y ENTER
5. Remove the script
rm linux_masternode_setup_script.sh
Now come back to your wallet in your PC.
STEP 4. Set Masternode config
Now hopefully your transaction to yourself has been confirmed. Let us see. 1. Go to Tools -> Debug Console 2. In text box below run the following command
masternode outputs
It should print something like this:
{ “sgthd5a539ea889sgs434287ce8hyy6s5rqf1p12bbb58ac8uusy2eb885l”: “1” }
The long string is the transaction id of your payment and the number is transaction index. Save them too, you will use them shortly.
Note that transaction id and index number do not contain quotes. In the example above transaction id is:    sgthd5a539ea889sgs434287ce8hyy6s5rqf1p12bbb58ac8uusy2eb885l .
3. Go to Tools -> Masternode configuration file. It will open your masternode config file. 4. In a new line type your masternode data, the syntax is as following:
alias vps_ip_address:14520 masternode_private_key transaction_id_of_your_payment transaction_index_number
You can copy paste the line above and replace with your own ip, privkey, transaction id and index. Note that each data is separated by space, so do not introduce any space yourself. For example giving the following alias is wrong
My alias that gives me a trouble
5. Save and close the config file. Restart the wallet. 6. Go to “Masternodes” tab. You should see your configured masternode as missing. Click on “Start Missing”, give your passphrase and confirm. Now you should see your masternode as “Pre_Enabled” or “Enabled” If so you are all set. It will start getting rewards in 24 hours. Happy Collecting your Masternode Rewards! 



rpcuser=innovauser
rpcpassword=
rpcport=14519
port=14520
listen=1
maxconnections=256
masternode=1
masternodeprivkey=
