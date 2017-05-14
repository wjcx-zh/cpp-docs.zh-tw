---
title: wcrtomb_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcrtomb_s
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
- wcrtomb_s
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: d80bcc1bfda2fa5b7495b9ea0fb92a99056494b6
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="wcrtombs"></a>wcrtomb_s
將寬字元轉換為其多位元組字元表示法。 這是具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char *mbchar,  
   size_t sizeOfmbchar,  
   wchar_t *wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char (&mbchar)[size],  
   wchar_t *wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `pReturnValue`  
 傳回寫入的位元組數目，如果發生錯誤則為 -1。  
  
 [輸出] `mbchar`  
 產生的多位元組轉換字元。  
  
 [in] `sizeOfmbchar`  
 `mbchar` 變數的大小，以位元組為單位。  
  
 [in] `wchar`  
 要轉換的寬字元。  
  
 [in] `mbstate`  
 `mbstate_t` 物件的指標。  
  
## <a name="return-value"></a>傳回值  
 傳回零，如果發生錯誤則為 `errno` 值。  
  
## <a name="remarks"></a>備註  
 `wcrtomb_s` 函式會轉換寬字元，從 `mbstate` 包含的指定轉換狀態開始，從 `wchar` 包含的值中，變成 `mbchar` 代表的位址。 `pReturnValue` 值會是轉換的位元組數，但不超過 `MB_CUR_MAX` 個位元組，如果發生錯誤則為 -1。  
  
 如果 `mbstate` 為 Null，則使用內部的 `mbstate_t` 轉換狀態。 如果 `wchar` 包含的字元沒有對應的多位元組字元，則 `pReturnValue` 值會是 -1 且函式會傳回 `EILSEQ` 的 `errno` 值。  
  
 `wcrtomb_s` 函式因為可以重新開機，而與 [wctomb_s、_wctomb_s_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md) 不同。 針對相同或其他可重新啟動的函式的後續呼叫，轉換狀態會儲存在 `mbstate` 中。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如，如果使用了 `wcsrtombs_s` 的後續呼叫，而不是 `wcstombs_s.`，應用程式應該使用 `wcsrlen`，而不是 `wcslen`。  
  
 C++ 利用多載樣板簡化了此函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="exceptions"></a>例外狀況  
 `wcrtomb_s` 函式是安全多執行緒，但前提是當這個函式執行中、且 `mbstate` 為 Null 時，目前執行緒中沒有任何函式呼叫 `setlocale`。  
  
## <a name="example"></a>範例  
  
```  
// crt_wcrtomb_s.c  
// This program converts a wide character  
// to its corresponding multibyte character.  
//  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    errno_t     returnValue;  
    size_t      pReturnValue;  
    mbstate_t   mbstate;  
    size_t      sizeOfmbStr = 1;  
    char        mbchar = 0;  
    wchar_t*    wchar = L"Q\0";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),  
                            *wchar, &mbstate);  
    if (returnValue == 0) {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wchar);  
        printf(" was converted to a the \"%c\" ", mbchar);  
        printf("multibyte character.\n");  
    }  
    else  
    {  
        printf("No corresponding multibyte character "  
               "was found.\n");  
    }  
}  
```  
  
```Output  
The corresponding wide character "Q" was converted to a the "Q" multibyte character.  
```  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`wcrtomb_s`|\<wchar.h>|  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)
