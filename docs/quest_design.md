# Zone Quest & Mission System Design

## Overview

The Zone quest system focuses on the dangerous, profit-driven nature of stalker life. Unlike traditional RPG quests, Zone missions are primarily economic transactions with high risk and potentially high reward.

## Mission Categories

### **Artifact Hunting**
*"There's a Moonlight artifact in the Red Forest. Bring it back and I'll make you rich."*

**Characteristics**:
- High-risk, high-reward operations
- Require advanced detection equipment  
- Knowledge of anomaly fields essential
- Competition from other stalkers
- Weather and emission timing crucial

**Mission Types**:
- **Specific Artifact Retrieval**: Client wants particular artifact type
- **Quantity Collection**: "Bring me 5 Droplets for my research"
- **Rare Artifact Hunt**: Legendary items with massive payouts
- **Time-Sensitive Retrieval**: Artifacts that decay or move

**Risk Factors**:
- Deadly anomaly fields
- Territorial mutants
- Bandit ambushes
- Equipment failure
- Getting lost in anomalies
- Emission events

### **Escort & Protection**
*"I need to get to Yantar. I'll pay well for safe passage."*

**Mission Types**:
- **Scientist Escort**: Researchers need protection during field work
- **Trader Convoy**: Merchants crossing dangerous territory
- **Military Liaison**: Official business requiring stalker guide
- **Refugee Evacuation**: Civilians trapped in dangerous areas

**Challenges**:
- Route planning around anomalies
- Defending against mutant attacks
- Avoiding faction conflicts
- Managing client safety vs. mission completion
- Equipment and supply management

### **Information & Reconnaissance** 
*"We need to know what's in Lab X-18. Scout it and report back."*

**Mission Types**:
- **Location Scouting**: Map dangerous or unknown areas
- **Faction Intelligence**: Monitor enemy movements and activities
- **Scientific Survey**: Collect environmental data for researchers  
- **Anomaly Mapping**: Chart new or shifted anomaly fields
- **Missing Person Search**: Find lost stalkers or civilians

**Skills Required**:
- Stealth and observation
- Survival in hostile environments
- Electronic surveillance equipment
- Photography and documentation
- Communication and reporting

### **Elimination Contracts**
*"There's a Controller in the Underground. Kill it and I'll pay triple rate."*

**Target Categories**:
- **Mutant Extermination**: Clear dangerous creatures from areas
- **Bandit Elimination**: Remove criminal threats to trade routes
- **Faction Warfare**: Military contracts against enemy factions
- **Rogue Stalker Bounties**: Hunt down criminals and psychopaths

**Difficulty Scaling**:
- Target strength and intelligence
- Environmental hazards at target location  
- Time constraints and urgency
- Collateral damage restrictions
- Equipment and ammunition requirements

### **Supply & Trading**
*"I need medical supplies delivered to the Army Warehouses. Discretely."*

**Mission Types**:
- **Supply Run**: Deliver goods between locations
- **Smuggling Operation**: Transport illegal or restricted items
- **Equipment Recovery**: Salvage valuable gear from dangerous locations
- **Resource Gathering**: Collect raw materials from Zone environment

**Complications**:
- Faction checkpoints and searches
- Bandit robbery attempts
- Environmental hazards during transport
- Spoilage of perishable goods
- Equipment breakdown

### **Technical & Repair**
*"The generator at our outpost is down. Can you fix it?"*

**Mission Types**:
- **Equipment Repair**: Fix broken machinery and electronics
- **Installation Jobs**: Set up communication or detection equipment
- **Maintenance Contracts**: Regular upkeep of faction facilities  
- **Salvage Operations**: Strip useful parts from abandoned equipment

**Required Skills**:
- Electronics and mechanical knowledge
- Problem-solving under pressure
- Resource improvisation
- Safety protocols in hazardous environments

## Faction-Specific Missions

### **Military Contracts**
- Zone containment operations
- Illegal stalker elimination
- Intelligence gathering on faction activities
- Equipment testing and evaluation
- Border security reinforcement

### **Duty Missions**
- Mutant extermination campaigns
- Anomaly field stabilization
- Civilian protection operations
- Anti-Freedom warfare
- Zone expansion prevention

### **Freedom Operations**
- Scientific research protection
- Anti-Military sabotage
- Information liberation missions
- Duty facility raids
- Zone access rights enforcement

### **Scientific Expeditions**
- Artifact collection and analysis
- Mutant specimen acquisition  
- Environmental data collection
- Equipment testing and deployment
- Research facility security

### **Loner Jobs**
- Independent trading operations
- Information brokerage
- Freelance protection services
- Artifact hunting cooperation
- Survival assistance

## Mission Mechanics

### **Payment Structure**

**Base Payment Rates**:
```
Mission Type          Base Rate    Risk Multiplier
Artifact Hunting     2,000 RU         1.5-5.0x
Escort Services      1,500 RU         1.2-3.0x  
Reconnaissance       1,000 RU         1.0-2.5x
Elimination          3,000 RU         2.0-8.0x
Supply/Trading         800 RU         1.1-2.0x
Technical Work       1,200 RU         1.0-1.8x
```

**Payment Modifiers**:
- **Urgency Bonus**: +25-100% for time-sensitive missions
- **Difficulty Bonus**: +50-200% for extreme danger
- **Reputation Bonus**: +10-50% based on faction standing  
- **Equipment Penalty**: -25% if client provides gear
- **Failure Penalty**: -50% to -100% for partial completion

### **Risk Assessment System**

**Environmental Hazards**:
- Radiation levels (background and hotspots)
- Anomaly density and types
- Mutant population and aggression
- Weather conditions and emission timing
- Terrain difficulty and navigation challenges

**Human Threats**:
- Faction territorial disputes
- Bandit activity levels
- Military patrol schedules
- Competitive stalker interference
- Political tensions and conflicts

**Equipment Requirements**:
- Protective gear specifications
- Detection and navigation equipment
- Medical supplies and emergency gear
- Communication equipment
- Specialized tools for mission type

### **Success & Failure Conditions**

**Mission Success Criteria**:
- **Primary Objective**: Core mission goal completion
- **Secondary Objectives**: Bonus tasks for extra payment
- **Time Limits**: Completion within specified timeframe
- **Condition Requirements**: Specific standards for delivery/completion
- **Safety Standards**: Minimizing casualties and collateral damage

**Failure Consequences**:
- **Reputation Loss**: Faction standing decreases
- **Financial Penalties**: Reduced or no payment
- **Equipment Confiscation**: Loss of provided gear
- **Future Restrictions**: Reduced access to high-value missions
- **Personal Consequences**: Injury, equipment damage, or death

### **Mission Progression System**

**Stalker Reputation Levels**:
1. **Rookie** (0-100 points): Basic missions, low pay, high supervision
2. **Experienced** (101-300 points): Standard missions, moderate pay
3. **Veteran** (301-600 points): Complex missions, good pay, autonomy
4. **Master** (601-1000 points): Elite missions, high pay, leadership roles
5. **Legend** (1000+ points): Unique missions, massive pay, faction influence

**Mission Unlocks by Reputation**:
- Rookie: Supply runs, basic escort, simple elimination
- Experienced: Artifact hunting, reconnaissance, technical work
- Veteran: High-value targets, dangerous locations, faction warfare
- Master: Legendary artifacts, deep Zone exploration, leadership missions
- Legend: Unique story missions, faction changing operations

## Dynamic Mission Generation

### **Procedural Elements**

**Location Randomization**:
- Mission sites generated based on current Zone conditions
- Anomaly field shifts create new opportunities and dangers
- Faction territorial changes affect mission availability
- Weather patterns influence mission timing and difficulty

**Target Variation**:
- Artifact spawns based on recent emission events
- Mutant migrations create elimination opportunities
- Faction conflicts generate time-sensitive missions
- NPC needs create supply and escort missions

**Economic Factors**:
- Market demand affects artifact prices and mission rates
- Resource scarcity creates supply mission opportunities
- Faction funding levels determine mission availability
- Competition from other stalkers affects difficulty

### **Adaptive Difficulty**

**Player Skill Scaling**:
- Mission difficulty increases with player reputation
- Equipment quality affects available mission types
- Faction relationships unlock or restrict missions
- Past performance influences future mission offers

**Zone State Response**:
- Recent emissions increase artifact hunting missions
- Faction wars create military contract opportunities
- Mutant population booms increase elimination missions
- Infrastructure damage creates repair and supply missions

## Quest Narrative Integration

### **Environmental Storytelling**
- Mission briefings include Zone lore and history
- Locations contain environmental narrative elements
- Audio logs and documents provide background context
- NPC dialogue reveals faction motivations and conflicts

### **Player Choice Consequences**
- Mission completion methods affect faction relationships
- Moral choices in missions have long-term consequences
- Resource allocation decisions impact future opportunities
- Information sharing affects competitive relationships

### **Emergent Narratives**
- Multiple missions can create interconnected storylines
- Player actions influence Zone political dynamics
- Random events create unique situational narratives
- Faction conflicts evolve based on player involvement

---

*"In the Zone, every mission is a gamble with your life. The smart stalker calculates the odds, but the successful one knows when to ignore them."*