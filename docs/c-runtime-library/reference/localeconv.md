---
title: localeconv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- localeconv
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- localeconv
dev_langs:
- C++
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe3cc75430dfa9bb2f4c5513f4b2ba5a2fd1c4c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405246"
---
# <a name="localeconv"></a>localeconv

取得地區設定上的詳細資訊。

## <a name="syntax"></a>語法

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>傳回值

**localeconv**傳回類型的區域分布中物件的指標[結構 lconv](../../c-runtime-library/standard-types.md)。 物件中包含的值從在執行緒區域儲存區中的地區設定來複製和後續呼叫會覆寫**localeconv**。 此物件中的值所做的變更進行修改的地區設定。 呼叫[setlocale](setlocale-wsetlocale.md)與*類別*值**LC_ALL**， **LC_MONETARY**，或**LC_NUMERIC**覆寫結構的內容。

## <a name="remarks"></a>備註

**Localeconv**函式會取得目前的地區設定的數值格式設定的詳細的資訊。 這項資訊會儲存在類型為 **lconv** 的結構中。 於 LOCALE.H 中定義的 **Lconv** 結構，包含下列成員︰

|欄位|意義|
|-|-|
decimal_point，<br/>_W_decimal_point|小數點 nonmonetary 數量的字元指標。
thousands_sep，<br/>_W_thousands_sep|指向字元分隔 nonmonetary 數量的小數點左邊數字的群組。
群組|指標**char**-調整大小的整數，其中包含每個群組中 nonmonetary 數量的數字的大小。
int_curr_symbol，<br/>_W_int_curr_symbol|到目前的地區設定的國際貨幣符號的指標。 前三個字元依照「ISO 4217 貨幣和資金代碼」標準的定義，指定字母國際貨幣符號。 第四個字元 (緊接在 Null 字元之前) 會分隔國際貨幣符號與貨幣的數量。
currency_symbol，<br/>_W_currency_symbol|到目前的地區設定的本地貨幣符號的指標。
mon_decimal_point，<br/>_W_mon_decimal_point|小數點金錢數量的字元指標。
mon_thousands_sep，<br/>_W_mon_thousands_sep|指標的金錢數量中小數點左邊數字群組分隔符號。
mon_grouping|指標**char**-調整大小的整數，其中包含每個群組中金錢數量的數字的大小。
positive_sign，<br/>_W_positive_sign|表示非負值貨幣數量之正負號的字串。
negative_sign，<br/>_W_negative_sign|表示負值貨幣數量之正負號的字串。
int_frac_digits|國際格式化貨幣數量之小數點右邊的數字數目。
frac_digits|格式化貨幣數量之小數點右邊的數字數目。
p_cs_precedes|如果貨幣符號在非負值格式化貨幣數量的值之前，請設定為 1。 如果符號在值之後，請設定為 0。
p_sep_by_space|如果貨幣符號與非負值格式化貨幣數量之間以空格分隔，請設定為 1。 如果沒有空格分隔，請設定為 0。
n_cs_precedes|如果貨幣符號在負值格式化貨幣數量的值之前，請設定為 1。 如果符號在值之後，請設定為 0。
n_sep_by_space|如果貨幣符號與負值格式化貨幣數量之間以空格分隔，請設定為 1。 如果沒有空格分隔，請設定為 0。
p_sign_posn|非負值格式化貨幣數量的正號位置。
n_sign_posn|負值的格式化貨幣數量的正號位置。

指定的成員，除非**lconv**有結構`char *`和`wchar_t *`版本都是字串指標。 任何一項都等於 **""** (或**L""** 如**wchar_t \*** ) 是長度為零，或在目前的地區設定中不支援。 請注意， **decimal_point**和 **_W_decimal_point**一律支援與非零長度。

**Char**結構成員是小型非負數數字，不是字元。 任何一項若等於 **CHAR_MAX**，則其於目前地區設定中不受支援。

值**分組**和**mon_grouping**解譯根據下列規則：

- **CHAR_MAX** -不會執行任何進一步分組。

- 0-使用上一個項目，每個其餘的數字。

- *n* -組成目前群組的位數。 檢查下一個項目，以在目前群組之前判斷下一個數字群組的大小。

**int_curr_symbol** 的值會根據下列規則解釋：

- 前三個字元依照「ISO 4217 貨幣和資金代碼」標準之定義，指定字母國際貨幣符號。

- 第四個字元 (緊接在 Null 字元之前) 會分隔國際貨幣符號與貨幣的數量。

**p_cs_precedes** 和 **n_cs_precedes** 的值會根據下列規則解釋 (**n_cs_precedes** 規則位於括弧內)：

- 0-貨幣符號會遵循負值 （負） 格式化貨幣值的值。

- 1-貨幣符號前面會有非負值 （負） 格式化貨幣值的值。

**p_sep_by_space** 和 **n_sep_by_space** 的值會根據下列規則解釋 (**n_sep_by_space** 規則位於括弧內)：

- 0-貨幣符號會分隔值乘以負值 （負） 格式化貨幣值的空間。

- 1-貨幣符號和負值 （負） 格式化貨幣值的值之間沒有空格分隔。

**p_sign_posn** 和 **n_sign_posn** 的值根據下列規則解釋：

- 0-括號括住數量和貨幣符號。

- 1-符號的字串前面會有數量和貨幣符號。

- 2-符號的字串會遵循數量和貨幣符號。

- 3-符號的字串前面貨幣符號。

- 4-正負號的立即字串如下所示的貨幣符號。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[地區設定](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll 函式](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
