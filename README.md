[![REUSE status](https://api.reuse.software/badge/github.com/SAP/abap-open-source-namespaces)](https://api.reuse.software/info/github.com/SAP/abap-open-source-namespaces)

# ABAP Open Source Namespaces

## About this project

In response to the suggestions and feedback from our community, SAP made available dedicated [ABAP Open Source Namespaces](https://me.sap.com/namespaces/opensource). The list of already existing namespaces is [available in the Development Namespace Application](https://me.sap.com/namespaces/opensource). In addition, we list them here, including the development and repair keys for DEMOSYSTEM installations like the [ABAP Cloud Developer Trial](https://community.sap.com/t5/technology-blogs-by-sap/abap-cloud-developer-trial-2022-available-now/ba-p/13598069). If you would like to create an own namespace for an open source project, please reach out to the [SAP Open Source Program Office via e-mail](mailto:ospo@sap.com). We’ll be happy to get your project onboarded.
If you have any questions or feedback regarding ABAP Open Source Namespaces, feel free to post a issue here or [reach out to us via e-mail](mailto:ospo@sap.com).

## Requirements and Setup

There are no specific requirements for the request of a new ABAP Open Source Namespace. As outlined [in the official documentation](https://support.sap.com/content/dam/support/en_us/library/ssp/my-support/keys/new-request-namespace.pdf), please [reach out to the SAP Open Source Program Office via e-mail](mailto:ospo@sap.com) and mention a few details about your project to get the namespace approved and created.

## Existing ABAP Open Source Namespaces

**Note:** The development keys listed below are exclusively for ABAP Cloud Developer Trial systems (or any others with 'DEMOSYSTEM' as installation ID). For all other systems, please use the [Development Namespace Application](https://me.sap.com/namespaces/opensource). The given repair keys should work on any system.

| Namespace | Description | Project URL | DEMOSYSTEM development key | Repair key |
| --------- | ----------- | ----------- | -------------------------- | --------------------- |
| /ABAPGIT/ | Git client for ABAP | https://github.com/abapGit | 23994246593733623882 | 40091955262536808301 |
| /APMG/ | Package Manager for ABAP | https://github.com/abapPM | 19377473852358672491 | 41813564412598342476 |
| /ATRM/ | Transport Request Manager | https://github.com/RegestaItalia/trm-docs | 18531191373370851361 | 00211665563784583720 |
| /AWSEX/ | AWS Example Code Library | https://github.com/awsdocs/aws-doc-sdk-examples | 14651386910339465450 | 38127449234049228390 |
| /AWSLABS/ | AWS Labs | https://github.com/awslabs | 08687220553514260293 | 06678115934145756969 |
| /AWSSAMP/ | AWS Samples | https://github.com/aws-samples | 13391533940099332908 | 39944149741907428904 |
| /AWSSOL/ | AWS Solution Library | https://github.com/aws-solutions-library-samples | 08428002090177052957 | 06628540192866312031 |
| /C2A/ | cds2alv - Generate ALV List Reports for CDS Views | https://github.com/rku-it-GmbH/cds2alv | 03688288682419678361 | 37246368571464575750 |
| /CC4A/ | Code Pal for ABAP Cloud | https://github.com/SAP/code-pal-for-abap-cloud | 19443791570447289803 | 22229904900326563203 |
| /OTCT/ | Open Tax Compliance Technologies | https://github.com/openTCT | 06491018313941499730 | 20057332490737420344 |
| /RBGRP/ | Rule-based Group | https://github.com/rulebased-group | 01116174434106589083 | 04764198110284863201 |
| /XLWB/ | XLSX Workbench | https://github.com/igor-borodin/XLWB | 06882850232695308586 | 40644561731137480400 |

## Automated Import to ABAP Cloud Developer Trial

You can import the namespaces including development and repair keys into your A4H System using [abapGit](https://github.com/abapGit/abapGit).

As a prerequisite, you needs to implement the following [abapGit exit](https://docs.abapgit.org/user-guide/reference/exits.html#change-supported-data-objects) to allow write access to the SAP Namespace tables for systems with `DEMOSYSTEM` license number.


```abap
METHOD zif_abapgit_user_exit~change_supported_data_objects.

  DATA lv_license_num TYPE c LENGTH 10.
  DATA ls_object LIKE LINE OF ct_objects.

  CALL FUNCTION 'SLIC_GET_LICENCE_NUMBER'
    IMPORTING
      license_number = lv_license_num.

  IF lv_license_num = 'DEMOSYSTEM'.
    ls_object-type = 'TABU'.
    ls_object-name = 'TRNSPACE*'.
    INSERT ls_object INTO TABLE ct_objects.
  ENDIF.

ENDMETHOD.
```

Once the exit is active, start abapGit, create an [Online Repository](https://docs.abapgit.org/user-guide/projects/online/install.html) for `https://github.com/SAP/abap-open-source-namespaces` (use any new local package), and pull the namespace data into your system.

## Support, Feedback, Contributing

This project is open to feature requests/suggestions, bug reports etc. via [GitHub issues](https://github.com/SAP/abap-open-source-namespaces/issues). Contribution and feedback are encouraged and always welcome. For more information about how to contribute, the project structure, as well as additional contribution information, see our [Contribution Guidelines](CONTRIBUTING.md).

## Security / Disclosure

If you find any bug that may be a security problem, please follow our instructions at [in our security policy](https://github.com/SAP/abap-open-source-namespaces/security/policy) on how to report it. Please do not create GitHub issues for security-related doubts or problems.

## Code of Conduct

We as members, contributors, and leaders pledge to make participation in our community a harassment-free experience for everyone. By participating in this project, you agree to abide by its [Code of Conduct](https://github.com/SAP/.github/blob/main/CODE_OF_CONDUCT.md) at all times.

## Licensing

Copyright 2024 SAP SE or an SAP affiliate company and abap-open-source-namespaces contributors. Please see our [LICENSE](LICENSE) for copyright and license information. Detailed information including third-party components and their licensing/copyright information is available [via the REUSE tool](https://api.reuse.software/info/github.com/SAP/abap-open-source-namespaces).
