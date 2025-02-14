# Descrition

Création d'une instance ldap pour Oracle Directory Server Entreprise Edition 11g (v11.1.1.7).

Annuaire agents (AAA) par défaut


# Prérequis

RHEL6 ou RHEL7


# Variables de rôle

```
# Repertoire d'installation de OSDEE
odseeHome: '/var/opt'
# Repertoire odsee dans l'archive oracle (dsee7 par defaut)
odseeDir: 'dsee7'
# Emplacement des binaires d'administration OSDEE
odseeBin: '{{ odseeHome }}/{{ odseeDir }}/bin'

# Emplacement pour la création de l'instance
instanceHome: '/data/ldap'
# Nom de l'instance
instanceName: 'slapd-data-aaa'
# Port
instancePort: '389'
# Port secure (ssl)
instancePortSecure: '636'
# Activation du démarrage automatique de l'instance au boot (systemctl enable) : yes / no
instanceAutoStart: yes
# Répertoire de destination des fichiers de password
instancePasswordDir: "/root/ldap"
# Nom du fichier contenant le password de l'instance (utilisé pour toutes les configurations, droits = root 600)
instancePasswordFile: "{{ instanceName }}"
# Password de l'instance
instancePassword: 'password@changer!'

# Liste des extension de schémas utilisées pour l'instance (AAA par défaut)
instanceSchemas: [
              { url: 'http://pole.in.ac-orleans-tours.fr/fileadmin/user_upload/pole-identite/Annuaires/schemas/97educ.ldif', sum: 'md5:ecd8b6833c1db4373bae0c7b16c2e5ec'},
              { url: 'http://pole-id.in.ac-orleans-tours.fr/bin/axm/62rsa-axm.ldif'                            ,sum: 'md5:0ed5c9d621565fb27338417048be9287'}
              ]
```


# Dépendances

Oracle Directory Server Enterprise Edition 11G installé (par ex via role role-ldap_odsee_install)


---

*Auteur*

*Vincent Leblanc <vincent.leblanc2@ac-orleans-tours.fr>*
*Pôle de compétences - gestion des identités - Rectorat d'Orléans-Tours*

*Certaines parties des rôles sont tirées du travail réalisé par JC TOUSSAINT (Nancy) pour l'acv (http://gitlab.tyforge.in.ac-rennes.fr/acv)*
*Merci à Mathieu Jourdan (Rennes) pour la base des scripts de restart*
