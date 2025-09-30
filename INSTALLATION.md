# Installation Guide: CDDA Zone Mod

## System Requirements

### **Minimum Requirements**
- **Game**: Cataclysm: Dark Days Ahead (latest experimental build recommended)
- **OS**: Windows 7+, Linux (Ubuntu 18.04+), macOS 10.12+
- **RAM**: 4 GB RAM minimum, 8 GB recommended
- **Storage**: 2 GB free space for mod and save data
- **CPU**: Dual-core 2.4GHz processor or equivalent

### **Recommended Requirements**
- **Game**: CDDA Experimental build (less than 1 month old)
- **OS**: Windows 10, Linux (Ubuntu 20.04+), macOS 11+
- **RAM**: 8 GB RAM or more
- **Storage**: 5 GB free space (for multiple saves and debugging)
- **CPU**: Quad-core 3.0GHz processor or better

## Pre-Installation Setup

### **Step 1: Backup Your Game**
```bash
# Create backup of your CDDA installation
cp -r /path/to/cdda /path/to/cdda_backup

# Backup existing save data
cp -r ~/.cataclysm-dda/save ~/.cataclysm-dda/save_backup
```

### **Step 2: Update CDDA**
- Download the latest experimental build from the official CDDA site
- Ensure you have a build from the last 30 days for compatibility
- Test that the base game runs without issues

### **Step 3: Prepare Mod Directory**
```bash
# Navigate to CDDA installation
cd /path/to/cataclysm-dda

# Verify mods directory exists
ls -la data/mods/

# If mods directory doesn't exist:
mkdir -p data/mods/
```

## Installation Methods

### **Method 1: Direct Download (Recommended)**

1. **Download the Mod**
   ```bash
   # Clone or download from repository
   git clone https://github.com/yourusername/cdda-zone-mod.git
   
   # Or download ZIP and extract
   unzip cdda-zone-mod.zip
   ```

2. **Install to CDDA**
   ```bash
   # Copy mod to CDDA mods directory
   cp -r cdda-zone-mod/mods/stalker_zone /path/to/cdda/data/mods/
   
   # Verify installation
   ls -la /path/to/cdda/data/mods/stalker_zone/
   ```

3. **Verify File Structure**
   ```
   data/mods/stalker_zone/
   ├── modinfo.json
   ├── effects/
   ├── factions/
   ├── items/
   ├── mapgen/
   ├── monsters/
   ├── professions/
   └── spells/
   ```

### **Method 2: Git Submodule (Advanced)**

For developers or users who want automatic updates:

```bash
# Navigate to CDDA mods directory
cd /path/to/cdda/data/mods/

# Add as git submodule
git submodule add https://github.com/yourusername/cdda-zone-mod.git stalker_zone

# Initialize submodule
git submodule init
git submodule update
```

### **Method 3: Symbolic Link (Linux/macOS)**

For development or testing multiple versions:

```bash
# Create symbolic link to mod directory
ln -s /path/to/cdda-zone-mod/mods/stalker_zone /path/to/cdda/data/mods/stalker_zone

# Verify link
ls -la /path/to/cdda/data/mods/ | grep stalker_zone
```

## Mod Configuration

### **Step 1: Launch CDDA**
```bash
# Start CDDA
./cataclysm-tiles

# Or for terminal version:
./cataclysm
```

### **Step 2: Create New World**
1. Select "Create World" from main menu
2. Choose "Custom World" option
3. **Important**: Disable default zombie apocalypse mods:
   - Uncheck "Classic Zombies"
   - Uncheck "Zombie Evolution" 
   - Uncheck any other zombie-related mods

### **Step 3: Enable Zone Mod**
1. In mod selection screen, find "Zone: S.T.A.L.K.E.R. Overhaul"
2. Check the box to enable it
3. Review dependency warnings (should be none for base installation)
4. Click "Confirm" to proceed

### **Step 4: World Settings**
Configure these settings for optimal Zone experience:

**Monster Settings**:
- Monster spawn rate: 0.1x (anomalies replace zombies)
- Monster evolution: OFF
- Monster upgrade timer: OFF

**Environmental Settings**:
- Season length: 14 days (default)
- Initial season: Spring
- Eternal season: OFF
- Weather generation: ON

**Game Balance**:
- Skill rust: ON (realistic)
- Stat through skills: ON
- Multiple loot: OFF

**Technical Settings**:
- Z-levels: ON (for underground areas)
- Freeform buildings: ON
- Experimental 3D field of view: ON

### **Step 5: Character Creation**
1. Choose "Custom Character" for full control
2. Select Zone-appropriate profession:
   - **Stalker** (recommended for new players)
   - **Scientist** (research focused)
   - **Military Deserter** (combat focused)
   - **Rookie Stalker** (challenging start)

3. **Recommended Starting Traits**:
   - **Positive**: Robust, Night Vision, Quick Learner
   - **Negative**: Addictive Personality, Light Sensitive, Pacifist (for non-combat builds)

4. **Essential Starting Skills**:
   - Survival: 2-3 points minimum
   - Electronics: 1-2 points (for detectors)
   - First Aid: 1-2 points (medical supplies)
   - Rifles or Pistols: 2-3 points (combat)

## First-Time Setup Checklist

### **Verify Installation**
- [ ] Mod appears in mod list during world creation
- [ ] No error messages during world generation
- [ ] Game launches successfully with mod enabled
- [ ] Zone professions appear in character creation

### **Test Basic Functionality**
- [ ] Spawn with appropriate starting equipment
- [ ] Artifact detector functions (if included in profession)
- [ ] Geiger counter responds to radiation
- [ ] PDA shows Zone information
- [ ] Faction relationships display correctly

### **Performance Check**
- [ ] Game runs smoothly during normal play
- [ ] No significant lag during map generation
- [ ] Anomaly effects render properly
- [ ] Sound effects work (if using soundpack)

## Troubleshooting

### **Common Installation Issues**

#### **Mod Not Appearing in List**
```bash
# Check file permissions
chmod -R 755 /path/to/cdda/data/mods/stalker_zone/

# Verify modinfo.json syntax
cat /path/to/cdda/data/mods/stalker_zone/modinfo.json | python -m json.tool

# Check for hidden files or incorrect directory structure
find /path/to/cdda/data/mods/stalker_zone/ -name ".*" -o -name "*~"
```

#### **Game Crashes on World Creation**
1. **Check CDDA Version Compatibility**:
   ```bash
   ./cataclysm --version
   ```
   Ensure version is from the last 30 days.

2. **Disable Conflicting Mods**:
   - Zombie-related mods
   - Total conversion mods
   - Mods that modify core game systems

3. **Verify JSON Syntax**:
   ```bash
   # Check all JSON files for syntax errors
   find stalker_zone/ -name "*.json" -exec python -m json.tool {} \; > /dev/null
   ```

#### **Missing Items/Monsters/Effects**
1. **Check Debug Log**:
   ```bash
   # Look for error messages in debug log
   tail -f ~/.cataclysm-dda/config/debug.log
   ```

2. **Verify File Loading Order**:
   - Ensure modinfo.json has correct dependencies
   - Check that all required files are present

### **Performance Issues**

#### **Low FPS During Anomaly Effects**
1. **Reduce Visual Complexity**:
   - Lower tile animation settings
   - Disable particle effects
   - Reduce field-of-view distance

2. **Optimize Settings**:
   ```json
   // In config/options.json
   {
     "ANIMATION": false,
     "ANIMATIONS": false,
     "FORCE_REDRAW": true
   }
   ```

#### **High Memory Usage**
1. **Limit Save Data**:
   - Regular cleanup of old save files
   - Avoid extremely large maps
   - Limit number of NPCs

2. **System Optimization**:
   ```bash
   # Linux: Increase swap if needed
   sudo swapon --show
   sudo fallocate -l 4G /swapfile
   sudo chmod 600 /swapfile
   sudo mkswap /swapfile
   sudo swapon /swapfile
   ```

### **Compatibility Issues**

#### **Conflicting Mods**
**Incompatible Mods** (should not be used together):
- Classic Zombies
- Zombie Evolution
- Necromancy Mod
- Magic Item Mod
- Most total conversion mods

**Partially Compatible Mods** (may cause issues):
- Vehicle mods (some features may conflict)
- Faction mods (reputation systems may interfere)
- Weather mods (emission system conflicts)

**Compatible Mods** (work well together):
- Quality of Life improvements
- UI enhancements
- Soundpacks
- Tilesets
- Most equipment mods

#### **Save Game Compatibility**
**Warning**: Installing or removing the Zone mod on existing saves may cause:
- Missing items/monsters
- Corrupted faction relationships
- Map generation errors
- Save file corruption

**Recommended**: Always start fresh when installing major mods.

## Advanced Configuration

### **Custom Settings File**

Create `stalker_zone_config.json` in your config directory:

```json
{
  "zone_settings": {
    "emission_frequency_hours": 24,
    "anomaly_density_multiplier": 1.0,
    "artifact_rarity_modifier": 0.3,
    "faction_aggression_level": 1.0,
    "mutant_spawn_rate": 0.8,
    "radiation_danger_level": 1.2,
    "enable_dynamic_weather": true,
    "enable_faction_wars": true,
    "enable_artifact_degradation": false
  }
}
```

### **Debug Mode Setup**

For testing and development:

```bash
# Launch CDDA with debug options
./cataclysm --debug

# Enable debug messages in-game:
# Press ` (backtick) to open debug menu
# Select "Enable Debug Messages"
```

### **Mod Development Setup**

For contributors and advanced users:

```bash
# Set up development environment
git clone https://github.com/yourusername/cdda-zone-mod.git
cd cdda-zone-mod

# Install development dependencies
pip install -r requirements-dev.txt

# Run JSON validation
python tools/validate_json.py

# Run unit tests
python -m pytest tests/
```

## Post-Installation Tips

### **Getting Started in the Zone**
1. **Learn the Basics**:
   - Always carry a Geiger counter
   - Invest in a good artifact detector
   - Understand faction relationships
   - Plan around emission schedules

2. **Essential Equipment Priority**:
   1. Geiger counter (radiation safety)
   2. Artifact detector (income source)
   3. Protective suit (survival)
   4. Medical supplies (emergency treatment)
   5. PDA (information and communication)

3. **Survival Strategy**:
   - Start in safer outer zones
   - Build reputation with friendly factions
   - Learn anomaly patterns through experience
   - Always have escape routes planned

### **Community Resources**

- **Official Documentation**: Available in `/docs/` directory
- **Community Discord**: [Zone Mod Community Server]
- **Bug Reports**: GitHub Issues page
- **Mod Updates**: Check GitHub releases page
- **Video Tutorials**: [YouTube Playlist Link]

### **Save Game Management**

```bash
# Backup save before major updates
cp -r ~/.cataclysm-dda/save/YourWorldName ~/.cataclysm-dda/save/YourWorldName_backup

# Clean up old saves periodically
find ~/.cataclysm-dda/save/ -name "*.sav" -mtime +30 -delete
```

## Support & Updates

### **Getting Help**
1. **Check Documentation First**: Read all files in `/docs/`
2. **Search Known Issues**: GitHub Issues page
3. **Community Support**: Discord server or forums
4. **Bug Reports**: Use GitHub issue template

### **Updating the Mod**
```bash
# Git method
cd /path/to/cdda/data/mods/stalker_zone
git pull origin main

# Manual method
# Download new version and replace files
# Always backup saves before updating
```

### **Version Compatibility**
- **Patch Updates** (1.0.x): Save compatible
- **Minor Updates** (1.x.0): May require new character
- **Major Updates** (x.0.0): Requires fresh installation

---

**Good hunting, Stalker. Welcome to the Zone.**