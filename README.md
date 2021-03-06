# cryptsy-api
Forked from Forked from Brian Water's cryptsy-api at https://github.com/abwaters/cryptsy-api to include Maven support

Small fast (and complete) Java API for the Cryptsy crypto-currency exchange with minimal dependencies.  The only external library needed to use this API is the [Google Gson Library](https://code.google.com/p/google-gson/).

Note: While the API is complete and functional in its current state, I am refining the naming conventions for the API and adding documentation.  This may require small but critical changes to your code if you upgrade to future versions.

## Installation

Add the file Cryptsy.java to your project and include the Gson jar as a reference.  Thats all thats needed.  The unit tests for this library use a properties file for saving the API keys but thats not a requirement.  The use of the properties file is only a requirement of the unit tests and not the API itself.

## Basic Usage

Create a Cryptsy API object using the following code:

```java
cryptsy = new Cryptsy();
cryptsy.setAuthKeys("<api_key>", "<api_secret>");
```

After this, using the API is as simple as calling the appropriate method off of your `cryptsy` object.  It is useful to look at the com.abwaters.cryptsy.Cryptsy_Test.java source code since the unit tests in this file contain sample code for all of the APIs.  I'll be adding a complete javadoc in the near future.

## Examples

### Get account info
Obtain account info including account balances and amounts on hold due to open orders:

```java
InfoReturn info = cryptsy.getInfo();
System.out.println(info);
for (String currency : info.balances_available.keySet()) {
	double val = info.balances_available.get(currency);
	if (val > 0)
		System.out.println("    Available " + currency + "=" + val);
}
for (String currency : info.balances_hold.keySet()) {
	double val = info.balances_hold.get(currency);
	if (val > 0)
		System.out.println("    Hold " + currency + "=" + val);
}
```

### Get account transactions
Get the account transactions.

```java
Transaction[] transactions = cryptsy.getMyTransactions() ;
for(Transaction t:transactions) {
	System.out.println(t) ;
}
```

### Get market orders for a single market
Returns all the orders (order book) for a single currency market.

```java
MarketOrderReturn mo = cryptsy.getMarketOrders(Markets.WDC_BTC) ;
System.out.println("Sell Orders") ;
for(MarketSellOrder so:mo.sellorders) {
	System.out.println(so) ; 
}

System.out.println("Buy Orders") ;
for(MarketBuyOrder bo:mo.buyorders) {
	System.out.println(bo) ; 
}
```

## Donations

If you use this library please donate to any of the following addresses:

Cryptsy Trade Key: 77c1602534b3d7642bcc24891a9dab6198d2f526  
AlphaCoin (ALF): aEPKscFNtCct8qvp4o8PE6mqheHJRqFf6U  
AmericanCoin (AMC): B26Bc2mAMEPA3BCpQTsoCUEudk2TTnx1UT  
AndroidsTokens (ADT): 27z6AR3poRk3CVqGLXFw6RU3zKBHiDXENC  
AnonCoin (ANC): Af2aFxCKhSraHnzfnxfBJDFJhw1PFo8g9i  
Argentum (ARG): AaAXRnok1nRZX7ehAePLnfGkD2Xh44us2K  
AsicCoin (ASC): 9uc5oeFTu3ueVtxfrFq2q2tTCEvR8P31zA  
BBQCoin (BQC): bZLDp9yZoRaQAZXihqEeL67MuBXxEna92v  
Betacoin (BET): BMUfvoWiZkwkbyFLpsiK6ZFYVUPhGXNVzp  
BitBar (BTB): B9TS2MEXgfv6yZEFZXqHjioq6z6YP4bUH8  
BitCoin (BTC): 15VgKx3fzYVnv4zEiGci7EfRgBRfRRgwzx  
BitGem (BTG): gWiPbYJaWoTWMRyNRoaoGpyCZ1LTJQD6nz  
BottleCaps (CAP): ExiLdNvPhzfMhfGTruB9Lam55aEL3Lrjxq  
ByteCoin (BTE): 8JaAiahWdP6RrxHs2mfQEAkZivbQTe5xos  
CasinoCoin (CSC): CUmT6bJo7ZU48vyvySHMXfDibgLSDp4D58  
CHNCoin (CNC): CZeAVYhojEEoMHb6keHTUFtp3VXRxuLPgh  
CopperBars (CPR): CU9uW7Dmsmeeuzyub8yR7qwtDwqGwnRgEP  
CopperLark (CLR): CVssD5iit7Hh2HPDdseZX1eAgqHGCX56uL  
Cosmoscoin (CMC): C5VLQuUnCpy8ysETRMA81ddgDUuVzDsgsn  
CraftCoin (CRC): QD7Kqz64JeuYxo12qnjKUm4EBgswNqnEKP  
CryptoBuck (BUK): 32GU65DUVjRRgzCgSoMWLCHMW9wSvxZzhS  
CryptogenicBullion (CGB): 5VqPys6hVcPv7oh3DiFNnhjQhW5yGmir3m  
DevCoin (DVC): 19f6Ba23VSNcGu5Kt3CEmPvhEGaKUeW9Bz  
Diamond (DMD): dJUYmT1bak1UtmAqBT8JTxPugpENVi6JbZ  
DigitalCoin (DGC): DLcNBqvTdhLQryQ1RhZc4sdBZkQvAJw4fU  
Dogecoin (DOGE): DDEkLaveBR35Jz8oxcajGdeg1marYfaD22  
Doubloons (DBL): Ay8bfDD7Fa74efy3xEdhZic3ku3sZ5nLsc  
ElaCoin (ELC): Ee8WZyWX5T8P59PaxY747znTe42jhzoeHX  
ElephantCoin (ELP): eHryeFd2wUYqypkuWeCmSSgJZz9KD8i1p8  
eMark (DEM): NPTSf9AXm7v2qQUAsnSc8mrj7ruHSGGEyT  
Emerald (EMD): F4p4RoBGszknWcpR9kNnjvQmwie9uVjMgs  
EZCoin (EZC): EQWSXCJxrfMLbqd2fqAsqaehJZviowUEAY  
FastCoin (FST): fnFwUnLKxTm8xApQyzUbGoSCp3FLfJ3NAM  
FlorinCoin (FLO): FA9DVTKTJEMbc6C7aD2cmnR8qrGrYH9rgt  
Franko (FRK): FBm4R5PJd6MLgoxSbWhCMB4x6zoynyiy2d  
FreiCoin (FRC): 17PiitiXGNbz3eVPouLwZBtqPPovbR2ixZ  
Galaxycoin (GLX): gkfa9FMD7CCqDLF2mNrgS9tZn2tWn6ghW4  
GameCoin (GME): GPqetspVFr1aBdpjdQ4KDw6sYiTvQuXxu9  
Globalcoin (GLC): 7JAFhPUd5rGBCSnTanEdJLykh6QnkxCDvV  
GoldCoin (GLD): DtMAdVHFWzMNAwb2NWwuknwL86rsdn4uuV  
GrandCoin (GDC): gQFwYoG2MmuBtyr451zdD6PaUhcDPE1D2m  
HoboNickels (HBN): EziUqcTd7dYwmid7XvgYTbo9S1GqGhZNp4  
InfiniteCoin (IFC): iQg1Ki1uCpEkkQ5pKqjhzcZegotMxPmBV7  
IXCoin (IXC): xcVP634FHjQUZLGh3tm8Ust5zjscKgdo2q  
JouleCoin (XJO): JbWHvQCgN3wkMsXyhYSD7Do7bMepNqe9GG  
JunkCoin (JKC): 7jHV9wAf9RHQXKopv1rSL6TQmWAdtMXiws  
KrugerCoin (KGC): YrdvZTWYbeSbQLb7fvyatNojmK1d9wMZDZ  
LiteCoin (LTC): LSjiTrRZRse6ZhPCwzU5YVr9RETVJsnRQU  
LuckyCoin (LKY): LHjrAc1hW6M9e88KopCG3AdpUDA2v5qFkc  
MasterCoin (MST): K75zTNe4kZZAQge51irPRzR1rLZU3VgL59  
MegaCoin (MEC): MCYNJjSLgkWCw45KJUDWinrqeSTjxmkoW9  
MemeCoin (MEM): JBHatqJG5EsvbwkDHToiScf3Q24tgMn8ZU  
MinCoin (MNC): MCAqVk6iLCZusrT9rfvwHNofDNFocMHBTh  
NameCoin (NMC): NA1LEncYN4JeUixJDyeXjTyw78U5yJisig  
NeoCoin (NEC): NXSp3djSZDBZPP1k9uu3FV2kGcXFfHouNh  
Netcoin (NET): nGBNWojQk4pCCouiezUDiTAtPQRxGSLXnC  
Nibble (NBL): NUz4j4Rd8rVULZus3WBVt9haCxoq63xqog  
NoirBits (NRB): DwGygLUsxCiFbtMDszJeqSJWik5wkSLqMz  
NovaCoin (NVC): 4YuLLDPHvbHpktrPkSyTREY3uWM6BNLuS8  
Orbitcoin (ORB): oYYsesw9NcioGjtdTZt2J2h2F8mctRUK1k  
PayCoin (PYC): PJmATsrVJPwhKU41meC97JEft3WbsCJgb1  
Peercoin (PPC): PPzADhNgJnhfKYynWNpFgh4DfCoWUEZSXR  
Pennies (CENT): P9tKPgJXYVPCcFW3ZxBJAVongdpgwV7Tab  
PhilosopherStone (PHS): 9gpuWHopGwyKj8nSuDdoJZUvL7h6cZmsHi  
PhoenixCoin (PXC): PfMMhCykPffk6beCNqu55QZKhvYjL6B7Lg  
PrimeCoin (XPM): AUGUWwcqA3sA44BPQz6WXsiyRdGi127Tiw  
ProtoShares (PTS): Ptmdtb8RWimiSzEH5sVny7u245MSzteT1g  
Quark (QRK): QS9PCVMSL8GcgjnoGQ4zw7MVVGD5dDj4e4  
RedCoin (RED): RiPrBHE8ESzV818rV7G7dwE6tREx7jTUDx  
RoyalCoin (RYC): RRLoLtJ8BudTaLf3yV1suXCgWTgK5nCb4L  
SecureCoin (SRC): sNyPMwgZanMqbVxZRSCeb6rX18wukq9EHq  
SexCoin (SXC): SF5PDgLDLcuxJa8RrmTfAo5faFTpAmHAn4  
Spots (SPT): MBgwWwB76FVA5wgGXNoRo2ExCyEHQ63FVj  
TagCoin (TAG): TH7rvti3EwfFvxkCUGC4osNcLi57tMZGvN  
TekCoin (TEK): Bn4K4rzHUgbJvbSBUEKsLdD1AEJ2m8PEp3  
TerraCoin (TRC): 1D3TNLzM6f9F31yNw9gS4xnYtzyCdHc6Wm  
Tickets (TIX): 8nNAu1VHpW6omAwgEtbW9eq5NFCjg1GQfF  
TigerCoin (TGC): tRJ8pWhHvyqArwUJrQgsA9aPxL4Mot7Z44  
Unobtanium (UNO): uM63uT2RWcbrvTDHHnmtDEmqzL1AYuuvWn  
WorldCoin (WDC): WYsjF3XvmXYtn85aKPzwH3F1gRoVfDJ2AZ  
XenCoin (XNC): Xw2sWPyS9fxFqZ6GVNxGSmR1GpYLjrx3Ez  
YaCoin (YAC): Y8N3Sq4icsarBYwQatJRTMVWiTYhBVxAJK  
ZetaCoin (ZET): ZKmFiwsfiQTyzjatQDX1KuGdP8xfeUGrG3  