---
title: "_ultoa、_ultow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ultoa"
  - "_ultow"
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
  - "ultot"
  - "ultow"
  - "_ultoa"
  - "_ultow"
  - "_ultot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ultoa 函式"
  - "_ultot 函式"
  - "_ultow 函式"
  - "轉換整數"
  - "轉換數字, 到字串"
  - "整數, 轉換"
  - "ultot 函式"
  - "ultow 函式"
ms.assetid: 7a472dc4-5652-4513-93c3-3358522c23be
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _ultoa、_ultow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換成不帶正負號的長整數的字串。  這些函式已有更安全的版本可用，請參閱 [\_ultoa\_s、\_ultow\_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md)。  
  
## 語法  
  
```  
char *_ultoa(  
   unsigned long value,  
   char *str,  
   int radix   
);  
wchar_t *_ultow(  
   unsigned long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ultoa(  
   unsigned long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ultow(  
   unsigned long value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
```  
  
#### 參數  
 `value`  
 被轉換的數字。  
  
 `str`  
 字串的結果。  
  
 `radix`  
 `value`的基底*。*  
  
## 傳回值  
 這些函式都會傳回一個 `str`的指標。  不會回傳錯誤。  
  
## 備註  
 `_ultoa` 函式轉換 `value` 至以 null 結尾的字元字串並將結果儲存至 `str` \(至多33 位元組\)。  不執行超值檢查。  `radix` 指定 `value`基底; `radix` 必須介於 2 – 36。  `_ultow` 是 `_ultoa`的寬字元版本。  
  
> [!IMPORTANT]
>  若要防止緩衝區滿溢，請確定 `str` 緩衝區有足夠空間去儲存轉換位元和多出來的 null 字元。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用更新、更安全的這些函式的相對版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_ultot`|`_ultoa`|`_ultoa`|`_ultow`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ultoa`|\<stdlib.h\>|  
|`_ultow`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [\_itoa](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [\_itoa、\_i64toa、\_ui64toa、\_itow、\_i64tow、\_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)