---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: 子网
---

# Subnetworks

<GameScene zoom="4" interactive={true}>
<ImportStructure src="../assets/assemblies/subnet_demonstration.snbt" />

<DiamondAnnotation pos="6.5 2.5 0.5" color="#00ff00">
        物品管道子网
    </DiamondAnnotation>

<DiamondAnnotation pos="5.5 2.5 0.5" color="#00ff00">
        流体管道子网
    </DiamondAnnotation>

<DiamondAnnotation pos="4.5 2.5 0.5" color="#00ff00">
        已过滤的破坏面板
    </DiamondAnnotation>

<DiamondAnnotation pos="3.5 2.5 0.5" color="#00ff00">
        成型面板子网
    </DiamondAnnotation>

<DiamondAnnotation pos="2.5 2.5 0.5" color="#00ff00">
        使用接口-存储总线交互的子网，主网络会将其视为普通的容器来访问
    </DiamondAnnotation>

<DiamondAnnotation pos="1.5 1.5 0.5" color="#00ff00">
        另一个物品管道子网，用于把充能完成的物品送回样板供应器
    </DiamondAnnotation>

<IsometricCamera yaw="195" pitch="30" />
</GameScene>

"子网"并没有严格的定义，但有人认为子网是任意的辅助主网络或完成某些简单任务的网络。一般情况下，子网规模都较小而不需要使用控制器。
子网主要有两个用途：

*   限制[设备](../ae2-mechanics/devices.md)的存储访问范围(你肯定不希望"管道"子网中的输入总线能访问你的网络主存储，不然它会把物品放进存储元件而非目标容器中)；
*   减少主网中的频道使用，例如让样板供应器把物品输出到连接了若干机器上的若干总线的面板上而仅需消耗1个频道，而不需要在每台机器上都放置一个样板控制器，消耗更多频道。

线缆的不同颜色除了防止它们互相连接外与子网的构成无关。

They can be

*   an import bus and storage bus set up to transfer items or fluids from one container to another like an item or fluid pipe
*   an annihilation plane and storage bus, so that the only place the annihilation plane can put what it breaks is the storage bus, allowing you to filter the plane
*   an interface and formation plane, so that whatever is inserted into the interface gets pushed to the formation plane and placed/dropped in the world
*   a setup to automatically make certus quartz, regulated and controlled by a <ItemLink id="level_emitter" /> on the main network
*   a specialized storage system accessible from the main network via the special storage-bus-on-interface interaction, in order to store the output of a farm without endlessly overflowing your main storage
*   and so on

Very useful for making subnetworks is the <ItemLink id="quartz_fiber" />. It transfers power between networks without
connecting them, allowing you to power subnets without needing to put energy acceptors and power cables everywhere.
