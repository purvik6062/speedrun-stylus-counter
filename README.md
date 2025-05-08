# 🚩 Challenge #0: 🎟 Simple Counter Example

🎫 Create a simple Counter:

👷‍♀️ You'll compile and deploy your first smart contracts. Then, you'll use a template React app full of important components and hooks. Finally, you'll deploy a Counter contract written in RUST to a public network to share with friends!  🚀

🌟 The final deliverable is an app that lets users interact with the counter contract. Deploy your contracts to a testnet, then build and upload your app to a public web server.

## Checkpoint 0: 📦 Environment Setup 📚

Before you begin, you need to install the following tools:

- [Node (>= v18.17)](https://nodejs.org/en/download/)
- Yarn ([v1](https://classic.yarnpkg.com/en/docs/install/) or [v2+](https://yarnpkg.com/getting-started/install))
- [Git](https://git-scm.com/downloads)

Then download the challenge to your computer and install dependencies by running:

> ⚠️ IMPORTANT: Please make sure to run the below commands through WSL only. In PowerShell, you'll get an error because some files are not supported on Windows.

```sh
git clone https://github.com/abhi152003/speedrun_stylus.git
cd speedrun_stylus
git checkout counter
yarn install
```

> In the same terminal, after all the dependencies have installed, run the below commands to start the local devnode in Docker. You'll need to spin up the Stylus nitro devnode by running the script through commands. This script will deploy the contract and generate the ABI so you can interact with the contracts written in RUST:

Contracts will be deployed through the cargo stylus command using the pre-funded account's private key so users can perform any transaction through the frontend while interacting with the contract.

```sh
cd speedrun_stylus # if not done
cd packages
cd stylus-demo
```

> Now open your Docker desktop and then return to your IDE and run bash run-dev-node.sh. This will spin up the nitro devnode in Docker. You can check it out in your Docker desktop. This will take some time to deploy the RUST contract, and then the script will automatically generate the ABI. You can view all these transactions in your terminal and Docker desktop. The Docker node is running at localhost:8547,
but before running this command make sure about below thing

## 🚨 Fixing Line Endings and Running Shell Scripts in WSL on a CRLF-Based Windows System

> ⚠️ This guide provides step-by-step instructions to resolve the Command not found error caused by CRLF line endings in shell scripts when running in a WSL environment.

---

## 🛠️ Steps to Fix the Issue

###  Convert Line Endings to LF
Shell scripts created in Windows often have `CRLF` line endings, which cause issues in Unix-like environments such as WSL. To fix this:

#### Using `dos2unix`
1. Install `dos2unix` (if not already installed):
   ```bash
   sudo apt install dos2unix
   ```

2. Convert the script's line endings:
    ```bash
   dos2unix run-dev-node.sh
   ```

3. Make the Script Executable:
    ```bash
    chmod +x run-dev-node.sh
    ```

4. Run the Script in WSL
    ```bash
    bash run-dev-node.sh
    ```

> Then in a second WSL terminal window, you can run below commands to start your 📱 frontend:

```sh
cd speedrun_stylus ( if not done )
cd packages ( if not done )
cd nextjs
yarn run dev OR yarn dev
```

📱 Open [http://localhost:3000](http://localhost:3000) to see the app.

---

## 💫 Checkpoint 1:  Frontend Magic

> ⛽ You'll be redirected to the below page after you complete checkpoint 0

![image](https://github.com/user-attachments/assets/e4b8dc4a-f304-43ef-8817-ae6d028beea4)

> Then you have to click on the debug contracts to start interacting with your contract. Click on "Debug Contracts" from the Navbar or from the Debug Contracts Div placed in the middle of the screen

![image](https://github.com/user-attachments/assets/11197d34-bb2a-4ab7-8f06-3ff2dfabb67a)

The interface allows you to:

1. Set any number
2. Add numbers
3. Increment count
4. Perform multiplications
5. Track all transactions in the Block Explorer

> After that, you can easily view all of your transactions from the Block Explorer Tab

![image](https://github.com/user-attachments/assets/48ab1e39-7560-4441-b7dc-2acbdf8cedfe)


💼 Take a quick look at your deploy script `run-dev-node.sh` in `speedrun-rust/packages/stylus-demo/run-dev-node.sh`.

📝 If you want to edit the frontend, navigate to `speedrun-rust/packages/nextjs/app` and open the specific page you want to modify. For instance: `/debug/page.tsx`. For guidance on [routing](https://nextjs.org/docs/app/building-your-application/routing/defining-routes) and configuring [pages/layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts) checkout the Next.js documentation.

---

## Checkpoint 2: 💾 Deploy your contract! 🛰

🛰  You don't need to provide any specifications to deploy your contract because contracts are automatically deployed from the `run-dev-node.sh`

> You can check that below :

![image](https://github.com/user-attachments/assets/d84c4d6a-be20-426b-9c68-2c021caefb29)

The above command will automatically deploy the contract functions written inside `speedrun_stylus/packages/stylus-demo/src/lib.rs`

> This local account will deploy your contracts, allowing you to avoid entering a personal private key because the deployment happens using the pre-funded account's private key.

## Checkpoint 3: 🚢 Ship your frontend! 🚁

> We are deploying all the RUST contracts at the `localhost:8547` endpoint where the nitro devnode is spinning up in Docker. You can check the network where your contract has been deployed in the frontend (http://localhost:3000):

![image](https://github.com/user-attachments/assets/bb82e696-97b9-453e-a7c7-19ebb7bd607f)

🚀 Deploy your NextJS App

```shell
yarn vercel
```

> Follow the steps to deploy to Vercel. Once you log in (email, github, etc), the default options should work. It'll give you a public URL.

> If you want to redeploy to the same production URL you can run `yarn vercel --prod`. If you omit the `--prod` flag it will deploy it to a preview/test URL.

⚠️ Run the automated testing function to make sure your app passes

```shell
yarn test
```

---

## Checkpoint 4: 📜 Contract Verification

You can verify your smart contract by running:

```bash
cargo stylus verify -e http://127.0.0.1:8547 --deployment-tx "$deployment_tx"
# here deployment_tx can be received through the docker desktop's terminal when you have depoloyed your contract using the below command:

cargo stylus deploy -e http://127.0.0.1:8547 --private-key "$your_private_key"
# here you can use pre-funded account's private-key as well
```

> It is okay if it says your contract is already verified. 


---


> 🏃 Head to your next challenge [here](https://github.com/abhi152003/speedrun_stylus).
