---
title: "_ultoa_s、_ultow_s | Microsoft Docs"
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
  - "_ultow_s"
  - "_ultoa_s"
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
  - "_ultow_s"
  - "ultoa_s"
  - "ultow_s"
  - "_ultoa_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ultoa_s 函式"
  - "_ultow_s 函式"
  - "轉換整數"
  - "轉換數字, 到字串"
  - "整數, 轉換"
  - "ultoa_s 函式"
  - "ultow_s 函式"
ms.assetid: 606ce905-6752-46ac-a15a-bdc22920e1d4
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ultoa_s、_ultow_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換成不帶正負號的長整數的字串。  這些是 [\_ultoa、\_ultow](../../c-runtime-library/reference/ultoa-ultow.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t _ultoa_s(  
    unsigned long value,  
    char *str,  
    size_t sizeOfstr,  
    int radix   
);  
errno_t _ultow_s(  
    unsigned long value,  
    wchar_t *str,  
    size_t sizeOfstr,  
    int radix   
);  
template <size_t size>  
errno_t _ultoa_s(  
    unsigned long value,  
    char (&str)[size],  
    int radix   
); // C++ only  
template <size_t size>  
errno_t _ultow_s(  
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
  
 `sizeOfstr`  
 `_ultoa_s`以位元組為單位的 `str` 大小，或 `_ultow_s`以字為單位的大小。  
  
 `radix`  
 `value`的基底。  
  
## 傳回值  
 如果函式成功，回傳零，反之為錯誤碼。  
  
## 備註  
 `_ultoa_s` 函式轉換 `value` 中的字元至以 null 結尾的字元字串並將結果儲存至 `str` \(至多33位元組\)。   `radix` 引數指定 `value`的基底，必須介於 2 – 36 之間。  `_ultow_s` 是 `_ultoa_s` 的寬字元版本；`_ultow_s` 的第二引數是寬字元字串。  
  
 如果 `str` 是 `NULL` 指標，或者`sizeOfstr`小於或等於零，將呼叫無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式傳回 \-1 並將 `errno` 設為 `EINVAL` ，或是 `value` 或 `str` 超過長整數的範圍，這些函式會傳回 \-1 並將`errno` 設定為 `ERANGE`。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_ultot_s`|`_ultoa_s`|`_ultoa_s`|`_ultow_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ultoa_s`|\<stdlib.h\>|  
|`_ultow_s`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [\_ultoa、\_ultow](../../c-runtime-library/reference/ultoa-ultow.md)   
 [\_ltoa、\_ltow](../../c-runtime-library/reference/ltoa-ltow.md)   
 [\_ltoa\_s、\_ltow\_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)   
 [\_ltoa\_s、\_ltow\_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)