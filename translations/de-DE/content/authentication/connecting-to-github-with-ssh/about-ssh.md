---
title: Informationen zu SSH
intro: 'Mithilfe des SSH-Protokolls kannst Du eine Verbindung herstellen und Dich bei Remote-Servern und -Diensten authentifizieren. With SSH keys, you can connect to {% data variables.product.product_name %} without supplying your username and personal access token at each visit.'
redirect_from:
  - /articles/about-ssh
  - /github/authenticating-to-github/about-ssh
  - /github/authenticating-to-github/connecting-to-github-with-ssh/about-ssh
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
topics:
  - SSH
---

When you set up SSH, you will need to generate a new SSH key and add it to the ssh-agent. You must add the SSH key to your account on {% data variables.product.product_name %} before you use the key to authenticate. For more information, see "[Generating a new SSH key and adding it to the ssh-agent](/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)" and "[Adding a new SSH key to your {% data variables.product.prodname_dotcom %} account](/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)."

You can further secure your SSH key by using a hardware security key, which requires the physical hardware security key to be attached to your computer when the key pair is used to authenticate with SSH. You can also secure your SSH key by adding your key to the ssh-agent and using a passphrase. Weitere Informationen findest Du unter „[SSH-Schlüssel-Passphrasen verwenden](/github/authenticating-to-github/working-with-ssh-key-passphrases).“

{% ifversion fpt %}To use your SSH key with a repository owned by an organization that uses SAML single sign-on, you must authorize the key. Weitere Informationen findest Du unter „[Einen SSH-Schlüssel für die Verwendung in einer Organisation mit SAML Single Sign-On autorisieren](/articles/authorizing-an-ssh-key-for-use-with-saml-single-sign-on)“.{% endif %}

To maintain account security, you can regularly review your SSH keys list and revoke any keys that are invalid or have been compromised. Weitere Informationen findest Du unter „[SSH-Schlüssel überprüfen](/github/authenticating-to-github/reviewing-your-ssh-keys).“

{% ifversion fpt %}
Wenn Sie Ihren SSH-Schlüssel seit einem Jahr nicht mehr verwendet haben, löscht {% data variables.product.prodname_dotcom %} aus Sicherheitsgründen automatisch Ihren inaktiven SSH-Schlüssel. Weitere Informationen findest Du unter „[Gelöschte oder fehlende SSH-Schlüssel](/articles/deleted-or-missing-ssh-keys).“
{% endif %}

Wenn Sie Mitglied einer Organisation sind, die SSH-Zertifikate bereitstellt, können Sie mit Ihrem Zertifikat auf die Repositorys dieser Organisation zugreifen, ohne das Zertifikat zu Ihrem {% data variables.product.product_name %}-Konto hinzuzufügen. Weitere Informationen findest Du unter „[Informationen zu SSH-Zertifizierungsstellen](/articles/about-ssh-certificate-authorities).“

## Weiterführende Informationen

- „[Nach vorhandenen SSH-Schlüsseln suchen](/articles/checking-for-existing-ssh-keys)“
- „[SSH-Verbindung testen](/articles/testing-your-ssh-connection)“
- „[Fehlerbehebung bei SSH](/articles/troubleshooting-ssh)“
