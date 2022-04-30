# Nimbus
 Blockchain project

# Simulating
What you need to get started: 
* Two Git Bash terminals open
* Postman

Running the Blockchain demo
1. Open both Git Bash terminal in the root of Nimbus
2. Open Postman create a new collection
   1. Right click on the new collection
   2. Selet Add Request
   3. Repeat the last two steps twice
   4. Rename the requests "3001 Get Blocks", "Mine", and "3002 Get Blocks".
![image](https://user-images.githubusercontent.com/16611773/166111105-623fa4e7-0327-416f-9a20-bccaa81e3927.png)
3. In the "3001 Get Blocks" request, make it a GET request with an address of *localhost:3001/blocks*
4. In the "3002 Get Blocks" request, make it a GET request with an address of *localhost:3002/blocks*
5. In the "Mine" request, make it a POST request with an address of *localhost:3001/mine*
   1. This request adds new blocks to the chain. You will need to add a body to the HTTP message.
      1. Select Body under the url, then make sure the left dropdown says *raw* and dropdown to the right says *JSON*
      2. Put this string in the body: *{"data":"ThisIsTheSecondBlock"}*
![image](https://user-images.githubusercontent.com/16611773/166111078-9fc43565-fd6d-49b5-9522-cb387c6f3eda.png)

6. In the first Git Bash terminal, run this command *npm run dev*.
7. In the second Git Bash terminal, run this command *HTTP_PORT=3002 P2P_PORT=5002 PEERS=ws://localhost:5001 npm run dev*
8. Now you have set up the basis for a Peer-to-peer architecture. You will now need to ensure that you can see both terminals and your Postman instance at the same time. When you do a request in post man, things are going to happen in your terminals.
9. In Postman under the "Get Blocks" request, click send.
   1.  All this should do is return the Genesis Block of the blockchain. This is the block that starts all blockchains.
![image](https://user-images.githubusercontent.com/16611773/166111162-ac3a21a8-00f6-41b1-bd08-e52aa3cfa5f0.png)
10. Navigate to your "Mine" request tab and insure that the JSON string provided in 5.1.2 is inserted into the body. Then click send.
    1.  This creates the second block in your blockchain instance. 
11. In your two other GET requests (3002 & 3001) click send.
    1.  You should see that the HTTP message returns 200 OK and the body contains two blocks now. 
    2.  Plus, in your Git Bash terminals there should be activity as well. 

# Tests
* npm run test ensures that the blockchain functionality is working
* Testing for the wallet can be found at ~/Nimbus/wallet/transactions.test.js
* Testing for the blockchain can be found at ~/Nimbus/blockchain/block.test.js
* Testing for validation can be found at ~/Nimbus/blockchain/index.test.js
* npm run dev-test is used to simulate block creation and creating a wallet.
