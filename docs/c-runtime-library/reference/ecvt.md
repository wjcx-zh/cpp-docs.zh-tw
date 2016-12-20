---
title: "_ecvt | Microsoft Docs"
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
  - "_ecvt"
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
  - "_ecvt"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ecvt 函式"
  - "轉換雙精度浮點數"
  - "ecvt 函式"
  - "數字, 轉換"
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ecvt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將 `double` 數字轉換成字串。  這些函式已有更安全的版本可用，請參閱 [\_ecvt\_s](../../c-runtime-library/reference/ecvt-s.md)。  
  
## 語法  
  
```  
char *_ecvt(   
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
```  
  
#### 參數  
 `value`  
 被轉換的數字。  
  
 `count`  
 儲存的位數。  
  
 `dec`  
 儲存的小數點位置。  
  
 `sign`  
 轉換數字的正負號  
  
## 傳回值  
 `_ecvt` 將指標傳回數值字串;，如果發生錯誤，則為 null。  
  
## 備註  
 `_ecvt` 函式轉換成浮點數的字串。  `value` 參數是要轉換的雙精確度浮點數。  這個函式將由 `count` `value` 數值為字串並將 null 字元 \(「\\ 0 "\)。  如果數字數目的 `value` 超出 `count`，低序位數字捨入。  如果小於 `count` 的數字有，字串填補零。  
  
 `_ecvt` 所傳回的數值總數不會超過 `_CVTBUFSIZE`。  
  
 只有數值資料儲存。  小數點的位置與 `value` 的符號可以從 `dec` 和 `sign` 取得在呼叫之後。  將小數點位置的整數值的 `dec` 參數點與字串的開頭。  0 或負整數值表示小數點在第一個數字左邊加入水平軸。  表示要轉換的數字的正負號整數的 `sign` 參數\)。  如果整數值是 0，它是正數。  否則，數值為負數。  
  
 在 `_ecvt` 和 `_fcvt` 的差異在於 `count` 參數的說明。  `_ecvt` 解譯 `count` ，在數值總數輸出字串，而 `_fcvt` ，說明 `count` 做為數字的小數點之後。  
  
 請注意 `_ecvt` 和 `_fcvt` 使用單一靜態配置轉換的緩衝區。  每個呼叫這些常式都會終結之前呼叫的結果。  
  
 這個函式會驗證它的參數。  如果 `dec` 或`sign`為 NULL或`count`為 0，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行， `errno` 會設為 `EINVAL` ，並回傳 NULL。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_ecvt`|\<stdlib.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_ecvt.c  
// compile with: /W3  
// This program uses _ecvt to convert a  
// floating-point number to a character string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int     decimal,   sign;  
   char    *buffer;  
   int     precision = 10;  
   double  source = 3.1415926535;  
  
   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996  
   // Note: _ecvt is deprecated; consider using _ecvt_s instead  
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",  
           source, buffer, decimal, sign );  
}  
```  
  
  **來源:3.1415926535 緩衝區:「3141592654 "十進位:1 個標記:0**   
## .NET Framework 對等用法  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)