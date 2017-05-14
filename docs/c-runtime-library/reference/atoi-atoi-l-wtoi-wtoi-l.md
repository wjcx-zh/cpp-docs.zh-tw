---
title: "atoi、_atoi_l、_wtoi、_wtoi_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wtoi
- _wtoi_l
- atoi
- _atoi_l
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tstoi
- _wtoi
- _ttoi
- atoi
- _atoi_l
- _wtoi_l
dev_langs:
- C++
helpviewer_keywords:
- _atoi_l function
- ttoi function
- atoi_l function
- string conversion, to integers
- _wtoi function
- wtoi_l function
- tstoi function
- _ttoi function
- _tstoi function
- _wtoi_l function
- atoi function
- wtoi function
ms.assetid: ad7fda30-28ab-421f-aaad-ef0b8868663a
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 5ed38a5d4c5a9ff6d976302cc52cc14672a4d60b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="atoi-atoil-wtoi-wtoil"></a>atoi、_atoi_l、_wtoi、_wtoi_l
將字串轉換成整數。  
  
## <a name="syntax"></a>語法  
  
```  
int atoi(  
   const char *str   
);  
int _wtoi(  
   const wchar_t *str   
);  
int _atoi_l(  
   const char *str,  
   _locale_t locale  
);  
int _wtoi_l(  
   const wchar_t *str,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>參數  
 `str`  
 要轉換的字串。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 每個函式都會傳回將輸入字元解譯為數字所產生的 `int` 值。 如果輸入無法轉換成該類型的值，則 `atoi` 和 `_wtoi` 的傳回值為 0。  
  
 如果溢位具有大型負整數值，則傳回 `LONG_MIN`。 `atoi` 和 `_wtoi` 會對這些條件傳回 `INT_MAX` 和 `INT_MIN`。 在所有超出範圍的情況下，`errno` 設為 `ERANGE`。 如果傳入的參數為 `NULL`，則會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 0。  
  
## <a name="remarks"></a>備註  
 這些函式會將字元字串轉換成整數值 (`atoi` 和 `_wtoi`)。 輸入字串是一串字元，可解譯為所指定類型的數值。 此函式會從無法辨識為數字一部分的第一個字元處停止讀取輸入字串。 此字元可能是終止字串的 Null 字元 ('\0' 或 L'\0')。  
  
 `atoi` 和 `_wtoi` 的 `str` 引數具有下列形式：  
  
 [`whitespace`] [`sign`] [`digits`]]  
  
 A`whitespace`包含空格或定位字元，都會被忽略;`sign`是加號 （+） 或減號 （-）; 和`digits`一或多個位數。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定參數，而不使用目前的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstoi`|`atoi`|`atoi`|`_wtoi`|  
|`_ttoi`|`atoi`|`atoi`|`_wtoi`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|--------------|---------------------|  
|`atoi`|\<stdlib.h>|  
|`_atoi_l`, `_wtoi`, `_wtoi_l`|\<stdlib.h> 或 \<wchar.h>|  
  
## <a name="example"></a>範例  
 此程式示範如何使用 `atoi` 函式將儲存為字串的數字轉換成數值。  
  
```  
// crt_atoi.c  
// This program shows how numbers   
// stored as strings can be converted to  
// numeric values using the atoi functions.  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    int     value = 0;  
  
    // An example of the atoi function.  
    str = "  -2309 ";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atoi function.  
    str = "31412764";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atoi function   
    // with an overflow condition occuring.  
    str = "3336402735171707160320";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
```Output  
Function: atoi( "  -2309 " ) = -2309  
Function: atoi( "31412764" ) = 31412764  
Function: atoi( "3336402735171707160320" ) = 2147483647  
Overflow condition occurred.  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)
