---
title: wcsrtombs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcsrtombs
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
- wcsrtombs
dev_langs:
- C++
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
caps.latest.revision: 26
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 6dfe7e2293f9544b64a0dfd7dfaa1889e65a64dc
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="wcsrtombs"></a>wcsrtombs
將寬字元字串轉換為其多位元組字元字串表示法。 此函式已有更安全的版本，請參閱 [wcsrtombs_s](../../c-runtime-library/reference/wcsrtombs-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
size_t wcsrtombs(  
   char *mbstr,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t wcsrtombs(  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `mbstr`  
 產生的已轉換多位元組字串的位址位置。  
  
 [in] `wcstr`  
 間接指向要轉換的寬字元字串位置。  
  
 [in] `count`  
 要轉換的字元數。  
  
 [in] `mbstate`  
 `mbstate_t` 轉換狀態物件的指標。  
  
## <a name="return-value"></a>傳回值  
 傳回成功轉換的位元組數，不含 Null 終止 Null 位元組 (如果有的話)，如果發生錯誤則為 -1。  
  
## <a name="remarks"></a>備註  
 `wcsrtombs` 函式會轉換寬字元字串，從 `mbstate` 包含的指定轉換狀態開始，從 `wcstr` 中間接指向的值，變成 `mbstr` 的位址。 每個字元都會轉換，一直持續到︰遇到以 Null 終止的寬字元後、遇到非對應的字元時，或下一個字元會超過 `count` 包含的限制時。 如果在 `count` 發生前或發生時，`wcsrtombs` 遇到寬字元 Null 字元 (L'\0')，就會將它轉換成 8 位元的 0 並停止。  
  
 因此，只有當 `wcsrtombs` 在轉換期間遇到寬字元的 Null 字元時，`mbstr` 的多位元組字元字串才能以 Null 終止。 如果 `wcstr` 和 `mbstr` 所指向的序列重疊，`wcsrtombs` 的行為不明。 `wcsrtombs` 受到目前地區設定之 LC_TYPE 分類的影響。  
  
 `wcsrtombs` 函式因為可以重新開機，而與 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) 不同。 針對相同或其他可重新啟動的函式的後續呼叫，轉換狀態會儲存在 `mbstate` 中。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，如果使用了 `wcsrtombs` 的後續呼叫，而不是 `wcstombs`，應用程式應該使用 `wcsrlen`，而不是 `wcsnlen`。  
  
 如果 `mbstr` 引數為 `NULL`，則 `wcsrtombs` 會傳回目的字串所需的大小 (以位元組為單位)。 如果 `mbstate` 為 Null，則使用內部的 `mbstate_t` 轉換狀態。 如果字元序列 `wchar` 沒有對應的多位元組字元表示法，則傳回 -1，並將 `errno` 設為 `EILSEQ`。  
  
 在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="exceptions"></a>例外狀況  
 `wcsrtombs` 函式是安全多執行緒，但前提是當這個函式執行中、且 `mbstate` 不為 Null 時，目前執行緒中沒有任何函式呼叫 `setlocale`。  
  
## <a name="example"></a>範例  
  
```  
// crt_wcsrtombs.cpp  
// compile with: /W3  
// This code example converts a wide  
// character string into a multibyte  
// character string.  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
int main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    countConverted = wcsrtombs(mbString, &wcsIndirectString,  
                               MB_BUFFER_SIZE, &mbstate); // C4996  
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s  
    if (errno == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfuly converted.\n" );  
    }  
}  
```  
  
```Output  
The string was successfuly converted.  
```  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`wcsrtombs`|\<wchar.h>|  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)
