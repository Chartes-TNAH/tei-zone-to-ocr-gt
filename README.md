# tei-zone-to-ocr-gt

## Installation

*À compléter par les étudiant-e-s*

## Description générale

L'outil tei-zone-to-ocr permet, à partir d'un fichier TEI usant de `<zone>` et des fichiers images liés, de générer des fichiers d'entraînements pour [Kraken](https://github.com/kba/kraken).

L'outil prend les options suivantes :

`cli.py to-kraken input output --seg //seg --seg-to-zone //zone[@id=./@facs] --zone-to-image ../graphic/@url`
- `input` : fichier XML TEI
- `output` : dossier de sortie
- `--seg` : XPATH permettant d'aller aux conteneurs de texte transcrit
- `--seg-to-zone` : XPath permettant d'aller du conteneur de texte à la zone image
- `--zone-to-image` : XPath permettant d'aller de l'image

Il génère un dossier `output` contenant:
- les images complètes binarisées par kraken.
	- Une alerte sera émise si l'image est plus petite que 600*600 (Mauvais pour de l'OCR).
- les fichiers json de zonage par rapport à ces images binarisées.
- un dossier `gt` (pour *ground truth*) comprenant
	- un fichier `[LINE].txt` par ligne de texte transcrit
	- un fichier `[LINE].png` par ligne de texte transcrit correspondant uniquement à la zone de transcription.
