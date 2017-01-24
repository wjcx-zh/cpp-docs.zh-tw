---
title: "_fcvt | Microsoft Docs"
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
  - "_fcvt"
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
  - "_fcvt"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fcvt 函式"
  - "轉換浮點, 到字串"
  - "fcvt 函式"
  - "浮點函式"
  - "浮點函式, 將數值轉換為字串"
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fcvt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換浮點數值至字串。  這些函式已有更安全的版本可用，請參閱 [\_fcvt\_s](../../c-runtime-library/reference/fcvt-s.md)。  
  
## 語法  
  
```  
char *_fcvt(   
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
 小數點後的位數。  
  
 `dec`  
 要儲存的小數點位置的指標。  
  
 `sign`  
 要儲存的標記指標的指標。  
  
## 傳回值  
 `_fcvt` 將指標傳回數值字串，在錯誤的空。  
  
## 備註  
 `_fcvt` 函式將浮點數轉換成空的終止字串。  `value` 參數是要轉換的雙精確度浮點數。  `_fcvt` 中 `value` 數值為字串並將 null 字元 \(「\\ 0 」\)。  `count`參數指定小數點之後需要倍儲存的位數。  剩餘數字四捨五入到 `count` 位元。  如果精準度小於 `count` 的數字，字串填補零。  
  
 `_fcvt` 所傳回的數值總數不會超過 `_CVTBUFSIZE`。  
  
 只有數值資料儲存。  小數點的位置與 `value` 的符號可以從 `dec` 取得在呼叫之後。  `dec` 參數指向一個整數值；此整數值告知小數點位置與字串的開頭。  0 或負整數值表示小數點在第一個數字左邊加入水平軸。  表示 `value`的正負號整數參數的 `sign` 。  整數設為 0，如果 `value` 為正值且設為非零值，如果 `value` 是負值。  
  
 在 `_ecvt` 和 `_fcvt` 的差異在於 `count` 參數的說明。  `_ecvt` 解譯 `count` ，在數值總數輸出字串，而 `_fcvt` ，說明 `count` 做為數字的小數點之後。  
  
 請注意 `_ecvt` 和 `_fcvt` 使用單一靜態配置轉換的緩衝區。  每個呼叫這些常式都會終結之前呼叫的結果。  
  
 這個函式會驗證它的參數。  如果 `dec` 或`sign`為 NULL或`count`為 0，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行， `errno` 會設為 `EINVAL` ，並回傳 NULL。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_fcvt`|\<stdlib.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_fcvt.c  
// compile with: /W3  
// This program converts the constant  
// 3.1415926535 to a string and sets the pointer  
// buffer to point to that string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int  decimal, sign;  
   char *buffer;  
   double source = 3.1415926535;  
  
   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996  
   // Note: _fcvt is deprecated; consider using _fcvt_s instead  
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",  
            source, buffer, decimal, sign );  
}  
```  
  
  **來源:3.1415926535 緩衝區:「3141592654 」十進位:1 個標記:0**   
## .NET Framework 對等用法  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)