# NFT-коллекция

![](ipfs/images/../my-nft-contract-front.png)

# Реализованные подзадачи
- написан смарт-контракт с использованием библиотек OpenZeppelin
- написаны тесты 100% покрывающие код собственного смарт-контракта, coverage report приведен ниже
- в папке `scripts` находятся скрипты для деплоя и минта NFT
- в папке `ipfs` находятся файлы которые были размещены в IPFS

# Coverage report

```bash
  NFT
    Basic checks
      ✔ Should be deployed
      ✔ Can update baseURI
    Minting
      ✔ Should mint token
      ✔ Minted token URI check
      ✔ Should revert on max supply (54ms)
      ✔ Should revert on the low payment
    Withdrawal
      ✔ Should not revert on normal usage
      ✔ Should work only for owner


  8 passing (414ms)

------------|----------|----------|----------|----------|----------------|
File        |  % Stmts | % Branch |  % Funcs |  % Lines |Uncovered Lines |
------------|----------|----------|----------|----------|----------------|
 contracts/ |      100 |      100 |      100 |      100 |                |
  NFT.sol   |      100 |      100 |      100 |      100 |                |
------------|----------|----------|----------|----------|----------------|
All files   |      100 |      100 |      100 |      100 |                |
------------|----------|----------|----------|----------|----------------|
```

# Gas report

```bash
·------------------------------|----------------------------|-------------|-----------------------------·
|     Solc version: 0.8.17     ·  Optimizer enabled: false  ·  Runs: 200  ·  Block limit: 30000000 gas  │
·······························|····························|·············|······························
|  Methods                     ·               22 gwei/gas                ·       1795.01 usd/eth       │
·············|·················|··············|·············|·············|···············|··············
|  Contract  ·  Method         ·  Min         ·  Max        ·  Avg        ·  # calls      ·  usd (avg)  │
·············|·················|··············|·············|·············|···············|··············
|  NFT       ·  changeBaseURI  ·           -  ·          -  ·      33245  ·            2  ·       1.31  │
·············|·················|··············|·············|·············|···············|··············
|  NFT       ·  safeMint       ·      103914  ·     149314  ·     122831  ·           12  ·       4.85  │
·············|·················|··············|·············|·············|···············|··············
|  NFT       ·  withdraw       ·           -  ·          -  ·      30466  ·            2  ·       1.20  │
·············|·················|··············|·············|·············|···············|··············
|  Deployments                 ·                                          ·  % of limit   ·             │
·······························|··············|·············|·············|···············|··············
|  NFT                         ·           -  ·          -  ·    3344177  ·       11.1 %  ·     132.06  │
·------------------------------|--------------|-------------|-------------|---------------|-------------·
```

# Типичные команды при работе с проектом

## Компиляция
```console
npx hardhat clean && npx hardhat compile
```

## Запуск тестов, проверка покрытия кода тестами

Для показа цены за газ необходимо указать `COINMARKETCAP_API_KEY` в файле `.env`

```console
npx hardhat test [--grep text]
REPORT_GAS=true npx hardhat test
npx hardhat coverage
```

## Деплой и минт

```console
npx hardhat run scripts/deploy.js --network bnbt
npx hardhat run scripts/mint.js --network bnbt
```

## Верификация кода контракта на BscScan Testnet

Для использования необходимо указать `BSCSCAN_API_KEY` в файле `.env`

```console
npx hardhat verify --network bnbt {contractAddress}
```