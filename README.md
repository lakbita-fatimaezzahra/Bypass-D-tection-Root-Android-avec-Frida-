# Bypass-Detection-Root-Android-avec-Frida

Ce laboratoire pédagogique démontre comment analyser et neutraliser les mécanismes de sécurité (Root Detection) au sein d'une application Android (Uncrackable Level 1) en utilisant l'instrumentation dynamique.

**Étapes du Lab**

1. Vérification de la connexion ADB
   
Avant toute manipulation, nous vérifions que l'émulateur est correctement reconnu par le système via le pont de débogage Android (ADB).

<img width="829" height="140" alt="Screenshot 2026-04-22 164838" src="https://github.com/user-attachments/assets/f20d281a-35dc-4942-8362-b367f2111262" />

2. Configuration du transfert de port
   
Pour permettre la communication entre Frida sur l'ordinateur et le serveur Frida sur le mobile, nous redirigeons les ports TCP nécessaires.

<img width="768" height="163" alt="Screenshot 2026-04-22 164826" src="https://github.com/user-attachments/assets/0c2f80db-7ef0-4636-9f20-5b56df9aaf85" />

3. Identification de l'application cible
   
Nous listons les processus et les packages installés sur le périphérique pour identifier le nom exact du package à cibler.

<img width="944" height="765" alt="Screenshot 2026-04-22 164730" src="https://github.com/user-attachments/assets/d2377097-d9f0-4bea-97ce-e90abda0363d" />

4. Constat de l'échec (Détection active)
   
Sans intervention, l'application détecte que l'appareil est "rooté" ou qu'il s'agit d'un émulateur et refuse de se lancer.

<img width="476" height="762" alt="Screenshot 2026-04-22 165650" src="https://github.com/user-attachments/assets/54b087f9-b384-47a6-baa4-41f93747ce0e" />

5. Analyse et Script de Hooking (JavaScript)
   
Nous créons un script Frida pour intercepter les méthodes de détection. Le code cible la classe sg.vantagepoint.a.c et redéfinit ses fonctions a(), b() et c() pour qu'elles retournent systématiquement false (indiquant que le root n'est pas détecté).

<img width="915" height="629" alt="Screenshot 2026-05-01 122710" src="https://github.com/user-attachments/assets/e6b914b7-91b6-4413-8950-c9270095edf6" />

6. Injection et Contournement
   
Nous lançons l'application en injectant le script bypass.js. Frida "spawn" le processus et applique les hooks en temps réel.

<img width="1109" height="442" alt="Screenshot 2026-04-22 165705" src="https://github.com/user-attachments/assets/9d633136-d52d-4d64-8acf-20bb9c0bac04" />

7. Résultat final
   
Une fois la détection neutralisée, l'application s'ouvre normalement sur son écran principal sans se fermer.

<img width="482" height="774" alt="Screenshot 2026-04-22 164510" src="https://github.com/user-attachments/assets/e18b39fa-950c-4fdf-8a6f-7661022394ae" />

