目前 BGP 高防包支持购买的区域：
- 中国内地（大陆）区域：华北地区（北京）、华东地区（上海）和华南地区（广州）。

## 计费方式
BGP 高防包服务使用组合计费方式，包括包年包月和按量计费两种方式。其中，保底防护峰值为按月付费，弹性防护峰值为按实际用量后付费，按天结算。

| 计费项       | 计费模式     | 付费方式 | 付费说明                                                     |
| ------------ | ------------ | -------- | ------------------------------------------------------------ |
| 保底防护峰值 | 包年包月     | 冻结付费   | 提供基础防护带宽，预付费价格由保底防护峰值和购买时长确定。</br>购买成功后先冻结费用，次月1号再结算上月费用，以此类推。 |
| 弹性防护峰值 | 按天按量计费 | 后付费   | 触发弹性防护后，按当天最高攻击峰值所对应的弹性防护峰值区间计费，账单次日生成。</br>若未触发弹性防护，则不收取任何费用。支持升级、降级配置。 |


## 产品价格
- **保底防护**
保底防护具体价格请参考如下表格：
<table>
     <tr>
         <th>类型</th>  
         <th>保底防护峰值</th>  
         <th>防护 IP 个数</th>  
         <th>CC 防护峰值</th> 
		 <th>单价（美元/月）</th> 
     </tr>
	 <tr>
         <td   rowspan="5">独享包</td>  
         <td>5Gbps</td>  
         <td   rowspan="5">1</td>  
         <td>10,000QPS</td>
		 <td>77</td>
     </tr> 
	 <tr>
         <td>20Gbps</td>  
         <td>40,000QPS</td>  
		 <td>2,558</td>
     </tr>
	 <tr>
         <td>30Gbps</td>  
         <td>70,000QPS</td>  
         <td>3,946</td>
     </tr>
	 <tr>
         <td>50Gbps</td>  
         <td>150,000QPS</td>  
         <td>8,723</td>
     </tr>
	 <tr>
         <td>100Gbps</td>  
         <td>300,000QPS</td>  
         <td>28,790</td>
     </tr>
	 <tr>
         <td   rowspan="15">共享包</td>  
         <td   rowspan="5">20Gbps</td>  
         <td>5</td>  
         <td   rowspan="5">40,000QPS</td>
		 <td>3,583</td>
     </tr> 
	 <tr>
         <td>10</td>  
		 <td>6,808</td>
     </tr>
	 <tr>
         <td>20</td>  
		 <td>12,900</td>
     </tr>
	 <tr>
         <td>50</td>  
		 <td>25,084</td>
     </tr>
	 <tr>
         <td>100</td>  
		 <td>43,000</td>
     </tr>
		  <tr>
         <td   rowspan="5">50Gbps</td>  
         <td>5</td>  
         <td   rowspan="5">150,000QPS</td>
		 <td>12,213</td>
     </tr> 
	 <tr>
         <td>10</td>  
		 <td>23,204</td>
     </tr>
	 <tr>
         <td>20</td>  
		 <td>43,966</td>
     </tr>
	 <tr>
         <td>50</td>  
		 <td>85,489</td>
     </tr>
	 <tr>
         <td>100</td>  
		 <td>146,553</td>
     </tr>
	 <tr>
         <td   rowspan="5">100Gbps</td>  
         <td>5</td>  
         <td   rowspan="5">300,000QPS</td>
		 <td>34,548</td>
     </tr> 
	 <tr>
         <td>10</td>  
		 <td>65,642</td>
     </tr>
	 <tr>
         <td>20</td>  
		 <td>124,374</td>
     </tr>
	 <tr>
         <td>50</td>  
		 <td>241,838</td>
     </tr>
	 <tr>
         <td>100</td>  
		 <td>414,580</td>
     </tr>
</table>


>- Query Per Second（QPS），此处用于衡量 BGP 高防包实例每秒可防护的 CC 攻击请求数。
>- 购买并绑定高防包后，被绑定 IP 仅具有购买的高防包的防护能力，不叠加基础防护。

- **弹性防护**
用户可根据实际业务防护需求自助开启弹性防护。
	- 未开启弹性防护时，最高防护峰值为保底防护峰值且不会产生后付费。
	- 开启弹性防护时，弹性防护峰值为实例的最高防护峰值。
		- 未触发弹性防护时，不产生费用。
		- 当触发弹性防护（攻击峰值超过保底防护峰值且在弹性防护范围内）时，取当天实际发生的最高攻击峰值所对应计费区间进行计费，账单次日生成。
	
	

弹性防护具体价格请参考如下表格：

| DDoS 防护峰值                | 单价（美元/天） |
| ---------------------------- | ----------------- |
| 20Gbps ≤ 攻击峰值 < 30Gbps   | 260             |
| 30Gbps ≤ 攻击峰值 < 40Gbps   | 450             |
| 40Gbps ≤ 攻击峰值 < 50Gbps   | 600             |
| 50Gbps ≤ 攻击峰值 < 60Gbps   | 800             |
| 60Gbps ≤ 攻击峰值 < 70Gbps   | 1,200             |
| 70Gbps ≤ 攻击峰值 < 80Gbps   | 1,500             |
| 80Gbps ≤ 攻击峰值 < 90Gbps   | 1,700             |
| 90Gbps ≤ 攻击峰值 < 100Gbps  | 1,900            |
| 100Gbps ≤ 攻击峰值 < 120Gbps | 2,100            |
| 120Gbps ≤ 攻击峰值 < 150Gbps | 2,300            |
| 150Gbps ≤ 攻击峰值 < 200Gbps | 2,700            |
| 200Gbps ≤ 攻击峰值 < 250Gbps | 4,800            |
| 250Gbps ≤ 攻击峰值 < 300Gbps | 5,600            |


## 计费示例
BGP 高防包使用组合计费方式，计费示例说明如下：
- **单 IP 类型费用计算示例**
例：用户在上海区域购买了一个独享型单 IP 的 BGP 高防包，规格是“20Gbps保底防护峰值 + 50Gbps弹性防护峰值”。
若当天发生 DDoS 攻击事件且最高攻击流量峰值为45Gbps，超过保底防护峰值范围且使用了弹性防护峰值，落入40Gbps ＜ 弹性峰值 ≤ 50Gbps 计费区间，当天产生弹性费用600美元。
则用户需支付费用合计为3158美元，其中包含当月的保底防护费用2558美元，当天产生的弹性费用600美元。
- **多 IP 类型费用计算示例**
例：用户在上海区域购买了一个共享型多 IP 的 BGP 高防包，规格是“20Gbps保底防护峰值 + 80Gbps弹性防护峰值，IP 数量5个”。
若当天发生多个 IP 同时被攻击的事件，有3个 IP 同时受到攻击攻击流量分别为10Gbps、15Gbps和30Gbps。则同时遭受攻击的叠加峰值为10 + 15 + 30 = 55Gbps，超过了20Gbps的保底防护峰值且使用了弹性防护峰值，落到了50Gbps ＜ 弹性峰值 ≤ 60Gbps计费区间，当天产生弹性费用800美元。
则用户需支付费用合计为4383美元，其中包含当月的保底防护费用3583美元，当天产生的弹性费用800美元。
