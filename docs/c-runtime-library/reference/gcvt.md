---
title: "_gcvt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_gcvt"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_gcvt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CVTBUFSIZE"
  - "_gcvt 函式"
  - "轉換, 浮點到字串"
  - "CVTBUFSIZE"
  - "浮點函式, 將數值轉換為字串"
  - "gcvt 函式"
  - "數字, 轉換為字串"
  - "字串 [C++], 從浮點轉換"
ms.assetid: 5761411e-c06b-409a-912f-810fe7f4bcb5
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# _gcvt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換浮點數值為字串，儲存於緩衝區。  這個函式更安全的版本可用;請參閱 [\_gcvt\_s](../../c-runtime-library/reference/gcvt-s.md)。  
  
## 語法  
  
```  
char *_gcvt(   
   double value,  
   int digits,  
   char *buffer   
);  
```  
  
#### 參數  
 `value`  
 要轉換的值。  
  
 `digits`  
 儲存的有效位數。  
  
 `buffer`  
 結果的儲存位置。  
  
## 傳回值  
 `_gcvt`傳回數值字串的指標。  
  
## 備註  
 `_gcvt` 函式轉換浮點數 `value` 為一個字元字串 \(包含小數點和可能的正負號位元組\) 並將字串儲存於 `buffer` 。  `buffer` 必須足以容納轉換後的值加上末尾的空字元，空字元會被自動加入。  如果緩衝區大小\+1被使用，則`digits` 函式會覆寫緩衝區的結尾。  這是因為轉換後的字串包含小數點，而且可以包含標記和指數資訊。  沒有溢位的規則。  `_gcvt` 嘗試在十進位下產生 `digits` 位數。  如果不行，它將以指數格式產生 `digits` 位數。  末尾的零可能在轉換中被隱藏。  
  
 具有`_CVTBUFSIZE` 長度的`buffer` 足夠容納任何浮點數值。  
  
 這個函式會驗證它的參數。  如果 `buffer` 是 `NULL`，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `NULL` 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_gcvt`|\<stdlib.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_gcvt.c  
// compile with: /W3  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
  
int main( void )  
{  
   char buffer[_CVTBUFSIZE];  
   double value = -1234567890.123;  
   printf( "The following numbers were converted by _gcvt(value,12,buffer):\n" );  
   _gcvt( value, 12, buffer ); // C4996  
   // Note: _gcvt is deprecated; consider using _gcvt_s instead  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
  
   printf( "\n" );  
   value = -12.34567890123;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
}  
```  
  
  **下列數字由 \_gcvt\(value,12,buffer\)所轉換:**  
**buffer: '\-1234567890.12'\(14 個字元\)**  
**buffer: '\-12345678901.2'\(14 個字元\)**  
**buffer: '\-123456789012'\(13 個字元\)**  
**緩衝區:「\- 1.23456789012e\+012」\(19 個字元\)。**  
**buffer: '\-12.3456789012'\(14 個字元\)**  
**buffer: '\-1.23456789012'\(14 個字元\)**  
**buffer: '\-0.123456789012'\(15 個字元\)**  
**buffer: '\-1.23456789012e\-002' \(19 個字元\)**   
## .NET Framework 對等用法  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)