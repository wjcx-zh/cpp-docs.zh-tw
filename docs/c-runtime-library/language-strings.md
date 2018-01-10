---
title: "語言字串 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.strings
dev_langs: C++
helpviewer_keywords: language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 85f0c9b06ae85128209f06d95375e09043b3f9c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="language-strings"></a>語言字串
`setlocale` 和 `_create_locale` 函式可以在不使用 Unicode 字碼頁的作業系統上，使用由 Windows NLS API 所支援的語言。 如需依作業系統版本分類的支援語言清單，請參閱[國家語言支援 (NLS) API 參考](https://www.microsoft.com/resources/msdn/goglobal/default.mspx) \(英文\)。 語言字串可以是支援語言清單的「語言」和「語言名稱縮寫」欄位中的任何值。 如需依作業系統版本分類的語言支援詳細資訊，請參閱＜[MS-LCID]：Windows 語言代碼識別碼 (LCID) 參考＞中的[附錄 A：產品行為](http://msdn.microsoft.com/goglobal/bb896001.aspx) \(英文\)   
  
C 執行階段程式庫實作也支援下列語言字串：  
  
|語言字串|對等的地區設定名稱|  
|---------------------|----------------------------|  
|american|zh-TW|  
|american english|zh-TW|  
|american-english|zh-TW|  
|australian|en-AU|  
|belgian|nl-BE|  
|canadian|en-CA|  
|chh|zh-HK|  
|chi|zh-SG|  
|chinese|zh|  
|chinese-hongkong|zh-HK|  
|chinese-simplified|zh-CN|  
|chinese-singapore|zh-SG|  
|chinese-traditional|zh-TW|  
|dutch-belgian|nl-BE|  
|english-american|zh-TW|  
|english-aus|en-AU|  
|english-belize|en-BZ|  
|english-can|en-CA|  
|english-caribbean|en-029|  
|english-ire|en-IE|  
|english-jamaica|en-JM|  
|english-nz|en-NZ|  
|english-south africa|en-ZA|  
|english-trinidad y tobago|en-TT|  
|english-uk|en-GB|  
|english-us|zh-TW|  
|english-usa|zh-TW|  
|french-belgian|fr-BE|  
|french-canadian|fr-CA|  
|french-luxembourg|fr-LU|  
|french-swiss|fr-CH|  
|german-austrian|de-AT|  
|german-lichtenstein|de-LI|  
|german-luxembourg|de-LU|  
|german-swiss|de-CH|  
|irish-english|en-IE|  
|italian-swiss|it-CH|  
|norwegian|否|  
|norwegian-bokmal|nb-NO|  
|norwegian-nynorsk|nn-NO|  
|portuguese-brazilian|pt-BR|  
|spanish-argentina|es-AR|  
|spanish-bolivia|es-BO|  
|spanish-chile|es-CL|  
|spanish-colombia|es-CO|  
|spanish-costa rica|es-CR|  
|spanish-dominican republic|es-DO|  
|spanish-ecuador|es-EC|  
|spanish-el salvador|es-SV|  
|spanish-guatemala|es-GT|  
|spanish-honduras|es-HN|  
|spanish-mexican|es-MX|  
|spanish-modern|es-ES|  
|spanish-nicaragua|es-NI|  
|spanish-panama|es-PA|  
|spanish-paraguay|es-PY|  
|spanish-peru|es-PE|  
|spanish-puerto rico|es-PR|  
|spanish-uruguay|es-UY|  
|spanish-venezuela|es-VE|  
|swedish-finland|sv-FI|  
|swiss|de-CH|  
|uk|en-GB|  
|us|zh-TW|  
|usa|en-US|  
  
## <a name="see-also"></a>請參閱  
 [地區設定名稱、語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [國家/地區字串](../c-runtime-library/country-region-strings.md)   
 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)