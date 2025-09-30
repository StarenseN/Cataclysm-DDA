# Zone Expeditions: Innawood-Inspired System Design

## 🎯 **Core Philosophy Change**

**Problème Original**: Notre mod transformait tout CDDA en Zone, mais cela perdait l'aspect "expédition dangereuse dans territoire hostile" du S.T.A.L.K.E.R.

**Solution Innawood**: Créer un **hub sécurisé** + **expéditions temporaires** dans la Zone = expérience plus authentique et équilibrée.

## 🏠 **Le Système Hub + Expédition**

### **Hub: Poste de Contrôle du Cordon**
Inspiré du checkpoint militaire de S.T.A.L.K.E.R., c'est votre base sécurisée:

```json
{
  "type": "overmap_terrain",
  "id": "zone_cordon_base",
  "name": "Cordon Checkpoint",
  "description": "Fortified military checkpoint on the Zone perimeter. Safe from emissions and mutants.",
  "see_cost": 5,
  "travel_cost": 10,
  "symbol": "▣",
  "color": "green",
  "spawns": { "group": "GROUP_MILITARY_TRADER", "population": [ 5, 8 ] }
}
```

**Services du Hub**:
- **Traders spécialisés**: Sidorovich (artefacts), Barman (équipement), Doc (médical)
- **Ateliers de maintenance**: Réparation d'équipement endommagé par la Zone
- **Système de coffres**: Stockage sécurisé entre expéditions
- **Briefings de mission**: NPCs donnent contrats d'exploration
- **Planification d'expédition**: Choisir durée, équipement, objectifs

### **Expéditions dans la Zone**
Comme Innawood, chaque expédition est temporaire et dangereuse:

```json
{
  "type": "effect_on_condition",
  "id": "zone_expedition_start",
  "condition": { "u_has_item": "zone_expedition_permit" },
  "effect": [
    { "u_message": "You enter the Zone. The Geiger counter starts clicking ominously..." },
    { "u_add_effect": "zone_expedition_timer", "duration": "6 hours" },
    { "u_teleport": "zone_expedition_map" }
  ]
}
```

## ⏰ **Mécaniques Temporelles Critiques**

### **Système d'Émissions (vs Warp Sickness d'Innawood)**
```json
{
  "type": "effect_type",
  "id": "emission_countdown",
  "name": [ "Emission Warning" ],
  "description": [ 
    "Atmospheric pressure is dropping. Electronics malfunction. You have 15 minutes to find shelter.",
    "The air feels heavy. 10 minutes until emission.",
    "Static fills the air. 5 minutes until the Zone screams."
  ],
  "max_duration": "15 m",
  "int_dur_factor": "1 m"
}
```

**Phases d'Émission**:
1. **Pré-émission (15 min)**: Warnings, electronics malfunction, animals flee
2. **Émission (2-5 min)**: Dégâts massifs si pas à l'abri
3. **Post-émission (30 min)**: Nouveaux artefacts, anomalies déplacées

### **Pression Temporelle Multiple**
- **Timer d'expédition**: 4-8 heures avant retour forcé
- **Timer d'émission**: Cycle imprévisible tous les 1-3 heures
- **Dégradation d'équipement**: Détecteurs tombent en panne
- **Radiation cumulative**: Doit rentrer avant empoisonnement fatal

## 🎪 **Système de Missions Structurées**

### **Types de Contrats d'Expédition**

```json
{
  "type": "mission",
  "id": "zone_artifact_recovery",
  "name": "Artifact Recovery: Red Forest",
  "description": "Ecologist Professor Sakharov needs a 'Soul' artifact from the Red Forest. Payment: 50,000 RU + scientific equipment access.",
  "start": { "assign_mission_target": { "om_terrain": "zone_red_forest" } },
  "goal": "MGOAL_FIND_ITEM",
  "item": "artifact_soul",
  "deadline_low": "6 h",
  "deadline_high": "8 h"
}
```

**Categories de Missions**:
- **Récupération d'Artefacts**: Objectifs spécifiques avec localisation
- **Reconnaissance**: Cartographier nouvelles zones, identifier menaces
- **Élimination**: Contrats sur mutants spécifiques (Controller dans Lab X-18)
- **Escorte**: Accompagner scientifiques vers sites de recherche
- **Sabotage**: Missions factionnelles (détruire équipement ennemi)
- **Récupération d'Urgence**: Sauver stalkers perdus/blessés

### **Système de Réputation et Accès**
```json
{
  "type": "effect_on_condition",
  "id": "unlock_veteran_missions",
  "condition": { 
    "and": [
      { "u_has_trait": "ZONE_REPUTATION_VETERAN" },
      { "u_completed_mission": "zone_artifact_recovery" }
    ]
  },
  "effect": [
    { "u_message": "Your reputation opens access to high-risk, high-reward expeditions." },
    { "set_string_var": { "veteran_missions": "unlocked" } }
  ]
}
```

## 🗺️ **Génération Procédurale de Zone**

### **Layers de Danger Progressifs**
Inspiré d'Innawood mais thématisé Zone:

```json
{
  "type": "overmap_terrain",
  "id": "zone_outer_ring",
  "name": "Zone Outer Perimeter", 
  "description": "Relatively safe Zone border. Light anomaly presence.",
  "danger_level": 1,
  "radiation_level": 2,
  "anomaly_density": 0.3,
  "artifact_spawn_rate": 0.1
},
{
  "type": "overmap_terrain", 
  "id": "zone_inner_sanctum",
  "name": "Zone Heart",
  "description": "Reality breaks down here. Extreme danger, legendary artifacts.",
  "danger_level": 10,
  "radiation_level": 15,
  "anomaly_density": 3.0,
  "artifact_spawn_rate": 0.8
}
```

### **Zones Thématiques Procédurales**
- **Périphérie (0-5km)**: Anomalies éparses, mutants basiques, artefacts communs
- **Zone Intermédiaire (5-15km)**: Champs d'anomalies, mutants avancés, laboratoires
- **Zone Profonde (15-25km)**: Anomalies mortelles, boss mutants, artefacts rares
- **Cœur de la Zone (25km+)**: Réalité déformée, Monolithe, artefacts légendaires

## 🎒 **Préparation et Équipement d'Expédition**

### **Interface de Planification**
```json
{
  "type": "effect_on_condition",
  "id": "expedition_planning_menu",
  "effect": [
    { "u_message": "Plan your expedition:" },
    { "u_message": "1. Choose duration (4h/6h/8h)" },
    { "u_message": "2. Select equipment loadout" },
    { "u_message": "3. Review mission objectives" },
    { "u_message": "4. Check emission forecast" }
  ]
}
```

**Équipement Critique**:
- **Détecteur d'artefacts**: Obligatoire, différents niveaux
- **Combinaison de protection**: Résistance radiation/anomalies
- **Médicaments**: Anti-rad, psi-protection, soins d'urgence
- **Vivres**: Nourriture/eau pour la durée prévue
- **Équipement de navigation**: PDA, cartes, balises de retour

### **Système de Poids et Endurance**
```json
{
  "type": "effect_type",
  "id": "expedition_fatigue",
  "name": [ "Expedition Fatigue" ],
  "description": [ "Long exposure to Zone stress is wearing you down." ],
  "base_mods": {
    "stamina_min": [ -20 ],
    "stamina_regen_modifier": [ -0.5 ]
  }
}
```

## 🏆 **Progression et Méta-Jeu**

### **Grades de Stalker**
```json
{
  "type": "mutation",
  "id": "ZONE_ROOKIE",
  "name": "Rookie Stalker",
  "description": "New to the Zone. Access to basic missions only.",
  "points": 0,
  "mixed_effect": true,
  "profession": true
},
{
  "type": "mutation", 
  "id": "ZONE_VETERAN",
  "name": "Veteran Stalker",
  "description": "Experienced Zone explorer. Access to dangerous expeditions.",
  "points": 3,
  "prereqs": [ "ZONE_ROOKIE" ],
  "threshreq": [ "THRESH_ZONE" ]
}
```

### **Unlocks Progressifs**
- **Rookie**: Périphérie seulement, missions de base, équipement limité
- **Experienced**: Zone intermédiaire, missions d'escorte, meilleur équipement
- **Veteran**: Zone profonde, missions d'élimination, accès artefacts rares
- **Master**: Cœur de Zone, missions uniques, équipement expérimental
- **Legend**: Accès total, missions narratives, influence sur factions

### **Base Building dans le Hub**
```json
{
  "type": "construction",
  "id": "zone_stash_upgrade",
  "description": "Expand your personal stash with reinforced containers.",
  "category": "FURN",
  "required_skills": [ [ "fabrication", 3 ] ],
  "time": "4 h",
  "components": [ [ [ "steel_chunk", 10 ], [ "pipe", 4 ] ] ]
}
```

## 🔄 **Cycle de Jeu Complet**

### **Session Type Expédition**
1. **Planification** (Hub): Choisir mission, équipement, durée
2. **Déploiement**: Transport vers zone d'opération
3. **Exploration Active**: Navigation, collecte, survie sous pression temporelle
4. **Crise Management**: Réagir aux émissions, pannes d'équipement, blessures
5. **Extraction**: Retour au hub avant deadline ou émission fatale
6. **Débrief**: Vendre artefacts, réparer équipement, progression réputation

### **Mécaniques de Tension**
- **Timer visible**: Compte à rebours jusqu'émission suivante
- **Equipment degradation**: Détecteurs se cassent, combinaisons s'abîment
- **Resource management**: Munitions, médicaments, nourriture s'épuisent
- **Navigation challenges**: Se perdre = mort certaine
- **Risk/reward decisions**: Pousser plus loin vs sécurité du retour

## 🎨 **Améliorations Atmosphériques**

### **Messages Contextuels**
```json
{
  "type": "snippet",
  "category": "zone_atmosphere",
  "text": [
    "Your Geiger counter's clicking accelerates as you approach the anomaly field.",
    "The air shimmers with heat distortion. A Burner anomaly lies ahead.",
    "Electronic static fills your headset. Something is interfering with communications.",
    "The zone feels different today. More alive. More hostile."
  ]
}
```

### **Système Audio/Visuel**
- **Soundscape**: Clics Geiger, grésillements radio, bruits de mutants
- **Visual cues**: Distorsions d'anomalies, éclairages d'artefacts
- **Interface améliorée**: Mini-map avec marqueurs d'anomalies
- **Effets weather**: Tempêtes radioactives, brouillards toxiques

## 📊 **Avantages vs Version Originale**

| **Aspect** | **Version Originale** | **Version Expédition** |
|------------|----------------------|------------------------|
| **Pacing** | Exploration continue | Sessions intensives ciblées |
| **Tension** | Diluée sur temps long | Concentrée et urgente |
| **Progression** | Linéaire standard | Unlocks basés réputation |
| **Risk/Reward** | Standard CDDA | Système expédition authentique |
| **Rejouabilité** | Une campagne longue | Multiples runs courts |
| **Authenticité** | Mod thématique | Vraie expérience S.T.A.L.K.E.R. |

## 🚀 **Implémentation par Phases**

### **Phase 1: Hub de Base**
- Créer overmap Cordon Checkpoint
- NPCs traders essentiels (Sidorovich, Barman)
- Système de coffres/stockage
- Interface planning basique

### **Phase 2: Expéditions Simples**
- Téléportation vers zones génériques
- Timer d'expédition basique
- Retour forcé au hub
- Missions d'artefacts simples

### **Phase 3: Système d'Émissions**
- Warnings pre-émission
- Mécaniques d'abri obligatoire
- Dégâts émission + effets post-émission
- Intégration avec timer d'expédition

### **Phase 4: Contenu Avancé**
- Zones thématiques spécialisées
- Système de réputation complexe
- Missions narratives
- Upgrades de hub

---

Cette approche transformerait complètement l'expérience, la rendant beaucoup plus fidèle à l'esprit S.T.A.L.K.E.R. tout en bénéficiant de la structure éprouvée d'Innawood. Voulez-vous que je commence l'implémentation de certains éléments spécifiques ?