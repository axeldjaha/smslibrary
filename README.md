# Avant propos
Les Classes et interfaces de toute librairie 'axeldjaha' commencent toujours par AD (Axel Djaha).
# Description
Librairie pour envoyer des SMS simplement.
# Gradle
compile 'axeldjaha.library:sms:1.2'
# Exemple d'utilisation
Envoyer un SMS et gérer la réussite ou l'échec de l'envoi est très simple:

        /**
         * On crée une instance de ADSMS à laquelle on attache le message à envoyer,
         * le numéro du destinataire ainsi qu'un écouteur d'évènement (callback) qui nous notifie de la
         * réussite ou de l'échec de l'envoi du SMS
         */
        ADSMS.newInstance(ExempleActivity.this)
                .bindMessage("Message test") //message à envoyer
                .bindPhoneNumber("58000001") //numéro destinataire
                .bindListener(new ADSMSListener() //écouteur d'évènement
                {
                    @Override
                    public void onADSmsSucces() {
                        //SMS envoyé, faire qqch
                        Toast.makeText(ExempleActivity.this, "SMS envoyé", Toast.LENGTH_SHORT).show();
                    }

                    @Override
                    public void onADSmsFailed() {
                        //SMS non envoyé, faire qqch
                        Toast.makeText(ExempleActivity.this, "Echec de l'envoi", Toast.LENGTH_SHORT).show();
                    }
                })
                .send();

# Fonctionnalités

| Méthodes applicables à ADSMS  | Description |
| --------------------------------- | ----------- |
| bindListener(ADSMSListener listener) | Définir un écouteur d'évènement pour l'envoi du SMS |
| bindMessage(java.lang.String message) | Définir le message à envoyer |
| bindPhoneNumber(java.lang.String phoneNumber) | Définir le numéro destinataire du SMS à envoyer |
| newInstance(android.support.v7.app.AppCompatActivity activity) | Créer l'instance de ADSMS qui permettra d'envoyer un SMS |
| send() | Envoyer le SMS |

# Interface
Pour être notifié de la réussite ou de l'échec de l'envoi, implémenter ADSMSListener

| Méthodes à implémenter  | Description |
| --------------------------------- | ----------- |
| onADSmsFailed() | Appelé lorsque l'envoi a échoué |
| onADSmsSucces() | Appelé lorsque le SMS est envoyé |

