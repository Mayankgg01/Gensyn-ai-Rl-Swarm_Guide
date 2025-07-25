<div align="center">

# 💻 Gensyn-ai-Rl-Swarm_Guide {Mac/Linux} 💻

</div>


## Device/System Requirements 🖥️

![image](https://github.com/user-attachments/assets/4fbf23bb-846c-4def-be24-157c51fa0b4e)



* Open Your Vps

```
ssh username@ip
```

## Pre-Requirements 🛠

# Install Python and Other Tools

* For **Linux/Wsl**

```
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof

```

* **For Mac**

```
brew install python
```

Check Version

```
python3 --version
```


# Install Node.js , npm & yarn

* For **Linux/Wsl**

```
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt update && sudo apt install -y nodejs
```

* Install Yarn (linux)

```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
```

```
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list > /dev/null
```

```
sudo apt update && sudo apt install -y yarn
```


* For **Mac**

```
brew install node && corepack enable && npm install -g yarn
```

* Check version **(Linux/Mac)**

```
node -v
```
```
npm -v
```

```
yarn -v
```


<div align="center">

# 👨🏻‍💻 Start The Node (Linux/Mac) 

</div>


 1️⃣ Create a screen session **(vps only)**

```
screen -S gensyn
````


 2️⃣ Clone RL-SWARM Repo

```
git clone https://github.com/gensyn-ai/rl-swarm.git
```


 3️⃣ Navigate to rl-swarm

```
cd rl-swarm
```

 4️⃣ Create & Activate a Virtual Environment

```
python3 -m venv .venv
source .venv/bin/activate
```


#### 5️⃣ Run the swarm Node 

```
./run_rl_swarm.sh
```

* Now it will promt you to login: Follow: [1️⃣ How to Login or access  http://localhost:3000/ in VPS? 📶](https://github.com/Mayankgg01/Gensyn-ai-Rl-Swarm_Guide?tab=readme-ov-file#1%EF%B8%8F%E2%83%A3-how-to-login-or-access--httplocalhost3000-in-vps-)

* Now It will promt `Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N]` Enter `N`

* Now It will promt `>> Enter the name of the model you want to use in huggingface repo/name format, or press [Enter] to use the default model.`  press `Enter` & get defalut model:


---❗ If U put model manually then it can be cause of terminated❗--- So better to use Default:

------>>>If u want to select the model then choose between them: [5️⃣ Choose customised model's](https://github.com/Mayankgg01/Gensyn-ai-Rl-Swarm_Guide/edit/main/README.md#5%EF%B8%8F%E2%83%A3-choose-customised-models)


Here we go🚀

Its Done ✅

It will Generate Logs Soon🙌


# Detach & Attach from screen

`ctrl` `A` `D` To Detach from screen 

* Attach with previous screen:

```
screen -r gensyn
```



<div align="center">

#  🛠 FAQ & Troubleshoot 🛠

</div>


## 1️⃣ How to Login or access  http://localhost:3000/ in VPS? 📶

* Open a new Terminal and login ur vps 

* Allow Incoming connection on VPS

```
sudo apt install ufw -y
sudo ufw allow 22
sudo ufw allow 3000/tcp
```

* Enable ufw

```
sudo ufw enable
```

* Install cloudflared on the VPS

```
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
````

```
sudo dpkg -i cloudflared-linux-amd64.deb
```

* Check version

```
cloudflared --version
```

* Make sure your Node is running on port 3000 in Previous Screen

* Run the tunnel command

```
cloudflared tunnel --url http://localhost:3000
```

* Access the Link from your local machine

    
    ![image](https://github.com/user-attachments/assets/c5bdfec5-123d-4625-8da8-f46269700950)

* Now follow Login!
 
* Done!✅



## 2️⃣ How to get the Node Name?

* Check the image below to get your Node id!

![image](https://github.com/user-attachments/assets/110a146e-d920-4713-b6b7-f5f5377b9bac)


## 3️⃣ Save your `swarm.pem` file (for future login)

* open a wsl window 

* If U have to copy this file to your local machine from VPS then Run this command from your local Terminal--

```
scp USERNAME@YOUR_IP:~/rl-swarm/swarm.pem ~/swarm.pem
```

It will save here in ur Terminal's Root Directory!


## 4️⃣ How To start the Next Day (Local Pc)

*
 ```
  cd rl-swarm
 ```

*
 ```
  python3 -m venv .venv
```

*
```
source .venv/bin/activate
```

*
```
./run_rl_swarm.sh
```



## 5️⃣ Choose customised model's

----> Recommend for Mac 


<pre>

 Gensyn/Qwen2.5-0.5B-Instruct

 Qwen/Qwen3-0.6B

 nvidia/AceInstruct-1.5B

 dnotitia/Smoothie-Qwen3-1.7B

 Gensyn/Qwen2.5-1.5B-Instruct

</pre>
    
📋 Model-by-Model Breakdown

![image](https://github.com/user-attachments/assets/4d28dc52-c83f-4a1d-82b2-820023ee554d)


## 6️⃣ **Resolve Terminated Error**

* Follow these command one by one: (You should be in Rl-swarm directory) ❗


```
deactivate 
rm -rf .venv
```

```
python3 -m venv .venv
source .venv/bin/activate
```

```
./run_rl_swarm.sh
```

* Now follow all the process from [5️⃣ Run the swarm Node](https://github.com/Mayankgg01/Gensyn-ai-Rl-Swarm_Guide/edit/main/README.md#5%EF%B8%8F%E2%83%A3-run-the-swarm-node)

* If u still Got terminated error then just restart 1-2 times: or just wait few minutes:

<div align="center">

# 📈 Upgrade to new release (v0.5.7) {Mac/Linux} 

</div>

* Go to gensyn screen (Vps)

```
screen -r gensyn
```

* Stop your node by `ctrl+c` if u are on gensyn screen (Vps)

* Move to rl-swarm directory
```
cd rl-swarm
```

* Pull the latest release 


```
git switch main
git reset --hard
git clean -fd
git pull origin main
```


* Start the swarm Node 🚀

```
./run_rl_swarm.sh
```

* Now follow all the process from [5️⃣ Run the swarm Node](https://github.com/Mayankgg01/Gensyn-ai-Rl-Swarm_Guide/edit/main/README.md#5%EF%B8%8F%E2%83%A3-run-the-swarm-node)

* If u got terminated then follow: [6️⃣Resolve Terminated Error](https://github.com/Mayankgg01/Gensyn-ai-Rl-Swarm_Guide/edit/main/README.md#6%EF%B8%8F%E2%83%A3-resolve-terminated-error)

<pre>

👉 Join TG for more Updates: https://telegram.me/cryptogg

If U have any issue then open a issue on this repo or Dm me on TG~

Thank U! 👨🏻‍💻    Happy Coding💗

</pre>
Push contribution trigger by jisjoe22
