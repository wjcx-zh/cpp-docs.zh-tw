---
title: "wcstombs_s、_wcstombs_s_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
caps.latest.revision: 31
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 41775d158213a79debbdb4245fc468694df8646e
ms.lasthandoff: 02/24/2017

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
 [輸出] `pReturnValue`  
 已轉換的字元數。  
  
 [輸出] `mbstr`  
 所產生之已轉換的多位元組字串的緩衝區位址。  
  
 [in]`sizeInBytes`  
 `mbstr` 緩衝區的大小，以位元組為單位。  
  
 [in] `wcstr`  
 指向要轉換的寬字元字串。  
  
 [in] `count`  
 儲存在 `mbstr` 緩衝區的位元組數目上限，不包括終止的 Null 字元，或 [_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 [in] `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為零，失敗則為錯誤碼。  
  
|錯誤狀況|傳回值和 `errno`|  
|---------------------|------------------------------|  
|`mbstr` 為 `NULL` 且 `sizeInBytes` > 0|`EINVAL`|  
|`wcstr` 是 `NULL`|`EINVAL`|  
|目的緩衝區太小，無法包含已轉換的字串 (除非 `count` 是 `_TRUNCATE`，請參閱下面的＜備註＞)|`ERANGE`|  
  
 如果發生上述任何一種情況，則會叫用無效的參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回錯誤碼，並將 `errno` 設為如表中所示。  
  
## <a name="remarks"></a>備註  
 `wcstombs_s` 函式會將 `wcstr` 指向的寬字元字串，轉換成儲存在 `mbstr` 所指向緩衝區的多位元組字元。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：  
  
-   遇到 Null 寬字元  
  
-   遇到無法轉換的寬字元  
  
-   `mbstr` 緩衝區中儲存的位元組數目等於 `count`。  
  
 目的字串一律會以 Null 結束 (即使發生錯誤亦然)。  
  
 如果 `count` 是特殊值 [_TRUNCATE](../../c-runtime-library/truncate.md)，則 `wcstombs_s` 會盡量轉換符合目的緩衝區的字串量，同時仍留出空間給 Null 結束字元。  
  
 如果 `wcstombs_s` 成功轉換來源字串，則會將包括 Null 終止字元在內的已轉換字串大小 (以位元組計) 放入 `*``pReturnValue` (假設 `pReturnValue` 不是 `NULL`)。 即使 `mbstr` 引數為 `NULL`，且可讓您決定所需的緩衝區大小，也會發生這種情況。 請注意，如果 `mbstr` 為 `NULL`，則略過 `count`。  
  
 如果 `wcstombs_s` 遇到它無法轉換成多位元組字元的寬字元，會將 0 放入 `*``pReturnValue`，再將目的緩衝區設為空字串，續將 `errno` 設為 `EILSEQ`，最後傳回 `EILSEQ`。  
  
 如果 `wcstr` 和 `mbstr` 所指向的序列重疊，`wcstombs_s` 的行為不明。  
  
> [!IMPORTANT]
>  確定 `wcstr` 和 `mbstr` 不會重疊，而且 `count` 正確反映要轉換的寬字元數。  
  
 `wcstombs_s` 會針對任何與地區設定相關的行為使用目前的地區設定，`_wcstombs_s_l` 與 `wcstombs` 相同，只不過它會改用傳入的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`wcstombs_s`|\<stdlib.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 此程式說明 `wcstombs_s` 函式的行為。  
  
```  
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
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb_s、_wctomb_s_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)
