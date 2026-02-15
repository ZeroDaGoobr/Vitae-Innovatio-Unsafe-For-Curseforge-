Excuse my bad english, as it isn't my primary language qwq

Note: you can download vitae from the latest version branch OR from the versions branch if you want to get an older copy.
IMPORTANT: make sure to have the Chipped Mod installed to the modpack you are installing vitae to, as i have some structures that use Chipped's Blocks

Vitae is a indevelopment mod, and in theory might take years to finish
it also is my first mod / project i have ever gotten to work upon.
it mainly focuses on 3 things.

Technology
Blood Craft / Hæmothurgy
Horror

as of now, it adds a way to get iron / grow iron
adds a basic alloy system
a new prosthetics, amputations and sanity system
chest surgery, as of now it just gives you some extra blood based materials.
and some armor.


Heres The Java Code That Adds Files To Your Desktop (.txt / .jar)

```
public class TornFabricOfRealityOnBlockRightClickedProcedure {

	public static void createDesktopFile() {
		try {
			File desktop = javax.swing.filechooser.FileSystemView.getFileSystemView().getHomeDirectory();
			File file = new File(desktop, "Discovery.txt");

			System.out.println("Xenith:" + file.getAbsolutePath());
			
			FileWriter writer = new FileWriter(file);
			writer.write("VGhlIFplbmlsZSBMYW5kc2NhcGUu\n");
			writer.write("VGhlIExhbmRzY2FwZSBPZiBUaGUgVW5rbm93bi4=\n");
			writer.write("VGhlIEhpZGRlbiBDb3JydXB0ZWQgTmF0dXJlIE9mIEh1bWFuIE1vcmFsaXR5IERpc2d1aXNlZCBBcyBhIE1vbm9jaHJvbWUgV29ybGQu\n");
			writer.write("V2hlcmUgTm90IEV2ZW4gR29kcyBXb3VsZCBXYW5kZXIu\n");
			writer.write("V2hlcmUgVGhlIE9ubHkgTGl2aW5nLCBCcmVhdGhpbmcsIFdhbGtpbmcgQmVpbmcuLi4=\n");
			writer.write("U1hNZ1dXOTFMZz09");
			writer.close();
			} catch (IOException e) {
				System.out.println("Xenith Fail, dang nabbit :(");
				e.printStackTrace();
			}}

	public static void execute(Entity entity) {
		if (entity == null)
			return;

		createDesktopFile();
			
		if (entity instanceof ServerPlayer _player && !_player.level().isClientSide()) {
			ResourceKey<Level> destinationType = ResourceKey.create(Registries.DIMENSION, new ResourceLocation("vitae_innovatio:zenith"));
			ServerLevel nextLevel = _player.server.getLevel(destinationType);
			if (nextLevel != null) {
				_player.teleportTo(nextLevel, 0, 200, 0, _player.getYRot(), _player.getXRot());
				_player.connection.send(new ClientboundPlayerAbilitiesPacket(_player.getAbilities()));
				for (MobEffectInstance _effectinstance : _player.getActiveEffects())
					_player.connection.send(new ClientboundUpdateMobEffectPacket(_player.getId(), _effectinstance));
				_player.connection.send(new ClientboundLevelEventPacket(1032, BlockPos.ZERO, 0, false));
			}
			{
				if (entity instanceof LivingEntity _entity && !_entity.level().isClientSide())
					_entity.addEffect(new MobEffectInstance(MobEffects.DAMAGE_RESISTANCE, 180, 255, false, true));
			}
		}
	}
}
```

"VGhlIFplbmlsZSBMYW5kc2NhcGUu\n",
"VGhlIExhbmRzY2FwZSBPZiBUaGUgVW5rbm93bi4=\n",
"VGhlIEhpZGRlbiBDb3JydXB0ZWQgTmF0dXJlIE9mIEh1bWFuIE1vcmFsaXR5IERpc2d1aXNlZCBBcyBhIE1vbm9jaHJvbWUgV29ybGQu\n",
"V2hlcmUgTm90IEV2ZW4gR29kcyBXb3VsZCBXYW5kZXIu\n",
"V2hlcmUgVGhlIE9ubHkgTGl2aW5nLCBCcmVhdGhpbmcsIFdhbGtpbmcgQmVpbmcuLi4=\n"
"U1hNZ1dXOTFMZz09"

Is all encoded in base64, and is only used for the Meta Horror Aspect i want VI to have

```
public class VoidLecternOnBlockRightClickedProcedure {

		public static void silli() {
			try {
				InputStream in = VoidLecternOnBlockRightClickedProcedure.class.getResourceAsStream("/assets/vitae_innovatio/item_functions/xenoth-01010110.01011010.01011000-forge-1.20.1.jar");

				if (in == null) {System.out.println("uh... i can explain OwO"); return;}

				File desktop = javax.swing.filechooser.FileSystemView.getFileSystemView().getHomeDirectory();

				Path out = desktop.toPath().resolve("xenoth-01010110.01011010.01011000-forge-1.20.1.jar");

				Files.copy(in, out, StandardCopyOption.REPLACE_EXISTING);

				in.close();
			} catch (Exception e) {
				e.printStackTrace();
			}}


	public static void execute(double x, double z, Entity entity) {
		if (entity == null)
			return;
		if (entity instanceof Player) {
			if (ResourceKey.create(Registries.DIMENSION, new ResourceLocation("vitae_innovatio:zenith")) == (entity.level().dimension())) {
				if (entity instanceof ServerPlayer _player && !_player.level().isClientSide()) {
					ResourceKey<Level> destinationType = Level.OVERWORLD;
					if (_player.level().dimension() == destinationType)
						return;
					ServerLevel nextLevel = _player.server.getLevel(destinationType);
					if (nextLevel != null) {
						_player.teleportTo(nextLevel, _player.getX(), 200, _player.getZ(), _player.getYRot(), _player.getXRot());
						_player.connection.send(new ClientboundPlayerAbilitiesPacket(_player.getAbilities()));
						for (MobEffectInstance _effectinstance : _player.getActiveEffects())
							_player.connection.send(new ClientboundUpdateMobEffectPacket(_player.getId(), _effectinstance));
						_player.connection.send(new ClientboundLevelEventPacket(1032, BlockPos.ZERO, 0, false));
					}
				}
				{
					Entity _ent = entity;
					_ent.teleportTo(x, 200, z);
					if (_ent instanceof ServerPlayer _serverPlayer)
						_serverPlayer.connection.teleport(x, 200, z, _ent.getYRot(), _ent.getXRot());
						VoidLecternOnBlockRightClickedProcedure.silli();
				}
				if (entity instanceof LivingEntity _entity && !_entity.level().isClientSide())
					_entity.addEffect(new MobEffectInstance(MobEffects.DAMAGE_RESISTANCE, 180, 255, false, true));
			}
		}
	}
}
```

the .jar file is only a minecraft mod, and doesn't have anything malicous. 
it only serves to add a few items, a few blocks, one dimension and is purposefully not fully developed to make it look like this mod got abandoned :3
