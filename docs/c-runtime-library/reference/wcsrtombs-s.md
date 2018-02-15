---
title: wcsrtombs_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- wcsrtombs_s
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
- wcsrtombs_s
dev_langs:
- C++
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0bb43cf628abfabe7b5900579ec6995c95c980b2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="wcsrtombss"></a>wcsrtombs_s
將寬字元字串轉換為其多位元組字元字串表示法。 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [wcsrtombs](../../c-runtime-library/reference/wcsrtombs.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `pReturnValue`  
 已轉換的字元數。  
  
 [輸出] `mbstr`  
 所產生之已轉換的多位元組字串的緩衝區位址。  
  
 [輸出] `sizeInBytes`  
 `mbstr` 緩衝區的大小，以位元組為單位。  
  
 [輸入] `wcstr`  
 指向要轉換的寬字元字串。  
  
 [輸入] `count`  
 要儲存在 `mbstr` 緩衝區中的位元組數目上限，或 [_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 [輸入] `mbstate`  
 `mbstate_t` 轉換狀態物件的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為零，如果失敗，則為錯誤碼。  
  
|錯誤狀況|傳回值和 `errno`|  
|---------------------|------------------------------|  
|`mbstr` 為 `NULL` 且 `sizeInBytes` > 0|`EINVAL`|  
|`wcstr` 是 `NULL`|`EINVAL`|  
|目的緩衝區太小，無法包含已轉換的字串 (除非 `count` 是 `_TRUNCATE`，請參閱下面的＜備註＞)|`ERANGE`|  
  
 如果發生上述任何一種情況，則會叫用無效的參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回錯誤碼，並將 `errno` 設為如表中所示。  
  
## <a name="remarks"></a>備註  
 `wcsrtombs_s` 函式會將 `wcstr` 指向的寬字元字串轉換成儲存在 `mbstr` 所指向緩衝區的多位元組字元，使用 `mbstate` 包含的轉換狀態。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：  
  
-   遇到 Null 寬字元  
  
-   遇到無法轉換的寬字元  
  
-   `mbstr` 緩衝區中儲存的位元組數目等於 `count`。  
  
 目的字串一律會以 Null 結束 (即使發生錯誤亦然)。  
  
 如果 `count` 是特殊值 [_TRUNCATE](../../c-runtime-library/truncate.md)，則 `wcsrtombs_s` 會盡量轉換符合目的緩衝區的字串量，同時仍留出空間給 Null 結束字元。  
  
 如果 `wcsrtombs_s` 成功轉換來源字串，則會將包括 Null 終止字元在內的已轉換字串大小 (以位元組計) 放入 `*pReturnValue` (假設 `pReturnValue` 不是 `NULL`)。 即使 `mbstr` 引數為 `NULL`，且可讓您決定所需的緩衝區大小，也會發生這種情況。 請注意，如果 `mbstr` 為 `NULL`，則略過 `count`。  
  
 如果 `wcsrtombs_s` 遇到它無法轉換成多位元組字元的寬字元，會將 -1 放入 `*pReturnValue`，再將目的緩衝區設為空字串，續將 `errno` 設為 `EILSEQ`，最後傳回 `EILSEQ`。  
  
 如果 `wcstr` 和 `mbstr` 所指向的序列重疊，`wcsrtombs_s` 的行為不明。 `wcsrtombs_s` 受到目前地區設定之 LC_TYPE 分類的影響。  
  
> [!IMPORTANT]
>  確定 `wcstr` 和 `mbstr` 不會重疊，而且 `count` 正確反映要轉換的寬字元數。  
  
 `wcsrtombs_s` 函式因為可以重新開機，而與 [wcstombs_s、_wcstombs_s_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md) 不同。 針對相同或其他可重新啟動的函式的後續呼叫，轉換狀態會儲存在 `mbstate` 中。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如，如果使用了 `wcsrtombs_s` 的後續呼叫，而不是 `wcstombs_s.`，應用程式應該使用 `wcsrlen`，而不是 `wcslen`。  
  
 C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="exceptions"></a>例外狀況  
 `wcsrtombs_s` 函式是安全多執行緒，但前提是當這個函式執行中、且 `mbstate` 為 Null 時，目前執行緒中沒有任何函式呼叫 `setlocale`。  
  
## <a name="example"></a>範例  
  
```  
// crt_wcsrtombs_s.cpp  
//   
// This code example converts a wide  
// character string into a multibyte  
// character string.  
//  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
void main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    errno_t         err;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,  
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);  
    if (err == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfully converted.\n" );  
    }  
}  
```  
  
```Output  
The string was successfully converted.  
```  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`wcsrtombs_s`|\<wchar.h>|  
  
## <a name="see-also"></a>請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)