---
title: 國家-地區字串
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: 49eb6bc4473d9e54c06c3bf9290f8c3c96640415
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500238"
---
# <a name="countryregion-strings"></a>Country/Region Strings

國家/地區字串可以結合語言字串，建立適合 `setlocale`、 `_wsetlocale`、 `_create_locale`和 `_wcreate_locale` 函式的地區設定規格。 如需各 Windows 作業系統支援的國家與地區名稱清單，請參閱 [Language] \(語言\)  、[Location] \(位置\)  與 [Language tag] \(語言標記\)  欄 (在[附錄 A：產品行為](https://msdn.microsoft.com/library/cc233982.aspx)) (在 [MS-LCID]：Windows 語言代碼識別碼 (LCID) 參考) 中。 如需會列舉可用地區設定名稱與相關值之程式碼的範例，請參閱 [NLS：名稱型 API 範例](/windows/win32/intl/nls--name-based-apis-sample)。

## <a name="additional-supported-country-and-region-strings"></a>其他支援的國家與地區設定字串

Microsoft C 執行階段程式庫實作也支援下列其他國家/地區字串和縮寫：

|國家/地區字串|縮寫|對等的地區設定名稱|
|----------------------------|------------------|----------------------------|
|美洲|USA|zh-TW|
|英國|GBR|en-GB|
|中國|CHN|zh-CN|
|捷克|CZE|cs-CZ|
|英國|GBR|en-GB|
|英國|GBR|en-GB|
|荷蘭|NLD|nl-NL|
|香港特別行政區|HKG|zh-HK|
|紐西蘭|NZL|en-NZ|
|nz|NZL|en-NZ|
|中華人民共和國|CHN|zh-CN|
|pr-china|CHN|zh-CN|
|波多黎各|PRI|es-PR|
|斯洛伐克|SVK|sk-SK|
|南非|ZAF|af-ZA|
|南韓|KOR|ko-KR|
|南非|ZAF|af-ZA|
|南韓|KOR|ko-KR|
|千里達及托巴哥|TTO|en-TT|
|uk|GBR|en-GB|
|英國|GBR|en-GB|
|美國|USA|en-US|
|us|USA|en-US|

## <a name="see-also"></a>另請參閱

[地區設定名稱、語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[語言字串](../c-runtime-library/language-strings.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
