# Avant propos
Les Classes et interfaces de toute librairie 'axeldjaha' commencent toujours par AD, qui signifie Axel Djaha (l'auteur).
# smslibrary
Librairie pour envoyer des SMS simplement.
# Gradle
compile 'axeldjaha.library:sms:1.2'
# Usage
Envoyer un SMS et gérer la réussite ou l'échec de l'envoi est très simple:

        /**
         * On crée une instance de ADSMS à laquelle on attache le message à envoyer,
         * le numéro du destinataire ainsi qu'un écouteur d'évènement (callback) qui nous notifie de la
         * réussite ou de l'échec de l'envoi du SMS
         */
        ADSMS.newInstance(ExempleActivity.this)
                .bindMessage("Message test") //message à envoyer
                .bindPhoneNumber("58000001") //numéro destinataire
                .bindListener(new ADSMSListener() { //écouteur d'évènement
                    @Override
                    public void onADSmsSucces() {
                        //SMS envoyé, faire qqch ici
                        Toast.makeText(ExempleActivity.this, "SMS envoyé", Toast.LENGTH_SHORT).show();
                    }

                    @Override
                    public void onADSmsFailed() {
                        //SMS non envoyé, faire qqch ici
                        Toast.makeText(ExempleActivity.this, "Echec de l'envoi", Toast.LENGTH_SHORT).show();
                    }
                })
                .send();
        
