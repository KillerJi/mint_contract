# mint_contract

## contract

dev endpoint: `http://18.180.227.173:8545/`

### mint `0x21CBB347829aE16aa1aE67fcf3811E2806f25069`

**Function**

- nonceOf() return(uint256)
    * return uint256: 返回合约nonce值

- lock(uint256[])：锁定用户NFT
    * uint256[]:tokenid数组

- unlock(uint256[]):解锁用户NFT
    * uint256[]:tokenid数组

- buyCommercialCity(uint256, uint8, uint8, uint256, uint256, address, 
    uint256, uin256, uint8, bytes32, bytes32):购买中心城坐标
    * uint256: 购买方式
    > 0 800商业城 1 1000商业城 2 1300商业城 3 1500商业城 
    * uint8: 横坐标正负
    > 0 正 1 负 （如：横坐标为-1，该值传1）
    * uint8: 纵坐标正负
    > 0 正 1 负 （如：纵坐标为1，该值传0）
    * uint256: 横坐标（输入不用带正负，如-2则传2）
    * uint256: 纵坐标（输入不用带正负，如-2则传2）
    * address: 用户地址
    * uint256: 合约维护的nonce值
    * uint8: v
    * bytes32: r
    * bytes32: s

- buyWorldMap(uint256, uint8, uint8, uint256, uint256, address, 
    uint256, uin256, uint8, bytes32, bytes32):购买中心城坐标
    * uint256: 购买方式
    > 4 200世界地图 5 400世界地图 6 700世界地图 7 900世界地图
    * uint8: 横坐标正负
    > 0 正 1 负 （如：横坐标为-2，该值传1）
    * uint8: 纵坐标正负
    > 0 正 1 负 （如：纵坐标为2，该值传0）
    * uint256: 横坐标（输入不用带正负，如-2则传2）
    * uint256: 纵坐标（输入不用带正负，如-2则传2）
    * address: 用户地址
    * uint256: 合约维护的nonce值
    * uint8: v
    * bytes32: r
    * bytes32: s

- buyOpenSea(uint256, uint256, address, 
    uint256, uint8, bytes32, bytes32):购买opensea上已有的坐标
    （ msg.value:至少发送0.03 * 10 ** 18)
    * uint256: 购买方式
    > 0 800商业城 1 1000商业城 2 1300商业城 3 1500商业城 
    > 4 200世界地图 5 400世界地图 6 700世界地图 7 900世界地图
    * uint256: tokenid
    * address: 用户地址
    * uint256: 合约维护的nonce值
    * uint8: v
    * bytes32: r
    * bytes32: s
  
- claim_eth(address, uint256):提取eth（只有owner能调用该函数）
    * address: claim用户地址
    * uint256: 提取eht数量
    
- claim_pot(address, uint256):提取pot（只有owner能调用该函数）
    * uint256: 提取pot数量

**Event**

```solidity
    event BuyCommercialCity(
        address account,
        uint256 buyway,（购买种类 0为商业城，1为世界地图）
        uint8 hpn,（横坐标正负）
        uint8 vpn,（纵坐标正负）
        uint256 horizontal,（横坐标）
        uint256 vertical,（纵坐标）
        uint256 tokenid
    ); 
    event BuyWorldMap(
        address account,
        uint256 buyway,
        uint8 hpn,
        uint8 vpn,
        uint256 horizontal,
        uint256 vertical,
        uint256 tokenid
    );
    event BuyOpenSea(address account,
        uint256 way, (0-7 购买方式)
        uint256 tokenid);
    event ClaimPot(address account,uint256 number);
    event ClaimEth(address account,uint256 number);
    event LockToken(address indexed account, uint256[] tokenId);
    event UnLockToken(address indexed account, uint256[] tokenId);
```

