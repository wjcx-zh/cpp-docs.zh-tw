---
title: "_ecvt_s | Microsoft Docs"
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
  - "_ecvt_s"
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
  - "ecvt_s"
  - "_ecvt_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ecvt_s 函式"
  - "轉換雙精度浮點數"
  - "ecvt_s 函式"
  - "數字, 轉換"
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
caps.latest.revision: 25
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ecvt_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將 `double` 數字轉換成字串。  這是 [\_ecvt](../../c-runtime-library/reference/ecvt.md) 的安全性強化版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 所述。  
  
## 語法  
  
```  
errno_t _ecvt_s(   
   char * _Buffer,  
   size_t _SizeInBytes,  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
);  
template <size_t size>  
errno_t _ecvt_s(   
   char (&_Buffer)[size],  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
); // C++ only  
```  
  
#### 參數  
 \[out\] `_Buffer`  
 使用指標填入至數值字串，轉換的結果。  
  
 \[in\] `_SizeInBytes`  
 緩衝區的大小 \(以位元組為單位\)。  
  
 \[in\] `_Value`  
 被轉換的數字。  
  
 \[in\] `_Count`  
 儲存的位數。  
  
 \[out\] `_Dec`  
 儲存的小數點位置。  
  
 \[out\] `_Sign`  
 轉換數字的正負號  
  
## 傳回值  
 如果成功，則為零。  如果發生失敗，則傳回值為錯誤碼。  錯誤碼在 Errno.h 中定義。  如需詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 在無效的參數的情況下，如下表所示，這個函式叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `EINVAL` 。  
  
### 錯誤狀況  
  
|`_Buffer`|`_SizeInBytes`|\_值|\_計數|"Dec"|\_標誌|傳回值|在 `buffer` 的值|  
|---------------|--------------------|---------|----------|-----------|----------|---------|-------------------|  
|`NULL`|any|any|any|any|any|`EINVAL`|未修改。|  
|不是 `NULL` \(指向有效的記憶體\)|\<\=0|any|any|any|any|`EINVAL`|未修改。|  
|any|any|any|any|`NULL`|any|`EINVAL`|未修改。|  
|any|any|any|any|any|`NULL`|`EINVAL`|未修改。|  
  
 **安全性問題**  
  
 如果 `buffer`沒有指向有效的記憶體且不是 `NULL` ， `_ecvt_s` 會發生存取被拒。  
  
## 備註  
 `_ecvt_s` 函式轉換成浮點數的字串。  `_Value` 參數是要轉換的雙精確度浮點數。  這個函式將由 `count` `_Value` 數值為字串並將 null 字元 \(「\\ 0 "\)。  如果數字數目的 `_Value` 超出 `_Count`，低序位數字捨入。  如果小於 `count` 的數字有，字串填補零。  
  
 只有數值資料儲存。  小數點的位置與 `_Value` 的符號可以從 `_Dec` 和 `_Sign` 取得在呼叫之後。  將小數點位置的整數值的 `_Dec` 參數點與字串的開頭。  0 或負整數值表示小數點在第一個數字左邊加入水平軸。  表示要轉換的數字的正負號整數的 `_Sign` 參數\)。  如果整數值是 0，它是正數。  否則，數值為負數。  
  
 足夠容納任何浮點數值的 `_CVTBUFSIZE` 長度的緩衝區。  
  
 在 `_ecvt_s` 和 `_fcvt_s` 的差異在於 `_Count` 參數的說明。  `_ecvt_s` 解譯 `_Count` ，在數值總數輸出字串，而 `_fcvt_s` ，說明 `_Count` 做為數字的小數點之後。  
  
 在 C\+\+ 中，此函式的使用被簡化為使用樣板多載。使用多載可以自動推斷緩衝區的大小而不必在參數中指明大小。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 此函式的偵錯版本會先將緩衝區填入 0xFD 。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## 需求  
  
|功能|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_ecvt_s`|\<stdlib.h\>|\<errno.h\>|  
  
 如需詳細資訊，請參閱介紹中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// ecvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( )  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_ecvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
  **Converted value: 12000**   
## .NET Framework 對等用法  
 <xref:System.Convert.ToString%2A>  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt\_s](../../c-runtime-library/reference/fcvt-s.md)   
 [\_gcvt\_s](../../c-runtime-library/reference/gcvt-s.md)