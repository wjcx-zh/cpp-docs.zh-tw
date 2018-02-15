---
title: mbrlen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbrlen
dev_langs:
- C++
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c5c110c1fc5917614514b4e4fd7e474569026207
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="mbrlen"></a>mbrlen
判斷完成目前地區設定的多位元組字元所需的位元組數目，並提供在多位元組字元中間重新啟動的功能。  
  
## <a name="syntax"></a>語法  
  
```  
size_t mbrlen(  
   const char * str,  
   size_t count,  
   mbstate_t * mbstate  
);  
```  
  
#### <a name="parameters"></a>參數  
 `str`  
 多位元組字元字串中要檢查的下一個位元組指標。  
  
 `count`  
 要檢查的最大位元組數目。  
  
 `mbstate`  
 `str` 之初始位元組的目前移位狀態指標。  
  
## <a name="return-value"></a>傳回值  
 下列其中一個值：  
  
 0  
 後 `count` 個位元組 (或更少個位元組) 會完成代表 null 寬字元的多位元組字元。  
  
 1 到 `count` (含)  
 後 `count` 個位元組 (或更少個位元組) 會完成有效的多位元組字元。 傳回的值是完成多位元組字元的位元組數目。  
  
 (size_t)(-2)  
 後 `count` 個位元組會產生不完整但可能有效的多位元組字元，並且已處理所有 `count` 個位元組。  
  
 (size_t)(-1)  
 發生編碼錯誤。 後 `count` 個位元組 (或更少個位元組) 不會產生完整且有效的多位元組字元。 在這個情況下，`errno` 會設為 EILSEQ，且 `mbstate` 中的轉換狀態為未指定。  
  
## <a name="remarks"></a>備註  
 `mbrlen` 函式會從 `count` 所指向的位元組開始，最多檢查 `str` 個位元組，來判斷完成下一個多位元組字元所需的位元組數目，包括任何移位序列。 函式相當於呼叫 `mbrtowc(NULL, str, count, &mbstate)`，其中 `mbstate` 是使用者提供的 `mbstate_t` 物件，或程式庫提供的靜態內部物件。  
  
 `mbrlen` 函式會在 `mbstate` 參數中，儲存及使用不完整多位元組字元的移位狀態。 這讓 `mbrlen` 可視需要在多位元組字元的中間重新啟動，並檢查最多 `count` 個位元組。 如果 `mbstate` 是 null 指標，`mbrlen` 會使用內部靜態 `mbstate_t` 物件儲存移位狀態。 由於內部 `mbstate_t` 物件不是安全執行緒，因此建議您一律配置及傳遞自己的 `mbstate` 參數。  
  
 `mbrlen` 函式的重新啟動能力與 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md) 不同。 移位狀態會儲存在 `mbstate` 中，以對相同或其他可重新啟動的函式進行後續呼叫。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，如果使用 `wcsrlen` 的後續呼叫，而不是 `wcslen`，應用程式應該使用 `wcsrtombs`，而不是 `wcstombs.`。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|不適用|不適用|`mbrlen`|不適用|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`mbrlen`|\<wchar.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
 這個範例示範多位元組字元的解譯如何取決於目前的字碼頁，並示範 `mbrlen` 的繼續功能。  
  
```C  
// crt_mbrlen.c  
// Compile by using: cl crt_mbrlen.c  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
#include <locale.h>  
#include <wchar.h>  
  
size_t Example(const char * pStr)  
{  
    size_t      charLen = 0;  
    size_t      charCount = 0;  
    mbstate_t   mbState = {0};  
  
    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&  
            charLen != (size_t)-1)  
    {  
        if (charLen != (size_t)-2) // if complete mbcs char,  
        {  
            charCount++;  
        }  
    }   
    return (charCount);  
}   
  
int main( void )  
{  
    int         cp;  
    size_t      charCount = 0;  
    const char  *pSample =   
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";  
  
    cp = _getmbcp();  
    charCount = Example(pSample);  
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",   
        cp, pSample, charCount);  
  
    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale  
    _setmbcp(932); // and Japanese multibyte code page  
    cp = _getmbcp();  
    charCount = Example(pSample);  
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",   
        cp, pSample, charCount);  
}  
```  
  
```Output  
  
Code page: 0  
é╨éτé¬é╚: Shift-jis hiragana.  
Character count: 29  
  
Code page: 932  
????: Shift-jis hiragana.  
Character count: 25  
  
```  
  
## <a name="see-also"></a>請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)