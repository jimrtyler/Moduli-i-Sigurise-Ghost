# 👻 Moduli i Sigurisë Ghost
**Mjeti i Fortifikimit të Sigurisë Windows & Azure të Bazuar në PowerShell**

> **Fortifikimi proaktiv i sigurisë për pikat fundore Windows dhe ambientet Azure.** Ghost ofron funksione fortifikimi të bazuara në PowerShell që mund të ndihmojnë në reduktimin e vektorëve të zakonshëm të sulmeve duke çaktivizuar shërbimet dhe protokollet e panevojshme.

## ⚠️ Mohimet e Rëndësishme

**TESTIMI I KËRKUAR**: Gjithmonë testoni Ghost në ambiente jo-produksioni së pari. Çaktivizimi i shërbimeve mund të ndikojë në funksionet legjitimate të biznesit.

**ASNJË GARANCI**: Edhe pse Ghost synon vektorët e zakonshëm të sulmeve, asnjë mjet sigurie nuk mund të parandalojë të gjitha sulmet. Ky është një komponent i një strategjie sigurie të plotë.

**NDIKIMI OPERACIONAL**: Disa funksione mund të ndikojnë në funksionalitetin e sistemit. Rishikoni çdo cilësim me kujdes para zbatimit.

**VLERËSIMI PROFESIONAL**: Për ambientet e produksionit, konsultohuni me profesionistët e sigurisë për të siguruar që cilësimet të jenë në përputhje me nevojat e organizatës suaj.

## 📊 Peizazhi i Sigurisë

Dëmet e ransomware arritën **$57 miliardë në 2025**, me kërkime që tregojnë se shumë sulme të suksesshme shfrytëzojnë shërbimet bazë Windows dhe konfigurimimet e gabuara. Vektorët e zakonshëm të sulmeve përfshijnë:

- **90% e incidenteve të ransomware** përfshijnë shfrytëzimin e RDP
- **Dobësitë e SMBv1** mundësuan sulme si WannaCry dhe NotPetya
- **Makrot e dokumenteve** mbeten një metodë kryesore e dorëzimit të malware
- **Sulmet e bazuara në USB** vazhdojnë të synojnë rrjetet e izoluara nga ajri
- **Keqpërdorimi i PowerShell** ka rritur ndjeshëm në vitet e fundit

## 🛡️ Funksionet e Sigurisë Ghost

Ghost ofron **16 funksione fortifikimi Windows** plus **integrimi i sigurisë Azure**:

### Fortifikimi i Pikave Fundore Windows

| Funksioni | Qëllimi | Konsiderata |
|-----------|---------|-------------|
| `Set-RDP` | Menaxhon qasjen Remote Desktop | Mund të ndikojë në administrimin në distancë |
| `Set-SMBv1` | Kontrollon protokollin SMB legacy | E nevojshme për sistemet shumë të vjetra |
| `Set-AutoRun` | Kontrollon AutoPlay/AutoRun | Mund të ndikojë në lehtësinë e përdoruesit |
| `Set-USBStorage` | Kufizon pajisjet e depozitimit USB | Mund të ndikojë në përdorimin legjitim të USB |
| `Set-Macros` | Kontrollon ekzekutimin e makrove Office | Mund të ndikojë në dokumentet e aktivizuara me makro |
| `Set-PSRemoting` | Menaxhon PowerShell remoting | Mund të ndikojë në menaxhimin në distancë |
| `Set-WinRM` | Kontrollon Windows Remote Management | Mund të ndikojë në administrimin në distancë |
| `Set-LLMNR` | Menaxhon protokollin e zgjidhjes së emrave | Zakonisht i sigurt për çaktivizim |
| `Set-NetBIOS` | Kontrollon NetBIOS mbi TCP/IP | Mund të ndikojë në aplikacionet legacy |
| `Set-AdminShares` | Menaxhon ndarjet administrative | Mund të ndikojë në qasjen në skedarë në distancë |
| `Set-Telemetry` | Kontrollon mbledhjen e të dhënave | Mund të ndikojë në aftësitë diagnostike |
| `Set-GuestAccount` | Menaxhon llogarinë Guest | Zakonisht i sigurt për çaktivizim |
| `Set-ICMP` | Kontrollon përgjigjet ping | Mund të ndikojë në diagnostikën e rrjetit |
| `Set-RemoteAssistance` | Menaxhon Remote Assistance | Mund të ndikojë në operacionet e help desk |
| `Set-NetworkDiscovery` | Kontrollon zbulimin e rrjetit | Mund të ndikojë në shfletimin e rrjetit |
| `Set-Firewall` | Menaxhon Windows Firewall | Kritik për sigurinë e rrjetit |

### Siguria e Cloud Azure

| Funksioni | Qëllimi | Kërkesat |
|-----------|---------|----------|
| `Set-AzureSecurityDefaults` | Aktivizon sigurinë bazë Azure AD | Lejet Microsoft Graph |
| `Set-AzureConditionalAccess` | Konfiguron politikat e qasjes | Licencimi Azure AD P1/P2 |
| `Set-AzurePrivilegedUsers` | Auditon llogaritë e privilegjuara | Lejet Global Admin |

### Opsionet e Zbatimit të Ndërmarrjes

| Metoda | Rasti i Përdorimit | Kërkesat |
|--------|---------------------|----------|
| **Ekzekutimi i Drejtpërdrejtë** | Testimi, ambiente të vogla | Të drejtat admin lokale |
| **Group Policy** | Ambientet e domenit | Admin domain, menaxhimi GP |
| **Microsoft Intune** | Pajisjet e menaxhuara cloud | Licencimi Intune, Graph API |

## 🚀 Fillimi i Shpejtë

### Vlerësimi i Sigurisë
```powershell
# Ngarko modulin Ghost
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1

# Kontrollo qëndrimin aktual të sigurisë
Get-Ghost
```

### Fortifikimi Bazë (Testo Së Pari)
```powershell
# Fortifikimi thelbësor - testo në ambient laboratori së pari
Set-Ghost -SMBv1 -AutoRun -Macros

# Rishiko ndryshimet
Get-Ghost
```

### Zbatimi i Ndërmarrjes
```powershell
# Zbatimi Group Policy (ambientet e domenit)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Zbatimi Intune (pajisjet e menaxhuara cloud)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Metodat e Instalimit

### Opsioni 1: Shkarkimi i Drejtpërdrejtë (Testimi)
```powershell
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1
```

### Opsioni 2: Instalimi i Modulit
```powershell
# Instalo nga PowerShell Gallery (kur të jetë i disponueshëm)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Opsioni 3: Zbatimi i Ndërmarrjes
```powershell
# Kopjo në vendndodhjen e rrjetit për zbatimin Group Policy
# Konfiguro skriptet PowerShell Intune për zbatimin cloud
```

## 💼 Shembuj Rastkesh Përdorimi

### Biznesi i Vogël
```powershell
# Mbrojtja bazë me ndikim minimal
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Kujdesi Shëndetësor Ambienti
```powershell
# Fortifikimi i fokusuar HIPAA
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Shërbimet Financiare
```powershell
# Konfigurimi i sigurisë së lartë
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Organizata Cloud-First
```powershell
# Zbatimi i menaxhuar Intune
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Detajet e Funksioneve

### Funksionet Kryesore të Fortifikimit

#### Shërbimet e Rrjetit
- **RDP**: Bllokon qasjen remote desktop ose randomize portit
- **SMBv1**: Çaktivizon protokollin e ndarjes së skedarëve legacy
- **ICMP**: Parandalon përgjigjet ping për njohjen
- **LLMNR/NetBIOS**: Bllokon protokollet e zgjidhjes së emrave legacy

#### Aplikacionet Sigurie
- **Makrot**: Çaktivizon ekzekutimin e makrove në aplikacionet Office
- **AutoRun**: Parandalon ekzekutimin automatik nga media e heqshme

#### Menaxhimi në Distancë
- **PSRemoting**: Çaktivizon sesionet e largëta PowerShell
- **WinRM**: Ndal Windows Remote Management
- **Remote Assistance**: Bllokon lidhjet e ndihmës së largët

#### Kontrolli i Qasjes
- **Admin Shares**: Çaktivizon ndarjet C$, ADMIN$
- **Guest Account**: Çaktivizon qasjen e llogarisë Guest
- **USB Storage**: Kufizon përdorimin e pajisjeve USB

### Integrimi Azure
```powershell
# Lidhu me tenant Azure
Connect-AzureGhost -Interactive

# Aktivizo defaults sigurie
Set-AzureSecurityDefaults -Enable

# Konfiguro qasjen e kushtëzuar
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Audito përdoruesit e privilegjuar
Set-AzurePrivilegedUsers -AuditOnly
```

### Integrimi Intune (I ri në v2)
```powershell
# Lidhu me Intune
Connect-IntuneGhost -Interactive

# Zbato përmes politikave Intune
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Konsiderata të Rëndësishme

### Kërkesat e Testimit
- **Ambienti i Laboratorit**: Testo të gjitha cilësimet në ambient të izoluar së pari
- **Zbatimi i Fazuar**: Zbato gradualisht për të identifikuar problemet
- **Plani i Kthimit**: Sigurohu që mund t'i kthesh ndryshimet nëse nevojitet
- **Dokumentimi**: Shëno cilët cilësime funksionojnë për ambientin tënd

### Ndikimi i Mundshëm
- **Produktiviteti i Përdoruesit**: Disa cilësime mund të ndikojnë në workflow e përditshëm
- **Aplikacionet Legacy**: Sistemet e vjetra mund të kërkojnë protokolle të caktuara
- **Qasja në Distancë**: Konsidero ndikimin në administrimin legjitim në distancë
- **Proceset e Biznesit**: Verifiko që cilësimet nuk thyejnë funksionet kritike

### Kufizimet e Sigurisë
- **Mbrojtja në Thellësi**: Ghost është një shtresë sigurie, jo një zgjidhje e plotë
- **Menaxhimi i Vazhdueshëm**: Siguria kërkon monitorim dhe përditësime të vazhdueshme
- **Trajnimi i Përdoruesit**: Kontrollet teknike duhet të çiftohen me ndërgjegjësimin e sigurisë
- **Evolucioni i Kërcënimeve**: Metodat e reja të sulmeve mund të anashkalojnë mbrojtjen aktuale

## 🎯 Skenarët Shembull të Sulmeve

Ndërsa Ghost synon vektorët e zakonshëm të sulmeve, parandalimi specifik varet nga implementimi dhe testimi i duhur:

### Sulmet Stili WannaCry
- **Reduktimi**: `Set-Ghost -SMBv1` çaktivizon protokollin e dobët
- **Konsiderata**: Sigurohu që asnjë sistem legacy nuk kërkon SMBv1

### Ransomware të Bazuar në RDP
- **Reduktimi**: `Set-Ghost -RDP` bllokon qasjen remote desktop
- **Konsiderata**: Mund të kërkojë metoda alternative qasje në distancë

### Malware të Bazuar në Dokumente
- **Reduktimi**: `Set-Ghost -Macros` çaktivizon ekzekutimin e makrove
- **Konsiderata**: Mund të ndikojë në dokumentet legjitimë të aktivizuara me makro

### Kërcënimet e Dërguara me USB
- **Reduktimi**: `Set-Ghost -USBStorage -AutoRun` kufizon funksionalitetin USB
- **Konsiderata**: Mund të ndikojë në përdorimin legjitim të pajisjeve USB

## 🏢 Veçoritë e Ndërmarrjes

### Mbështetja e Group Policy
```powershell
# Apliko cilësimet përmes regjistrit Group Policy
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Cilësimet aplikohen në të gjithë domenin pas rifreskimit GP
gpupdate /force
```

### Integrimi Microsoft Intune
```powershell
# Krijo politika Intune për cilësimet Ghost
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Politikat zbehen automatikisht në pajisjet e menaxhuara
```

### Raportimi i Pajtueshmërisë
```powershell
# Gjenero raport vlerësimi sigurie
Get-Ghost | Export-Csv -Path "SecurityAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Raport qëndrimi sigurie Azure
Get-AzureGhost | Out-File "AzureSecurityReport.txt"
```

## 📚 Praktikat më të Mira

### Para-Zbatimit
1. **Dokumento Gjendjen Aktuale**: Ekzekuto `Get-Ghost` para ndryshimeve
2. **Testo Thellësisht**: Valido në ambient jo-produksioni
3. **Planifiko Kthimin**: Dije si t'i kthesh çdo cilësim
4. **Rishikimi i Palëve të Interesuara**: Sigurohu që njësitë e biznesit i aprovuan ndryshimet

### Gjatë Zbatimit
1. **Qasja e Fazuar**: Zbato në grupet pilot së pari
2. **Monitorimi i Ndikimit**: Vëzhgo për ankesa përdoruesish ose probleme sistemi
3. **Dokumento Problemet**: Shëno çdo problem për referencë të ardhshme
4. **Komuniko Ndryshimet**: Informo përdoruesit për përmirësimet e sigurisë

### Pas-Zbatimit
1. **Vlerësimi i Rregullt**: Ekzekuto periodikisht `Get-Ghost` për të verifikuar cilësimet
2. **Përditëso Dokumentimin**: Mbaj konfiguracionet e sigurisë të përditësuara
3. **Rishiko Efektivitetin**: Monitorimi për incidente sigurie
4. **Përmirësimi i Vazhdueshëm**: Rregullo cilësimet bazuar në peizazhin e kërcënimeve

## 🔧 Zgjidhja e Problemeve

### Problemet e Zakonshme
- **Gabimet e Lejeve**: Sigurohu sesion PowerShell të ngritur
- **Varësitë e Shërbimeve**: Disa shërbime mund të kenë varësi
- **Përputhshmëria e Aplikacioneve**: Testo me aplikacionet e biznesit
- **Lidhja e Rrjetit**: Verifiko që qasja në distancë funksionon ende

### Opsionet e Rikuperimit
```powershell
# Riaktivizo shërbimet specifike nëse nevojitet
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Rreth Autorit

**Jim Tyler** - Microsoft MVP për PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10,000+ abonentë)
- **Buletini**: [PowerShell.News](https://powershell.news) - Inteligjenca e sigurisë javore
- **Autori**: "PowerShell for Systems Engineers"
- **Përvoja**: Dekada automatizimi PowerShell dhe sigurie Windows

## 📄 Licensa & Mohimi

### Licensa MIT
Ghost ofrohet nën Licensën MIT për përdorim, modifikim dhe shpërndarje falas.

### Mohimi i Sigurisë
- **Asnjë Garanci**: Ghost ofrohet "si është" pa garanci të çdo lloji
- **Testimi i Kërkuar**: Gjithmonë testo në ambiente jo-produksioni së pari
- **Udhëzimi Profesional**: Konsultohuni me profesionistët e sigurisë për zbatimet e produksionit
- **Ndikimi Operacional**: Autorët nuk janë përgjegjës për çdo prishje operacionale
- **Siguria e Plotë**: Ghost është një komponent i një strategjie sigurie të plotë

### Mbështetja
- **Problemet GitHub**: [Raporto gabime ose kërko veçori](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentimi**: Përdor `Get-Help <function> -Full` për ndihmë të detajuar
- **Komuniteti**: Forumet e komunitetit PowerShell dhe sigurisë

---

**🔐 Forco qëndrimin tënd të sigurisë me Ghost - por gjithmonë testo së pari.**

```powershell
# Fillo me vlerësim, jo me supozime
Get-Ghost
```

**⭐ Yje këtë repository nëse Ghost ndihmon në përmirësimin e qëndrimit tënd të sigurisë!**