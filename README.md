# Avant propos
Les Classes et interfaces de toute librairie 'axeldjaha' commencent toujours par AD (Axel Djaha).
# Description
Librairie pour envoyer des SMS simplement.
# Gradle
compile 'axeldjaha.library:sms:1.3'
# Exemple d'utilisation
Envoyer un SMS et gérer la réussite ou l'échec de l'envoi est très simple:

        /**
         * On crée une instance de ADSMS avec l'instance d'une activité,
         * on attache le message à envoyer, ainsi que le numéro de téléphone du destinataire,
         * on définit un écouteur d'évènement pour être notifié de la réussite ou de l'échec de l'envoi du SMS
         * et on envoie le SMS ainsi créé
         */
        ADSMS.newInstance(ExempleActivity.this)
                .bindMessage("Message à envoyer")
                .bindPhoneNumber("58000001")
                .bindListener(new ADSMSListener(){
                    @Override
                    public void onADSmsSucces() {
                        //SMS envoyé, faire qqch
                    }

                    @Override
                    public void onADSmsFailed() {
                        //SMS non envoyé, faire qqch
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

