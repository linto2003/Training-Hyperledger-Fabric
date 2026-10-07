# CarTrade Fabric Case Study

Basic Hyperledger Fabric 2.5.x case study for a used-car purchase.

## Organizations

- Org1 - Car Dealer
- Org2 - Buyer
- Org3 - Vehicle Inspector

## Channel

`cartrade-channel`

## Chaincodes

### Vehicle

Manages:

- vehicle registration
- vehicle inspection
- vehicle verification
- ownership transfer
- vehicle history
- private dealer/buyer deal

### ERC20

Manages:

- AutoCoin initialization
- mint
- balance
- transfer
- approve
- allowance
- transferFrom
- burn
- total supply

## Private Data Collection

`DealerBuyerPrivateCollection`

Members:

- Org1MSP
- Org2MSP

Org3 is not a member.

## Node SDK

The SDK follows a simple Express layered structure inspired by the supplied reference:

```text
routes
  -> controllers
      -> services
          -> wallet / Fabric Gateway
```

The SDK dynamically creates wallet identities using Fabric CA. It does not require users to export certificate/private-key paths.

The current Fabric Gateway API requires an Identity and signing implementation when creating a Gateway. The wallet in this project is the application's local credential store used to load those credentials. See the official Gateway API documentation.

## Network setup

From `fabric-samples/test-network`:

```bash
./network.sh up -ca
./network.sh createChannel -c cartrade-channel
```

Deploy vehicle chaincode with the PDC:

```bash
./network.sh deployCC   -ccn vehicle   -ccp ../chaincode/vehicle   -ccl javascript   -c mychannel   -cccg ../collections/collections_config.json
```

Deploy ERC20:

```bash
./network.sh deployCC   -ccn erc20   -ccp ../chaincode/erc20   -ccl javascript   -c mychannel
```

## Start SDK

```bash
cd ../cartrade-fabric/sdk
npm install
cp .env.example .env
npm start
```

Do not commit `.env` or `sdk/wallet/`.
# Training-Hyperledger-Fabric
# Training-Hyperledger-Fabric
# Training-Hyperledger-Fabric
