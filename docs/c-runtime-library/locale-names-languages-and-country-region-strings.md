---
title: 地區設定名稱、語言和國家/地區字串
description: 使用 Microsoft 通用 CRT 地區設定、語言及國家/地區字串的總覽。
ms.topic: conceptual
ms.date: 12/10/2018
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
ms.openlocfilehash: fabb3cd584af6f6e19e2ac3444c76bede299dc8d
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589922"
---
# <a name="ucrt-locale-names-languages-and-countryregion-strings"></a>UCRT 地區設定名稱、語言和國家/地區字串

[setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)、[\_create\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) 與 [\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) 函式的 *locale* 引數可使用 Windows NLS API 支援的地區設定名稱、語言、國家/地區碼與字碼頁來設定。 *locale* 引數有下列形式：

> *locale* :: "*locale-name*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|「* * \[ **\_** _國家/_ 地區 \[ __。__*字碼頁*]] "<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "__.__*字碼頁*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "C"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| ""<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| NULL

*locale-name* 格式是簡短的 IETF 標準化字串；例如， `en-US` 代表英文 (美國) 或 `bs-Cyrl-BA` 代表波士尼亞文 (斯拉夫，波士尼亞赫塞哥維納)。 這些是慣用格式。 如需 Windows 作業系統版本所支援的地區設定名稱清單，請參閱[附錄 a](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c)中的資料表**語言標記**資料行： MS-Lcid 中的產品行為（英文） \[ ： WINDOWS 語言代碼識別碼 (LCID) 參考。 這項資源列出所支援的語言、指令碼和地區部分的地區設定名稱。 如需有關具有非預設排序次序之受支援地區設定名稱的詳細資訊，請參閱 **Sort Order Identifiers (排序次序識別項)** 中 [Locale name](地區設定名稱) [](/windows/win32/Intl/sort-order-identifiers)一欄。 Windows 10 或更新版本會允許對應至有效 [BCP-47](https://tools.ietf.org/html/bcp47) 語言標記的地區設定名稱。 例如，`jp-US` 為有效的 BCP-47 標記，但就地區設定功能性而言，它基本上等同於 `US`。

*language* \[ **\_** _國家/_ 地區的語言 \[ __。__*字碼頁*]]當使用語言字串或語言字串和國家或地區字串建立地區設定時，表單會儲存在分類的地區設定中。 [Language Strings](../c-runtime-library/language-strings.md)中描述的一組受支援語言字串，以及 [Country/Region Strings](../c-runtime-library/country-region-strings.md)所列的受支援國家與地區字串清單。 如果指定的語言和指定的國家或地區沒有關聯，則指定的國家或地區的預設語言會儲存在地區設定中。 我們不建議內嵌於程式碼或對儲存體序列化的地區設定字串使用此格式，因為這些字串比地區設定名稱格式更容易被作業系統更新變更。

*code-page* 是與地區設定相關聯的 ANSI/OEM 字碼頁。 當您以語言或是以語言和國家/地區指定地區設定時，便會為您判定字碼頁。 特殊值 `.ACP` 會指定國家/地區的 ANSI 字碼頁。 特殊值 `.OCP` 會指定國家/地區的 OEM 字碼頁。 例如，如果您指定 `"Greek_Greece.ACP"` 作為地區設定，地區設定便會儲存為 `Greek_Greece.1253` (希臘文的 ANSI 字碼頁)。如果您指定 `"Greek_Greece.OCP"` 作為地區設定，則會儲存為 `Greek_Greece.737` (希臘文的 OEM 字碼頁)。 如需字碼頁的詳細資訊，請參閱 [Code Pages](../c-runtime-library/code-pages.md)。 如需 Windows 上受支援字碼頁的清單，請參閱 [Code Page Identifiers (字碼頁識別項)](/windows/win32/Intl/code-page-identifiers)。

如果您僅使用字碼頁來指定地區設定，就會使用 [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename) 回報的使用者預設語言和國家/地區。 例如，如果您指定 `".1254"` (ANSI 土耳其文) 作為配置英文 (美國) 使用者的地區設定，儲存的地區設定便是 `English_United States.1254`。 因為這可能會導致不一致的行為，所以不建議使用這個格式。

`C` 的 *locale* 引數值會指定 C 轉譯的最小 ANSI 符合環境。 地區設定會 `C` 假設每個 **`char`** 資料類型都是1個位元組，而其值一律小於256。 如果 *locale* 指向空字串，地區設定即為由實作所定義的原生環境。

藉由使用 `setlocale` 分類，可以為 `_wsetlocale` 和 `LC_ALL` 函式同時指定所有地區設定分類。 藉由使用具有此格式的地區設定引數，您可以將分類全設定為相同的地區設定，或是為每個分類個別設定：

> *LC-ALL-規範* ：： *locale*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| \[**LC_COLLATE=**_locale_]\[**;LC_CTYPE=**_locale_]\[**;LC_MONETARY=**_locale_]\[**;LC_NUMERIC=**_locale_]\[**;LC_TIME=**_locale_]

您可以指定多個分類類型，並以分號隔開。 未指定的分類類型會使用目前的地區設定。 例如，這個程式碼片段會將所有分類的目前地區設定設為 `de-DE`，然後將分類 `LC_MONETARY` 設為 `en-GB` ，並將 `LC_TIME` 設為 `es-ES`：

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```

## <a name="utf-8-support"></a>UTF-8 支援

您可以在地區設定字串中使用 UTF-8 字碼頁來啟用 UTF-8 支援。 如需詳細資訊，請參閱的[Utf-8 支援一節 `setlocale` ](../c-runtime-library/reference/setlocale-wsetlocale.md#utf-8-support) 。

## <a name="see-also"></a>另請參閱

[C 執行時間程式庫參考](../c-runtime-library/c-run-time-library-reference.md)<br/>
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[語言字串](../c-runtime-library/language-strings.md)<br/>
[國家/地區字串](../c-runtime-library/country-region-strings.md)
