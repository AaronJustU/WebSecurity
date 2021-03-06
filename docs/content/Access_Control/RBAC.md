#RBAC

Role-based access control

---

###基于角色的访问控制

MAC和DAC两种访问控制模型都存在的不足是将主体和客体直接绑定在一起，授权时需要对每对（主体、客体）指定访问许可，这样存在的问题是当主体和客体达到较高的数量级之后，授权工作将非常困难。20世纪90年代以来，随着对在线的多用户、多系统研究的不断深入，角色的概念逐渐形成，并产生了以角色为中心的访问控制模型，并被广泛应用到各种计算机系统中。
####RBAC定义

RBAC就是Role-Based Access Control，基于角色的访问控制。角色访问控制（RBAC）引入了Role的概念,目的是为了隔离User(即动作主体，Subject)与Privilege(权限，表示对Resource的一个操作，即Operation+Resource) ，更符合企业的用户、组织、数据和应用特征。 

RBAC的关注点在于Role与user，Role与privilege的关系，也就是User Assignment与Permission Assignment的关系。

####RBAC中的几个重要概念：

    Who：权限的拥有者或主体。典型的有Principal、User、Group、Role、Actor等等。跟授权有关系的实体就只有角色（Role）和用户（User）。譬如：业务经理（Role），张三（User）
	
	Role：作为一个用户(User)与权限(Privilege)的代理层，解耦了权限和用户的关系，所有的授权应该给予Role而不是直接给User或Group。基于角色的访问控制方法的思想就是把对用户的授权分成两部份，用角色来充当用户行驶权限的中介。角色是一组访问权限的集合，一个用户可以是很多角色的成员，一个角色也可以有很多个权限，而一个权限也可以重复配置于多个角色。
	
	User：用户就是一个可以独立访问计算机系统中的数据或者用数据表示的其它资源的主体，我们用USERS表示一个用户集合。用户在一般情况下是指人。
	
	Group:是一组相关user的集合。User从group继承出来，也就具有了该group的角色权限。
	
####RABC中的几种重要关系

#####用户（User）和角色（Role）

用户指访问系统中的资源的主体，一般为人，也可为 Agent 等智能程序。角色指应用领域内一种权力和责任的语义综合体，可以是一个抽象概念，也可以是对应于实际系统中的特定语义体，比如组织内部的职务等。针对角色 属性的不同，某些模型中将角色进一步细分为普通角色和管理员角色（可理解为全局角色）。

#####许可（Permissions）和权限（Permission）

许可描述了角色对计算机资源的访问和操作所具有的权限，其反映的是授权的结果。比如授予某个角色对计算机资源有读的权限，则代表了一个许可的存在，这个许 可表示：角色获取了对计算机资源的读许可。针对操作来说，其描述的是许可和操作之间的一种关联关系，而这层关系则表示了某一角色对某一操作所具有的权限及 权限状态。

#####角色（Role）和指派（Assignment）	

指派包含两个方面，用户指派和许可指派。用户指派表示的是，将用户指派给特定的角色。许可指派表示的是为角色指派计算机资源的访问和操作许可。

#####角色（Role）和角色等级（Role Hierarchies） 

角色本身仅仅只是一个名词，其本身并不能代表权限的大小。比如，我们可以定一个“Director”的角色，也可以定一个“Project Leader”的角色。对于现实中我们来说，看到这样两个角色，就清楚 DIR 的权限要比一个 PL 的权限级别高。但是对计算机来说，这两个角色仅仅是两个“词语”，是等同的。可以采用分等级角色，在角色上实现层次化来解决这些问题。也可以采用复合角色 （其表示的就是一个角色组的概念），对角色实现一定的分组和复合，以便于权限指派。在一些 OA 产品中经常出现分等级角色。
