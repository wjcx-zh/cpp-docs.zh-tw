---
title: "_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
dev_langs:
- C++
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: f947080d27efa7794d08db06adef307072739984
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="strncnt-wcsncnt-mbsnbcnt-mbsnbcntl-mbsnccnt-mbsnccntl"></a>_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l
傳回指定計次數內的字元或位元組數目。  
  
> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中無法使用  `_mbsnbcnt`、`_mbsnbcnt_l`、`_mbsnccnt` 和 `_mbsnccnt_l`。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
size_t _strncnt(  
   const char *str,  
   size_t count  
);  
size_t _wcsncnt(  
   const wchar_t *str,  
   size_t count  
);  
size_t _mbsnbcnt(  
   const unsigned char *str,  
   size_t count   
);  
size_t _mbsnbcnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
size_t _mbsnccnt(  
   const unsigned char *str,  
   size_t count  
);  
size_t _mbsnccnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `str`  
 要檢查的字串。  
  
 `count`  
 要以 `str` 檢查的字元或位元組數。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 `_mbsnbcnt` 和 `_mbsnbcnt_l` 傳回在 `str` 的前 `count` 個多位元組字元中找到的位元組數目。 `_mbsnccnt` 和 `_mbsnccnt_l` 傳回在 `str` 的前 `count` 個位元組中找到的字元數目。 如果在 `str` 檢查完成前碰到 NULL 字元，它們會傳回在 NULL 字元前找到的字元或位元組數。 如果 `str` 的組成字元或位元組數少於 `count`，它們會傳回字串中的字元或位元組數。 如果 `count` 小於零，它們會傳回 0。 在舊版中，這些函式有 `int` 類型的傳回值，而不是 `size_t`。  
  
 `_strncnt` 傳回單一位元組字串 `str` 的前 `count` 個位元組。 `_wcsncnt` 傳回寬字元字串 `str` 的前 `count` 個寬字元。  
  
## <a name="remarks"></a>備註  
 `_mbsnbcnt` 和 `_mbsnbcnt_l` 計算在 `str` 的前 `count` 個多位元組字元中找到的位元組數目。 `_mbsnbcnt` 和 `_mbsnbcnt_l` 取代 `mtob`，應該用於取代 `mtob`。  
  
 `_mbsnccnt` 和 `_mbsnccnt_l` 計算在 `str` 的前 `count` 個位元組中找到的字元數目。 如果 `_mbsnccnt` 和 `_mbsnccnt_l` 在雙位元組字元的第二個位元組碰到 NULL，則第一個位元組也視為 NULL 且不包含在傳回的計數值中。 `_mbsnccnt` 和 `_mbsnccnt_l` 取代 `btom`，應該用於取代 `btom`。  
  
 如果 `str` 為 Null 指標，或 `count` 為 0，則這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述，`errno` 設為 `EINVAL` 且函式傳回 0。  
  
 輸出值會受到地區設定的 `LC_CTYPE` 類別設定影響；如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 這些沒有 `_l` 後置字元的函式版本，會針對此與地區設定相關的行為使用目前的地區設定；具有 `_l` 後置字元的版本也一樣，只不過它們會改用傳遞的地區設定參數。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|-------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnbcnt`|`_strncnt`|`_mbsnbcnt`|`_wcsncnt`|  
|`_tcsnccnt`|`_strncnt`|`_mbsnbcnt`|`n/a`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnbcnt`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnccnt`|  
|`n/a`|`n/a`|`_mbsnbcnt_l`|`_mbsnccnt_l`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_mbsnbcnt`|\<mbstring.h>|  
|`_mbsnbcnt_l`|\<mbstring.h>|  
|`_mbsnccnt`|\<mbstring.h>|  
|`_mbsnccnt_l`|\<mbstring.h>|  
|`_strncnt`|\<tchar.h>|  
|`_wcsncnt`|\<tchar.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_mbsnbcnt.c  
  
#include  <mbstring.h>  
#include  <stdio.h>  
  
int main( void )  
{  
   unsigned char str[] = "This is a multibyte-character string.";  
   unsigned int char_count, byte_count;  
   char_count = _mbsnccnt( str, 10 );  
   byte_count = _mbsnbcnt( str, 10 );  
   if ( byte_count - char_count )  
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );  
   else  
      printf( "The first 10 characters are single-byte.\n");  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
The first 10 characters are single-byte.  
```  
  
## <a name="see-also"></a>另請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbsnbcat、_mbsnbcat_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)
