<div align="center">
  <img src="https://github.com/Selimjerbi66/CyberAtaraxia-Suite/blob/main/cyberataraxia_new_logo.png?raw=true" width="180" alt="CyberAtaraxia Logo"/>
  <h1>CyberAtaraxia Careers — SOC Analyst Advanced</h1>

  <p>
    Un laboratoire d'entreprise complet et pratique pour passer des fondamentaux du SOC à la détection avancée, la défense Active Directory, le purple teaming et la réponse à incident — fait partie de la <strong>CyberAtaraxia Suite</strong> par <strong>Selim JERBI</strong>
  </p>
  <p>
    <img src="https://img.shields.io/badge/Statut-En%20Développement-blue?style=for-the-badge" />
    <img src="https://img.shields.io/badge/Licence-Open%20Source-green?style=for-the-badge" />
    <img src="https://img.shields.io/badge/Coût-Outils%20Gratuits%20%26%20Open%20Source-success?style=for-the-badge" />
    <a href="https://github.com/Selimjerbi66">
      <img src="https://img.shields.io/badge/Créé%20par-Selim%20JERBI-blueviolet?style=for-the-badge" />
    </a>
  </p>
  <p>
    🇬🇧 <a href="README.md">English</a> &nbsp;|&nbsp; 🇫🇷 <a href="README_FR.md">Français</a>
  </p>
</div>

---

## 🧭 À propos de ce parcours

**CyberAtaraxia Careers** est une ligne de la CyberAtaraxia Suite : des **parcours métier** guidés et pratiques plutôt que des outils isolés — chacun conçu pour produire des compétences démontrables, prêtes à figurer dans un portfolio, à partir de ressources gratuites et open source.

**SOC Analyst Advanced** fait suite au parcours *SOC Analyst*. Là où le premier parcours repose sur une détection légère, basée sur des fichiers, avec 3 VM, celui-ci construit ce qu'un vrai SOC exploite : un **système d'information d'entreprise virtualisé** avec un domaine Active Directory, un **SIEM/XDR centralisé (Wazuh)**, une **plateforme de supervision réseau (Security Onion avec Suricata et Zeek)** et une machine d'attaque dédiée. Vous attaquez ensuite votre propre environnement de manière contrôlée, observez ce que le SOC voit, ce qu'il rate, et **améliorez les défenses jusqu'à combler les lacunes**.

Ce n'est pas un cours à lire — c'est un environnement que vous *construisez, attaquez, défendez et mesurez*.

Aucun système de production n'est touché. Toute opération offensive reste dans un laboratoire virtuel isolé.

---

## 🎯 Objectif principal

Vous amener des fondamentaux du SOC à une **expérience pratique sur l'ensemble du cycle défensif d'un environnement d'entreprise** — non pas lire sur le SIEM, MITRE ATT&CK, les attaques Active Directory et la réponse à incident, mais exécuter chacun de bout en bout face à de vraies attaques (simulées en toute sécurité) :

> construire → sécuriser → superviser → attaquer → détecter → investiguer → répondre → améliorer → rejouer

Tout est organisé autour d'**un fil conducteur unique et d'une boucle itérative (Purple Team)** : chaque scénario d'attaque est confronté à la chaîne de détection, chaque lacune devient une nouvelle règle de détection ou une mesure de durcissement, et chaque scénario est rejoué pour **prouver** l'amélioration.

---

## 🏁 Ce que vous obtiendrez

| # | Livrable | Ce que cela démontre |
|---|---|---|
| 1 | Un **laboratoire d'entreprise virtualisé** fonctionnel (domaine AD, serveur et poste Windows, Linux, Kali attaquant) | Vous savez concevoir et déployer un environnement réaliste, segmenté et documenté |
| 2 | Un **Active Directory** fonctionnel (OU, utilisateurs, groupes, privilèges, DNS) avec durcissement et faiblesses volontaires documentées | Vous comprenez l'AD côté administrateur comme côté attaquant |
| 3 | Une **plateforme SOC** configurée : Wazuh + Security Onion (Suricata, Zeek) avec sources de journaux Windows et Linux | Vous savez centraliser, corréler et exploiter les événements de sécurité |
| 4 | Des **règles de détection** personnalisées (Wazuh, Suricata, Zeek) associées à MITRE ATT&CK | Vous passez de « aucune visibilité » à « détecté et cartographié » |
| 5 | Des **scénarios d'attaque contrôlés** documentés (reconnaissance, énumération, attaques AD, élévation de privilèges, déplacement latéral) | Vous menez des attaques réalistes avec rigueur et maîtrise du périmètre |
| 6 | Une correspondance **MITRE ATT&CK ↔ traces observables ↔ détection ↔ MITRE D3FEND** et une évaluation de la couverture de détection | Vous mesurez la défense au lieu de la supposer |
| 7 | Des **rapports d'investigation** et des **procédures de réponse aux incidents** | Vous savez conduire tout le cycle de réponse et le restituer |
| 8 | Un **audit technique** et une **analyse des risques** inspirée d'EBIOS Risk Manager, avec recommandations priorisées | Vous savez évaluer un système et piloter les améliorations |
| 9 | Un **dépôt GitHub** avec configurations, règles, scénarios, scripts et rapports | Un livrable concret à présenter en entretien |

Ce n'est pas « j'ai installé des outils » — c'est un laboratoire vivant et mesurable, avec une histoire d'amélioration avant/après documentée.

---

## 🧰 Matériel & budget

| Élément | Requis ? | Notes |
|---|---|---|
| **PC / machine hôte** | Requis | Recommandé : **32 Go de RAM**, 8+ threads CPU, **~500 Go de SSD libre**. 16 Go est possible uniquement avec les *profils d'exécution* ci-dessous (tout ne tourne pas en même temps). |
| **Hyperviseur** | Requis | **VMware Workstation** (Pro ou Player selon votre licence). |
| **Routeur / switch physique** | Non nécessaire | Tout est virtuel. |
| **Logiciels** | Gratuits / évaluation | Windows Server et Windows 11 utilisent les ISO d'évaluation officielles de Microsoft. Le reste est open source. |

> 💡 Le laboratoire est conçu pour que **toutes les VM n'aient pas besoin de fonctionner simultanément**. Voir *Profils d'exécution*.

---

## 🗺️ Architecture du laboratoire

| VM | Rôle | Composants principaux |
|---|---|---|
| **Windows Server 2022** | Contrôleur de domaine | AD DS, DNS, gestion des utilisateurs/groupes/GPO |
| **Windows 11** | Poste du domaine | Agent Wazuh, Sysmon, audit avancé, journalisation PowerShell |
| **Ubuntu Server LTS** | SIEM/XDR | Serveur Wazuh, indexeur, tableau de bord |
| **Security Onion** | Supervision réseau | Suricata (IDS), Zeek (métadonnées réseau), PCAP, console d'analyse |
| **Kali Linux** | Attaquant | Reconnaissance, énumération, analyse de vulnérabilités, attaques AD |

```
                       ┌───────────────────────────┐
                       │   Kali Linux (attaquant)  │
                       └─────────────┬─────────────┘
                                     │  réseau d'attaque
   ┌─────────────────────────────────┴──────────────────────────────┐
   │                 LAN entreprise (switch virtuel)                 │
   │   ┌────────────────────┐              ┌─────────────────────┐  │
   │   │ Windows Server 2022│              │      Windows 11     │  │
   │   │   AD DS + DNS      │◄────────────►│    poste du domaine │  │
   │   └─────────┬──────────┘              └──────────┬──────────┘  │
   └─────────────┼──────────────────────────┬─────────┼─────────────┘
                 │ agents Wazuh (journaux)  │ trafic mis en miroir
                 ▼                          ▼
        ┌─────────────────┐        ┌─────────────────────┐
        │ Ubuntu + Wazuh  │        │    Security Onion   │
        │ SIEM / XDR      │        │  Suricata + Zeek    │
        └─────────────────┘        └─────────────────────┘
                   (réseau de management / SOC)
```

**Principes réseau**

- Un **réseau de laboratoire** dédié avec IP statiques et un plan d'adressage documenté (LAN entreprise, réseau d'attaque, réseau de management/SOC).
- L'interface de sniffing de Security Onion est placée sur un segment qui **voit le trafic supervisé** (mode promiscuité / mise en miroir sur le switch virtuel).
- Le laboratoire est **isolé** de votre réseau réel. Internet n'est utilisé que temporairement pour les mises à jour et téléchargements.
- **Snapshots propres** à chaque étape stable (après l'AD, après l'intégration du client, avant le durcissement, avant chaque campagne d'attaque).

### ⚙️ Profils d'exécution

| Profil | VM actives | Usage |
|---|---|---|
| **Fondations** | Windows Server + Windows 11 | Construction AD, durcissement, GPO |
| **SOC Endpoint** | + Ubuntu/Wazuh | Détection côté hôte, règles, tableaux de bord |
| **SOC Réseau** | + Security Onion | Réglage Suricata/Zeek, analyse PCAP |
| **Purple complet** | + Kali (toutes les VM) | Scénarios d'attaque et rejeu |

---

## 🛠️ Outils utilisés

- **Hyperviseur :** VMware Workstation
- **Identité & infrastructure :** Windows Server 2022 (AD DS, DNS, GPO), Windows 11
- **SIEM / XDR / HIDS :** **Wazuh** (serveur, indexeur, tableau de bord, agents)
- **Visibilité endpoint :** audit avancé Windows, PowerShell Script Block Logging, **Sysmon** (configuration communautaire), auditd (Linux)
- **Supervision réseau :** **Security Onion**, **Suricata**, **Zeek**, analyse PCAP, Wireshark
- **Outils offensifs (laboratoire uniquement) :** Kali Linux — Nmap, outils d'énumération, BloodHound/SharpHound, Impacket, NetExec/CrackMapExec, Responder, Metasploit, etc.
- **Référentiels :** **MITRE ATT&CK** (+ Navigator), **MITRE D3FEND**, EBIOS Risk Manager (démarche inspirée)
- **Simulation d'attaque (optionnel) :** Atomic Red Team
- **Documentation :** Markdown dans le dépôt, draw.io / diagrams.net, Obsidian
- **Compléments optionnels :** Docker (et exploration Kubernetes), scripts Python/PowerShell/Bash, cas d'usage de l'IA en SOC

---

## 🔄 Méthodologie — La boucle itérative

```
 1 Concevoir & déployer ─► 2 Sécuriser & configurer ─► 3 Collecter les logs & superviser
          ▲                                                          │
          │                                                          ▼
 10 Documenter & recommander                               4 Réaliser des attaques contrôlées
          ▲                                                          │
 9 Rejouer ◄─ 8 Combler les lacunes ◄─ 7 Cartographier ATT&CK/D3FEND ◄─ 5 Observer les traces ◄─ 6 Détecter, investiguer, répondre
```

Chaque scénario suit le même schéma : **attaque → traces observables → alerte (ou angle mort) → investigation → cartographie → règle/durcissement amélioré → rejeu → résultat mesuré.**

---

## 📅 La feuille de route

<details>
<summary><strong>Phase 1 — Concevoir & construire le laboratoire (octobre)</strong></summary>

- Définir le cahier des charges détaillé, le périmètre, les livrables et la « définition de terminé » de chacun.
- Concevoir l'architecture, le plan d'adressage, la convention de nommage, les flux de journaux et la stratégie de snapshots.
- Installer et configurer VMware et les réseaux virtuels.
- Créer et installer les VM Windows Server 2022 et Windows 11.
- Déployer **Active Directory** (domaine, DNS, OU, utilisateurs, groupes, comptes de service) et intégrer le poste au domaine.
- Installation initiale de **Wazuh** et déploiement de l'agent.
- Premières mesures de durcissement et de journalisation (politique d'audit, journalisation PowerShell, Sysmon).

**Résultat attendu :** une infrastructure de base documentée et stable, prête à être supervisée.
</details>

<details>
<summary><strong>Phase 2 — Déployer le SOC & premières détections (novembre)</strong></summary>

- Finaliser la configuration de Wazuh.
- Déployer **Security Onion** avec **Suricata** et **Zeek**.
- Intégrer les journaux Windows et Linux, vérifier la collecte de bout en bout.
- Créer et tester les premières règles de détection (décodeurs/règles Wazuh, règles Suricata).
- Réaliser des scénarios simples et débuter la cartographie **MITRE ATT&CK**.
- Construire des tableaux de bord et des routines de qualification d'alertes.

**Résultat attendu :** un SOC fonctionnel qui collecte les événements et détecte plusieurs activités suspectes.
</details>

<details>
<summary><strong>Phase 3 — Scénarios d'attaque & Purple Team (décembre)</strong></summary>

- Mettre en place Kali Linux et préparer les scénarios offensifs.
- Reconnaissance et énumération de l'environnement.
- Tests de sécurité sur Windows, Linux et **Active Directory** (Kerberoasting, AS-REP roasting, attaques sur mots de passe, accès aux identifiants, etc.).
- Élévation de privilèges et déplacement latéral lorsque le contexte le permet.
- Observer et analyser les traces système et réseau ; corréler les événements.
- Associer chaque technique aux contre-mesures **MITRE D3FEND**.
- Améliorer les règles, rejouer les scénarios, mesurer les progrès.

**Résultat attendu :** des scénarios documentés qui évaluent le SOC et mènent à des améliorations concrètes.
</details>

<details>
<summary><strong>Phase 4 — Audit, risques & automatisation (fin décembre – début janvier)</strong></summary>

- Audit technique de l'environnement (configuration, disponibilité des journaux, capacités de détection).
- Identifier les faiblesses et les lacunes de détection.
- Analyse des risques inspirée d'**EBIOS Risk Manager** (actifs, menaces, scénarios de risque, traitement).
- Recommandations priorisées.
- Scripts d'automatisation lorsqu'ils apportent une réelle valeur.
- *Optionnel :* exploration Docker / Kubernetes et étude de cas d'usage de l'IA.

**Résultat attendu :** un bilan technique structuré, une analyse des risques et des recommandations priorisées.
</details>

<details>
<summary><strong>Phase 5 — Validation finale & restitution (janvier)</strong></summary>

- Finaliser les configurations et les scénarios, vérifier l'ensemble de l'environnement.
- Rejouer tous les scénarios d'attaque et évaluer les améliorations.
- Consolider la cartographie ATT&CK / D3FEND et la matrice de couverture.
- Finaliser les rapports d'investigation, les procédures et la documentation.
- Rédiger le rapport final, préparer le support de présentation et la démonstration technique.

**Résultat attendu :** un laboratoire documenté, des résultats évalués et une démo présentant l'architecture, les scénarios, les capacités de détection et les améliorations.
</details>

---

## 🧩 Les axes de travail en détail

### 🏗️ 1. Architecture & environnement
Conception réseau et système, identification des composants et flux à superviser, besoins en journalisation/collecte/détection, documentation de chaque choix technique.

### 🔒 2. Durcissement des systèmes
Configuration Windows et Linux, mesures de durcissement, comptes/droits/politiques, mécanismes de journalisation, et vérification que les protections fonctionnent réellement.

### 🛡️ 3. Plateforme SOC
Déploiement de Wazuh et Security Onion, intégration des journaux Windows et Linux, supervision réseau Suricata/Zeek, centralisation et corrélation des événements, règles personnalisées, tableaux de bord et alertes.

### 🔎 4. Détection des menaces
Identifier les événements pertinents, détecter les comportements suspects sur les hôtes et le réseau, distinguer légitime et malveillant, **corrélation système ↔ réseau**, et **réduction des faux positifs**.

### 🧭 5. MITRE ATT&CK & D3FEND
Associer les scénarios aux tactiques/techniques, identifier traces et indicateurs observables, associer les contre-mesures D3FEND, évaluer la couverture de détection et documenter les lacunes.

### ⚔️ 6. Pentesting contrôlé
Reconnaissance et énumération, exploitation contrôlée de vulnérabilités du laboratoire, scénarios Windows/Linux, scénarios AD, élévation de privilèges et déplacement latéral, observation des traces offensives et évaluation de la détection par le SOC.

### 🏰 7. Sécurité Active Directory
Déploiement du domaine, utilisateurs/groupes/privilèges, analyse des journaux, scénarios d'attaque AD, mise en place et évaluation de mesures de détection et de durcissement.

### 🟣 8. Purple Team
Confronter attaques et détections, analyser traces et alertes, repérer les techniques non détectées ou mal couvertes, améliorer règles et défenses, rejouer les scénarios pour mesurer les progrès.

### 🚨 9. Investigation & réponse aux incidents
Qualification des alertes, reconstitution chronologique, corrélation des traces système et réseau, identification des systèmes et comptes affectés, propositions de confinement / éradication / remédiation, rapports d'investigation et procédures de réponse.

### 📋 10. Audit technique
Évaluation de la configuration des systèmes et de la sécurité, vérification de la collecte et de la disponibilité des journaux, évaluation des capacités de supervision et de détection, identification des vulnérabilités et recommandations.

### ⚖️ 11. Analyse des risques
Identification des actifs, menaces/vulnérabilités/scénarios de risque, évaluation inspirée d'EBIOS Risk Manager, mesures de traitement et priorisation.

### 🧪 12. Objectifs secondaires *(uniquement si le temps et les ressources le permettent)*
- **Docker / cloud-native :** principes de conteneurisation, services complémentaires, risques de sécurité des conteneurs, supervision et détection dans cet environnement (Kubernetes à titre exploratoire).
- **Automatisation :** scripts de collecte, d'analyse et de tâches répétitives, structurés et documentés.
- **Intelligence artificielle :** étude exploratoire de cas d'usage SOC et, éventuellement, prototype limité.

---

## 📊 Matrice de couverture de détection (modèle)

La preuve centrale du projet est une matrice reliant chaque scénario à ce qui a été observé et défendu :

| Tactique ATT&CK | Technique | Scénario | Traces observables | Détection (règle) | Contre-mesure D3FEND | Statut (1er passage) | Statut (rejeu) |
|---|---|---|---|---|---|---|---|
| Credential Access | T1558.003 Kerberoasting | Scénario AD | Événement 4769 (ticket RC4), journaux Kerberos Zeek | Règle Wazuh personnalisée | Durcissement des identifiants | ❌ / ⚠️ / ✅ | ✅ |
| Discovery | T1046 Network Service Discovery | Reconnaissance | Rafales de connexions, alertes de scan Suricata | Suricata / Zeek | Analyse du trafic réseau | ✅ | ✅ |

*(Lignes illustratives — la matrice complète est construite tout au long du projet.)*

---

## 📁 Structure du dépôt

```
/docs            # cahier des charges, décisions d'architecture, journal
/architecture    # schémas, plan d'adressage, flux réseau
/configs         # configurations systèmes, Wazuh, Security Onion, Sysmon
/scenarios       # scénarios d'attaque documentés
/detections      # règles Wazuh, Suricata, Zeek + cartographie ATT&CK/D3FEND
/reports         # rapports d'investigation, audit, analyse des risques
/scripts         # scripts d'automatisation
```

---

## ✅ Critères de réussite

- Cohérence et qualité de l'architecture
- Fonctionnement et stabilité de l'environnement virtualisé
- Pertinence des mesures de sécurisation
- Qualité de la collecte et de la centralisation des événements
- Pertinence des mécanismes de détection
- Réalisme et maîtrise des scénarios d'attaque
- Qualité des investigations et des procédures de réponse
- Capacité à identifier les lacunes et à améliorer les défenses
- Qualité de la cartographie MITRE ATT&CK et D3FEND
- Pertinence de l'audit et de l'analyse des risques
- Qualité de la documentation, du rapport et de la démonstration

---

## ⚠️ Éthique & mentions légales

Toutes les opérations offensives sont **strictement limitées au laboratoire virtuel isolé** construit dans ce projet. N'exécutez jamais ces techniques contre des systèmes qui ne vous appartiennent pas ou sans autorisation écrite explicite. Ce dépôt est destiné à un usage **pédagogique et défensif uniquement**.

---

## 🚧 Note sur le périmètre

La supervision de la sécurité cloud (AWS/Azure/GCP), l'automatisation SOAR complète et l'exploitation de SIEM à l'échelle de la production sont hors périmètre. Docker, Kubernetes, l'automatisation et l'IA sont des objectifs **secondaires ou optionnels**, traités uniquement après l'atteinte des objectifs principaux.

---

## 👤 À propos du développeur

- 🎓 Étudiant ingénieur en Réseaux à **Polytech Dijon**, spécialisation Cybersécurité
- 🔵 Blue Teamer | Auditeur SI | Administrateur réseau
- 🏢 Stagiaire en cybersécurité chez **Axem Belgium**
- 🌱 Prépare actuellement **Blue Team L1 · ISO 27001/2022 · CCNA**

<p align="center">
  <a href="https://linkedin.com/in/selim-jerbi-b355a0202">
    <img src="https://img.shields.io/badge/LinkedIn-Connect%20with-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />
  </a>
  &nbsp;
  <a href="mailto:selimjerbi66@gmail.com">
    <img src="https://img.shields.io/badge/Gmail-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white" />
  </a>
</p>

<div align="center">
  <sub>CyberAtaraxia Careers — Open Source · Créé avec passion par Selim JERBI</sub>
</div>
