TP 2 : Spring IOC

Injection des dépendances avec @Qualifier

On utilise @Autowired pour injecter automatiquement une implémentation de IDao dans MetierImpl.

Avec @Qualifier("dao"), on sélectionne DaoImpl, qui retourne 100.0. Le résultat final est 200.0.

<img width="760" height="246" alt="Screenshot 2026-10-12 165904" src="https://github.com/user-attachments/assets/eaa98d66-d0b6-4128-9143-25a4a19edd66" />

Avec @Qualifier("dao2"), on sélectionne DaoImpl2, qui retourne 150.0. Le résultat final est 300.0.

<img width="833" height="316" alt="Screenshot 2026-10-12 170447" src="https://github.com/user-attachments/assets/c22a020f-01c9-42d3-948a-020b75e3818b" />

Exercices supplémentaires

La classe MetierImplTest permet de tester la méthode calcul().

Une implémentation fictive de IDao retourne la valeur 10.0. Le résultat attendu est 20.0.

Le test s'est exécuté avec succès (exit code 0).

<img width="882" height="376" alt="Screenshot 2026-10-13 202811" src="https://github.com/user-attachments/assets/3e32985f-016e-4d6e-b140-86cb504a6073" />



<img width="679" height="258" alt="Screenshot 2026-10-13 203345" src="https://github.com/user-attachments/assets/c568c199-a1de-4d23-9769-19e831ea246a" />


<img width="874" height="393" alt="Screenshot 2026-10-13 203409" src="https://github.com/user-attachments/assets/61a6f192-4ca5-4231-8338-a6a0dd5c1b63" />

Test unitaire : le test de la méthode calcul() est réussi.

Configuration XML : le résultat affiché est 300.0.

Profil Spring : le profil dev utilise DaoImpl2 et le résultat affiché est 300.0.

Ces résultats montrent que l'injection des dépendances et la configuration des Beans fonctionnent correctement.

