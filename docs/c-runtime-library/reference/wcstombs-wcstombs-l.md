---
title: "wcstombs、_wcstombs_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcstombs
- _wcstombs_l
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
- wcstombs
- _wcstombs_l
dev_langs:
- C++
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
caps.latest.revision: 30
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 200337a53155b27b76a944d025c8fb013c29c4e6
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="wcstombs-wcstombsl"></a>wcstombs、_wcstombs_l
將一連串的寬字元轉換為對應的一連串多位元組字元。 這些函式已有更安全的版本，請參閱 [wcstombs_s、_wcstombs_s_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)。  
  
## <a name="syntax"></a>語法  
  
```  
size_t wcstombs(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count   
);  
size_t _wcstombs_l(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t wcstombs(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _wcstombs_l(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `mbstr`  
 多位元組字元序列的位址。  
  
 `wcstr`  
 寬字元序列的位址。  
  
 `count`  
 可以儲存在多位元組輸出字串的最大位元組數。  
  
 `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 如果 `wcstombs` 成功轉換多位元組字串，即會傳回寫入多位元組輸出字串的位元組數目，不包括終止的 `NULL` (如果有的話)。 如果 `mbstr` 引數為 `NULL`，則 `wcstombs` 會傳回目的字串所需的大小 (以位元組為單位)。 如果`wcstombs`遇到寬字元不能轉換的多位元組字元，則傳回-1 轉換為類型`size_t`並設定`errno`至`EILSEQ`。  
  
## <a name="remarks"></a>備註  
 `wcstombs` 函式會將 `wcstr` 指向的寬字元字串轉換成對應的多位元組字元，並將結果儲存在 `mbstr` 陣列中。 `count` 參數指出可以儲存在多位元組輸出字串的最大位元組數 (亦即 `mbstr` 的大小)。 轉換寬字元字串時通常不知道需要多少個位元組。 某些寬字元只需要輸出字串的一個位元組，有些則需要兩個。 如果多位元組輸出字串為輸入字串的每個寬字元都提供兩個位元組 (包括寬字元 `NULL`)，結果保證符合。  
  
 如果在 `count` 發生前或發生時，`wcstombs` 遇到寬字元 Null 字元 (L'\0')，就會將它轉換成 8 位元的 0 並停止。 因此，只有當 `wcstombs` 在轉換期間遇到寬字元的 Null 字元時，`mbstr` 的多位元組字元字串才能以 Null 終止。 如果 `wcstr` 和 `mbstr` 所指向的序列重疊，`wcstombs` 的行為不明。  
  
 如果 `mbstr` 引數為 `NULL`，則 `wcstombs` 會傳回目的字串所需的大小 (以位元組為單位)。  
  
 `wcstombs` 會驗證其參數。 如果`wcstr`是`NULL`，或如果`count`大於`INT_MAX`，此函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則函式會將 `errno` 設定為 `EINVAL` 並傳回 -1。  
  
 `wcstombs` 會針對任何與地區設定相關的行為使用目前的地區設定，`_wcstombs_l` 與其相同，只不過它會改用傳入的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`wcstombs`|\<stdlib.h>|  
|`_wcstombs_l`|\<stdlib.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 此程式說明 `wcstombs` 函式的行為。  
  
```  
// crt_wcstombs.c  
// compile with: /W3  
// This example demonstrates the use  
// of wcstombs, which converts a string  
// of wide characters to a string of   
// multibyte characters.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t  count;  
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t *pWCBuffer = L"Hello, world.";  
  
    printf("Convert wide-character string:\n" );  
  
    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s instead  
    printf("   Characters converted: %u\n",  
            count );  
    printf("    Multibyte character: %s\n\n",  
           pMBBuffer );  
  
    free(pMBBuffer);  
}  
```  
  
```Output  
Convert wide-character string:  
   Characters converted: 13  
    Multibyte character: Hello, world.  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)
