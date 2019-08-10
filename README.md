# Reproducer for <https://github.com/MinecraftForge/MinecraftForge/issues/6029>

**Steps to Reproduce:**
 1. Build jar file with `gradlew reobfJar`
 2. Copy the jar file `build/libs/modid-1.0.jar` into a forge server installation (into the mod dir)
 3. Start the server

Results in:

```
java -jar forge-1.14.4-28.0.45.jar
2019-08-10 23:14:04,445 main WARN Disabling terminal, you're running in an unsupported environment.
[23:14:04.540] [main/INFO] [cp.mo.mo.Launcher/MODLAUNCHER]: ModLauncher running: args [--gameDir, ., --launchTarget, fmlserver, --fml.forgeVersion, 28.0.45, --fml.mcpVersion, 20190719.225934, --fml.mcVersion, 1.14.4, --fml.forgeGroup, net.minecraftforge]
[23:14:04.543] [main/INFO] [cp.mo.mo.Launcher/MODLAUNCHER]: ModLauncher 3.2.0+60+b86c1d4 starting: java version 1.8.0_212 by Oracle Corporation
[23:14:04.875] [main/INFO] [ne.mi.fm.lo.FixSSL/CORE]: Added Lets Encrypt root certificates as additional trust
[23:14:05.503] [main/INFO] [cp.mo.mo.LaunchServiceHandler/MODLAUNCHER]: Launching target 'fmlserver' with arguments [--gameDir, .]
[23:14:13.779] [main/WARN] [minecraft/Commands]: Ambiguity between arguments [teleport, destination] and [teleport, targets] with inputs: [Player, 0123, @e, dd12be42-52a9-4a91-a8a1-11c01849e498]
[23:14:13.781] [main/WARN] [minecraft/Commands]: Ambiguity between arguments [teleport, location] and [teleport, destination] with inputs: [0.1 -0.5 .9, 0 0 0]
[23:14:13.784] [main/WARN] [minecraft/Commands]: Ambiguity between arguments [teleport, location] and [teleport, targets] with inputs: [0.1 -0.5 .9, 0 0 0]
[23:14:13.813] [main/WARN] [minecraft/Commands]: Ambiguity between arguments [teleport, targets] and [teleport, destination] with inputs: [Player, 0123, dd12be42-52a9-4a91-a8a1-11c01849e498]
[23:14:13.830] [main/WARN] [minecraft/Commands]: Ambiguity between arguments [teleport, targets, location] and [teleport, targets, destination] with inputs: [0.1 -0.5 .9, 0 0 0]
[23:14:14.709] [Server thread/INFO] [minecraft/DedicatedServer]: Starting minecraft server version 1.14.4
[23:14:15.299] [modloading-worker-1/INFO] [ne.mi.co.ForgeMod/FORGEMOD]: Forge mod loading, version 28.0.45, for MC 1.14.4 with MCP 20190719.225934
[23:14:15.300] [modloading-worker-1/INFO] [ne.mi.co.MinecraftForge/FORGE]: MinecraftForge v28.0.45 Initialized
[23:14:15.310] [modloading-worker-3/INFO] [STDOUT/]: [com.example.examplemod.ExampleMod:<init>:34]: modjar://examplemod/greeting.txt
[23:14:15.313] [modloading-worker-3/INFO] [STDOUT/]: [com.example.examplemod.ExampleMod:<init>:36]: sun.misc.CompoundEnumeration@3feeabcd
[23:14:15.315] [modloading-worker-3/INFO] [STDOUT/]: [com.example.examplemod.ExampleMod:<init>:37]: []
[23:14:15.318] [modloading-worker-3/ERROR] [ne.mi.fm.ja.FMLModContainer/LOADING]: Failed to create mod instance. ModID: examplemod, class com.example.examplemod.ExampleMod
java.lang.AssertionError: null
        at com.example.examplemod.ExampleMod.<init>(ExampleMod.java:39) ~[?:1.0] {}
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method) ~[?:1.8.0_212] {}
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source) ~[?:1.8.0_212] {}
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source) ~[?:1.8.0_212] {}
        at java.lang.reflect.Constructor.newInstance(Unknown Source) ~[?:1.8.0_212] {}
        at java.lang.Class.newInstance(Unknown Source) ~[?:1.8.0_212] {}
        at net.minecraftforge.fml.javafmlmod.FMLModContainer.constructMod(FMLModContainer.java:131) ~[?:28.0] {}
        at java.util.function.Consumer.lambda$andThen$0(Unknown Source) ~[?:1.8.0_212] {}
        at java.util.function.Consumer.lambda$andThen$0(Unknown Source) ~[?:1.8.0_212] {}
        at net.minecraftforge.fml.ModContainer.transitionState(ModContainer.java:112) ~[?:?] {}
        at net.minecraftforge.fml.ModList.lambda$null$10(ModList.java:133) ~[?:?] {}
        at java.util.stream.ForEachOps$ForEachOp$OfRef.accept(Unknown Source) [?:1.8.0_212] {}
        at java.util.ArrayList$ArrayListSpliterator.forEachRemaining(Unknown Source) [?:1.8.0_212] {}
        at java.util.stream.AbstractPipeline.copyInto(Unknown Source) [?:1.8.0_212] {}
        at java.util.stream.ForEachOps$ForEachTask.compute(Unknown Source) [?:1.8.0_212] {}
        at java.util.concurrent.CountedCompleter.exec(Unknown Source) [?:1.8.0_212] {}
        at java.util.concurrent.ForkJoinTask.doExec(Unknown Source) [?:1.8.0_212] {}
        at java.util.concurrent.ForkJoinPool$WorkQueue.runTask(Unknown Source) [?:1.8.0_212] {}
        at java.util.concurrent.ForkJoinPool.runWorker(Unknown Source) [?:1.8.0_212] {}
        at java.util.concurrent.ForkJoinWorkerThread.run(Unknown Source) [?:1.8.0_212] {}
[23:14:15.636] [Server thread/FATAL] [ne.mi.fm.ModLoader/LOADING]: Failed to complete lifecycle event CONSTRUCT, 1 errors found
[23:14:15.697] [Server thread/ERROR] [minecraft/MinecraftServer]: Encountered an unexpected exception
net.minecraftforge.fml.LoadingFailedException: null
        at net.minecraftforge.fml.ModLoader.dispatchAndHandleError(ModLoader.java:198) ~[?:?] {}
        at net.minecraftforge.fml.ModLoader.gatherAndInitializeMods(ModLoader.java:180) ~[?:?] {}
        at net.minecraftforge.fml.server.ServerModLoader.begin(ServerModLoader.java:45) ~[?:?] {}
        at net.minecraft.server.dedicated.DedicatedServer.func_71197_b(DedicatedServer.java:121) ~[?:?] {pl:accesstransformer:B}
        at net.minecraft.server.MinecraftServer.run(MinecraftServer.java:598) [?:?] {pl:accesstransformer:B,pl:runtimedistcleaner:A}
        at java.lang.Thread.run(Unknown Source) [?:1.8.0_212] {}
[23:14:15.853] [Server thread/ERROR] [minecraft/MinecraftServer]: This crash report has been saved to: C:\Users\Adrodoc\devel\workspace\wol-server-1.14.4\.\crash-reports\crash-2019-08-10_23.14.15-server.txt
[23:14:15.908] [Server thread/INFO] [minecraft/MinecraftServer]: Stopping server
[23:14:15.910] [Server thread/INFO] [minecraft/MinecraftServer]: Saving worlds
[23:14:15.929] [Server thread/ERROR] [minecraft/MinecraftServer]: Exception stopping the server
java.lang.IllegalArgumentException: Can not hotload overworld. This must be loaded at all times by main Server.
        at org.apache.commons.lang3.Validate.isTrue(Validate.java:158) ~[server-1.14.4-extra.jar:?] {}
        at net.minecraftforge.common.DimensionManager.initWorld(DimensionManager.java:201) ~[?:?] {}
        at net.minecraftforge.common.DimensionManager.getWorld(DimensionManager.java:170) ~[?:?] {}
        at net.minecraft.server.MinecraftServer.func_71218_a(MinecraftServer.java:974) ~[?:?] {pl:accesstransformer:B,pl:runtimedistcleaner:A}
        at net.minecraft.server.MinecraftServer.func_213211_a(MinecraftServer.java:521) ~[?:?] {pl:accesstransformer:B,pl:runtimedistcleaner:A}
        at net.minecraft.server.MinecraftServer.func_71260_j(MinecraftServer.java:553) ~[?:?] {pl:accesstransformer:B,pl:runtimedistcleaner:A}
        at net.minecraft.server.dedicated.DedicatedServer.func_71260_j(DedicatedServer.java:544) ~[?:?] {pl:accesstransformer:B}
        at net.minecraft.server.MinecraftServer.run(MinecraftServer.java:661) [?:?] {pl:accesstransformer:B,pl:runtimedistcleaner:A}
        at java.lang.Thread.run(Unknown Source) [?:1.8.0_212] {}
```
