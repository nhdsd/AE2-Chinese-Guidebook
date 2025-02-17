---
navigation:
  parent: ae2-mechanics/ae2-mechanics-index.md
  title: 自动合成
  icon: pattern_provider
---

# 自动合成

### 大家伙

<GameScene zoom="4" interactive={true}>
  <ImportStructure src="../assets/assemblies/autocraft_setup_greebles.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>

自动合成是AE2的基础功能之一。你可以利用你的ME系统完成合成，或是自动合成并运输到某处，
抑或是通过<u>智能涌现</u><sup>\[注\]</sup>存储一定数量的物品，而不是自己先合成正确数量的各种原料，像个*底层劳动人民*一样辛勤劳作。
该系统也可处理流体及来自增加了新的材料类型的模组的附加项（如通用机械的气体）。这可谓是很棒了。

这是个复杂的话题。所以，系好安全带，我们要出发了！

自动合成系统由以下三部分组成：
- 合成请求来源；
- 合成CPU；
- <ItemLink id="pattern_provider" />。

合成过程如下：

1.  某个来源发送了合成请求。这种请求的来源包括你在终端中点击可自动合成的物品以及带有合成卡的输出总线或接口请求它们需要输出/存储的物品之一。

*   (**重要事项：** 使用“选取方块”键(默认为鼠标中键)来发起对网络中已存储的物品的请求。这可能与物品栏整理模组有键位冲突。)

2.  ME系统计算完成合成所需的原料以及预处理步骤，并把物品储存在所选CPU中。

3.  带有有关[样板](../items-blocks-machines/patterns.md)的<ItemLink id="pattern_provider" />将物品送入相邻的容器。
    如果是合成类配方(合成样板)，该容器将会是<ItemLink id="molecular_assembler" />；
    如果是非合成类配方(处理样板)，该容器可能是一些其他的方块或者机器，抑或是精心设计的红石控制的处理装置。

4.  合成产物通过某种方式返回系统，这可以是通过输入总线或接口，也可以是把产物送入样板供应器。
    **产物必须要进入系统内，例如通过<ItemLink id="import_bus" />、<ItemLink id="interface" />或者<ItemLink id="pattern_provider" />的产物返回栏。你无法直接把产物导入接有<ItemLink id="storage_bus" />的箱子。**

5.  若此次合成是某次合成的预处理，则产物会被缓存在CPU内用于下次合成。

**\[注\]** 原文是"clever emergent behavior"。译者无法确认此处该词语的实际意义，采取了直译。

# 样板

<ItemImage id="crafting_pattern" scale="4" />

空白样板在<ItemLink id="pattern_encoding_terminal" />内被制作成样板。

为应对不同需求，样板有以下不同类型：

*   <ItemLink id="crafting_pattern" />编码合成台配方。它们可以被放在<ItemLink id="molecular_assembler" />里，让它只要有原料就合成相应产物，
但是它们主要用于与分子装配室相邻的<ItemLink id="pattern_provider" />里。此时样板供应器会有特殊的行为，会把样板和原料一同送进相邻的分子装配室。
鉴于分子装配室会把产物自动弹出至相邻容器中，装配室与样板供应器的组合足以自动化工作台合成。

***

*   <ItemLink id="smithing_table_pattern" />和合成样板很相似，但是它们编码锻造台配方。它们也可以用装配室和样板提供器自动化，且工作方式完全相同。
实际上合成、锻造和切石配方可以用同样的机器处理。

***

*   <ItemLink id="stonecutting_pattern" />和合成样板很相似，但是它们编码切石配方。它们也可以用装配室和样板提供器自动化，且工作方式完全相同。
实际上合成、锻造和切石配方可以用同样的机器处理。

***

*   <ItemLink id="processing_pattern" />为自动合成带来了极大的灵活性。它们是最具有普适性的一种，
只表明“如果样板供应器将原料送进相邻容器，那么ME系统就会在将来某时刻收到产物”。
这是你使用模组机器、熔炉以及类似物来合成时使用的样板。鉴于它们使用得很频繁并且不关注合成过程，你可以用它们做一些真正不同寻常的事，
例如，把原料放进复杂的物品整理产线，或是从不断产出的可再生农场中取出其他原料，抑或是把整个《蜜蜂总动员》的剧本打印出来。
ME系统不关心这些，它只关心它收没收到样板所指明的产物。实际上，它甚至不关心原料和产物是否有任何关系。
你可以给它一个“1樱花木板 = 1下界之星”的样板，并让你的凋灵农场在接收到1个樱花木板时杀死1只凋灵，这样也能正常工作。

多个具有完全相同的样板的<ItemLink id="pattern_provider" />可同时使用并且可以并行处理。此外，你可以编码一个8圆石 = 8石头的样板而不是1圆石 = 1石头的。
这时，样板供应器会每次把8个圆石放入你的烧炼机器，而非1个。

## "样板"的最一般形式

实际上有比处理样板更“一般”的“样板”形式。带有合成卡的<ItemLink id="level_emitter" />可被设置为为了合成某物而发出红石信号。该“样板”不指明，也不关心原料。
它只表明“如果该标准发信器发出红石信号，那么ME系统就会在将来某时刻收到产物”。这一般用于激活或停止无需输入的可再生农场，
或是激活递归合成系统（标准的自动合成无法解析），一个例子是“1圆石=2圆石”，如果你有一台圆石复制机。

# 合成CPU

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/assemblies/crafting_cpus.snbt" />
  <IsometricCamera yaw="195" pitch="30" />
</GameScene>
合成CPU处理合成请求。它们在执行多步合成时储存中间产物，还会影响请求的最大大小并在一定程度上影响执行速度。它必须是有至少1个合成储存器的实心长方体多方块结构。 

合成CPU由如下部分组成：

*   (必选)[合成存储器](../items-blocks-machines/crafting_cpu_multiblock.md)，各种标准元件大小均有(1k、4k、16k、64k、256k)。它们存储合成过程中的中间产物
因此，为使CPU可以处理有更多的原料的合成请求，必须要有更大的存储空间。
*   (可选)<ItemLink id="crafting_accelerator" />，它们让系统能够一次性通过样板提供器送出更多批原料。这使得六面均被分子装配室包围的样板提供器可一次性把原料送进（进而能够使用）全部六个装配室，而不是一个。
*   (可选)<ItemLink id="crafting_monitor" />，它们显示CPU当前正在处理的请求。可用<ItemLink id="color_applicator" />上色。
*   (可选)<ItemLink id="crafting_unit" />，它们仅仅用于占位，以使得CPU呈长方体。

每个合成CPU只能同时处理1个请求。因此如果你想请求同时合成运算处理器以及256个平滑石头，你需要建造2个CPU多方块结构。

它们可以被设置为只接受玩家请求、只接受自动化系统（输出总线或者接口）请求或是均接受。

# 样板供应器

<Row>
<BlockImage id="pattern_provider" scale="4" />

<BlockImage id="pattern_provider" p:push_direction="up" scale="4" />

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/blocks/cable_pattern_provider.snbt" />
</GameScene>
</Row>

<ItemLink id="pattern_provider" />是自动合成系统与世界进行交互的基础。它们把内含的[样板](../items-blocks-machines/patterns.md)中的原料送入相邻的容器中，
此外，物品可被放入其中，以将这些物品送入网络。大多数情况下把机器的产物通过旁边的样板供应器(一般是送入原料的那一个)送回网络，而非使用<ItemLink id="import_bus" />拉取产物可以节省1个频道。

值得注意的是，鉴于它们直接从合成CPU中的[合成存储器](../items-blocks-machines/crafting_cpu_multiblock.md#crafting-storage)中获取并送出原料，
它们本身并不会存储这些原料，你也无法把原料从中泵出。你需要让供应器把原料送进其他的容器(如木桶)并从该容器中泵出原料。
此外，样板供应器必须一次性送出所有原料，无法送出不完整的一批原料。这是个值得利用的特性。

样板供应器与[子网](../ae2-mechanics/subnetworks.md)上的接口有特殊的交互行为：若该接口未被更改(请求栏中无物品/流体)，供应器会直接跳过接口并直接将原料送入子网的[存储](../ae2-mechanics/import-export-storage.md)中，而不是送入接口。更重要的是，供应器会在有充足的存储空间前停止送入下一批原料。

多个具有完全相同的样板的样板供应器可同时使用并且可以并行处理。

样板供应器采取轮询调度，因此所有相邻的机器可并行运作。

## 变种

样板供应器有3种变种：普通型，定向型及面板型。这会影响它们向哪些面送入原料，从哪些面接收产物以及向哪些面提供网络连接。

*   普通样板供应器会向各面送入原料，从各面接受产物，并如大部分AE2元件一样向各面提供网络连接。

*   定向样板供应器是通过对普通的样板供应器使用<ItemLink id="certus_quartz_wrench" />切换方向得到的。它们只向指向面提供原料，从各面接受产物，
以及**不**向指向的面提供网络连接。在你想建立子网的情况下，这让你能够把原料送入AE2元件而不会使得网络相连。

*   面板样板供应器是[线缆组分](../ae2-mechanics/cable-subparts.md)，因此可以在同一线缆上放置多个使得机器紧凑。它们与指向其面板方向的定向样板供应器行为一致。

通过合成，普通型和面板型样板供应器可以相互转换。

## 设置项

样板供应器有许多模式：

*   **阻塞模式**在机器中已有原料的情况下阻止新一批原料进入机器。
*   **锁定合成**可在不同的红石信号输入下或是在上次的合成产物返回该样板供应器前锁定该样板供应器。
*   供应器可选择是否在<ItemLink id="pattern_access_terminal" />中展示。

## 优先级

点击GUI右上角的扳手按钮可以设置优先级。当有多个合成相同物品的[样板](../items-blocks-machines/patterns.md)时，
高优先级供应器中的样板将会比低优先级供应器中的样板先得到使用，除非网络中高优先级样板的原料不足。

# 分子装配室

<BlockImage id="molecular_assembler" scale="4" />

<ItemLink id="molecular_assembler" />接受物品输入并执行相邻<ItemLink id="pattern_provider" />或放入其中的<ItemLink id="crafting_pattern" />、<ItemLink id="smithing_table_pattern" />或<ItemLink id="stonecutting_pattern" />指定的合成操作，然后把产物送入相邻容器中。

它们主要与<ItemLink id="pattern_provider" />合用，放在它旁边。此时样板供应器会有特殊的行为，会把样板和原料一同送进相邻的分子装配室。
鉴于分子装配室会把产物自动弹出至相邻容器中，装配室与样板供应器的组合足以自动化工作台合成。

<GameScene zoom="4" background="transparent">
<ImportStructure src="../assets/assemblies/assembler_tower.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>