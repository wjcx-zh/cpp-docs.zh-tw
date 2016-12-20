---
title: "_ltoa、_ltow | Microsoft Docs"
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
  - "_ltoa"
  - "_ltow"
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
  - "ltow"
  - "_ltot"
  - "_ltoa"
  - "_ltow"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ltoa 函式"
  - "_ltow 函式"
  - "轉換整數"
  - "轉換數字, 到字串"
  - "將長整數轉換為字串"
  - "ltoa 函式"
  - "ltow 函式"
ms.assetid: 14036104-2c25-4759-87c0-918ed8521e47
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ltoa、_ltow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將長整數轉換成字串。  這些函式已有更安全的版本可用，請參閱 [\_ltoa\_s、\_ltow\_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)。  
  
## 語法  
  
```  
char *_ltoa(  
   long value,  
   char *str,  
   int radix   
);  
wchar_t *_ltow(  
   long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ltoa(  
   long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ltow(  
   long value,  
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
 `value`的基底。  
  
## 傳回值  
 這些函式都會傳回一個 `str`的指標。  不會回傳錯誤。  
  
## 備註  
 `_ltoa` 函式轉換 `value` 中的字元至以 null 結尾的字元字串並將結果儲存至 `str` \(至多33位元組\)。   `radix` 引數指定 `value`的基底，必須介於 2 – 36 之間。  如果 `radix` 等於 10，而且 `value` 是負數，儲存的字串的第一個字元為負號 \(\-\)。  `_ltow` 是 `_ltoa` 的寬字元版本，`_ltow` 函式的第二參數和回傳值是寬字元字串。  這些功能都是 Microsoft 專有的。  
  
> [!IMPORTANT]
>  若要防止緩衝區滿溢，請確定 `str` 緩衝區有足夠空間去儲存轉換位元和多出來的 null 字元以及一個正負號字元。  
  
 在 C\+\+ 中，這些函式有範本多載。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_ltot`|`_ltoa`|`_ltoa`|`_ltow`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ltoa`|\<stdlib.h\>|  
|`_ltow`|\<stdlib.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
 請參閱 [\_itoa](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [\_itoa、\_i64toa、\_ui64toa、\_itow、\_i64tow、\_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [\_ultoa、\_ultow](../../c-runtime-library/reference/ultoa-ultow.md)