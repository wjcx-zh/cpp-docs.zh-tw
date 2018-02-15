---
title: localeconv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e93e21505a661deb470e4b31c8807ef5133a774
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="localeconv"></a>localeconv
取得地區設定上的詳細資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct lconv *localeconv( void );  
```  
  
## <a name="return-value"></a>傳回值  
 `localeconv` 將指標傳回至 [struct lconv](../../c-runtime-library/standard-types.md) 類型的填滿物件中。 物件中包含的值從在執行緒區域儲存區中的地區設定來複製和後續呼叫會覆寫`localeconv`。 此物件中的值所做的變更進行修改的地區設定。 使用 `LC_ALL`、`LC_MONETARY`或 `LC_NUMERIC` 的 `category` 值呼叫 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)，可覆寫結構內容。  
  
## <a name="remarks"></a>備註  
 `localeconv` 函式取得有關目前地區設定之數值格式的詳細資訊。 這項資訊會儲存在類型的結構`lconv`。 `lconv`地區設定中定義的結構。H、 包含下列成員：  
  
 `char *decimal_point, wchar_t *_W_decimal_point`  
 非貨幣數量的小數點字元。  
  
 `char *thousands_sep, wchar_t *_W_thousands_sep`  
 分隔非貨幣數量的小數點左邊的數字群組的字元。  
  
 `char *grouping`  
 指標`char`-調整大小的整數，其中包含每個群組中 nonmonetary 數量的數字的大小。  
  
 `char *int_curr_symbol, wchar_t *_W_int_curr_symbol`  
 配合目前地區設定的國際貨幣符號。 前三個字元依照「ISO 4217 貨幣和資金代碼」標準的定義，指定字母國際貨幣符號。 第四個字元 (緊接在 Null 字元之前) 會分隔國際貨幣符號與貨幣的數量。  
  
 `char *currency_symbol, wchar_t *_W_currency_symbol`  
 符合目前地區設定的本地貨幣符號。  
  
 `char *mon_decimal_point, wchar_t *_W_mon_decimal_point`  
 貨幣數量的小數點字元。  
  
 `char *mon_thousands_sep, wchar_t *_W_mon_thousands_sep`  
 貨幣數量中小數點左邊數字群組的分隔符號。  
  
 `char *mon_grouping`  
 指標`char`-調整大小的整數，其中包含每個群組中金錢數量的數字的大小。  
  
 `char *positive_sign, wchar_t *_W_positive_sign`  
 表示非負值貨幣數量之正負號的字串。  
  
 `char *negative_sign, wchar_t *_W_negative_sign`  
 表示負值貨幣數量之正負號的字串。  
  
 `char int_frac_digits`  
 國際格式化貨幣數量之小數點右邊的數字數目。  
  
 `char frac_digits`  
 格式化貨幣數量之小數點右邊的數字數目。  
  
 `char p_cs_precedes`  
 如果貨幣符號在非負值格式化貨幣數量的值之前，請設定為 1。 如果符號在值之後，請設定為 0。  
  
 `char p_sep_by_space`  
 如果貨幣符號與非負值格式化貨幣數量之間以空格分隔，請設定為 1。 如果沒有空格分隔，請設定為 0。  
  
 `char n_cs_precedes`  
 如果貨幣符號在負值格式化貨幣數量的值之前，請設定為 1。 如果符號在值之後，請設定為 0。  
  
 `char n_sep_by_space`  
 如果貨幣符號與負值格式化貨幣數量之間以空格分隔，請設定為 1。 如果沒有空格分隔，請設定為 0。  
  
 `char p_sign_posn`  
 非負值格式化貨幣數量的正號位置。  
  
 `char n_sign_posn`  
 負值的格式化貨幣數量的正號位置。  
  
指定的成員，除非`lconv`有結構`char *`和`wchar_t *`版本都是字串指標。 任何一項若等於 `""` (或`wchar_t *``L""`)，其長度為零，或於目前地區設定中不受支援。 請注意，`decimal_point` 和 `_W_decimal_point` 一律受支援，且長度不為零。  
  
結構的 `char` 成員是小型非負值數字，不是字元。 任何一項都等於`CHAR_MAX`不支援目前的地區設定。  
  
值`grouping`和`mon_grouping`解譯根據下列規則：  
  
- `CHAR_MAX` -不會執行任何進一步分組。  
  
- 0-使用上一個項目，每個其餘的數字。  
  
- *n* 目前群組所組成的數字的數字。 檢查下一個項目，以在目前群組之前判斷下一個數字群組的大小。  
  
值`int_curr_symbol`解譯根據下列規則：  
  
-   前三個字元依照「ISO 4217 貨幣和資金代碼」標準之定義，指定字母國際貨幣符號。  
  
-   第四個字元 (緊接在 Null 字元之前) 會分隔國際貨幣符號與貨幣的數量。  
  
值`p_cs_precedes`和`n_cs_precedes`解譯根據下列規則 (`n_cs_precedes`規則位於括號內):  
  
- 0-貨幣符號會遵循負值 （負） 格式化貨幣值的值。  
  
- 1-貨幣符號前面會有非負值 （負） 格式化貨幣值的值。  
  
值`p_sep_by_space`和`n_sep_by_space`解譯根據下列規則 (`n_sep_by_space`規則位於括號內):  
  
- 0-貨幣符號會分隔值乘以負值 （負） 格式化貨幣值的空間。  
  
- 1-貨幣符號和負值 （負） 格式化貨幣值的值之間沒有空格分隔。  
  
值`p_sign_posn`和`n_sign_posn`解譯根據下列規則：  
  
- 0-括號括住數量和貨幣符號。  
  
- 1-符號的字串前面會有數量和貨幣符號。  
  
- 2-符號的字串會遵循數量和貨幣符號。  
  
- 3-符號的字串前面貨幣符號。  
  
- 4-正負號的立即字串如下所示的貨幣符號。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`localeconv`|\<locale.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>請參閱  
 [Locale](../../c-runtime-library/locale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [strcoll Functions](../../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)