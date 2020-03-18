---
title: Language Strings
ms.date: 11/04/2016
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: 18a94d33f9ca382bb6c7cd77a4f2b33ed800f2c6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438245"
---
# <a name="language-strings"></a>Language Strings

[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 與 [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) 函式可以在不使用 Unicode 字碼頁的作業系統上，使用由 Windows NLS API 所支援的語言。 如需依作業系統版本分類的支援語言清單，請參閱＜[MS-LCID]：Windows 語言代碼識別碼 (LCID) 參考＞中的[附錄 A：產品行為](https://msdn.microsoft.com/library/cc233982.aspx) \(英文\)。 語言字串可以是支援語言清單的「語言」和「語言標記」欄中的任何值。 如需會列舉可用地區設定名稱與相關值之程式碼的範例，請參閱 [NLS：名稱型 API 範例](/windows/win32/intl/nls--name-based-apis-sample)。

## <a name="additional-supported-language-strings"></a>其他支援的語言字串

Microsoft C 執行階段程式庫實作也支援下列語言字串：

|語言字串|對等的地區設定名稱|
|---------------------|----------------------------|
|美國|zh-TW|
|american english|zh-TW|
|american-english|zh-TW|
|澳洲|en-AU|
|比利時|nl-BE|
|加拿大|en-CA|
|chh|zh-HK|
|chi|zh-SG|
|中文|zh|
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
|挪威文|否|
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
|瑞士|de-CH|
|uk|en-GB|
|us|zh-TW|
|usa|zh-TW|

## <a name="see-also"></a>另請參閱

[地區設定名稱、語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[國家/地區字串](../c-runtime-library/country-region-strings.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
