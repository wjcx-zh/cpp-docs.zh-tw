---
title: "_fcvt_s | Microsoft Docs"
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
  - "_fcvt_s"
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
  - "fcvt_s"
  - "_fcvt_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fcvt_s 函式"
  - "轉換浮點, 到字串"
  - "fcvt_s 函式"
  - "浮點函式, 將數值轉換為字串"
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
caps.latest.revision: 27
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fcvt_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換浮點數值至字串。  這是 [\_fcvt](../../c-runtime-library/reference/fcvt.md) 的安全性強化版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 所述。  
  
## 語法  
  
```  
errno_t _fcvt_s(   
   char* buffer,  
   size_t sizeInBytes,  
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
template <size_t size>  
errno_t _fcvt_s(   
   char (&buffer)[size],  
   double value,  
   int count,  
   int *dec,  
   int *sign   
); // C++ only  
```  
  
#### 參數  
 \[out\] `buffer`  
 所提供的緩衝區將保留轉換的結果。  
  
 \[in\] `sizeInBytes`  
 緩衝區的大小 \(以位元組為單位\)。  
  
 \[in\] `value`  
 被轉換的數字。  
  
 \[in\] `count`  
 小數點後的位數。  
  
 \[out\] `dec`  
 要儲存的小數點位置的指標。  
  
 \[out\] `sign`  
 要儲存的標記指標的指標。  
  
## 傳回值  
 如果成功，則為零。  如果發生失敗，則傳回值為錯誤碼。  錯誤碼在 Errno.h 中定義。  如需這些錯誤的清單，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
 在無效的參數的情況下，如下表所示，這個函式叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `EINVAL` 。  
  
### 錯誤狀況  
  
|`buffer`|`sizeInBytes`|值|count|dec|sign|傳回|在 `buffer` 的值|  
|--------------|-------------------|-------|-----------|---------|----------|--------|-------------------|  
|`NULL`|any|any|any|any|any|`EINVAL`|未修改。|  
|不是 `NULL` \(指向有效的記憶體\)|\<\=0|any|any|any|any|`EINVAL`|未修改。|  
|any|any|any|any|`NULL`|any|`EINVAL`|未修改。|  
|any|any|any|any|any|`NULL`|`EINVAL`|未修改。|  
  
 **安全性問題**  
  
 如果 `buffer`沒有指向有效的記憶體且不是 `NULL` ， `_fcvt_s` 會發生存取被拒。  
  
## 備註  
 `_fcvt_s` 函式將浮點數轉換成空的終止字串。  `value` 參數是要轉換的雙精確度浮點數。  `_fcvt_s` 中 `value` 數值為字串並將 null 字元 \(「\\ 0 」\)。  `count`參數指定小數點之後需要倍儲存的位數。  剩餘數字四捨五入到 `count` 位元。  如果精準度小於 `count` 的數字，字串填補零。  
  
 只有數值資料儲存。  小數點的位置與 `value` 的符號可以從 `dec` 和 `sign` 取得在呼叫之後。  `dec` 參數指向一個整數值；此整數值告知小數點位置與字串的開頭。  0 或負整數值表示小數點在第一個數字左邊加入水平軸。  表示 `value`的正負號整數參數的 `sign` 。  整數設為 0，如果 `value` 為正值且設為非零值，如果 `value` 是負值。  
  
 足夠容納任何浮點數值的 `_CVTBUFSIZE` 長度的緩衝區。  
  
 在 `_ecvt_s` 和 `_fcvt_s` 的差異在於 `count` 參數的說明。  `_ecvt_s`將`count`解譯為輸出字串的數值總數，而且`_fcvt_s` 將c`ount`解譯為小數點之後的數值數。  
  
 在 C\+\+ 中，此函式的使用被簡化為使用樣板多載。使用多載可以自動推斷緩衝區的大小而不必在參數中指明大小。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 此函式的偵錯版本會先將緩衝區填入 0xFD 。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## 需求  
  
|功能|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_fcvt_s`|\<stdlib.h\>|\<errno.h\>|  
  
 如需詳細資訊，請參閱介紹中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
 **程式庫:** [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// fcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_fcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
  **Converted value: 120000**   
## .NET Framework 對等用法  
 <xref:System.Convert.ToString%2A>  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt\_s](../../c-runtime-library/reference/ecvt-s.md)   
 [\_gcvt\_s](../../c-runtime-library/reference/gcvt-s.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)