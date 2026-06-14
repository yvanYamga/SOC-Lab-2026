
---

## 📅 JOUR 7 - Mardi 9 juin 2026 : Purple Team + Playbook IR

### Objectif
Simuler un incident complet, rédiger le playbook final, préparer le portfolio.

---

### ⏰ Planning (08:00 → 12:00)

| Heure | Action | Durée |
|-------|--------|-------|
| 08:00 | Allumer toutes les VMs | 5 min |
| 08:05 | Scénario : "Ransomware simulation" | 30 min |
| 08:35 | Détection + réponse | 30 min |
| 09:05 | Rédiger IR Playbook #003 | 45 min |
| 09:50 | Créer diagramme réseau final | 20 min |
| 10:10 | Prendre screenshots pour portfolio | 20 min |
| 10:30 | Rédiger README final projet | 30 min |
| 11:00 | Git push final semaine 1 | 10 min |
| 11:10 | Post LinkedIn #2 | 15 min |
| 11:25 | **Semaine 1 terminée** | |

---

### 🔧 Scénario Ransomware Simulation

**Étapes** :
1. Depuis Kali, scan réseau complet
2. Tentative brute force SSH
3. "Infection" simulée (créer fichier `RANSOMWARE_SIMULATION.txt` sur Ubuntu)
4. Détection Wazuh (alertes multiples)
5. Réponse : isoler VM, documenter IOCs

**Depuis Kali** :
```bash
# Étape 1 : Reconnaissance
nmap -A 10.0.0.0/24

# Étape 2 : Brute force
hydra -l root -P /tmp/pass.txt ssh://10.0.0.101

# Étape 3 : Simulation "infection" (si réussite)
# En réalité, on simule juste la détection