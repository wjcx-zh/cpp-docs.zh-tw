---
title: wcrtomb | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcrtomb
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
- wcrtomb
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
caps.latest.revision: 26
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 853295a50158caa92ed9370b6267e4e623f7d790
ms.lasthandoff: 02/24/2017

---
# <a name="wcrtomb"></a>wcrtomb
將寬字元轉換為其多位元組字元表示法。 此函式已有更安全的版本，請參閱 [wcrtomb_s](../../c-runtime-library/reference/wcrtomb-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
size_t wcrtomb(  
   char *mbchar,  
   wchar_t wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t wcrtomb(  
   char (&mbchar)[size],  
   wchar_t wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `mbchar`  
 產生的多位元組轉換字元。  
  
 [in] `wchar`  
 要轉換的寬字元。  
  
 [in] `mbstate`  
 `mbstate_t` 物件的指標。  
  
## <a name="return-value"></a>傳回值  
 傳回代表已轉換多位元組字元的必要位元組數，如果發生錯誤則為 -1。  
  
## <a name="remarks"></a>備註  
 `wcrtomb` 函式會轉換寬字元，從 `mbstate` 包含的指定轉換狀態開始，從 `wchar` 包含的值中，變成 `mbchar` 代表的位址。 傳回值是表示對應的多位元組字元所需的位元組數目，但它不會傳回超過 `MB_CUR_MAX` 個位元組。  
  
 如果 `mbstate` 為 Null，則使用包含 `mbchar` 轉換狀態的內部 `mbstate_t` 物件。 如果字元序列 `wchar` 沒有對應的多位元組字元表示法，則傳回 -1，並將 `errno` 設為 `EILSEQ`。  
  
 `wcrtomb` 函式因為可以重新開機，而與 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md) 不同。 針對相同或其他可重新啟動的函式的後續呼叫，轉換狀態會儲存在 `mbstate` 中。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如，如果使用了 `wcsrtombs` 的後續呼叫，而不是 `wcstombs`，應用程式應該使用 `wcsrlen`，而不是 `wcsnlen`。  
  
 在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="exceptions"></a>例外狀況  
 `wcrtomb` 函式是安全多執行緒，但前提是當這個函式執行中、且 `mbstate` 為 Null 時，目前執行緒中沒有任何函式呼叫 `setlocale`。  
  
## <a name="example"></a>範例  
  
```  
// crt_wcrtomb.c  
// compile with: /W3  
// This program converts a wide character  
// to its corresponding multibyte character.  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    size_t      sizeOfCovertion = 0;  
    mbstate_t   mbstate;  
    char        mbStr = 0;  
    wchar_t*    wcStr = L"Q";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996  
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead  
    if (sizeOfCovertion > 0)  
    {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wcStr);  
        printf(" was converted to the \"%c\" ", mbStr);  
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
The corresponding wide character "Q" was converted to the "Q" multibyte character.  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`wcrtomb`|\<wchar.h>|  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)
