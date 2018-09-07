---
title: 地區設定名稱、語言和國家/地區字串 | Microsoft Docs
ms.custom: ''
ms.date: 08/13/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.strings
dev_langs:
- C++
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c072074c24466458ebd19e1335f49169c5c22bd5
ms.sourcegitcommit: 3b78ddea5fd3e22b7c5cd2d787ec71a518a52223
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2018
ms.locfileid: "42578420"
---
# <a name="locale-names-languages-and-countryregion-strings"></a>地區設定名稱、語言和國家/地區字串

針對 `setlocale` 和 `_create_locale` 函式的 *locale* 引數，可使用 Windows NLS API 支援的地區設定名稱、語言、國家/地區碼和字碼頁來設定。 *locale* 引數有下列形式：

> *locale* :: "*locale_name*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "*language*\[\_*country-region*]\[.*code_page*]]"  
&nbsp;&nbsp;&nbsp;&nbsp;| ".*code_page*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "C"  
&nbsp;&nbsp;&nbsp;&nbsp;| ""  
&nbsp;&nbsp;&nbsp;&nbsp;| NULL  

建議使用地區設定名稱格式，例如使用 `en-US` 來表示英文 (美國)，或使用 `bs-Cyrl-BA` 來表示波士尼亞文 (斯拉夫，波士尼亞赫塞哥維納)。 [地區設定名稱](/windows/desktop/Intl/locale-names)中描述的一組地區設定名稱。 如需依作業系統版本分類的支援地區設定名稱清單，請參閱＜[MS-LCID]：Windows 語言代碼識別碼 (LCID) 參考＞中的[附錄 A：產品行為](https://msdn.microsoft.com/library/cc233982.aspx) \(英文\) 中之表格的 [Language tag] \(語言標記\) 欄。 這項資源列出所支援的語言、指令碼和地區部分的地區設定名稱。 如需有關具有非預設排序次序之受支援地區設定名稱的詳細資訊，請參閱 **Sort Order Identifiers (排序次序識別項)** 中 [Locale name(地區設定名稱) ](/windows/desktop/Intl/sort-order-identifiers)一欄。 Windows 10 或更新版本會允許對應至有效 BCP-47 語言標記的地區設定名稱。 例如，`jp-US` 為有效的 BCP-47 標記，但就地區設定功能性而言，它基本上等同於 `US`。

當使用語言字串或語言字串和國家/地區字串建立地區設定時， *語言*[*_國家/地區*[.*字碼頁*]] form is stored in the locale setting for a category when a 語言 string, or 語言 string and country/region string, is used to create the locale. [Language Strings](../c-runtime-library/language-strings.md)中描述的一組受支援語言字串，以及 [Country/Region Strings](../c-runtime-library/country-region-strings.md)所列的受支援國家/地區字串清單。 如果指定的語言和指定的國家/地區沒有關聯，則指定的國家/地區的預設語言會儲存在地區設定中。 我們不建議內嵌於程式碼或對儲存體序列化的地區設定字串使用此格式，因為這些字串比地區設定名稱格式更容易被作業系統更新變更。

字碼頁是與地區設定相關聯的 ANSI/OEM 字碼頁。 當您以語言或是以語言和國家/地區指定地區設定時，便會為您判定字碼頁。 特殊值 `.ACP` 會指定國家/地區的 ANSI 字碼頁。 特殊值 `.OCP` 會指定國家/地區的 OEM 字碼頁。 例如，如果您指定 `"Greek_Greece.ACP"` 作為地區設定，地區設定便會儲存為 `Greek_Greece.1253` (希臘文的 ANSI 字碼頁)。如果您指定 `"Greek_Greece.OCP"` 作為地區設定，則會儲存為 `Greek_Greece.737` (希臘文的 OEM 字碼頁)。 如需字碼頁的詳細資訊，請參閱 [Code Pages](../c-runtime-library/code-pages.md)。 如需 Windows 上受支援字碼頁的清單，請參閱 [Code Page Identifiers (字碼頁識別項)](/windows/desktop/Intl/code-page-identifiers)。

如果您僅使用字碼頁來指定地區設定，就會使用 [GetUserDefaultLocaleName](/windows/desktop/api/winnls/nf-winnls-getuserdefaultlocalename) 回報的使用者預設語言和國家/地區。 例如，如果您指定 `".1254"` (ANSI 土耳其文) 作為配置英文 (美國) 使用者的地區設定，儲存的地區設定便是 `English_United States.1254`。 因為這可能會導致不一致的行為，所以不建議使用這個格式。

`C` 的 *locale* 引數值會指定 C 轉譯的最小 ANSI 符合環境。 `C` 地區設定會假設每個 **char** 資料類型都是 1 位元組，而其值永遠小於 256。 如果 *locale* 指向空字串，地區設定即為由實作所定義的原生環境。

藉由使用 `setlocale` 分類，可以為 `_wsetlocale` 和 `LC_ALL` 函式同時指定所有地區設定分類。 藉由使用具有此格式的地區設定引數，您可以將分類全設定為相同的地區設定，或是為每個分類個別設定：

> LC_ALL_specifier :: locale  
&nbsp;&nbsp;&nbsp;&nbsp;| [LC_COLLATE=locale][;LC_CTYPE=locale][;LC_MONETARY=locale][;LC_NUMERIC=locale][;LC_TIME=locale]

您可以指定多個分類類型，並以分號隔開。 未指定的分類類型會使用目前的地區設定。 例如，這個程式碼片段會將所有分類的目前地區設定設為 `de-DE`，然後將分類 `LC_MONETARY` 設為 `en-GB` ，並將 `LC_TIME` 設為 `es-ES`：

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```

## <a name="see-also"></a>另請參閱

[C 執行階段程式庫參考](../c-runtime-library/c-run-time-library-reference.md)  
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)  
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)  
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)  
[語言字串](../c-runtime-library/language-strings.md)  
[國家/地區字串](../c-runtime-library/country-region-strings.md)  
