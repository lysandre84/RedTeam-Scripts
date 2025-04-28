<<<<<<< HEAD
﻿# RedTeam-Scripts
Ce dÃ©pÃ´t contient des fichiers liÃ©s Ã  RedTeam-Scripts. Il est actuellement privÃ©.
ðŸš€ **Mise Ã  jour en cours...**
=======
# RedTeam-Scripts

Ensemble de scripts et outils pour opérations Red Team et tests d’intrusion.

## Structure du projet

- **Scripts/** : scripts (Bash, PowerShell, Python, Go)
- **Docs/** : documentation des techniques
- **reports/** : rapports d’opérations
- **Tools/** : outils tiers pré-packagés (ne pas modifier)
- **requirements.txt** : dépendances Python

## Prérequis

- Python 3.8+
- Go 1.16+
- PowerShell 5.1+
- Bash

Installer les dépendances Python :
```bash
pip install -r requirements.txt
```

## Utilisation

### Bash
```bash
bash Scripts/Bash/port_sweep.sh --range 10.0.0.0/24
```

### Python
```bash
python3 Scripts/Python/password_cracker.py --hashes hashes.txt
```

### PowerShell
```powershell
.\Scripts\Powershell/escape_powershell.ps1 -Command "whoami"
```

### Go
```bash
go run Scripts/Go/lateral_move.go --hosts hosts.txt
```

## CI & Qualité

- Tests Python avec pytest
- Linting Bash & Go
- Workflow GitHub Actions dans `.github/workflows/ci.yml`

## Licence

MIT. Voir [LICENSE](LICENSE).
>>>>>>> 72d1a4b (Initial commit: RedTeam-Scripts)
