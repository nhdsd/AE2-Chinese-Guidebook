---
navigation:
  title: 入门（1.20+）
  position: 10
---

<div class="notification is-info">
  下面的内容仅适用于Minecraft 1.20或更高版本的AE2。
</div>

# 入门
## 获取初始材料

<GameScene zoom="4" background="transparent">
  <ImportStructure src="assets/assemblies/meteor_interior.snbt" />
</GameScene>

要开启AE2之旅，你首先要找到[陨石](ae2-mechanics/meteorites.md)。它们很常见并且一般会留下一个大洞，因此你很有可能已经碰见过它们了。
如果你还没有碰见过，那么你需要合成一个<ItemLink id="meteorite_compass" />，它会指向最近的<ItemLink id="mysterious_cube" />。

当你找到陨石后，挖到它的中心。你会找到赛特斯石英簇、赛特斯石英芽、不同种类的[赛特斯石英母岩](items-blocks-machines/budding_certus.md)、以及位于中央的神秘方块。

挖掉你找到的赛特斯石英簇和赛特斯石英块。你也可以挖掘赛特斯石英母岩，但是在没有精准采集附魔的情况下挖掘它们会使其降低1个等级。

不要挖掘无瑕的赛特斯石英母岩，因为即使有精准采集附魔挖掘它们也会使其变成有瑕的，且无法复原。

此外，挖掉陨石中央的神秘方块以获取全部4种压印板。

## 培养赛特斯石英

<GameScene zoom="4" background="transparent">
<ImportStructure src="assets/assemblies/budding_certus_1.snbt" />
</GameScene>

赛特斯石英芽会从[赛特斯石英母岩](items-blocks-machines/budding_certus.md)中长出来，就像紫水晶一样。如果你破坏未完成生长的赛特斯石英芽，它会掉落1个<ItemLink id="certus_quartz_dust" />，不受时运附魔影响。如果你破坏生长完成的赛特斯石英簇，它会掉落4个
<ItemLink id="certus_quartz_crystal" />，并且时运附魔会提升这一数目。

赛特斯石英母岩有4种等级：无瑕、有瑕、开裂和损坏。

<GameScene zoom="4" background="transparent">
<ImportStructure src="assets/assemblies/budding_blocks.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>

每当石英芽生长至下一阶段，母岩均有可能降级1级，直至变成普通的赛特斯石英块。 They can be repaired (and new budding blocks created) by throwing the budding block (or a
certus quartz block) in water with one or more <ItemLink id="charged_certus_quartz_crystal" />.

<RecipeFor id="damaged_budding_quartz" />

无暇的赛特斯石英母岩 will not degrade and will generate certus infinitely. However they cannot be crafted or moved
with a pickaxe, even with silk touch. (they *can* be moved with [](ae2-mechanics/spatial-io.md) though)

By themselves, certus quartz buds grow very slowly. Luckily the <ItemLink id="growth_accelerator" /> massively
accelerates this process when placed adjacent to the budding block. You should build a few of these as your first priority.

<GameScene zoom="4" background="transparent">
<ImportStructure src="assets/assemblies/budding_certus_2.snbt" />
<IsometricCamera yaw="195" pitch="30" />
</GameScene>

If you don't have enough quartz to also make an <ItemLink id="energy_acceptor" /> or <ItemLink id="vibration_chamber" />,
you can make a <ItemLink id="crank" /> and stick it on the end of your accelerator.

Harvesting the certus automatically is [described here](example-setups/simple-certus-farm.md).

## A Quick Aside on Fluix

Another material you will need is Fluix, which you have already encountered in making growth accelerators. It is made by throwing charged certus, redstone, and nether quartz in water. Doing this automatically is "left as an exercise for the reader."

The <ItemLink id="charger" /> is required to produce <ItemLink id="charged_certus_quartz_crystal" />., if you haven't made one already.

## Inscribing Some Processors

In your looting of a 陨石, you will have found four "presses" from breaking the Mysterious Cube. These are used in the <ItemLink id="inscriber" /> to make the three types of processor.

<ItemGrid>
  <ItemIcon id="silicon_press" />

  <ItemIcon id="logic_processor_press" />

  <ItemIcon id="calculation_processor_press" />

  <ItemIcon id="engineering_processor_press" />
</ItemGrid>

The inscriber is a sided machine, much like the vanilla furnace. Inserting from the top or bottom places items in the top or bottom slots, and inserting from the side or back inserts into the center slot. Results can be pulled from the side or back.

To facilitate automation with hoppers (and possibly reduce pipe spaghetti), inscribers can be rotated with a <ItemLink id="certus_quartz_wrench" />.

Produce a few of each type of processor in preparation for the next step, making a very basic ME system. Automating processor production is "left as an exercise for the reader".

## Matter Energy Tech: ME Networks and Storage

### What is ME Storage?

Its pronounced Emm-Eee, and stands for Matter Energy.

Matter Energy is the main component of Applied Energistics 2, it's like a mad scientist version of a Multi-Block chest,
and it can revolutionize your storage situation. ME is extremely different than other storage systems in Minecraft, and
it might take a little out of the box thinking to get used to; but once you get started vast amounts of storage in tiny
space, and multiple access terminals are just the tip of the iceberg of what becomes possible.

### What do I need to know to get started?

First, ME Stores items inside of other items, called [Storage cells](items-blocks-machines/storage_cells.md); there are 5 tiers with ever increasing amounts of
storage. In order to use a Storage Cell it must be placed inside either an <ItemLink id="chest" />,
or an <ItemLink id="drive" />.

The <ItemLink id="chest" /> shows you the contents of the Cell as soon as its placed inside, and you
can add and remove items from it as if it were a <ItemLink id="minecraft:chest" />, with the exception that the items are
actually stored in the Storage cells, and not the <ItemLink id="chest" /> itself.

While the <ItemLink id="chest" /> is a great way to get introduced to the concept of ME, to really
take advantage you need to set up an [ME Network](ae2-mechanics/me-network-connections.md).

## Your Very First ME System

Now that you have all of the basic materials and machines for Applied Energistics 2, you can make your first ME (Matter Energy) system. This will be a very basic one, no autocrafting, no logistics, just nice, simple, searchable storage.

<GameScene zoom="6" interactive={true}>
<ImportStructure src="assets/assemblies/tiny_me_system.snbt" />

</GameScene>

*   Your ingredients list:
    * 1x <ItemLink id="drive" />
    * 1x <ItemLink id="terminal" /> or <ItemLink id="crafting_terminal" />
    * 1x <ItemLink id="energy_acceptor" />
    * A few [cables](items-blocks-machines/cables.md), either glass, covered, or smart, but not dense
    * A few [storage cells](items-blocks-machines/storage_cells.md), recommended of the 4k variety for a good mix of
    capacity and types (it would be more efficient to [partition](items-blocks-machines/cell_workbench.md) a mix of 4k and 1k but that's a complexity we won't go into now)
---
1.  Place the drive down.
2.  The energy acceptor (and several other AE2 [devices](ae2-mechanics/devices.md)) comes in 2 modes, cube and flat. They can be switched between in a crafting grid. If your energy acceptor is a cube, place it down next to the drive. If it's a flat square, place a cable on the drive and place the acceptor on that.
3.  Run energy into the energy acceptor with a cable/pipe/conduit from your favorite energy-generation mod.
4.  Place a cable on top of the drive (or otherwise at eye level) and place your terminal or crafting terminal on it.
5.  Put your storage cells into the drive
6.  Profit
7.  Fiddle with the terminal's settings
8.  Bask in your ultimate power and ability
9.  Realize that this network is, in the grand scheme, rather small

### Expanding your Network

So you have some basic storage, and access to that storage, it's a good start, but you'll likely be looking to maybe
automate some processing.

A great example of this is to place a <ItemLink id="export_bus" /> on the top of a furnace to
dump in ores, and a <ItemLink id="import_bus" />
on the bottom of the furance to extract furnaced ores.

The <ItemLink id="export_bus" /> lets you export items from the network, into the attached
inventory, while the <ItemLink id="import_bus" /> imports items from the attached inventory into
the network.

### Overcoming Limits

At this point you probably getting close to 8 or so [devices](ae2-mechanics/devices.md), once you hit 9 devices you'll have to start
managing [channels](ae2-mechanics/channels.md). Many devices but not all, require a channel to
function.

By default a network can support 8 channels, once you break this limit, you'll have to add
an <ItemLink id="controller" /> to your network. this allows you to expand your network greatly.
[Smart cables](items-blocks-machines/cables.md) will allow you to see how channels are routed through your network. Use them extensively when starting out to learn how channels act, or if you have a lot of redstone and glowstone.
