---
title: "_ltoa_s、_ltow_s | Microsoft Docs"
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
  - "_ltoa_s"
  - "_ltow_s"
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
  - "_ltow_s"
  - "_ltoa_s"
  - "ltoa_s"
  - "ltow_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ltoa_s 函式"
  - "_ltow_s 函式"
  - "轉換整數"
  - "轉換數字, 到字串"
  - "將長整數轉換為字串"
  - "ltoa_s 函式"
  - "ltow_s 函式"
ms.assetid: d7dc61ea-1ccd-412d-b262-555a58647386
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ltoa_s、_ltow_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將長整數轉換成字串。  這些是 [\_ltoa、\_ltow](../../c-runtime-library/reference/ltoa-ltow.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t _ltoa_s(  
    long value,  
    char *str,  
    size_t sizeOfstr,  
    int radix   
);  
errno_t _ltow_s(  
    long value,  
    wchar_t *str,  
    size_t sizeOfstr,  
    int radix   
);  
template <size_t size>  
errno_t _ltoa_s(  
    long value,  
    char (&str)[size],  
    int radix   
); // C++ only  
template <size_t size>  
errno_t _ltow_s(  
    long value,  
    wchar_t (&str)[size],  
    int radix   
); // C++ only  
```  
  
#### 參數  
 `value`  
 被轉換的數字。  
  
 `str`  
 結果字串的緩衝區。  
  
 `sizeOfstr`  
 以位元組為單位的 `str` 大小用 `_ltoa_s` ，或以字為單位用 `_ltow_s`。  
  
 `radix`  
 `value`的基底。  
  
## 傳回值  
 如果函式成功，回傳零，反之為錯誤碼。  
  
## 備註  
 `_ltoa_s` 函式轉換 `value` 中的字元至以 null 結尾的字元字串並將結果儲存至 `str` \(至多33 位元組\)。  `radix` 引數指定 `value`的基底，必須介於 2 – 36 之間。  如果 `radix` 等於 10，而且 `value` 是負數，儲存的字串的第一個字元為負號 \(\-\)。  `_ltow_s` 是 `_ltoa_s` 的寬字元版本；`_ltow_s` 的第二引數是寬字元字串。  
  
 如果 `str` 是 `NULL` 指標或 `sizeOfstr` 小於或等於零，這些函式叫用無效參數的處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式傳回 \-1 並將 `errno` 設為 `EINVAL` ，或是 `value` 或 `str` 超過長整數的範圍，這些函式會傳回 \-1 並將`errno` 設定為 `ERANGE`。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_ltot_s`|`_ltoa_s`|`_ltoa_s`|`_ltow_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ltoa_s`|\<stdlib.h\>|  
|`_ltow_s`|\<stdlib.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [\_itoa、\_i64toa、\_ui64toa、\_itow、\_i64tow、\_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [\_ultoa、\_ultow](../../c-runtime-library/reference/ultoa-ultow.md)   
 [\_ultoa\_s、\_ultow\_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md)