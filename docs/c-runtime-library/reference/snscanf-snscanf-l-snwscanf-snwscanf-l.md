---
title: "_snscanf、_snscanf_l、_snwscanf、_snwscanf_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_snwscanf"
  - "_snscanf_l"
  - "_snscanf"
  - "_snwscanf_l"
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
  - "_snscanf"
  - "_snscanf_l"
  - "_snwscanf"
  - "snscanf_l"
  - "snscanf"
  - "_sntscanf_l"
  - "_sntscanf"
  - "_snwscanf_l"
  - "sntscanf_l"
  - "sntscanf"
  - "snwscanf"
  - "snwscanf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_snscanf 函式"
  - "_snscanf_l 函式"
  - "_sntscanf 函式"
  - "_sntscanf_l 函式"
  - "_snwscanf 函式"
  - "_snwscanf_l 函式"
  - "讀取資料, 字串"
  - "snscanf 函式"
  - "snscanf_l 函式"
  - "sntscanf 函式"
  - "sntscanf_l 函式"
  - "snwscanf 函式"
  - "snwscanf_l 函式"
  - "字串 [C++], 讀取"
  - "字串 [C++], 讀取資料來源"
ms.assetid: da1ac890-f905-4cd7-954b-3c90957b5551
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _snscanf、_snscanf_l、_snwscanf、_snwscanf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從字串讀取指定長度的格式化資料。  這些函式已有更安全的版本可用，請參閱 [\_snscanf\_s、\_snscanf\_s\_l、\_snwscanf\_s、\_snwscanf\_s\_l](../../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)。  
  
## 語法  
  
```  
int __cdecl _snscanf(  
   const char * input,  
   size_t length,  
   const char * format,  
   ...  
);  
int __cdecl _snscanf_l(  
   const char * input,  
   size_t length,  
   const char * format,  
   locale_t locale,  
   ...  
);  
int __cdecl _snwscanf(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   ...  
);  
int __cdecl _snwscanf_l(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   locale_t locale,  
   ...  
);  
```  
  
#### 參數  
 `input`  
 要檢查的輸入字串。  
  
 `length`  
 要檢查之 `input` 中的字元數。  
  
 `format`  
 一或多個格式規範。  
  
 `... (optional)`  
 要用來儲存由 `format`的格式規範從輸入字串擷取的值的變數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 每個這些函式都會傳回成功轉換和指派的欄位數；傳回值不包括已讀取但未指派的欄位。  傳回值 0 表示未指定欄位。  如果發生錯誤，或者在第一個轉換前就已經到達字串結尾，則傳回值是 `EOF`。  如需詳細資訊，請參閱[sscanf](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)。  
  
 如果 `input` 或 `format` 是 `NULL` 指標，或者，如果 `length` 小於或等於零，將呼叫無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會傳回 `EOF`，並將 `errno` 設為 `EINVAL`。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 這個函式與 `sscanf` 類似，差別在於它可讓您指定從輸入字串檢查字元的固定數目。  如需詳細資訊，請參閱[sscanf](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_sntscanf`|`_snscanf`|`_snscanf`|`_snwscanf`|  
|`_sntscanf_l`|`_snscanf_l`|`_snscanf_l`|`_snwscanf_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_snscanf`, `_snscanf_l`|\<stdio.h\>|  
|`_snwscanf`, `_snwscanf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_snscanf.c  
// compile with: /W3  
  
#include <stdio.h>  
int main( )  
{  
   char  str1[] = "15 12 14...";  
   wchar_t  str2[] = L"15 12 14...";  
   char  s1[3];  
   wchar_t  s2[3];  
   int   i;  
   float fp;  
  
   i = _snscanf( str1, 6,  "%s %f", s1, &fp); // C4996  
   // Note: _snscanf is deprecated; consider using _snscanf_s instead  
   printf("_snscanf converted %d fields: ", i);  
   printf("%s and %f\n", s1, fp);  
  
   i = _snwscanf( str2, 6,  L"%s %f", s2, &fp); // C4996  
   // Note: _snwscanf is deprecated; consider using _snwscanf_s instead  
   wprintf(L"_snwscanf converted %d fields: ", i);  
   wprintf(L"%s and %f\n", s2, fp);  
}  
```  
  
  **\_snscanf 轉換 2 欄位:15 和 12.000000**  
**\_snwscanf 轉換 2 欄位:15 和 12.000000**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [scanf 寬度規格](../../c-runtime-library/scanf-width-specification.md)