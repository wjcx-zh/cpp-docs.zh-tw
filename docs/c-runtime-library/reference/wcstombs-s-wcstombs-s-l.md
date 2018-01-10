---
title: "wcstombs_s、_wcstombs_s_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcstombs_s_l
- wcstombs_s
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
- wcstombs_s
- _wcstombs_s_l
dev_langs: C++
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5c57a82bef1a56925b414302fe2017df255ce2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="wcstombss-wcstombssl"></a>wcstombs_s、_wcstombs_s_l

將一連串的寬字元轉換為對應的一連串多位元組字元。 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count   
);  

errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  

template <size_t size>  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  

template <size_t size>  
errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  

[out]*pReturnValue*  
已轉換的字元數。  
  
[out]*mbstr*  
所產生之已轉換的多位元組字串的緩衝區位址。  
  
[in]*sizeInBytes*  
以位元組為單位的大小*mbstr*緩衝區。  
  
[in]*wcstr*  
指向要轉換的寬字元字串。  
  
[in]*計數*  
要儲存的位元組數目上限*mbstr*緩衝區，不包括結束的 null 字元，或[_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
[in]*地區設定*  
要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  

如果成功，則為零，如果失敗，則為錯誤碼。  
  
|錯誤狀況|傳回值和 `errno`|  
|---------------------|------------------------------|  
|*mbstr*是`NULL`和*sizeInBytes* > 0|`EINVAL`|  
|*wcstr*是`NULL`|`EINVAL`|  
|目的地緩衝區為太小，無法包含已轉換的字串 (除非*計數*是`_TRUNCATE`; 請參閱下面的備註)|`ERANGE`|  
  
如果發生上述任何一種情況，則會叫用無效的參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回錯誤碼，並將 `errno` 設為如表中所示。  
  
## <a name="remarks"></a>備註  

`wcstombs_s`函式所指向的寬字元字串，轉換為*wcstr*到儲存在緩衝區所指向的多位元組字元*mbstr*。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：  
  
-   遇到 Null 寬字元  
  
-   遇到無法轉換的寬字元  
  
-   儲存在位元組數目*mbstr*緩衝等於*計數*。  
  
目的字串一律會以 Null 結束 (即使發生錯誤亦然)。  
  
如果*計數*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md)，然後`wcstombs_s`轉換的字串會盡量符合目的緩衝區，同時仍保留留給 null 結束字元的空間。 如果字串遭到截斷，則傳回值是`STRUNCATE`，和轉換會被視為成功。  
  
如果`wcstombs_s`成功轉換來源的字串，它會將大小以位元組為單位的已轉換的字串，包含 null 結束字元，放`*pReturnValue`(提供*pReturnValue*不`NULL`)。 發生這種情況即使*mbstr*引數是`NULL`，並提供一個方式來判斷所需的緩衝區大小。 請注意，如果*mbstr*是`NULL`，*計數*會被忽略。  
  
如果 `wcstombs_s` 遇到它無法轉換成多位元組字元的寬字元，會將 0 放入 `*pReturnValue`，再將目的緩衝區設為空字串，續將 `errno` 設為 `EILSEQ`，最後傳回 `EILSEQ`。  
  
如果指向的序列*wcstr*和*mbstr*重疊，行為`wcstombs_s`是未定義。  
  
> [!IMPORTANT]
>  請確認*wcstr*和*mbstr*沒有重疊，而且*計數*會正確反映要轉換的寬字元數目。  
  
`wcstombs_s` 會針對任何與地區設定相關的行為使用目前的地區設定，`_wcstombs_s_l` 與 `wcstombs` 相同，只不過它會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`wcstombs_s`|\<stdlib.h>|  
  
如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  

此程式說明 `wcstombs_s` 函式的行為。  
  
```C  
// crt_wcstombs_s.c  
// This example converts a wide character  
// string to a multibyte character string.  
#include <stdio.h>  
#include <stdlib.h>  
#include <assert.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t   i;  
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t*pWCBuffer = L"Hello, world.";  
  
    printf( "Convert wide-character string:\n" );  
  
    // Conversion  
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,   
               pWCBuffer, (size_t)BUFFER_SIZE );  
  
    // Output  
    printf("   Characters converted: %u\n", i);  
    printf("    Multibyte character: %s\n\n",  
     pMBBuffer );  
  
    // Free multibyte character buffer  
    if (pMBBuffer)  
    {  
    free(pMBBuffer);  
    }  
}  
```  
  
```Output  
Convert wide-character string:  
   Characters converted: 14  
    Multibyte character: Hello, world.  
```  
  
## <a name="see-also"></a>請參閱  

[資料轉換](../../c-runtime-library/data-conversion.md)   
[地區設定](../../c-runtime-library/locale.md)   
[_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
[mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
[mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
[wctomb_s、_wctomb_s_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)   
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)