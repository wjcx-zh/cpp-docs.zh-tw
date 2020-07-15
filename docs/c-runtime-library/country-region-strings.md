---
title: 國家-地區字串
ms.date: 11/04/2016
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: ea0ac6ab89179683d04f6b6233c6fa1996e51a1f
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373563"
---
# <a name="countryregion-strings"></a>國家/地區字串

國家/地區字串可以結合語言字串，建立適合 `setlocale`、 `_wsetlocale`、 `_create_locale`和 `_wcreate_locale` 函式的地區設定規格。 如需各種 Windows 作業系統版本支援的國家/地區名稱清單，請參閱[附錄 A：產品行為](https://docs.microsoft.com/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c)（MS-lcid）： Windows 語言代碼識別碼（LCID）參考中資料表的**語言**、**位置**和**語言標記**資料行 \[ 。 如需會列舉可用地區設定名稱與相關值之程式碼的範例，請參閱 [NLS：名稱型 API 範例](/windows/win32/intl/nls--name-based-apis-sample)。

## <a name="additional-supported-country-and-region-strings"></a>其他支援的國家與地區設定字串

Microsoft C 執行階段程式庫實作也支援下列其他國家/地區字串和縮寫：

|國家/地區字串|縮寫|對等的地區設定名稱|
|----------------------------|------------------|----------------------------|
|美洲|USA|en-US|
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
|斯洛伐克文|SVK|sk-SK|
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
