---
title: Administrar la configuración de seguridad y análisis para tu repositorio
intro: 'Puedes controlar las características que dan seguridad y analizan tu código en tu proyecto dentro de {% data variables.product.prodname_dotcom %}.'
permissions: People with admin permissions to a repository can manage security and analysis settings for the repository.
redirect_from:
  - /articles/managing-alerts-for-vulnerable-dependencies-in-your-organization-s-repositories/
  - /articles/managing-alerts-for-vulnerable-dependencies-in-your-organizations-repositories/
  - /articles/managing-alerts-for-vulnerable-dependencies-in-your-organization
  - /github/managing-security-vulnerabilities/managing-alerts-for-vulnerable-dependencies-in-your-organization
  - /github/administering-a-repository/managing-security-and-analysis-settings-for-your-repository
  - /github/administering-a-repository/managing-repository-settings/managing-security-and-analysis-settings-for-your-repository
versions:
  fpt: '*'
  ghes: '>=3.0'
  ghae: '*'
type: how_to
topics:
  - Dependabot
  - Alerts
  - Advanced Security
  - Dependency graph
  - Secret scanning
  - Repositories
shortTitle: Seguridad & análisis
---

{% ifversion fpt %}
## Habilitar o inhabilitar las características de análisis y seguridad para los repositorios públicos

Puedes administrar un subconjunto de características de análisis y seguridad para los repositorios públicos. Otras características se encuentran habilitadas permanentemente, incluyendo la gráfica de dependencias y el escaneo de secretos.

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-settings %}
{% data reusables.repositories.navigate-to-security-and-analysis %}
4. Debajo de "Configurar la seguridad y las características de análisis", a la derecha de la característica, da clic en **Inhabilitar** o **Habilitar**. ![Botón de "Habilitar" o "Inhabilitar" para las características de "Configurar la seguridad y análisis" en un repositorio público.](/assets/images/help/repository/security-and-analysis-disable-or-enable-dotcom-public.png)
{% endif %}

## Habilitar o inhabilitar las características de seguridad y análisis{% ifversion fpt %} para los repositorios privados{% endif %}

Puedes administrar las características de seguridad y análisis para tu repositorio{% ifversion fpt %}privado o interno {% endif %}.{% ifversion fpt or ghes > 2.22 %} Si tu organización pertenece a una empresa que tiene una licencia para {% data variables.product.prodname_GH_advanced_security %}, entonces tendrás opciones adicionales disponibles. {% data reusables.advanced-security.more-info-ghas %}{% endif %}

{% data reusables.security.security-and-analysis-features-enable-read-only %}

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-settings %}
{% data reusables.repositories.navigate-to-security-and-analysis %}
{% ifversion fpt or ghes > 3.0 %}
4. Debajo de "Configurar la seguridad y las características de análisis", a la derecha de la característica, da clic en **Inhabilitar** o **Habilitar**. El control para "La {% data variables.product.prodname_GH_advanced_security %}" se inhabilita si tu empresa no tiene licencias disponibles para la {% data variables.product.prodname_advanced_security %}.{% ifversion fpt %}!["Enable" or "Disable" button for "Configure security and analysis" features](/assets/images/help/repository/security-and-analysis-disable-or-enable-dotcom-private.png){% else %}!["Enable" or "Disable" button for "Configure security and analysis" features](/assets/images/enterprise/3.1/help/repository/security-and-analysis-disable-or-enable-ghes.png){% endif %}
  {% note %}

  **Nota:** Si inhabilitas la {% data variables.product.prodname_GH_advanced_security %}, {% ifversion fpt %}revisión de dependencias, {% endif %}el {% data variables.product.prodname_secret_scanning %} y el {% data variables.product.prodname_code_scanning %} se inhabilitarán. Cualquier flujo de trabajo, cargas de SARIF o llamados de la API para el {% data variables.product.prodname_code_scanning %} fallarán.
  {% endnote %}
  {% endif %}
  {% ifversion ghes = 3.0 %}
4. Debajo de "Configurar la seguridad y las características de análisis", a la derecha de la característica, da clic en **Inhabilitar** o **Habilitar**. ![Botón de "Habilitar" o "Inhabilitar" para las características de "Configurar la seguridad y el análisis"](/assets/images/help/repository/security-and-analysis-disable-or-enable-ghe.png)
  {% endif %}
  {% ifversion ghae %}
4. Debajo de "Configurar la seguridad y las características de análisis", a la derecha de la característica, da clic en **Inhabilitar** o **Habilitar**. Antes de que puedas habilitar el "{% data variables.product.prodname_secret_scanning %}" para tu repositorio, puede que necesites habilitar la {% data variables.product.prodname_GH_advanced_security %}. ![Habilitar o inhabilitar la {% data variables.product.prodname_GH_advanced_security %} o el {% data variables.product.prodname_secret_scanning %} para tu repositorio](/assets/images/enterprise/github-ae/repository/enable-ghas-secret-scanning-ghae.png)
  {% endif %}

## Otorgar acceso a las alertas de seguridad

Después de que habilitas al {% ifversion not ghae %}{% data variables.product.prodname_dependabot %} o {% endif %}las alertas del {% data variables.product.prodname_secret_scanning %} para un repositorio en una organización, los propietarios de esta y los administradores de repositorio pueden ver las alertas predeterminadamente. Puedes dar acceso a equipos y personas adicionales para las alertas de un repositorio.

{% note %}

Los propietarios de las organizaciones y administradores de repositorio solo pueden otorgar acceso para visualizar alertas de seguridad, tales como alertas del {% data variables.product.prodname_secret_scanning %}, para las personas o equipos que tienen acceso de escritura en el repositorio.

{% endnote %}

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-settings %}
{% data reusables.repositories.navigate-to-security-and-analysis %}
4. Debajo de "Acceso a las alertas", en el campo de búsqueda, comienza a teclear el nombre de la persona o equipo que quieres encontrar y luego da clic en su nombre dentro de la lista de coincidencias.
   {% ifversion fpt %}
   ![Campo de búsqueda para otorgar acceso a las alertas de seguridad a personas y equipos](/assets/images/help/repository/security-and-analysis-security-alerts-person-or-team-search.png)
   {% endif %}
   {% ifversion ghes > 2.22 %}
   ![Campo de búsqueda para otorgar acceso a las alertas de seguridad a personas y equipos](/assets/images/help/repository/security-and-analysis-security-alerts-person-or-team-search-ghe.png)
   {% endif %}
   {% ifversion ghae %}
   ![Campo de búsqueda para otorgar acceso a las alertas de seguridad a personas y equipos](/assets/images/enterprise/github-ae/repository/security-and-analysis-security-alerts-person-or-team-search-ghae.png)
   {% endif %}

5. Haz clic en **Guardar cambios**.
   {% ifversion fpt or ghes > 2.22 %}
   ![Botón de "Guardar cambios" para los cambios realizados a la configuración de alertas de seguridad](/assets/images/help/repository/security-and-analysis-security-alerts-save-changes.png)
   {% endif %}
    {% ifversion ghae %}
   ![Botón de "Guardar cambios" para los cambios realizados a la configuración de alertas de seguridad](/assets/images/enterprise/github-ae/repository/security-and-analysis-security-alerts-save-changes-ghae.png)
   {% endif %}

## Eliminar el acceso a las alertas de seguridad

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.sidebar-settings %}
{% data reusables.repositories.navigate-to-security-and-analysis %}
4. Debajo de "Acceso a las alertas", a la derecha de la persona o equipo para el cual quieres eliminar el acceso, haz clic en {% octicon "x" aria-label="X symbol" %}.
   {% ifversion fpt %}
   ![Botón "x" para eliminar el acceso de alguien a las alertas de seguridad para tu repositorio](/assets/images/help/repository/security-and-analysis-security-alerts-username-x.png)
   {% endif %}
   {% ifversion ghes > 2.22 %}
   ![Botón "x" para eliminar el acceso de alguien a las alertas de seguridad para tu repositorio](/assets/images/help/repository/security-and-analysis-security-alerts-username-x-ghe.png)
   {% endif %}
   {% ifversion ghae %}
   ![Botón "x" para eliminar el acceso de alguien a las alertas de seguridad para tu repositorio](/assets/images/enterprise/github-ae/repository/security-and-analysis-security-alerts-username-x-ghae.png)
   {% endif %}

## Leer más

- "[Asegurar tu repositorio](/code-security/getting-started/securing-your-repository)"
- "[Administrar la seguridad y la configuración de análisis para tu organización](/organizations/keeping-your-organization-secure/managing-security-and-analysis-settings-for-your-organization)"
