#git #process

- Créer de petits commits
	- Avantages
		- Pouvoir revenir en arrière quand on veut
		- Faciliter la lecture de la PR du reviewer (Commits narratifs)
		- Empêcher la validation automatique des PR et donc le nombre de bugs potentiels dans la codebase
		- Écriture de meilleur messages
	 - Attention: Un commit !== un changement. Un commit doit être signifiant, un commit doit correspondre à un problème de résolu.
	 - Ne pas hésiter à revenir un peu en arrière avec un rebase pour ne pas créer de bruit dans la base de code
- Écrire de petites PR
	- Une PR !== une tâche
		- Une PR === une problèmatique
		- Cela évite de bloquer les autres développeurs
		- Cela facilite les rebases et empêche les conflits
		- Cela facilite et accélère le process de review
		- Cela nous empêche de perdre du temps sur une direction qui n'est pas la bonne
	 - Gérer les tâches
		 - Si nous ne sommes pas dans de l'intégration continue, créer une branche de tâche qui sera mergée au moment de la mise en prod.
- Ne pas oublier
	- La documentation
	- Les scripts d'initialisation et de mise à jour du projet
		- Chaque nouveaux entrants dans le projet doit pouvoir le configurer assez vite
- Écrire de bonnes PR
	- Une bonne description
		- Avantages
			- Alléger la charge mentale du lead
			- Documenter notre codebase
			- Faciliter l'intégration des nouveaux entrants
		 - Structure
			 - Lien vers le ticket
			 - Lien vers la PR précedente ?
			 - Pourquoi
			 - Ce qui change
			 - Comment
			 - Points notables qui influence la compréhension de la PR
			 - Visuels ?
			 - Des liens
			 - Des risques ? 
			 - Des changements dans un futur proche
	 - Un bon titre
		 - Un bon titre doit permettre au lead de faire le lien avec le ticket
		 - Un bon titre doit se décrire lui-même
- Commenter une PR
	- Soyez bienveillants
		- Parler comme membre d'une équipe
		- Posez des questions
		- N'accusez jamais, le commentaire doit être dirigé contre le code, jamais contre l'auteur
		- Utilisez le conditionnel
		- Demandez à l'autre développeur ce qu'il pense de vos propositions
		- Renvoyer à une documentation
		- Ne jamais prendre l'explication d'un développeur comme une manière de se débarasser d'un soucis. Si le changement n'est pas clair avant la review, il ne le sera pas plus après si aucune action n'est effectué suite à un retour sur un manque de clareté.
		- Une PR est un espace d'apprentissage.
- Gérer les feedbacks
	- Ne pas prendre les retours personnellement
	- Voir les retours comme un moyen de s'améliorer
	- Ne pas hésiter à répondre: une PR est un espace de discussion
	- Le lead a le dernier mot
- Chaîner les PRs
	- Avantages
		- Faciliter la gestion du merge des PR
		- Faciliter la lecture des PR
	- Quelques règles
		- La PR doit être dépendante d'une PR précédente
		- Bien spécifier au développeur qu'il doit faire attention à merger dans la bonne branche
- Quelques outils
	- PHPStorm
	- Lazygit
Nommage des commits ?
	// Conventionnal commit
	// Se mettre d'accord sur la convention finale avec les membres de l'équipe
Git hooks ? 
	// Facultatif, présent dans le repo, à installer soi-même (via le makefile)
Client git ? 
Jira et bitbucket



[The anatomy of a perfect pull request | by Hugo Dias | Medium](https://hugooodias.medium.com/the-anatomy-of-a-perfect-pull-request-567382bb6067)