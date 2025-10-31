le projet donné par l'encadreur est : Système de Formation et d'Apprentissage pour Églises - 
QzBible 
1- pour ce projet la première chose qui m'a été demandé de faire est lire la documentation du projet et comprendre chaque partie evoquée. Voir document de la description du projet Business requirement.pdf
2- tester l'api du lien suivant : https://dev-backend.qzbible.com/   
    pour tester cet API j'ai ouvert le lien ou on m'a proposé une route vers laquelle me rediriger pour avoir accès à toutes les routes possibles créer dans l'API
    a- tester un API consiste à faire quoi?
        -- acceder à la liste des routes
        -- télecharger postman pour les tests (est considéré comme la méthode la plus fiable et la plus recommandée)
        -- dans postman, on crée une nouvelle requete et on teste tous les liens donnée (en utilisant la méthode POST). Pour le cas de ce projet, on commence par tester les authentification
            * création d'un compte staff 
                - methode : POST
                - url : https://dev-backend.qzbible.com/users/create_staff
                - donnée : {
                                "name": "ana",
                                "first_name": "rahma",
                                "email": "awalnjiagupmun@gmail.com",
                                "password": "pass123",
                                "confirm_password": "pass123"
                            }
                - code obtenu : 201 created
                - résultat : {
                                "message": "Compte staff créé avec succès.",
                                "user_id": "6904c00d89e81f2e69712fe5",
                                "email": "awalnjiagupmun@gmail.com",
                                "name": "ana",
                                "first_name": "rahma",
                                "role": "staff",
                                "is_active": true
                            }
            * authentification pour un utilisateur
                - methode : POST
                - url : https://dev-backend.qzbible.com/auth/login
                - donnée : {
                                "email": "awarahma@gmail.com",
                                "password": "pass123"
                            }
                - code obtenu : 200 OK
                - résultat : {
                                "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmcmVzaCI6ZmFsc2UsImlhdCI6MTc2MTkxODA3MSwianRpIjoiMGZmMjMxNWMtZDRhZS00MzhhLWI3MDItZWE3NWI0ZWNlNmQzIiwidHlwZSI6ImFjY2VzcyIsInN1YiI6IjY5MDRiYWJlODllODFmMmU2OTcxMmZlMSIsIm5iZiI6MTc2MTkxODA3MSwiZXhwIjoxNzY3MTAyMDcxLCJyb2xlIjoic3RhZmYifQ.QLpGaYwuJN-uzEDo3C98x_wMJlkDz3_iq6m1-yq1-sE",
                                "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmcmVzaCI6ZmFsc2UsImlhdCI6MTc2MTkxODA3MSwianRpIjoiNjJhNjgzNDctN2MxOS00MDUzLThkNTItYTI4OGQ0OWI1NzNlIiwidHlwZSI6InJlZnJlc2giLCJzdWIiOiI2OTA0YmFiZTg5ZTgxZjJlNjk3MTJmZTEiLCJuYmYiOjE3NjE5MTgwNzEsImV4cCI6MTc2MjUyMjg3MX0.7biUQMsQB__Sb6ADALqD6l2LqNGuWQs9leuanAPyHE0",
                                "role": "staff",
                                "email": "awarahma@gmail.com"
                            }
            * activation d'un compte utilisateur via token
                - methode : POST
                - url : https://dev-backend.qzbible.com/auth/active_account/{token}
                - donnée : {
                                "user_id": "6904c00d89e81f2e69712fe5"
                            }
                - code obtenu : 400 Bad request 
                - résultat : {
                                "error": "'user_id'"
                             }
                             ou
                             {
                                "error": "token incorrect"
                             }
            * création d'un compte admin pour un magasin
                - methode : POST
                - url : https://dev-backend.qzbible.com/users/create_admin
                - donnée : {
                                "name": "awa",
                                "first_name": "njiagupmun",
                                "email": "awarahma2021@gmail.com",
                                "magasin_id": "magas1"
                            }
                - code obtenu : 500
                - résultat : {
                                "681a2386c5a2a10fd9d93874": "500 Internal Server Error: The server encountered an internal error and was unable to complete your request. Either the server is overloaded or there is an error in the application."
                            }
            * rafraichir le token
                - methode : POST
                - url : https://dev-backend.qzbible.com/auth/refresh
                - donnée : entrer le token de rafraichissement donné
                - code obtenu : 200 OK
                - résultat :{
                                "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmcmVzaCI6ZmFsc2UsImlhdCI6MTc2MTkyMTA2NywianRpIjoiN2M1ZmQxNDgtN2Y5Ni00Yjk0LWJiZmEtZmQwNjhjMTM3N2RmIiwidHlwZSI6ImFjY2VzcyIsInN1YiI6IjY5MDRiYWJlODllODFmMmU2OTcxMmZlMSIsIm5iZiI6MTc2MTkyMTA2NywiZXhwIjoxNzYxOTIxOTY3fQ.N6EidR63Xq3XDhScVDkoqFNaplIXg36Me_1JbRYJ18I"
                            }
            * forgot password
                - methode : POST
                - url : https://dev-backend.qzbible.com/auth/forgot_password
                - donnée : {
                                "email": "awalnjiagupmun@gmail.com"
                            }
                - code obtenu : 200 OK
                - résultat :{
                                "message": "Si cet email existe, un lien a été envoyé"
                            }
            * rénitialisation du mot de passe
                - methode : POST
                - url : https://dev-backend.qzbible.com/auth/refresh_password/{token}
                - donnée : {
                                "new_password": "motdepasse123",
                                "confirm_password": "motdepasse123",
                                "user_id": "6904c00d89e81f2e69712fe5"
                            }
                - code obtenu : 400 bad request
                - résultat :{
                                "error": "'user_id'"
                            }