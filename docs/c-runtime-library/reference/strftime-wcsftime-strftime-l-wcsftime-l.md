---
title: "strftime、wcsftime、_strftime_l、_wcsftime_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsftime
- strftime
- wcsftime
dev_langs:
- C++
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 990dab2b4cedbdb464a2e546a4c83758cb46c89a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime、wcsftime、_strftime_l、_wcsftime_l
設定時間字串的格式。  
  
## <a name="syntax"></a>語法  
  
```  
size_t strftime(  
   char *strDest,  
   size_t maxsize,  
   const char *format,  
   const struct tm *timeptr   
);  
size_t _strftime_l(  
   char *strDest,  
   size_t maxsize,  
   const char *format,  
   const struct tm *timeptr,  
   _locale_t locale  
);  
size_t wcsftime(  
   wchar_t *strDest,  
   size_t maxsize,  
   const wchar_t *format,  
   const struct tm *timeptr   
);  
size_t _wcsftime_l(  
   wchar_t *strDest,  
   size_t maxsize,  
   const wchar_t *format,  
   const struct tm *timeptr,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `strDest`  
 輸出字串。  
  
 `maxsize`  
 `strDest` 緩衝區的大小，以字元 (`char` 或 `wchart_t`) 為單位。  
  
 `format`  
 格式控制字串。  
  
 `timeptr`  
 `tm` 資料結構。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 `strftime` 會傳回放在 `strDest` 中的字元數，而 `wcsftime` 會傳回對應的寬字元數。  
  
 如果總字元數 (包括結束 Null) 超個 `maxsize`，`strftime` 和 `wcsftime` 會傳回 0 且無法確定 `strDest` 的內容。  
  
 `strDest` 中的字元數等於 `format` 中的常值字元數加上可能透過格式代碼新增至 `format` 的任何字元數。 字串的結束 Null 不會計入傳回值。  
  
## <a name="remarks"></a>備註  
 `strftime`和`wcsftime`函式格式`tm`時間值中的`timeptr`根據提供`format`引數和存放區的緩衝區中的結果`strDest`。 字串中最多可放置 `maxsize` 個字元。 如需 `timeptr` 結構中的欄位說明，請參閱 [asctime](../../c-runtime-library/reference/asctime-wasctime.md)。 `wcsftime` 是 `strftime` 的寬字元對應項，其字串指標引數會指向寬字元字串。 除此之外，這些函式的行為相同。  
  
> [!NOTE]
>  Visual C++ 2005 之前的版本文件將 `wcsftime` 的 `format` 參數描述成具有資料類型 `const wchar_t *`，但 `format` 資料類型的實際實作為 `const char *`。 實作`format`資料類型已更新以反映的先前和目前文件，也就是`const wchar_t *`。  
  
 這個函式會驗證它的參數。 如果`strDest`， `format`，或`timeptr`為 null 指標，或如果`tm`資料結構所定址`timeptr`無效 （例如，如果它包含超出範圍值的時間或日期），或如果`format`字串包含無效格式化程式碼無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則函式會傳回 0 並將 `errno` 設定為 `EINVAL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsftime`|`strftime`|`strftime`|`wcsftime`|  
  
 `format` 引數是由一或多個程式碼所組成；例如在 `printf` 中，格式代碼前會加上百分比符號 (`%`)。 不是以字元`%`會複製到不變`strDest`。 目前地區設定的 `LC_TIME` 分類會影響 `strftime` 的輸出格式 (如需 `LC_TIME` 的詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md))。沒有 `_l` 後置字元的函式會使用目前設定的地區設定。 具有 `_l` 後置字元的函式版本與其相同，只不過它會採用地區設定作為參數，並使用該地區設定，而不是目前設定的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
 以下列出 `strftime` 的格式代碼：  
  
 `%a`  
 工作日名稱縮寫  
  
 `%A`  
 完整工作日名稱  
  
 `%b`  
 月份名稱縮寫  
  
 `%B`  
 完整月份名稱  
  
 `%c`  
 適用於地區設定的日期和時間表示  
  
 `%d`  
 月份 (01 – 31) 的十進位數字日期  
  
 `%H`  
 24 小時制的小時 (00-23)  
  
 `%I`  
 12 小時制 (01-12) 的  
  
 `%j`  
 一天的年份為十進位數字 (001 到 366)  
  
 `%m`  
 月份 (01-12) 的十進位數字  
  
 `%M`  
 十進位數字為分鐘 (00-59)  
  
 `%p`  
 目前地區設定的上下/下午 12 小時制的指標  
  
 `%S`  
 第二個十進位數字 (00-59)  
  
 `%U`  
 十進位數字，其中星期日是週第一天的年度週次 (00-53)  
  
 `%w`  
 Weekday 為十進位數字 (0-6;星期日是 0）  
  
 `%W`  
 十進位數字，以星期一做為一週的第一天的年度週次 (00-53)  
  
 `%x`  
 適用於目前地區設定的日期表示  
  
 `%X`  
 適用於目前地區設定的時間表示  
  
 `%y`  
 不含世紀，為十進位數字的年份 (00-99)  
  
 `%Y`  
 含世紀的年份，以十進位數字表示  
  
 `%z, %Z`  
 時區名稱或時區縮寫，視登錄設定而定；如果時區不明，則沒有任何字元  
  
 `%%`  
 百分比符號  
  
 如同 `printf` 函式，`#` 旗標前面可以加上任何格式代碼。 在此情況下，格式代碼的意義會變更如下。  
  
|格式化程式碼|意義|  
|-----------------|-------------|  
|`%#a, %#A, %#b, %#B, %#p, %#X, %#z, %#Z, %#%`|會忽略 `#` 旗標。|  
|`%#c`|適用於目前地區設定的完整日期和時間表示。 例如：「1995 年 3 月 14 日星期二 12:41:29」。|  
|`%#x`|適用於目前地區設定的完整日期表示。 例如：「1995 年 3 月 14 日星期二」。|  
|`%#d, %#H, %#I, %#j, %#m, %#M, %#S, %#U, %#w, %#W, %#y, %#Y`|移除前置零 (如果有)。|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`strftime`|\<time.h>|  
|`wcsftime`|\<time.h> 或 \<wchar.h>|  
|`_strftime_l`|\<time.h>|  
|`_wcsftime_l`|\<time.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
 請參閱 [time](../../c-runtime-library/reference/time-time32-time64.md) 的範例。  
  
## <a name="see-also"></a>請參閱  
 [地區設定](../../c-runtime-library/locale.md)   
 [時間管理](../../c-runtime-library/time-management.md)   
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)