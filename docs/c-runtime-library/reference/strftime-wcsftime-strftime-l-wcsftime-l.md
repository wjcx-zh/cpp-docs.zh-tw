---
title: "strftime、wcsftime、_strftime_l、_wcsftime_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "strftime"
  - "_wcsftime_l"
  - "_strftime_l"
  - "wcsftime"
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
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tcsftime"
  - "strftime"
  - "wcsftime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strftime_l 函式"
  - "strftime 函式"
  - "tcsftime 函式"
  - "_wcsftime_l 函式"
  - "wcsftime 函式"
  - "_tcsftime 函式"
  - "時間字串"
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strftime、wcsftime、_strftime_l、_wcsftime_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

格式字串時間。  
  
## 語法  
  
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
  
#### 參數  
 `strDest`  
 輸出字串。  
  
 `maxsize`  
 `strDest` 緩衝區的大小，以字元 \(`char` 或 `wchart_t`測量\)。  
  
 `format`  
 格式控制字串。  
  
 `timeptr`  
 `tm`資料結構  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 傳回`strftime` 中 `strDest` 位置的字元數，並且此 `wcsftime` 所傳回的寬字元對應的數量。  
  
 如果包括結束的 null 字元總數比`maxsize`多，則 `strftime` 和 `wcsftime` 會傳回 0，而 `strDest` 內容為不定。  
  
 `strDest` 中的字元數與可能增加到 `format` 傳遞格式化程式碼常值字元以及所有字元數目相等的 `format` 。  字串的結尾的 NULL 未計算在傳回值中。  
  
## 備註  
 `strftime`和`wcsftime`函式依照提供的`format`引數格式化`timeptr`中的`tm`時間值，並將結果儲存在`strDest`*.*緩衝區。最多只有`maxsize` 的字元會被放置到字串中。  如需欄位的描述 `timeptr` 結構的詳細資訊，請參閱 [asctime](../../c-runtime-library/reference/asctime-wasctime.md)。  `wcsftime` 是與 `strftime`相等的寬字元；其為寬字元字串的字串指標引數點。  這三個函式其餘部分的運作相同。  
  
> [!NOTE]
>  在 Visual C\+\+ 2005 之前的版本中，文件描述了 `wcsftime` `format` 參數以具有資料型別，則為 `const wchar_t *`，但是 `format` 資料型別的實際實作是 `const char *`。  更新 `format`資料型別的實作反映先前與目前文件，例如， `const wchar_t *`。  
  
 這個函式會驗證它的參數。  如果 `strDest`、 `format`或`timeptr` 為 null 指標，則為，如果 `timeptr` 處理的 `tm` 資料結構無效 \(例如，\)，則包含超出時間或日期範圍值\)，或者，如果 `format` 字串包含無效的格式化程式碼，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，則函式會傳回 0 並將 `errno` 設定為 `EINVAL`。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE &  \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|-----------------------------|----------------|-------------------|  
|`_tcsftime`|`strftime`|`strftime`|`wcsftime`|  
  
 `format` 引數包含一個或多個程式碼;在 `printf`中，格式化程式碼在百分比符號 \(`%`\) 之後。  不從`%`開始的字元原封不動的複製到 `strDest`*.*目前地區設定的 `LC_TIME` 分類會影響 `strftime`輸出格式。\(如需`LC_TIME`的詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。\)沒有 `_l`尾碼的函式使用目前設定的地區設定。  這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於將地區設定設為參數，而不使用目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 `strftime` 的格式化程式碼如下所列:  
  
 `%a`  
 星期日期名稱的縮寫  
  
 `%A`  
 完整的星期名稱  
  
 `%b`  
 月份名稱的縮寫。  
  
 `%B`  
 月份的完整名稱。  
  
 `%c`  
 日期和時間表示適合地區設定  
  
 `%d`  
 月份的日期為十進位數字 \(01 – 31\) 。  
  
 `%H`  
 時間以24 小時格式 \(00 – 23\) 表示  
  
 `%I`  
 時間以12 小時格式 \(01 – 12\) 表示  
  
 `%j`  
 年份的天為十進位數字 \(001 – 366\) 。  
  
 `%m`  
 月份為十進位數字 \(01 – 12\) 。  
  
 `%M`  
 分鐘數為十進位數字 \(00 – 59\) 。  
  
 `%p`  
 目前地區設定的 A.M.\/P.M. 為12 小時制的指示器。  
  
 `%S`  
 秒數為十進位數字 \(00 – 59\)  
  
 `%U`  
 年的星期為十進位數字\(00 – 53\)，有星期日為星期的第一天資訊  
  
 `%w`  
 星期日期為十進位數字 \(0 – 6 ；星期日是 0\)  
  
 `%W`  
 年的星期為十進位數字\(00 – 53\)，有星期一為星期的第一天資訊  
  
 `%x`  
 目前地區設定的日期表示。  
  
 `%X`  
 目前地區設定的時間表示。  
  
 `%y`  
 沒有世紀的年份，為十進位數字 \(00 – 99\)  
  
 `%Y`  
 有世紀的年份，為十進位數字。  
  
 `%z, %Z`  
 根據登錄設定，任何時區名稱或時區縮寫；如果時區不明，則沒有任何字元  
  
 `%%`  
 百分比符號  
  
 在 `printf` 函式，則 `#` 旗標可能會提供所有格式化程式碼的前置字元。  在這種情況下，格式化程式碼的意義如下變更。  
  
|格式化程式碼|意義|  
|------------|--------|  
|`%#a, %#A, %#b, %#B, %#p, %#X, %#z, %#Z, %#%`|`#` 旗標會被忽略。|  
|`%#c`|為目前地區設定為適當完整日期和時間。  例如:「1995 年 3 月 14 日，星期二，12:41: 29 」。|  
|`%#x`|適合目前地區設定的完整日期表示。  例如:「1995 年 3 月 14 日，星期二」。|  
|`%#d, %#H, %#I, %#j, %#m, %#M, %#S, %#U, %#w, %#W, %#y, %#Y`|移除前置零 \(如果有的話\)。|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strftime`|\<time.h\>|  
|`wcsftime`|\<time.h\> or \<wchar.h\>|  
|`_strftime_l`|\<time.h\>|  
|`_wcsftime_l`|\<time.h\> or \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [time](../../c-runtime-library/reference/time-time32-time64.md) 的範例。  
  
## .NET Framework 對等用法  
  
-   [System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
## 請參閱  
 [地區設定](../../c-runtime-library/locale.md)   
 [時間管理](../../c-runtime-library/time-management.md)   
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll 函式](../../c-runtime-library/strcoll-functions.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)