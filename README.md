# CDDA: Zone - A S.T.A.L.K.E.R. Inspired Overhaul

Welcome to the Zone, Stalker. This comprehensive modification transforms Cataclysm: Dark Days Ahead into a S.T.A.L.K.E.R.-inspired post-apocalyptic survival experience.

## 🌟 Overview

**CDDA: Zone** replaces CDDA's zombie apocalypse with the mysterious and dangerous world inspired by the Chornobyl Exclusion Zone and the S.T.A.L.K.E.R. universe. Experience anomalies, mutants, artifacts, and the constant struggle for survival in an irradiated wasteland.

## 🎯 Key Features

### 🔮 **The Anomaly System**
- **Gravitational Anomalies**: Whirlgigs, Gravitational pits that crush and pull
- **Thermal Anomalies**: Burners that incinerate, Frost that freezes instantly  
- **Electrical Anomalies**: Electros that discharge deadly voltage
- **Chemical Anomalies**: Acidic clouds and poison fields
- **Spatial Anomalies**: Teleports and reality distortions

### ⚡ **Emissions & Blowouts**
- Periodic psi-storms that force all life underground
- Dynamic weather system with radioactive storms
- Safe zones become crucial during emissions
- Time-based survival mechanics

### 👥 **Faction Warfare**
- **Loners**: Independent stalkers seeking fortune
- **Duty**: Military faction maintaining order
- **Freedom**: Anarchist fighters opposing control
- **Scientists**: Researchers studying the Zone
- **Bandits**: Ruthless criminals and raiders
- **Military**: Government forces containing the Zone
- **Monolith**: Fanatic cult serving the Zone's will

### 🧬 **Mutant Ecosystem**
- **Flesh**: Mutated pigs with incredible resilience
- **Boars**: Aggressive territorial beasts
- **Dogs**: Pack hunters adapted to radiation
- **Pseudodogs**: Psi-capable canine predators
- **Controllers**: Telepathic humanoid horrors
- **Bloodsuckers**: Invisible vampiric stalkers
- **Snorks**: Agile gas-mask wearing mutants
- **Pseudogiants**: Massive tank-like creatures

### 💎 **Artifact System**
- **Healing Artifacts**: Moonlight, Soul, Pellicle
- **Protection Artifacts**: Bubble, Stone Heart, Fire Ball
- **Enhancement Artifacts**: Battery, Compass, Hypercube
- **Rare Artifacts**: Goldfish, Fireball, Star
- Dynamic artifact spawning in anomaly fields

### 🛠️ **Equipment & Gear**
- **Detectors**: Echo, Bear, Veles artifact detectors  
- **Suits**: Scientific, Military, Stalker protective gear
- **Weapons**: AK-series, Western firearms, improvised weapons
- **Medical**: Anti-radiation drugs, healing items, psi-protection

### 🗺️ **Zone Geography**
- **Garbage**: Entry point and trading hub
- **Cordon**: Military checkpoint and starting area
- **Dark Valley**: Bandit territory with laboratory ruins
- **Agroprom**: Underground facilities and anomaly fields
- **Yantar**: Scientific outpost studying mutants
- **Red Forest**: Highly irradiated dead zone
- **Pripyat**: Abandoned city center
- **CNPP**: Chornobyl Nuclear Power Plant - final destination

## 📋 Installation

1. **Prerequisites**: 
   - Cataclysm: Dark Days Ahead (latest experimental build recommended)
   - Basic understanding of CDDA modding

2. **Installation Steps**:
   ```bash
   # Clone or download this repository
   git clone https://github.com/yourusername/cdda-zone-mod
   
   # Copy mod to your CDDA mods directory
   cp -r stalker_zone /path/to/cdda/data/mods/
   
   # Launch CDDA and enable "Zone" mod in the mod selection screen
   ```

3. **Recommended Settings**:
   - Enable experimental Z-levels for underground areas
   - Set spawn rate to 0.1x for proper anomaly/mutant balance
   - Enable NPC needs for faction interactions

## 🎮 Getting Started

### Character Creation
- **Recommended Professions**: 
  - **Stalker** (balanced survivalist)
  - **Scientist** (research focused)  
  - **Military Deserter** (combat focused)
  - **Trader** (social/economic focused)

### Early Game Survival
1. **Find a Detector**: Essential for navigating anomaly fields safely
2. **Join a Faction**: Protection and trading opportunities
3. **Learn the Emissions**: Find shelter during psi-storms
4. **Scavenge Wisely**: Avoid obvious traps and ambushes
5. **Respect the Zone**: It's not just hostile - it's alive

### Progression Path
```
Rookie Stalker → Experienced Stalker → Veteran → Legend
    ↓              ↓                    ↓          ↓
Basic Gear → Military Equipment → Unique Artifacts → Zone Mastery
```

## 🔧 Technical Details

### Dependencies
- **Base Game**: Cataclysm: Dark Days Ahead
- **Recommended Mods**: 
  - Soundpack for enhanced audio
  - Tileset mods for visual improvements

### Compatibility
- **Compatible**: Most equipment and QoL mods
- **Incompatible**: Zombie-focused mods, magic systems
- **Partially Compatible**: Faction mods (may conflict with Zone factions)

### Performance Notes
- Anomaly calculations may impact performance on large maps
- Emission events are CPU intensive during active phase
- Recommended to limit Z-level depth for optimal performance

## 🛠️ Configuration

### Mod Settings (data/mods/stalker_zone/mod_settings.json)
```json
{
  "emission_frequency": 24,          // Hours between emissions
  "anomaly_density": 1.0,           // Multiplier for anomaly spawns  
  "artifact_rarity": 0.3,           // Chance modifier for artifacts
  "faction_aggression": 1.0,        // NPC hostility multiplier
  "mutant_spawn_rate": 0.8,         // Creature spawn modifier
  "zone_expansion": false           // Enable dynamic Zone growth
}
```

### Difficulty Adjustments
- **Tourist**: Lower radiation, fewer emissions, more supplies
- **Stalker** (Default): Balanced experience  
- **Master**: Higher radiation, frequent emissions, scarce resources
- **Zone Legend**: Maximum difficulty, permadeath mechanics

## 📚 Lore & Worldbuilding

### The Second Disaster
*"The first disaster in 1986 was just the beginning. The second one in 2006 changed everything. The Zone became something else - something alive."*

### The Zone's Nature
The Zone is not merely a radioactive wasteland. It's a reality-warping phenomenon that seems to possess its own consciousness. Scientists theorize it's:
- A dimensional rift caused by the second explosion
- An alien intelligence studying humanity
- The Earth's immune response to human destruction
- A convergence of parallel realities

### Key Locations Lore
Each major location has rich backstory and environmental storytelling through item descriptions, NPC dialogue, and environmental details.

## 🤝 Contributing

### How to Contribute
1. **Fork** the repository
2. **Create** feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** changes (`git commit -m 'Add AmazingFeature'`)
4. **Push** to branch (`git push origin feature/AmazingFeature`)
5. **Open** Pull Request

### Contribution Areas
- **Balancing**: Playtesting and feedback
- **Content**: New locations, items, creatures
- **Code**: JSON definitions, Lua scripts
- **Art**: Sprites, tiles, sound effects
- **Documentation**: Guides, lore, tutorials

### Development Roadmap
- [ ] **Phase 1**: Core systems (anomalies, factions, basic mutants)
- [ ] **Phase 2**: Advanced features (emissions, complex artifacts)
- [ ] **Phase 3**: Content expansion (new locations, quests)
- [ ] **Phase 4**: Polish & optimization
- [ ] **Phase 5**: Community features & mod support

## 📞 Support & Community

### Getting Help
- **GitHub Issues**: Bug reports and feature requests
- **Discord**: Real-time community chat and support
- **Reddit**: r/cataclysmdda for general CDDA community
- **Forums**: Official Cataclysm forums for mod discussions

### Known Issues
- Emission events may cause temporary FPS drops
- Some anomalies might interfere with vehicle pathfinding  
- Faction reputation system still in development
- Underground lab generation occasionally conflicts with anomalies

## 📄 License & Credits

### License
This mod is released under the Creative Commons Attribution-ShareAlike 4.0 License, compatible with Cataclysm: Dark Days Ahead's licensing.

### Credits & Inspiration
- **GSC Game World**: Original S.T.A.L.K.E.R. games and universe
- **CleverRaven**: Cataclysm: Dark Days Ahead base game
- **CDDA Community**: Modding tools and framework
- **Zone Community**: Continuous feedback and testing

### Special Thanks
- Andrei Tarkovsky's "Stalker" (1979) - Original inspiration
- Arkady & Boris Strugatsky - "Roadside Picnic" novel
- All contributors and playtesters who make this mod possible

---

*"Such is life in the Zone, Stalker. Every day is a gift - and every gift might be your last."*

**Good hunting, Stalker. The Zone is waiting.**