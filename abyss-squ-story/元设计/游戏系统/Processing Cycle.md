
Pre（前置处理）：指获取涉及的主数据的value属性的对应值与预期值比较（较值处理）。
Post（后置处理）：指更新对应的主数据的value属性为对应值（赋值处理）。


- Step-1 玩家完成一次交互行为（[[Interaction]]）
- Step-2 遍历Condition条件表（[[Trigger-Condition]]）
	- Step-2.1 对满足条件的数据条目执行Post（后置处理），Post的对象是叙事大纲（[[Narration]]）和剧情分支（[[Plot]]）
- Step-3 遍历叙事大纲（[[Narration]]）和剧情分支（[[Plot]]）
	- Step-3.1 抽取其中 value == 99 的故事线[[Settlement-Storyline]]或剧情[[Plot]]，验证每个数据条目的Pre（前置处理）是否完全满足，将完全满足的数据条目抽出至【待处理表-故事线】
- Step-4 遍历【待处理表-故事线】的数据条目
	- Step-4.1 对单位条目据优先级执行Post（后置处理），Post的对象可以是分支（[[Settlement-Branch]]）、线索（[[Settlement-Clue]]）、描绘（[[Settlement-Depiction]]）、时点（[[Settlement-Quest]]）、物品（[[Settlement-Property]]）、任务（[[Settlement-Quest]]）、倾向（[[Trending]]）

- Step-5 遍历各结算（[[Settlement]]）表
	- Step-5.1 抽取其中 value == 299 的结算（[[Settlement]]），验证每个数据条目的Pre（前置处理）是否完全满足，将完全满足的数据条目抽出至【待处理表-连锁展示】
	- Step-5.2 遍历【待处理表-连锁展示】，据优先级推送向呈现层（[[Presentation]]），并触发独立的特殊交互处理流程

- Step-6 遍历各结算（[[Settlement]]）表
	- Step-6.1 抽取其中 value == 199 的结算（[[Settlement]]），验证每个数据条目的Pre（前置处理）是否完全满足，将完全满足的数据条目抽出至【待处理表-单条展示】
	- Step-6.2 遍历【待处理表-单条展示】，据优先级推送向呈现层（[[Presentation]]）和执行Post（后置处理），Post的对象可以是自己、结算（[[Settlement]]）、倾向（[[Trending]]）

