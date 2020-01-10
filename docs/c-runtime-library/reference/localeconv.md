---
title: localeconv
ms.date: 11/04/2016
api_name:
- localeconv
api_location:
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localeconv
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
ms.openlocfilehash: ca7113903e1ed6e9ffb94bef79beba41e09bfb71
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953353"
---
# <a name="localeconv"></a>localeconv

取得地區設定上的詳細資訊。

## <a name="syntax"></a>語法

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>傳回值

**localeconv**會傳回[結構 lconv](../../c-runtime-library/standard-types.md)類型之實心物件的指標。 物件中包含的值會從執行緒區域儲存區中的地區設定複製，並可由後續呼叫**localeconv**來覆寫。 對這個物件中的值所做的變更不會修改地區設定。 呼叫具有**LC_ALL**、 **LC_MONETARY**或**LC_NUMERIC** *分類*值的[setlocale](setlocale-wsetlocale.md)會覆寫結構的內容。

## <a name="remarks"></a>備註

**Localeconv**函數會取得有關目前地區設定之數值格式的詳細資訊。 這項資訊會儲存在類型為 **lconv** 的結構中。 於 LOCALE.H 中定義的 **Lconv** 結構，包含下列成員︰

|欄位|意義|
|-|-|
decimal_point,<br/>_W_decimal_point|非貨幣數量的小數點字元指標。
thousands_sep,<br/>_W_thousands_sep|字元的指標，用來分隔非貨幣數量的小數點左邊數位群組。
群組|**Char**大小的整數指標，其中包含非貨幣數量中每個數位群組的大小。
int_curr_symbol,<br/>_W_int_curr_symbol|目前地區設定的國際貨幣符號指標。 前三個字元依照「ISO 4217 貨幣和資金代碼」標準的定義，指定字母國際貨幣符號。 第四個字元 (緊接在 Null 字元之前) 會分隔國際貨幣符號與貨幣的數量。
currency_symbol,<br/>_W_currency_symbol|目前地區設定的當地貨幣符號指標。
mon_decimal_point,<br/>_W_mon_decimal_point|貨幣數量之小數點字元的指標。
mon_thousands_sep,<br/>_W_mon_thousands_sep|貨幣數量中小數點左邊數位群組的分隔符號指標。
mon_grouping|**Char**大小的整數指標，其中包含貨幣數量中每個數位群組的大小。
positive_sign,<br/>_W_positive_sign|表示非負值貨幣數量之正負號的字串。
negative_sign,<br/>_W_negative_sign|表示負值貨幣數量之正負號的字串。
int_frac_digits|國際格式化貨幣數量之小數點右邊的數字數目。
frac_digits|格式化貨幣數量之小數點右邊的數字數目。
p_cs_precedes|如果貨幣符號在非負值格式化貨幣數量的值之前，請設定為 1。 如果符號在值之後，請設定為 0。
p_sep_by_space|如果貨幣符號與非負值格式化貨幣數量之間以空格分隔，請設定為 1。 如果沒有空格分隔，請設定為 0。
n_cs_precedes|如果貨幣符號在負值格式化貨幣數量的值之前，請設定為 1。 如果符號在值之後，請設定為 0。
n_sep_by_space|如果貨幣符號與負值格式化貨幣數量之間以空格分隔，請設定為 1。 如果沒有空格分隔，請設定為 0。
p_sign_posn|非負值格式化貨幣數量的正號位置。
n_sign_posn|負值的格式化貨幣數量的正號位置。

除了指定以外，具有`char *`和`wchar_t *`版本之**lconv**結構的成員是指向字串的指標。 其中任何等於 **""** （或**wchar_t** <strong>\*</strong>的**L "** "）的任何都是零長度，或在目前的地區設定中不受支援。 請注意， **decimal_point**和 **_W_decimal_point**一律受支援且長度不為零。

結構的**char**成員是小型非負數值，而不是字元。 任何一項若等於 **CHAR_MAX**，則其於目前地區設定中不受支援。

**群組**和**mon_grouping**的值會根據下列規則來進行轉譯：

- **CHAR_MAX** -不要執行任何進一步的分組。

- 0-針對剩餘的每個數位使用 previous 元素。

- *n* -組成目前群組的數位數目。 檢查下一個項目，以在目前群組之前判斷下一個數字群組的大小。

**int_curr_symbol** 的值會根據下列規則解釋：

- 前三個字元依照「ISO 4217 貨幣和資金代碼」標準之定義，指定字母國際貨幣符號。

- 第四個字元 (緊接在 Null 字元之前) 會分隔國際貨幣符號與貨幣的數量。

**p_cs_precedes** 和 **n_cs_precedes** 的值會根據下列規則解釋 (**n_cs_precedes** 規則位於括弧內)：

- 0-貨幣符號會在非負值（負值）格式化貨幣值的值之後。

- 1-貨幣符號會在非負值（負值）格式化貨幣值的值之前。

**p_sep_by_space** 和 **n_sep_by_space** 的值會根據下列規則解釋 (**n_sep_by_space** 規則位於括弧內)：

- 0-貨幣符號與非負值（負）格式化貨幣值的值是以空格分隔。

- 1-貨幣符號與非負值（負值）格式化貨幣值之間沒有空格分隔。

**p_sign_posn** 和 **n_sign_posn** 的值根據下列規則解釋：

- 0-括弧環繞數量和貨幣符號。

- 1-正負號字串在數量和貨幣符號之前。

- 2-符號字串會遵循數量和貨幣符號。

- 3-符號字串緊接在貨幣符號之前。

- 4-符號字串緊接在貨幣符號之後。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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
