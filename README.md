# BSC链持币分红代币合约开发教程
- 支持持币分红wETH/BTCB/USDT/DOGE等代币
- 该合约仅支持BNB池子，不支持USDT或其他池子，不支持分红 BNB、WBNB
- 仅支持PancakeSwap V2版本，不支持V3版本
- 合约有黑名单、白名单功能，丢弃权限后找ave申诉，可以实现全绿
- 不丢权限的情况下，合约权限拥有者可以修改税率
- 不支持分红本币、不支持LP分红、不支持杀机器人

Telegram交流群
- https://t.me/pandatool

# 视频教学
- https://youtu.be/kjzNQWnr72E

# 合约代码
- https://github.com/pandatoolcode/Dividends/blob/main/DividendsCode.sol

# 合约功能
- 分红：持有一定数额的本币，可以分其他代币（如USDT/BUSDT等）
- 营销：营销钱包可以从交易中获得一定比例的分红币（如USDT/BUSDT等）
- 销毁：每笔交易中一定比例的代币转入黑洞销毁
- 回流：每笔交易者一定比例的代币与BNB组成交易对回流到资金池
- 黑名单：地址被加入黑名单将不能进行交易和转账
- 白名单：白名单交易没有手续费
- 税率：最高不超过25，可以在发币之后手动修改

# 合约代码参数修改
- name_ = "Jack Token";//名称
- symbol_ = "Jack";//简称
- totalSupply_ = 300000;//供应量 不用后面 18 位
- rewardAddr_ = XXXXXXXX;//分红币合约地址
- marketingWalletAddr_ = XXXXXX;//营销钱包地址
- buyFeeSetting_ = [1,1,1,1];//买入税：持币分红、回流、营销钱包、销毁
- sellFeeSetting_ = [1,1,1,1];//卖出税：持币分红、回流、营销钱包、销毁
- tokenBalanceForReward_ = XXXX;//持币门槛，后面+18 个 0

# 合约编译/开源
- 版本号 COMPILER： v0.8.17+commit.e28d00a7.js
- Enable optimization: 开启并使用默认值 200
- 开源许可证类型：No licernes
- Optimization优化：yes

# 合约部署
- Environment：选择第三个 Injected Provider Metamask
- GAS LIMIT：300000（默认）
- Value：50000000000000000（5 后面 16 个 0）
- CONTRACT：选择Mytoken（主合约）

# 合约函数调用
- EnemyAddress 设置黑名单
  - account（address）：输入要拉黑的地址
  - value（bool）：填true，就是拉黑；填false，就是解除
- RenounceOwnership 放弃权限
- transferOwnership 转让权限
- 修改买入税率
  - setBuyDeadFee 销毁税率
  - setBuyLiquidityFee 回流税率
  - setBuyMarketingFee 营销税率
  - setBuyRewardsFee 分红税率
- 修改卖出税率
  - setSellDeadFee 销毁税率
  - setSellLiquidityFee 回流税率
  - setSellMarketingFee 营销税率
  - setSellRewardsFee 分红税率
