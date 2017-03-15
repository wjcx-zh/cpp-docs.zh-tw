---
title: "_gcvt_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_gcvt_s"
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
  - "_gcvt_s"
  - "gcvt_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CVTBUFSIZE"
  - "_gcvt_s 函式"
  - "轉換, 浮點到字串"
  - "CVTBUFSIZE"
  - "浮點函式, 將數值轉換為字串"
  - "gcvt_s 函式"
  - "數字, 轉換為字串"
  - "字串 [C++], 從浮點轉換"
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# _gcvt_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將浮點數值轉換成字串。  這是 [\_gcvt](../../c-runtime-library/reference/gcvt.md) 的安全性強化版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 所述。  
  
## 語法  
  
```  
errno_t _gcvt_s(   
   char *buffer,  
   size_t sizeInBytes,  
   double value,  
   int digits   
);  
template <size_t cchStr>  
errno_t _gcvt_s(   
   char (&buffer)[cchStr],  
   double value,  
   int digits   
); // C++ only  
```  
  
#### 參數  
 \[out\] `buffer`  
 儲存轉換結果的緩衝區。  
  
 \[in\] `sizeInBytes`  
 緩衝區的大小。  
  
 \[in\] `value`  
 要轉換的值。  
  
 \[in\] `digits`  
 儲存的有效位數。  
  
## 傳回值  
 如果成功，則為零。  如果因為無效的參數 \(關於無效值請參閱下表\) 導致失敗，無效參數處理常式會被調用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 所述。  如果允許繼續執行會回傳一個錯誤碼。  錯誤碼在 Errno.h 中定義。  如需這些錯誤的清單，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
### 錯誤情況  
  
|`buffer`|`sizeInBytes`|`value`|`digits`|Return|在 `buffer` 的值|  
|--------------|-------------------|-------------|--------------|------------|-------------------|  
|`NULL`|any|any|any|`EINVAL`|未修改。|  
|不是 `NULL` \(指向有效的記憶體\)|零|any|any|`EINVAL`|未修改。|  
|不是 `NULL` \(指向有效的記憶體\)|any|any|\>\= `sizeInBytes`|`EINVAL`|未修改。|  
  
 **安全性問題**  
  
 如果 `buffer` 沒有指向有效的記憶體且不是 `NULL` ， `_gcvt_s` 會發生存取被拒。  
  
## 備註  
 `_gcvt_s` 函式轉換浮點數 `value` 為一個字元字串 \(包含小數點和可能的正負號位元組\) 並將字串儲存於 `buffer` 。  `buffer` 必須足以容納轉換後的值加上末尾的空字元，空字元會被自動加入。  足夠容納任何浮點數值的 `_CVTBUFSIZE` 長度的緩衝區。  如果使用了 `digits` \+ 1 大小的緩衝區，函式將不會覆寫緩衝區的末尾，所以請確認為此操作提供了足夠的緩衝區。  `_gcvt_s` 嘗試在十進位下產生 `digits` 位數。  如果不行，它將以指數格式產生 `digits` 位數。  末尾的零可以在轉換中被隱藏。  
  
 在 C\+\+ 中，此函式的使用被簡化為使用樣板多載。使用多載可以自動推斷緩衝區的大小而不必在參數中指明大小。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 此函式的偵錯版本會先將緩衝區填入 0xFD 。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md) 。  
  
## 需求  
  
|程序|必要的標頭檔|選擇性標頭|  
|--------|------------|-----------|  
|`_gcvt_s`|\<stdlib.h\>|\<error.h\>|  
  
 如需詳細資訊，請參閱介紹中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_gcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char buf[_CVTBUFSIZE];  
  int decimal;  
  int sign;  
  int err;  
  
  err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);  
  
  if (err != 0)  
  {  
     printf("_gcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
  **Converted value: 1.2**   
## .NET Framework 對等用法  
 <xref:System.Convert.ToString%2A>  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt\_s](../../c-runtime-library/reference/ecvt-s.md)   
 [\_fcvt\_s](../../c-runtime-library/reference/fcvt-s.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)