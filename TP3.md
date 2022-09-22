**MOREL Loïc 3ICS**

# 1. Table des matières

- [1. Table des matières](#1-table-des-matières)
- [Exercice 1. Gestion des utilisateurs et des groupes](#exercice-1-gestion-des-utilisateurs-et-des-groupes)
  - [1. Utilisez la commande groupadd pour créer deux groupes dev et infra](#1-utilisez-la-commande-groupadd-pour-créer-deux-groupes-dev-et-infra)
  - [2. Créez ensuite 4 utilisateurs alice, bob, charlie, dave avec la commande useradd, en demandant lacréation de leur dossier personnel et avec bash pour shell](#2-créez-ensuite-4-utilisateurs-alice-bob-charlie-dave-avec-la-commande-useradd-en-demandant-lacréation-de-leur-dossier-personnel-et-avec-bash-pour-shell)
  - [3. Ajoutez les utilisateurs dans les groupes créés :](#3-ajoutez-les-utilisateurs-dans-les-groupes-créés-)
  - [4. Donnez deux moyens d’aﬀicher les membres de infra](#4-donnez-deux-moyens-daﬀicher-les-membres-de-infra)
  - [5. Faites de dev le groupe propriétaire des répertoires /home/alice et /home/bob et de infra le groupe propriétaire de /home/charlie et /home/dave](#5-faites-de-dev-le-groupe-propriétaire-des-répertoires-homealice-et-homebob-et-de-infra-le-groupe-propriétaire-de-homecharlie-et-homedave)
  - [6. Remplacez le groupe primaire des utilisateurs :](#6-remplacez-le-groupe-primaire-des-utilisateurs-)
  - [7. Créez deux répertoires /home/dev et /home/infra pour le contenu commun aux membres de chaque groupe, et mettez en place les permissions leur permettant d’écrire dans ces dossiers.](#7-créez-deux-répertoires-homedev-et-homeinfra-pour-le-contenu-commun-aux-membres-de-chaque-groupe-et-mettez-en-place-les-permissions-leur-permettant-décrire-dans-ces-dossiers)
  - [8. Comment faire pour que, dans ces dossiers, seul le propriétaire d’un fichier ait le droit de renommer ou supprimer ce fichier ?](#8-comment-faire-pour-que-dans-ces-dossiers-seul-le-propriétaire-dun-fichier-ait-le-droit-de-renommer-ou-supprimer-ce-fichier-)
  - [9. Pouvez-vous ouvrir une session en tant que alice ? Pourquoi ?](#9-pouvez-vous-ouvrir-une-session-en-tant-que-alice--pourquoi-)
  - [10. Activez le compte de l’utilisateur alice et vérifiez que vous pouvez désormais vous connecter avec son compte.](#10-activez-le-compte-de-lutilisateur-alice-et-vérifiez-que-vous-pouvez-désormais-vous-connecter-avec-son-compte)
  - [11. Comment obtenir l’uid et le gid de alice ?](#11-comment-obtenir-luid-et-le-gid-de-alice-)
  - [12. Quelle commande permet de retrouver l’utilisateur dont l’uid est 1003 ?](#12-quelle-commande-permet-de-retrouver-lutilisateur-dont-luid-est-1003-)
  - [13. Quel est l’id du groupe dev ?](#13-quel-est-lid-du-groupe-dev-)
  - [14. Quel groupe a pour gid 1002 ? ( Rien n’empêche d’avoir un groupe dont le nom serait 1002...)](#14-quel-groupe-a-pour-gid-1002---rien-nempêche-davoir-un-groupe-dont-le-nom-serait-1002)
  - [15. Retirez l’utilisateur charlie du groupe infra. Que se passe-t-il ? Expliquez.](#15-retirez-lutilisateur-charlie-du-groupe-infra-que-se-passe-t-il--expliquez)
  - [16. Modifiez le compte de dave de sorte que :](#16-modifiez-le-compte-de-dave-de-sorte-que-)
  - [17. Quel est l’interpréteur de commandes (Shell) de l’utilisateur root ?](#17-quel-est-linterpréteur-de-commandes-shell-de-lutilisateur-root-)
  - [18. Si vous regardez la liste des comptes présents sur la machine, vous verrez qu’il en existe ### un nommé](#18-si-vous-regardez-la-liste-des-comptes-présents-sur-la-machine-vous-verrez-quil-en-existe--un-nommé)
  - [nobody. A quoi correspond-il ?](#nobody-a-quoi-correspond-il-)
  - [19. Par défaut, combien de temps la commande sudo conserve-t-elle votre mot de passe en mémoire ? Quelle commande permet de forcer sudo à oublier votre mot de passe ?](#19-par-défaut-combien-de-temps-la-commande-sudo-conserve-t-elle-votre-mot-de-passe-en-mémoire--quelle-commande-permet-de-forcer-sudo-à-oublier-votre-mot-de-passe-)
- [Exercice 2. Gestion des permissions](#exercice-2-gestion-des-permissions)
  - [1. Dans votre $HOME, créez un dossier test, et dans ce dossier un fichier fichier contenant quelques lignes de texte. Quels sont les droits sur test et fichier ?](#1-dans-votre-home-créez-un-dossier-test-et-dans-ce-dossier-un-fichier-fichier-contenant-quelques-lignes-de-texte-quels-sont-les-droits-sur-test-et-fichier-)
  - [2. Retirez tous les droits sur ce fichier (même pour vous), puis essayez de le modifier et de l’aﬀicher en tant que root. Conclusion ?](#2-retirez-tous-les-droits-sur-ce-fichier-même-pour-vous-puis-essayez-de-le-modifier-et-de-laﬀicher-en-tant-que-root-conclusion-)
  - [3. Redonnez vous les droits en écriture et exécution sur fichier puis exécutez la commande echo "echo Hello" > fichier. On a vu lors des TP précédents que cette commande remplace le contenu d’un fichier s’il existe déjà. Que peut-on dire au sujet des droits ?](#3-redonnez-vous-les-droits-en-écriture-et-exécution-sur-fichier-puis-exécutez-la-commande-echo-echo-hello--fichier-on-a-vu-lors-des-tp-précédents-que-cette-commande-remplace-le-contenu-dun-fichier-sil-existe-déjà-que-peut-on-dire-au-sujet-des-droits-)
  - [4. Essayez d’exécuter le fichier. Est-ce que cela fonctionne ? Et avec sudo ? Expliquez.](#4-essayez-dexécuter-le-fichier-est-ce-que-cela-fonctionne--et-avec-sudo--expliquez)
  - [5. Placez-vous dans le répertoire test, et retirez-vous le droit en lecture pour ce répertoire. Listez le contenu du répertoire, puis exécutez ou aﬀichez le contenu du fichier fichier. Qu’en déduisez-vous ? Rétablissez le droit en lecture sur test.](#5-placez-vous-dans-le-répertoire-test-et-retirez-vous-le-droit-en-lecture-pour-ce-répertoire-listez-le-contenu-du-répertoire-puis-exécutez-ou-aﬀichez-le-contenu-du-fichier-fichier-quen-déduisez-vous--rétablissez-le-droit-en-lecture-sur-test)
  - [6. Créez dans test un fichier nouveau ainsi qu’un répertoire sstest. Retirez au fichier nouveau et au répertoire test le droit en écriture. Tentez de modifier le fichier nouveau. Rétablissez ensuite le droit en écriture au répertoire test. Tentez de modifier le fichier nouveau, puis de le supprimer. Que pouvez-vous déduire de toutes ces manipulations ?](#6-créez-dans-test-un-fichier-nouveau-ainsi-quun-répertoire-sstest-retirez-au-fichier-nouveau-et-au-répertoire-test-le-droit-en-écriture-tentez-de-modifier-le-fichier-nouveau-rétablissez-ensuite-le-droit-en-écriture-au-répertoire-test-tentez-de-modifier-le-fichier-nouveau-puis-de-le-supprimer-que-pouvez-vous-déduire-de-toutes-ces-manipulations-)
  - [7. Positionnez vous dans votre répertoire personnel, puis retirez le droit en exécution du répertoire test.Tentez de créer, supprimer, ou modifier un fichier dans le répertoire test, de vous y déplacer, d’en lister le contenu, etc...Qu’en déduisez vous quant au sens du droit en exécution pour les répertoires ?](#7-positionnez-vous-dans-votre-répertoire-personnel-puis-retirez-le-droit-en-exécution-du-répertoire-testtentez-de-créer-supprimer-ou-modifier-un-fichier-dans-le-répertoire-test-de-vous-y-déplacer-den-lister-le-contenu-etcquen-déduisez-vous-quant-au-sens-du-droit-en-exécution-pour-les-répertoires-)
  - [8. Rétablissez le droit en exécution du répertoire test. Positionnez vous dans ce répertoire et retirez lui à nouveau le droit d’exécution. Essayez de créer, supprimer et modifier un fichier dans le répertoire test, de vous déplacer dans ssrep, de lister son contenu. Qu’en concluez-vous quant à l’influence des droits que l’on possède sur le répertoire courant ? Peut-on retourner dans le répertoire parent avec ”cd ..” ? Pouvez-vous donner une explication ?](#8-rétablissez-le-droit-en-exécution-du-répertoire-test-positionnez-vous-dans-ce-répertoire-et-retirez-lui-à-nouveau-le-droit-dexécution-essayez-de-créer-supprimer-et-modifier-un-fichier-dans-le-répertoire-test-de-vous-déplacer-dans-ssrep-de-lister-son-contenu-quen-concluez-vous-quant-à-linfluence-des-droits-que-lon-possède-sur-le-répertoire-courant--peut-on-retourner-dans-le-répertoire-parent-avec-cd---pouvez-vous-donner-une-explication-)
  - [9. Rétablissez le droit en exécution du répertoire test. Attribuez au fichier fichier les droits suﬀisants pour qu’une autre personne de votre groupe puisse y accéder en lecture, mais pas en écriture.](#9-rétablissez-le-droit-en-exécution-du-répertoire-test-attribuez-au-fichier-fichier-les-droits-suﬀisants-pour-quune-autre-personne-de-votre-groupe-puisse-y-accéder-en-lecture-mais-pas-en-écriture)
  - [10. Définissez un umask très restrictif qui interdit à quiconque à part vous l’accès en lecture ou en écriture, ainsi que la traversée de vos répertoires. Testez sur un nouveau fichier et un nouveau répertoire.](#10-définissez-un-umask-très-restrictif-qui-interdit-à-quiconque-à-part-vous-laccès-en-lecture-ou-en-écriture-ainsi-que-la-traversée-de-vos-répertoires-testez-sur-un-nouveau-fichier-et-un-nouveau-répertoire)
  - [11. Définissez un umask très permissif qui autorise tout le monde à lire vos fichiers et traverser vos réper-toires, mais n’autorise que vous à écrire. Testez sur un nouveau fichier et un nouveau répertoire.](#11-définissez-un-umask-très-permissif-qui-autorise-tout-le-monde-à-lire-vos-fichiers-et-traverser-vos-réper-toires-mais-nautorise-que-vous-à-écrire-testez-sur-un-nouveau-fichier-et-un-nouveau-répertoire)
  - [12. Définissez un umask équilibré qui vous autorise un accès complet et autorise un accès en lecture aux membres de votre groupe. Testez sur un nouveau fichier et un nouveau répertoire.](#12-définissez-un-umask-équilibré-qui-vous-autorise-un-accès-complet-et-autorise-un-accès-en-lecture-aux-membres-de-votre-groupe-testez-sur-un-nouveau-fichier-et-un-nouveau-répertoire)
  - [13. Transcrivez les commandes suivantes de la notation classique à la notation octale ou vice-versa (vous pourrez vous aider de la commande stat pour valider vos réponses) :](#13-transcrivez-les-commandes-suivantes-de-la-notation-classique-à-la-notation-octale-ou-vice-versa-vous-pourrez-vous-aider-de-la-commande-stat-pour-valider-vos-réponses-)
  - [14. Aﬀichez les droits sur le programme passwd. Que remarquez-vous ? En aﬀichant les droits du fichier /etc/passwd, pouvez-vous justifier les permissions sur le programme passwd ?](#14-aﬀichez-les-droits-sur-le-programme-passwd-que-remarquez-vous--en-aﬀichant-les-droits-du-fichier-etcpasswd-pouvez-vous-justifier-les-permissions-sur-le-programme-passwd-)
- [Pour les plus rapides :](#pour-les-plus-rapides-)
  - [15. Access Control Lists (ACL) : suivez le tutoriel de cette page : https://doc.ubuntu-fr.org/acl.](#15-access-control-lists-acl--suivez-le-tutoriel-de-cette-page--httpsdocubuntu-frorgacl)
  - [16. Quotas disques : suivez le tutoriel de cette page : https://doc.ubuntu-fr.org/quota.](#16-quotas-disques--suivez-le-tutoriel-de-cette-page--httpsdocubuntu-frorgquota)

# Exercice 1. Gestion des utilisateurs et des groupes

## 1. Utilisez la commande groupadd pour créer deux groupes dev et infra

```console
User@localhost:~$ sudo groupadd dev
User@localhost:~$ sudo groupadd infra
```

## 2. Créez ensuite 4 utilisateurs alice, bob, charlie, dave avec la commande useradd, en demandant lacréation de leur dossier personnel et avec bash pour shell

```console
User@localhost:~$ sudo useradd -m alice
User@localhost:~$ sudo usermod --shell /bin/bash alice
User@localhost:~$ sudo useradd -m bob
User@localhost:~$ sudo usermod --shell /bin/bash bob
User@localhost:~$ sudo useradd -m charlie
User@localhost:~$ sudo usermod --shell /bin/bash charlie
User@localhost:~$ sudo useradd -m dave
User@localhost:~$ sudo usermod --shell /bin/bash dave
```

## 3. Ajoutez les utilisateurs dans les groupes créés :

- alice, bob, dave dans dev
- bob, charlie, dave dans infra

```console
User@localhost:~$ sudo usermod -aG dev alice
User@localhost:~$ sudo usermod -aG dev bob
User@localhost:~$ sudo usermod -aG dev dave
User@localhost:~$ sudo usermod -aG infra bob
User@localhost:~$ sudo usermod -aG infra charlie
User@localhost:~$ sudo usermod -aG infra dave
```

## 4. Donnez deux moyens d’aﬀicher les membres de infra

```console
User@localhost:~$ getent group infra
infra:x:1003:bob,charlie,dave
```

```console
User@localhost:~$ grep infra /etc/group
infra:x:1003:bob,charlie,dave
```

## 5. Faites de dev le groupe propriétaire des répertoires /home/alice et /home/bob et de infra le groupe propriétaire de /home/charlie et /home/dave

```console
User@localhost:~$ sudo chown :dev alice/
User@localhost:~$ sudo chown :dev bob/
User@localhost:~$ sudo chown :infra charlie/
User@localhost:~$ sudo chown :infra dave/
User@localhost:~$ ll

total 0
drwxr-xr-x  2 alice   dev       6 Sep 22 06:27 alice/
drwxr-xr-x  2 bob     dev       6 Sep 22 06:27 bob/
drwxr-xr-x  2 charlie infra     6 Sep 22 06:27 charlie/
drwxr-xr-x  2 dave    infra     6 Sep 22 06:27 dave/
```

## 6. Remplacez le groupe primaire des utilisateurs :

- dev pour alice et bob
- infra pour charlie et dave

```console
User@localhost:~$ sudo usermod alice -g dev
User@localhost:~$ id alice
uid=1002(alice) gid=1002(dev) groups=1002(dev)

User@localhost:~$ sudo usermod bob -g dev
User@localhost:~$ id bob
uid=1003(bob) gid=1002(dev) groups=1002(dev)

User@localhost:~$ sudo usermod charlie -g infra
User@localhost:~$ id charlie
uid=1004(charlie) gid=1003(infra) groups=1003(infra)

User@localhost:~$ sudo usermod dave -g infra
User@localhost:~$ id dave
uid=1005(dave) gid=1003(infra) groups=1003(infra)
```

## 7. Créez deux répertoires /home/dev et /home/infra pour le contenu commun aux membres de chaque groupe, et mettez en place les permissions leur permettant d’écrire dans ces dossiers.

```console
User@localhost:~$ sudo chown :dev /home/dev; sudo chmod g+w /home/dev/
User@localhost:~$ sudo chown :infra /home/infra; sudo chmod g+w /home/infra/
User@localhost:~$ ll /home

drwxrwxr-x  2 root    dev       6 Sep 22 06:46 dev/
drwxrwxr-x  2 root    infra     6 Sep 22 06:46 infra/
```

## 8. Comment faire pour que, dans ces dossiers, seul le propriétaire d’un fichier ait le droit de renommer ou supprimer ce fichier ?

```console
User@localhost:~$ sudo chmod 700 /home/bob
User@localhost:~$ ll /home

drwx------  2 bob     dev       6 Sep 22 06:27 bob/
```

## 9. Pouvez-vous ouvrir une session en tant que alice ? Pourquoi ?

```console
User@localhost:~$ su alice
Password:
```

On ne peut pas car on a pas le mot de passe d'alice

## 10. Activez le compte de l’utilisateur alice et vérifiez que vous pouvez désormais vous connecter avec son compte.

```console
User@localhost:~$ sudo passwd alice
New password:
Retype new password:
passwd: password updated successfully
```

On peux ce connecter un fois le mot de passe crée

```console
User@localhost:~$ su - alice
Password:
alice@localhost:~$
```

## 11. Comment obtenir l’uid et le gid de alice ?

```console
User@localhost:~$ id alice
uid=1002(alice) gid=1002(dev) groups=1002(dev)
```

## 12. Quelle commande permet de retrouver l’utilisateur dont l’uid est 1003 ?

```console
User@localhost:~$ id 1003
uid=1003(bob) gid=1002(dev) groups=1002(dev)
```

## 13. Quel est l’id du groupe dev ?

```console
User@localhost:~$ grep ^dev /etc/group
dev:x:1002:alice
```

## 14. Quel groupe a pour gid 1002 ? ( Rien n’empêche d’avoir un groupe dont le nom serait 1002...)

Le group `dev` a pour gid `1002`

## 15. Retirez l’utilisateur charlie du groupe infra. Que se passe-t-il ? Expliquez.

```console
User@localhost:~$ sudo gpasswd -d charlie infra
Removing user charlie from group infra
User@localhost:~$  id charlie
uid=1004(charlie) gid=1003(infra) groups=1003(infra)
```

L'utilisateur charlie n'est pas enlever du groupe infra car le group infra est le goupe primaire pour l'utilisateur charlie.

## 16. Modifiez le compte de dave de sorte que :

- il expire au 1er juin 2021

```console
User@localhost:~$ sudo chage -E 2021-06-01 dave
```

- il faut changer de mot de passe avant 90 jours

```console
User@localhost:~$ sudo chage -M 90 dave
```

- il faut attendre 5 jours pour modifier un mot de passe

```console
User@localhost:~$ sudo chage -m 5 dave
```

- l’utilisateur est averti 14 jours avant l’expiration de son mot de passe

```console
User@localhost:~$ sudo chage -W 14 dave
```

- le compte sera bloqué 30 jours après expiration du mot de passe

```console
User@localhost:~$ sudo chage -I 30 dave
```

```console
User@localhost:~$ sudo chage -l dave
Last password change                                    : Sep 22, 2022
Password expires                                        : Dec 21, 2022
Password inactive                                       : Jan 20, 2023
Account expires                                         : Jun 01, 2021
Minimum number of days between password change          : 5
Maximum number of days between password change          : 90
Number of days of warning before password expires       : 14
```

## 17. Quel est l’interpréteur de commandes (Shell) de l’utilisateur root ?

```console
User@localhost:~$ echo $SHELL
/bin/bash
```

## 18. Si vous regardez la liste des comptes présents sur la machine, vous verrez qu’il en existe ### un nommé

```console
User@localhost:~$ grep nobody /etc/passwdetc/passwd
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
```

L'utilisateur nobody est le nom conventionnel d'un compte d'utilisateur à qui aucun fichier n'appartient, qui n'est dans aucun groupe qui a des privilèges et dont les seules possibilités sont celles que tous les "autres utilisateurs"

## nobody. A quoi correspond-il ?

## 19. Par défaut, combien de temps la commande sudo conserve-t-elle votre mot de passe en mémoire ? Quelle commande permet de forcer sudo à oublier votre mot de passe ?

La commande sudo enregistre le mot de passe pendant 15 minutes.

Pour forcer l'oubli , on peut :

```console
User@localhost:~$ sudo -k
```

# Exercice 2. Gestion des permissions

## 1. Dans votre $HOME, créez un dossier test, et dans ce dossier un fichier fichier contenant quelques lignes de texte. Quels sont les droits sur test et fichier ?

```console
User@localhost:~$ mkdir test
User@localhost:~$ echo "Un peu de text" >> test/text
User@localhost:~$ ll
drwxrwxr-x  2 User User    18 Sep 22 07:43 test/
User@localhost:~$ ll test/
-rw-rw-r--  1 User User  15 Sep 22 07:43 text
```

## 2. Retirez tous les droits sur ce fichier (même pour vous), puis essayez de le modifier et de l’aﬀicher en tant que root. Conclusion ?

```console
User@localhost:~$ sudo chmod 000 test/text
```

En tant que root on peux pas modifier le fichier et il est en lecture seul mais on peux afficher son contenue.

## 3. Redonnez vous les droits en écriture et exécution sur fichier puis exécutez la commande echo "echo Hello" > fichier. On a vu lors des TP précédents que cette commande remplace le contenu d’un fichier s’il existe déjà. Que peut-on dire au sujet des droits ?

```console
User@localhost:~$ sudo chmod 777 test/text
```

## 4. Essayez d’exécuter le fichier. Est-ce que cela fonctionne ? Et avec sudo ? Expliquez.

```console
User@localhost:~$ chmod +x text
```

Il faut ajouter le droit d'executer sur le fichier. Cela fonctionne avec le sudo.

## 5. Placez-vous dans le répertoire test, et retirez-vous le droit en lecture pour ce répertoire. Listez le contenu du répertoire, puis exécutez ou aﬀichez le contenu du fichier fichier. Qu’en déduisez-vous ? Rétablissez le droit en lecture sur test.

Il est impossible de lister ou d'affichier le contenu du repertoire si on enleve les droits dessus

```console
User@localhost:~$ ls test
ls: cannot open directory 'test': Permission denied
```

## 6. Créez dans test un fichier nouveau ainsi qu’un répertoire sstest. Retirez au fichier nouveau et au répertoire test le droit en écriture. Tentez de modifier le fichier nouveau. Rétablissez ensuite le droit en écriture au répertoire test. Tentez de modifier le fichier nouveau, puis de le supprimer. Que pouvez-vous déduire de toutes ces manipulations ?

```console
User@localhost:~$ mkdir sstest
User@localhost:~$ touch nouveau
User@localhost:~$ chmod u-w test
User@localhost:~$ chmod u-w test/nouveau
```

On peux pas editer le fichier car il est "unwritable"

```console
User@localhost:~$ chmod u+w test/nouveau
```

On peux pas editer le fichier car il est "unwritable" donc il faut que le dossier parent soit en en écreiture pour povoir écrire.

## 7. Positionnez vous dans votre répertoire personnel, puis retirez le droit en exécution du répertoire test.Tentez de créer, supprimer, ou modifier un fichier dans le répertoire test, de vous y déplacer, d’en lister le contenu, etc...Qu’en déduisez vous quant au sens du droit en exécution pour les répertoires ?

```console
User@localhost:~$ chmod -x test/

User@localhost:~$ touch test/test2
User@localhost:~$ touch: cannot touch 'test/test2': Permission denied

User@localhost:~$ rm -rf test/test2
rm: cannot remove 'test/test2': Permission denied

User@localhost:~$ touch test/test2
touch: cannot touch 'test/test2': Permission denied

User@localhost:~$ cd test
ls: cannot open directory 'test': Permission denied
```

On peux plus utiliser les commandes pour créer, supprimer, ou modifier un fichier, On peux en conclure que les droits d'execution bloque toutes les execution des commandes dans le dossier.

## 8. Rétablissez le droit en exécution du répertoire test. Positionnez vous dans ce répertoire et retirez lui à nouveau le droit d’exécution. Essayez de créer, supprimer et modifier un fichier dans le répertoire test, de vous déplacer dans ssrep, de lister son contenu. Qu’en concluez-vous quant à l’influence des droits que l’on possède sur le répertoire courant ? Peut-on retourner dans le répertoire parent avec ”cd ..” ? Pouvez-vous donner une explication ?

## 9. Rétablissez le droit en exécution du répertoire test. Attribuez au fichier fichier les droits suﬀisants pour qu’une autre personne de votre groupe puisse y accéder en lecture, mais pas en écriture.

```console
User@localhost:~$ chmod g+r test
User@localhost:~$ chmod g-w test
User@localhost:~$ ll

drwxr-xr-x  2 User User    18 Sep 22 08:44 test/
```

## 10. Définissez un umask très restrictif qui interdit à quiconque à part vous l’accès en lecture ou en écriture, ainsi que la traversée de vos répertoires. Testez sur un nouveau fichier et un nouveau répertoire.

```console
User@localhost:~$ umask 077
User@localhost:~$ touch try
User@localhost:~$ ll
-rw-------  1 User User     0 Sep 22 08:58 text2
```

## 11. Définissez un umask très permissif qui autorise tout le monde à lire vos fichiers et traverser vos réper-toires, mais n’autorise que vous à écrire. Testez sur un nouveau fichier et un nouveau répertoire.

```console
User@localhost:~$ umask 022
User@localhost:~$ mkdir dossier
User@localhost:~$ touch fichier2
User@localhost:~$ ll
drwxr-xr-x  2 User User     6 Sep 22 09:00 dossier/
-rw-r--r--  1 User User     0 Sep 22 09:01 fichier2
```

## 12. Définissez un umask équilibré qui vous autorise un accès complet et autorise un accès en lecture aux membres de votre groupe. Testez sur un nouveau fichier et un nouveau répertoire.

On choisit l'umask : `umask 047`

```console
User@localhost:~$ umask 047
User@localhost:~$ umask -S
u=rwx,g=wx,o=
```

## 13. Transcrivez les commandes suivantes de la notation classique à la notation octale ou vice-versa (vous pourrez vous aider de la commande stat pour valider vos réponses) :

- chmod u=rx,g=wx,o=r fic\
  `chmod 534 fic`
- chmod uo+w,g-rx fic en sachant que les droits initiaux de fic sont r--r-x---\
  `chmod 602 fic`
- chmod 653 fic en sachant que les droits initiaux de fic sont 711\
  `rw-r-x-wx`
- chmod u+x,g=w,o-r fic en sachant que les droits initiaux de fic sont r--r-x---\
  `chmod 520 fic`

## 14. Aﬀichez les droits sur le programme passwd. Que remarquez-vous ? En aﬀichant les droits du fichier /etc/passwd, pouvez-vous justifier les permissions sur le programme passwd ?

```console
User@localhost:~$ ll /etc/passwd
-rw-r--r-- 1 root root 1947 Sep 22 06:56 /etc/passwd

User@localhost:~$ stat /etc/passwd
-rw-r--r-- 1 root root 1947 Sep 22 06:56 /etc/passwd
  File: /etc/passwd
  Size: 1947            Blocks: 8          IO Block: 4096   regular file
Device: fd00h/64768d    Inode: 25945503    Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2022-09-22 06:57:04.805746532 +0000
Modify: 2022-09-22 06:56:57.241777973 +0000
Change: 2022-09-22 06:56:57.245777956 +0000
 Birth: 2022-09-22 06:56:57.241777973 +0000
stat /etc/passwd
```
Ce fichier contient des informations sur tout les utilisateur. Il appartient à root . Et seulement root peut l'executer.

# Pour les plus rapides :

## 15. Access Control Lists (ACL) : suivez le tutoriel de cette page : https://doc.ubuntu-fr.org/acl.

## 16. Quotas disques : suivez le tutoriel de cette page : https://doc.ubuntu-fr.org/quota.
