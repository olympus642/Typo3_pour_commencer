# Annexes

## Création de liens symboliques sous Windows

[On considère que le répertoire « source » est au même niveau d’arborescence que le répertoire contenant le site]

```bash
	mklink /D typo3_src ..\source
	mklink index.php typo3_src\index.php
	mklink /D typo3 typo3_src\typo3
	copy typo3_src\_.htaccess .htaccess
```
[le drapeau /D indique qu’il s’agit d’un lien sur un répertoire (D = directory)]

## Création de liens symboliques sur un serveur mutualisé

Il faut pour cela déposer et exécuter les fichiers php suivants dans le répertoire d’installation du site :

```php
<?php
// fichier lien1.php
	system('ln -s ../source typo3_src', $retval);
?>
```

```php
<?php
// fichier lien2.php
	system('ln -s typo3_src/index.php index.php', $retval);
?>
```

```php
<?php
// fichier lien3.php
	system('ln -s typo3_src/typo3 typo3', $retval);
?>
```

```php
<?php
// fichier copy.php
	system('cp typo3_src/_.htaccess .htaccess', $retval);
?>
```

