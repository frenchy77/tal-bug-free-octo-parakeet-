---
title: Acerca del escaneo de código
intro: 'Puedes utilizar {% data variables.product.prodname_code_scanning %} para encontrar vulnerabilidades de seguridad y errores en el código de tu proyecto en {% data variables.product.prodname_dotcom %}.'
product: '{% data reusables.gated-features.code-scanning %}'
versions:
  ghes: '2.22'
topics:
  - Security
redirect_from:
  - /github/finding-security-vulnerabilities-and-errors-in-your-code/about-code-scanning
---

<!--See /content/code-security/secure-coding for the latest version of this article -->

{% data reusables.code-scanning.beta %}
{% data reusables.code-scanning.enterprise-enable-code-scanning %}

## Acerca de {% data variables.product.prodname_code_scanning %}

{% data reusables.code-scanning.about-code-scanning %}

Puedes utilizar {% data variables.product.prodname_code_scanning %} para encontrar, clasificar y priorizar los arreglos a problemas existentes en tu código. {% data variables.product.prodname_code_scanning_capc %} también previene a los desarrolladores de introducir nuevos problemas. Puedes programar días y horas específicos para los escaneos, o activarlos cuando ocurra un evento específico en el repositorio, tal como una carga de información.

Si {% data variables.product.prodname_code_scanning %} encuentra una vulnerabilidad potencial o un error en tu código, {% data variables.product.prodname_dotcom %} mostrará una alerta en el repositorio. {% data variables.product.prodname_dotcom %} cerrará la alerta una vez que arregles el código que la activó. Para obtener más información, consulta la sección "[Administrar las alertas de {% data variables.product.prodname_code_scanning %} para tu repositorio](/github/finding-security-vulnerabilities-and-errors-in-your-code/managing-code-scanning-alerts-for-your-repository)".

Para monitorear los resultados del {% data variables.product.prodname_code_scanning %} a lo largo de tus repositorios o de tu organización, puedes utilizar webhooks y la API del {% data variables.product.prodname_code_scanning %}. Para obtener más información sobre los webhooks para el {% data variables.product.prodname_code_scanning %}, consulta la sección [Cargas útiles y eventos de webhook](/developers/webhooks-and-events/webhook-events-and-payloads#code_scanning_alert)". Para obtener más información sobre las terminales de la API, consulta la sección "[{% data variables.product.prodname_code_scanning_capc %}](/rest/reference/code-scanning)".

Para iniciar con el {% data variables.product.prodname_code_scanning %}, consulta la sección "[Configurar el {% data variables.product.prodname_code_scanning %} en un repositorio](/github/finding-security-vulnerabilities-and-errors-in-your-code/setting-up-code-scanning-for-a-repository)".

## Acerca de {% data variables.product.prodname_codeql %}

Puedes ver y contribuir con las consultas para {% data variables.product.prodname_code_scanning %} en el repositorio [`github/codeql`](https://github.com/github/codeql). {% data variables.product.prodname_codeql %} trata el código como datos, lo cual te permite encontrar vulenrabilidades potenciales en tu código con más confianza que en los anallizadores estáticos trandicionales.

{% data variables.product.prodname_ql %}Es el lenguaje de consulta que impulsa a {% data variables.product.prodname_codeql %}. {% data variables.product.prodname_ql %} es un lenguaje de programación lógico orientado a objetos. {% data variables.product.company_short %}, los expertos del lenguaje, y los investigadores de seguridad crean las consultas que se utilizan para {% data variables.product.prodname_code_scanning %}, y éstas son de código abierto. La comunidad mantiene y actualiza estas consultas para mejorar el análisis y reducir los falsos positivos. Para obtener más información, consulta la sección [{% data variables.product.prodname_codeql %}](https://securitylab.github.com/tools/codeql) en el sitio web de GitHub Security Lab.

Para obtener más información acerca de las terminales de la API para {% data variables.product.prodname_code_scanning %}, consulta la sección "[{% data variables.product.prodname_code_scanning_capc %}](http://developer.github.com/v3/code-scanning)".

{% data reusables.code-scanning.codeql-languages-bullets %}

Puedes ver y contribuir con las consultas para {% data variables.product.prodname_code_scanning %} en el repositorio [`github/codeql`](https://github.com/github/codeql). Para obtener más información, consulta la sección [{% data variables.product.prodname_codeql %} queries](https://codeql.github.com/docs/writing-codeql-queries/codeql-queries/) en la documentación de {% data variables.product.prodname_codeql %}.

## Acerca de las herramientas de escaneo de código de terceros

{% data reusables.code-scanning.you-can-upload-third-party-analysis %}

{% data reusables.code-scanning.interoperable-with-tools-that-output-sarif %}

{% data reusables.code-scanning.get-started-uploading-third-party-data %}

## Leer más

- [{% data variables.product.prodname_security %}](https://securitylab.github.com/)
- [OASIS Static Analysis Results Interchange Format (SARIF) TC](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=sarif) en el sitio web del Comité OASIS
