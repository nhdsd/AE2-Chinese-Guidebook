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
鉴于分子装配室会把产物自动弹出至相邻容器这种，装配室与样板供应器的组合足以自动化工作台合成。

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

多个具有完全相同的样板的<ItemLink id="pattern_provider" />是受支持的并且可以并行处理。此外，你可以编码一个8圆石 = 8石头的样板而不是1圆石 = 1石头的。
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

# Pattern Providers

<Row>
<BlockImage id="pattern_provider" scale="4" />

<BlockImage id="pattern_provider" p:push_direction="up" scale="4" />

<GameScene zoom="4" background="transparent">
  <ImportStructure src="../assets/blocks/cable_pattern_provider.snbt" />
</GameScene>
</Row>

<ItemLink id="pattern_provider" />s are the primary way in which your autocrafting system interacts with the world. They push the ingredients in
their [patterns](../items-blocks-machines/patterns.md) to adjacent inventories, and items can be inserted into them in order to insert them into the network. Often
a channel can be saved by piping the output of a machine back into a nearby pattern provider (often the one that pushed the ingredients)
instead of using an <ItemLink id="import_bus" /> to pull the output of the machine into the network.

Of note, since they push the ingredients directly from the [crafting storage](../items-blocks-machines/crafting_cpu_multiblock.md#crafting-storage) in a crafting CPU, they
never actually contain the ingredients in their inventory, so you cannot pipe out from them. You have to have the provider push
to another inventory (like a barrel) then pipe from that.

Also of note, the provider has to push ALL of the ingredients at once, it can't push half-batches. This is useful
to exploit.

Pattern providers have a special interaction with interfaces on [subnets](../ae2-mechanics/subnetworks.md): if the interface is unmodified (nothing in the request slots)
the provider will skip the interface entirely and push directly to that subnet's [storage](../ae2-mechanics/import-export-storage.md),
skipping the interface and not filling it with recipe batches, and more importantly, not inserting the next batch until there's space in storage.

Multiple pattern providers with identical patterns are supported and work in parallel.

Pattern providers will attempt to round-robin their batches to all of their faces, thus using all attached machines in parallel.

## Variants

Pattern Providers come in 3 different variants: normal, directional, and flat. This affects which specific sides they push
ingredients to, receive items from, and provide a network connection to.

*   Normal pattern providers push ingredients to all sides, receive inputs from all sides, and, like most AE2 machines, act
    like a cable providing network connection to all sides.

*   Directional pattern providers are made by using a <ItemLink id="certus_quartz_wrench" /> on a normal pattern provider to change its
    direction. They only push ingredients to the selected side, receive inputs from all sides, and specifically don't provide a network
    connection on the selected side. This allows them to push to AE2 machines without connecting networks, if you want to make a subnetwork.

*   Flat pattern providers are a [cable subpart](../ae2-mechanics/cable-subparts.md), and so multiple can be placed on the same cable, allowing for compact setups.
    They act similar to the selected side on a directional pattern provider, providing patterns, receiving inputs, and not
    providing a network connection on their face.

Pattern providers can be swapped between normal and flat in a crafting grid.

## Settings

Pattern providers have a variety of modes:

*   **Blocking Mode** stops the provider from pushing a new batch of ingredients if there are already
    ingredients in the machine.
*   **Lock Crafting** can lock the provider under various redstone conditions, or until the result of the
    previous craft is inserted into that specific pattern provider.
*   The provider can be shown or hidden on <ItemLink id="pattern_access_terminal" />s.

## Priority

Priorities can be set by clicking the wrench in the top-right of the GUI. In the case of several [patterns](../items-blocks-machines/patterns.md)
for the same item, patterns in providers with higher priority will be used over patterns in providers with lower priority,
unless the network does not have the ingredients for the higher priority pattern.

# Molecular Assemblers

<BlockImage id="molecular_assembler" scale="4" />

The <ItemLink id="molecular_assembler" /> takes items input into it and carries out the operation defined by an adjacent <ItemLink id="pattern_provider" />,
or the inserted <ItemLink id="crafting_pattern" />, <ItemLink id="smithing_table_pattern" />, or <ItemLink id="stonecutting_pattern" />,
then pushes the result to adjacent inventories.

Their main use is next to a <ItemLink id="pattern_provider" />. Pattern providers have special behavior in this case,
and will send information about the relevant pattern along with the ingredients to adjacent assemblers. Since assemblers auto-eject the results of
crafts to adjacent inventories (and thus into the return slots of the pattern provider), an assembler on a pattern provider
is all that is needed to automate crafting patterns.

<GameScene zoom="4" background="transparent">
<ImportStructure src="../assets/assemblies/assembler_tower.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>