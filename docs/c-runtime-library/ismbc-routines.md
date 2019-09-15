---
title: _ismbc 常式
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbc
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
ms.openlocfilehash: 6dc14f269cafa8ccc343c5403ab0e23d319c71c3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940159"
---
# <a name="_ismbc-routines"></a>_ismbc 常式

每一個 **_ismbc** 常式都會測試指定的多位元組字元 `c` 是否符合指定的條件。

|||
|-|-|
|[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|
|[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|
|[_ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|

## <a name="remarks"></a>備註

每個 **_ismbc** 常式的測試結果都取決於作用中的多位元組字碼頁。 多位元組字碼頁具有單一位元組字母字元。 多位元組字碼頁預設為在程式啟動時從作業系統取得的系統預設 ANSI 字碼頁。 您可以查詢或變更分別與 [_getmbcp](../c-runtime-library/reference/getmbcp.md) 或 [_setmbcp](../c-runtime-library/reference/setmbcp.md) 搭配使用的多位元組字碼頁。

輸出值會受到地區設定的 `LC_CTYPE` 分類設定影響；如需詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些沒有 **_l** 尾碼的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 **_l** 尾碼的版本也一樣，只不過它們會改用傳遞的地區設定參數。

|常式傳回的值|測試條件|字碼頁 932 範例|
|-------------|--------------------|---------------------------|
|[_ismbcalnum、_ismbcalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|英數字元|只有在 `c` 是 ASCII 英文字母的單一位元組表示時，才傳回非零：請參閱 `_ismbcdigit` 和 `_ismbcalpha` 的範例。|
|[_ismbcalpha、_ismbcalpha](../c-runtime-library/reference/ismbcalnum-functions.md)|字母順序|只有在 `c` 是 ASCII 英文字母的單一位元組表示時，才傳回非零：請參閱 `_ismbcupper` 和 `_ismbclower` 的範例；或是片假名字母：0xA6<=`c`<=0xDF。|
|[_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|數字|只有在 `c` 是 ASCII 數字的單一位元組表示時，才傳回非零︰0x30<=`c`<=0x39。|
|[_ismbcgraph、_ismbcgraph_l](../c-runtime-library/reference/ismbcgraph-functions.md)|圖形|只有在 `c` 代表單一位元組，除了空白字元 ( ) 以外的任何 ASCII 或片假名可列印字元時，才傳回非零。 請參閱 `_ismbcdigit`、`_ismbcalpha` 和 `_ismbcpunct` 的範例。|
|[_ismbclegal、_ismbclegal_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|有效的多位元組字元|只在 `c` 的第一個位元組介於 0x81 - 0x9F 或 0xE0 - 0xFC 的範圍內，同時第二個位元組介於 0x40 - 0x7E 或 0x80 - FC 的範圍內時，才傳回非零。|
|[_ismbclower、_ismbclower_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|小寫字母|只有在 `c` 是 ASCII 小寫英文字母的單一位元組表示時，才傳回非零：0x61<=`c`<=0x7A.|
|[_ismbcprint、_ismbcprint_l](../c-runtime-library/reference/ismbcgraph-functions.md)|可列印|只有在 `c` 是任何 ASCII 或片假名可列印字元 (包含空白字元 ( )) 的單一位元組表示時，才傳回非零：請參閱 `_ismbcspace`、`_ismbcdigit`、`_ismbcalpha` 和 `_ismbcpunct` 的範例。|
|[_ismbcpunct、_ismbcpunct_l](../c-runtime-library/reference/ismbcgraph-functions.md)|標點符號|只有在 `c` 是代表任何 ASCII 或片假名標點符號字元的單一位元組時，才傳回非零。|
|[_ismbcblank、_ismbcblank_l、](../c-runtime-library/reference/ismbcgraph-functions.md)|空格或水平索引標籤|只有在 `c` 是代表空白字元或水平定位字元的單一位元組時，才會傳回非零︰`c`=0x20 或 `c`=0x09。|
|[_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Whitespace|只有在 `c` 是空白字元時，才傳回非零︰`c`=0x20 或 0x09<=`c`<=0x0D。|
|[_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|多位元組的符號|只在 0x8141<=`c`<=0x81AC 時，才傳回非零。|
|[_ismbcupper、_ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|大寫字母|只有在 `c` 是 ASCII 大寫英文字母的單一位元組表示時，才傳回非零：0x41<=`c`<=0x5A.|

**字碼頁 932 特定**

下列是字碼頁 932 特定的常式。

|常式傳回的值|測試條件 (限字碼頁 932)|
|-------------|-------------------------------------------|
|[_ismbchira、_ismbchira_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|雙位元組平假名：0x829F<=`c`<=0x82F1.|
|[_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|雙位元組片假名：0x8340<=`c`<=0x8396.|
|[_ismbcl0、_ismbcl0_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 非日文漢字：0x8140<=`c`<=0x889E.|
|[_ismbcl1、_ismbcl1_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 層級 1：0x889F<=`c`<=0x9872.|
|[_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 層級 2：0x989F<=`c`<=0xEA9E.|

`_ismbcl0`、`_ismbcl1` 和 `_ismbcl2` 會檢查指定的值 `c` 是否符合上表中所述的測試條件，但不會檢查 `c` 是否為有效的多位元組字元。 如果較低的位元組介於 0x00 - 0x3F、0x7F 或 0xFD - 0xFF 的範圍內，這些函式會傳回非零值，指出字元符合測試條件。 使用 [_ismbbtrail、_ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) 來測試是否已定義多位元組字元。

**END 字碼頁 932 特定**

## <a name="see-also"></a>另請參閱

[字元分類](../c-runtime-library/character-classification.md)<br/>
[is、isw 常式](../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 常式](../c-runtime-library/ismbb-routines.md)
