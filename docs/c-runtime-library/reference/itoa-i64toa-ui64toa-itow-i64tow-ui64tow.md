---
title: "_itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow | Microsoft Docs"
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
  - "_itow"
  - "_i64tow"
  - "_itoa"
  - "_i64toa"
  - "_ui64toa"
  - "_ui64tow"
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
  - "_i64tow"
  - "ui64toa"
  - "ui64tow"
  - "itot"
  - "_itot"
  - "_i64toa"
  - "_itoa"
  - "_itow"
  - "_ui64tow"
  - "i64toa"
  - "i64tow"
  - "itow"
  - "_ui64toa"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_i64toa 函式"
  - "_i64tow 函式"
  - "_itoa 函式"
  - "_itot 函式"
  - "_itow 函式"
  - "_ui64toa 函式"
  - "_ui64tow 函式"
  - "轉換整數"
  - "轉換數字, 到字串"
  - "i64toa 函式"
  - "i64tow 函式"
  - "整數, 轉換"
  - "itoa 函式"
  - "itot 函式"
  - "itow 函式"
  - "ui64toa 函式"
  - "ui64tow 函式"
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將一個整數轉換為字串。  更多這些函式的可用安全版本，請參閱 [\_itoa\_s、\_i64toa\_s、\_ui64toa\_s、\_itow\_s、\_i64tow\_s、\_ui64tow\_s](../../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md)。  
  
## 語法  
  
```  
char *_itoa(  
   int value,  
   char *str,  
   int radix   
);  
char *_i64toa(  
   __int64 value,  
   char *str,  
   int radix   
);  
char * _ui64toa(  
   unsigned _int64 value,  
   char *str,  
   int radix   
);  
wchar_t * _itow(  
   int value,  
   wchar_t *str,  
   int radix   
);  
wchar_t * _i64tow(  
   __int64 value,  
   wchar_t *str,  
   int radix   
);  
wchar_t * _ui64tow(  
   unsigned __int64 value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_itoa(  
   int value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
char *_i64toa(  
   __int64 value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
char * _ui64toa(  
   unsigned _int64 value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t * _itow(  
   int value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t * _i64tow(  
   __int64 value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t * _ui64tow(  
   unsigned __int64 value,  
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
 `value`的基底必須介於 2\-36之間。  
  
## 傳回值  
 這些函式都會傳回一個 `str`的指標。  不會回傳錯誤。  
  
## 備註  
 `_itoa`、 `_i64toa`和 `_ui64toa` 的函式轉換這些二進位數字，這些數字被賦予 `value` 至為 null 結尾字元的字串，並在 `str` 儲存結果 \( `_itoa` 有33個字元 ，`_i64toa` 和 `_ui64toa`則有65個字元\) 。  如果 `radix` 等於 10，而且 `value` 是負數，儲存的字串的第一個字元為負號\( `–` \)。  `_itow`、 `_i64tow`和 `_ui64tow` 分別為 `_itoa`、 `_i64toa`和 `_ui64toa`的寬字元版本。  
  
> [!IMPORTANT]
>  若要防止緩衝區滿溢，請確定 `str` 緩衝區有足夠空間去儲存轉換位元和多出來的 null 字元以及一個正負號字元。  
  
 在 C\+\+ 中，這些函式具有多載樣板，可以叫用更新、更安全的這些函式的相對版本。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_itot`|`_itoa`|`_itoa`|`_itow`|  
|`_i64tot`|`_i64toa`|`_i64toa`|`_i64tow`|  
|`_ui64tot`|`_ui64toa`|`_ui64toa`|`_ui64tow`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_itoa`|\<stdlib.h\>|  
|`_i64toa`|\<stdlib.h\>|  
|`_ui64toa`|\<stdlib.h\>|  
|`_itow`|\<stdlib.h\>|  
|`_i64tow`|\<stdlib.h\>|  
|`_ui64tow`|\<stdlib.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_itoa.c  
// compile with: /W3  
// This program makes use of the _itoa functions  
// in various examples.  
  
#include <string.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char buffer[65];  
   int r;  
   for( r=10; r>=2; --r )  
   {  
     _itoa( -1, buffer, r ); // C4996  
     // Note: _itoa is deprecated; consider using _itoa_s instead  
     printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
   }  
   printf( "\n" );  
   for( r=10; r>=2; --r )  
   {  
     _i64toa( -1L, buffer, r ); // C4996  
     // Note: _i64toa is deprecated; consider using _i64toa_s  
     printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
   }  
   printf( "\n" );  
   for( r=10; r>=2; --r )  
   {  
     _ui64toa( 0xffffffffffffffffL, buffer, r ); // C4996  
     // Note: _ui64toa is deprecated; consider using _ui64toa_s  
     printf( "base %d: %s (%d chars)\n", r, buffer, strnlen(buffer, _countof(buffer)) );  
   }  
}  
```  
  
  **十進位: \-1 \(2 個字元\)**  
**九進位: 12068657453 \(11 個字元\)**  
**八進位: 37777777777 \(11 個字元\)**  
**七進位: 211301422353 \(12 個字元\)**  
**六進位: 1550104015503 \(13 個字元\)**  
**五進位: 32244002423140 \(14 個字元\)**  
**四進位: 3333333333333333 \(16 個字元\)**  
**三進位: 102002022201221111210 \(21 個字元\)**  
**二進位: 11111111111111111111111111111111 \(32 個字元\)**  
**十進位: \-1 \(2 個字元\)**  
**九進位: 145808576354216723756 \(21 個字元\)**  
**八進位: 1777777777777777777777 \(22 個字元\)**  
**七進位: 45012021522523134134601 \(23 個字元\)**  
**六進位: 3520522010102100444244423 \(25 個字元\)**  
**五進位: 2214220303114400424121122430 \(28 個字元\)**  
**四進位: 33333333333333333333333333333333 \(32 個字元\)**  
**三進位: 11112220022122120101211020120210210211220 \(41 個字元\)**  
**二進位: 1111111111111111111111111111111111111111111111111111111111111111 \(64 個字元\)**  
**十進位: 18446744073709551615 \(20 個字元\)**  
**九進位: 145808576354216723756 \(21 個字元\)**  
**八進位: 1777777777777777777777 \(22 個字元\)**  
**七進位: 45012021522523134134601 \(23 個字元\)**  
**六進位: 3520522010102100444244423 \(25 個字元\)**  
**五進位: 2214220303114400424121122430 \(28 個字元\)**  
**四進位: 33333333333333333333333333333333 \(32 個字元\)**  
**三進位: 11112220022122120101211020120210210211220 \(41 個字元\)**  
**二進位: 1111111111111111111111111111111111111111111111111111111111111111 \(64 個字元\)**   
## .NET Framework 對等用法  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [\_ltoa、\_ltow](../../c-runtime-library/reference/ltoa-ltow.md)   
 [\_ltoa\_s、\_ltow\_s](../../c-runtime-library/reference/ltoa-s-ltow-s.md)   
 [\_ultoa、\_ultow](../../c-runtime-library/reference/ultoa-ultow.md)   
 [\_ultoa\_s、\_ultow\_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md)