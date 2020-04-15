---
title: localeconv
ms.date: 4/2/2020
api_name:
- localeconv
- _o_localeconv
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a617980d60b3a12c06b30aab6cd457792a1aa770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342149"
---
# <a name="localeconv"></a>localeconv

取得地區設定上的詳細資訊。

## <a name="syntax"></a>語法

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>傳回值

**localeconv**傳回指向類型[結構 lconv](../../c-runtime-library/standard-types.md)的填充物件的指標。 物件中包含的值從線程本地存儲中的區域設置複製,並且可以通過後續調用**localeconv**覆蓋。 對此物件中的值所做的更改不會修改區域設置。 使用**LC_ALL、LC_MONETARY**或**LC_NUMERIC**的*類別*值[設置局部性的](setlocale-wsetlocale.md)調用**LC_MONETARY**覆蓋結構的內容。

## <a name="remarks"></a>備註

**localeconv**函數獲取有關當前區域設置的數位格式的詳細資訊。 這項資訊會儲存在類型為 **lconv** 的結構中。 於 LOCALE.H 中定義的 **Lconv** 結構，包含下列成員︰

|欄位|意義|
|-|-|
decimal_point<br/>_W_decimal_point|指向非貨幣量的十進位字元。
thousands_sep,<br/>_W_thousands_sep|指向字元的指標,該字元將數位組分隔至非貨幣數量的十進位點左側。
群組|指向**字元**大小的整數的指標,該整數包含以非貨幣數量表示的每組數位的大小。
int_curr_symbol<br/>_W_int_curr_symbol|指向當前區域設置的國際貨幣符號。 前三個字元依照「ISO 4217 貨幣和資金代碼」** 標準的定義，指定字母國際貨幣符號。 第四個字元 (緊接在 Null 字元之前) 會分隔國際貨幣符號與貨幣的數量。
currency_symbol<br/>_W_currency_symbol|指向當前區域設置的本地貨幣符號。
mon_decimal_point<br/>_W_mon_decimal_point|指向貨幣數量的十進位字元。
mon_thousands_sep<br/>_W_mon_thousands_sep|指向分隔符的指標,數位組以貨幣數量向小數位數左側。
mon_grouping|指向**字元**大小的整數的指標,該整數包含每組數位的大小(以貨幣數量表示)。
positive_sign<br/>_W_positive_sign|表示非負值貨幣數量之正負號的字串。
negative_sign<br/>_W_negative_sign|表示負值貨幣數量之正負號的字串。
int_frac_digits|國際格式化貨幣數量之小數點右邊的數字數目。
frac_digits|格式化貨幣數量之小數點右邊的數字數目。
p_cs_precedes|如果貨幣符號在非負值格式化貨幣數量的值之前，請設定為 1。 如果符號在值之後，請設定為 0。
p_sep_by_space|如果貨幣符號與非負值格式化貨幣數量之間以空格分隔，請設定為 1。 如果沒有空格分隔，請設定為 0。
n_cs_precedes|如果貨幣符號在負值格式化貨幣數量的值之前，請設定為 1。 如果符號在值之後，請設定為 0。
n_sep_by_space|如果貨幣符號與負值格式化貨幣數量之間以空格分隔，請設定為 1。 如果沒有空格分隔，請設定為 0。
p_sign_posn|非負值格式化貨幣數量的正號位置。
n_sign_posn|負值的格式化貨幣數量的正號位置。

除指定內容外,具有`char *`和`wchar_t *`版本的**lconv**結構的成員是指向字串的指標。 對於**wchar_t),**<strong>\*</strong>任何等於 **""(** 或**L")** 的)的長度為零,或者在當前區域設置中不支援。 請注意,**始終支援decimal_point**和 **_W_decimal_point**且長度為非零。

結構的**字元**成員是小非負數,而不是字元。 任何一項若等於 **CHAR_MAX**，則其於目前地區設定中不受支援。

**群組**與**mon_grouping**的值根據以下規則進行解釋:

- **CHAR_MAX** - 不要執行任何進一步的分組。

- 0 - 對其餘每個數位使用上一個元素。

- *n* - 構成當前組的位數。 檢查下一個項目，以在目前群組之前判斷下一個數字群組的大小。

**int_curr_symbol** 的值會根據下列規則解釋：

- 前三個字元依照「ISO 4217 貨幣和資金代碼」** 標準之定義，指定字母國際貨幣符號。

- 第四個字元 (緊接在 Null 字元之前) 會分隔國際貨幣符號與貨幣的數量。

**p_cs_precedes** 和 **n_cs_precedes** 的值會根據下列規則解釋 (**n_cs_precedes** 規則位於括弧內)：

- 0 - 貨幣符號遵循非負(負)格式貨幣值的值。

- 1 - 貨幣符號位於非負(負)格式貨幣值的值之前。

**p_sep_by_space** 和 **n_sep_by_space** 的值會根據下列規則解釋 (**n_sep_by_space** 規則位於括弧內)：

- 0 - 貨幣符號與值由非負(負)格式化貨幣值的空間分隔。

- 1 - 貨幣符號和非負(負)格式貨幣值的值之間沒有空間分隔。

**p_sign_posn** 和 **n_sign_posn** 的值根據下列規則解釋：

- 0 - 括弧環繞數量和貨幣符號。

- 1 - 符號字串位於數量和貨幣符號之前。

- 2 - 符號字串跟隨數量和貨幣符號。

- 3 - 符號字串緊接貨幣符號。

- 4 - 符號字串緊隨貨幣符號。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[地區設定](../../c-runtime-library/locale.md)<br/>
[設定區域設定](../../preprocessor/setlocale.md)<br/>
[strcoll Functions](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
