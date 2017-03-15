---
title: "localeconv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "localeconv"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "localeconv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lconv 類型"
  - "localeconv 函式"
  - "地區設定, 取得相關資訊"
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# localeconv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如需地區設定的 Gets 詳細資訊。  
  
## 語法  
  
```  
  
struct lconv *localeconv( void );  
```  
  
## 傳回值  
 `localeconv` 傳回指標會填滿型別 [結構 lconv](../../c-runtime-library/standard-types.md)物件的。  在物件中包含的值可由對 `localeconv` 的後續呼叫覆寫，並不會直接修改物件。  對 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 的呼叫 `LC_ALL`、 `LC_MONETARY`或 `LC_NUMERIC` 等迴寫入的 `category` 值結構的內容。  
  
## 備註  
 `localeconv` 函式取得如需數值格式的詳細資訊目前地區設定的。  這項資訊會型別 **lconv**結構中。  **lconv** 結構，定義在 LOCALE.H，包含下列成員:  
  
 `char *decimal_point, wchar_t *_W_decimal_point`  
 非貨幣數量的小數點的字元。  
  
 `char *thousands_sep, wchar_t *_W_thousands_sep`  
 分隔數字群組向左非貨幣數量的小數點的字元。  
  
 `char *grouping`  
 數字的各個群組的大小以非貨幣的數目。  
  
 `char *int_curr_symbol, wchar_t *_W_int_curr_symbol`  
 目前地區設定的國際貨幣符號。  前三個字元指定字母的國際貨幣符號 \(如 *ISO 4217 程式碼定義為* 標準的貨幣和的有限資源的表示 。  第四個字元 \(在 Null 字元前\) 從貨幣數量分隔國際貨幣符號。  
  
 `char *currency_symbol, wchar_t *_W_currency_symbol`  
 目前地區設定的當地貨幣符號。  
  
 `char *mon_decimal_point, wchar_t *_W_mon_decimal_point`  
 貨幣數量的小數點的字元。  
  
 `char *mon_thousands_sep, wchar_t *_W_mon_thousands_sep`  
 數字群組分隔符號向左小數位數以貨幣數量。  
  
 `char *mon_grouping`  
 數字的各個群組的大小以貨幣的數目。  
  
 `char *positive_sign, wchar_t *_W_positive_sign`  
 表示負數貨幣數量的資料標記。  
  
 `char *negative_sign, wchar_t *_W_negative_sign`  
 表示負數貨幣數量的資料標記。  
  
 `char int_frac_digits`  
 數字的小數點右方國際格式化貨幣數量。  
  
 `char frac_digits`  
 數字的小數點右方格式化貨幣數量。  
  
 `char p_cs_precedes`  
 如果貨幣符號在非負數格式化貨幣數量的值之前，將設為 1。  若符號遵循值，則設定為 0。  
  
 `char p_sep_by_space`  
 如果貨幣符號以空格分隔的非負數格式化貨幣數量，值會設為 1。  如果沒有空格分隔，設定為 0。  
  
 `char n_cs_precedes`  
 如果貨幣符號在負數格式化貨幣數量的值之前，將設為 1。  若符號成功值，則設定為 0。  
  
 `char n_sep_by_space`  
 如果貨幣符號以空格分隔的負數格式化貨幣數量，值會設為 1。  如果沒有空格分隔，設定為 0。  
  
 `char p_sign_posn`  
 位置正號非負數格式化貨幣數量。  
  
 `char n_sign_posn`  
 位置正號負數格式化貨幣數量。  
  
 `char` 的`*` 和 `wchar_t *` 版本結構的成員是指向字串。  每一個包含以目前地區設定等於 `wchar_t *`的 `""` \( `L""` \) 或長度為零或不支援。  請注意 `decimal_point` 和 `_W_decimal_point` 永遠支援和非零長度。  
  
 結構的 `char` 成員是小非負數，而不是字元。  每一個等於 **CHAR\_MAX** 沒有在目前地區設定的支援。  
  
 **grouping** 和 **mon\_grouping** 的項目會根據下列規則進行解譯。  
  
 **CHAR\_MAX**  
 不要執行任何其他群組。  
  
 0  
 針對每個剩餘的數字使用上一個項目。  
  
 *n*  
 數字組成目前群組。  下一個項目被檢查以判斷數值的下一個群組的大小，在目前的群組。  
  
 **int\_curr\_symbol** 的值會根據下列規則解譯:  
  
-   前三個字元指定字母的國際貨幣符號 \(如 *ISO 4217 程式碼定義為* 標準的貨幣和的有限資源的表示 。  
  
-   第四個字元 \(在 Null 字元前\) 從貨幣數量分隔國際貨幣符號。  
  
 **p\_cs\_precedes** 和 **n\_cs\_precedes** 的值會根據下列規則解譯 \( **n\_cs\_precedes** 規則括號內\):  
  
 0  
 貨幣符號後面非負數 \(非\) 格式化貨幣值的值。  
  
 1  
 貨幣符號前面非負數 \(非\) 格式化貨幣值的值。  
  
 **p\_sep\_by\_space** 和 **n\_sep\_by\_space** 的值會根據下列規則解譯 \( **n\_sep\_by\_space** 規則括號內\):  
  
 0  
 貨幣符號從值分隔。負數 \(非\) 格式化貨幣值的空間。  
  
 1  
 沒有在貨幣符號和值之間的空格分隔非負數 \(非\) 格式化貨幣值的。  
  
 **p\_sign\_posn** 和 **n\_sign\_posn** 的值會根據下列規則解譯:  
  
 0  
 括號周圍量和貨幣符號。  
  
 1  
 標記字串在量和貨幣符號之前。  
  
 2  
 標記字串在量和貨幣符號後面。  
  
 3  
 標記字串緊接在貨幣符號之前。  
  
 4  
 標記字串緊接在貨幣符號。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`localeconv`|\<locale.h \- 地區設定\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 請參閱  
 [地區設定](../../c-runtime-library/locale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)