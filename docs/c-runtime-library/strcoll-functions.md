---
title: strcoll 函式
ms.date: 11/04/2016
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- strcoll
helpviewer_keywords:
- code pages, using for string comparisons
- string comparison [C++], culture-specific
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
ms.openlocfilehash: c6b4b45184ea4cc3320f3de069884ac084c7cfcd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450228"
---
# <a name="strcoll-functions"></a>strcoll 函式

每個 `strcoll` 與 `wcscoll` 函式皆會根據目前所用地區設定字碼頁的 `LC_COLLATE` 類別設定來比較兩個字串。 每個 `_mbscoll` 函式皆會根據目前所用的多位元組字碼頁來比較兩個字串。 因此，只有在目前字碼頁中字元集順序與字母字元順序 (亦即字母在字典中的順序) 不同，且想要比較這項差異時，才應該使用 `coll` 函式來比較字串。 使用對應的 `cmp` 函式，以便僅測試字串的相等程度。

### <a name="strcoll-functions"></a>strcoll 函式

|SBCS|Unicode|MBCS|描述|
|----------|-------------|----------|-----------------|
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|比較兩個字串|
|[_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_mbsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|比較兩個字串 (不區分大小寫)|
|[_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_mbsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|比較兩個字串的前 `count` 個字元|
|[_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_mbsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|比較兩個字串的前 `count` 個字元 (不區分大小寫)|

## <a name="remarks"></a>備註

這些函式 (`strcoll`、`stricoll`、`_strncoll` 與 `_strnicoll`) 的單一位元組字元 (SBCS) 版本，會根據目前地區設定的 `LC_COLLATE` 類別設定，以比較 `string1` 與 `string2`。 這些函式不同於對應的 `strcmp` 函式，差異在於 `strcoll` 函式使用提供比較序列的地區設定字碼頁資訊。 針對字元集順序與字母字元順序 (亦即字母在字典中的順序) 不同的地區設定，若要比較其中的字串，應該使用 `strcoll` 函式，而不是對應的 `strcmp` 函式。 如需 `LC_COLLATE` 的詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。

針對某些字碼頁和對應的字元集，字元集中的字元順序可能與字母字元順序 (亦即字母在字典中的順序) 不同。 在 "C" 地區設定中則不然：ASCII 字元集中的字元順序會與詞典編纂的字元順序相同。 不過，某些歐洲字碼頁中的字元順序卻不同，例如，字元 'a' (值 0x61) 在字元集中排在字元 'ä' (值 0xE4) 之前，但在詞典編纂上，字元 'a' 卻排在字元 'ä' 之後。 若要執行此類的字母順序比較，請使用 `strcoll`，而非使用 `strcmp`。 或者，您可以在原始字串上使用 `strxfrm`，然後在產生的字串上使用 `strcmp`。

`strcoll`、`stricoll`、`_strncoll` 與 `_strnicoll` 會根據目前所用的地區設定字碼頁，自動處理多位元組字元字串，及對應的寬字元 (Unicode)。 不過，這些函式的多位元組字元 (MBCS) 版本，會根據目前所用的多位元組字碼頁，以字元為基礎來比較字串。

因為 `coll` 函式會以詞典編纂方式對照字串以進行比較，而 `cmp` 函式只會測試字串是否相等，所以 `coll` 函式比對應的 `cmp` 版本慢很多。 因此，只有在目前字碼頁中字元集順序與字母字元順序 (亦即字母在字典中的順序) 不同，且想要比較此字串差異時，才應該使用 `coll` 函式。

## <a name="see-also"></a>請參閱

[地區設定](../c-runtime-library/locale.md)<br/>
[字串操作](../c-runtime-library/string-manipulation-crt.md)<br/>
[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcmp、wcscmp、_mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)