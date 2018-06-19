---
title: wcrtomb_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a035010c2af49c0d12b4b7f1d6429c66ba9032cc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415604"
---
# <a name="wcrtombs"></a>wcrtomb_s

將寬字元轉換為其多位元組字元表示法。 這是具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [wcrtomb](wcrtomb.md) 版本。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*pReturnValue*<br/>
傳回寫入的位元組數目，如果發生錯誤則為 -1。

*mbchar*<br/>
產生的多位元組轉換字元。

*sizeOfmbchar*<br/>
大小*mbchar*變數以位元組為單位。

*wchar*<br/>
要轉換的寬字元。

*mbstate*<br/>
指標**mbstate_t**物件。

## <a name="return-value"></a>傳回值

傳回零或**errno**值發生錯誤。

## <a name="remarks"></a>備註

**Wcrtomb_s**函式將轉換的寬字元，從包含在指定的轉換狀態*mbstate*中, 包含的值從*wchar*，到所代表的位址*mbchar*。 *PReturnValue*值將會是數個位元組轉換，但不是超過**MB_CUR_MAX**位元組，則為-1，發生錯誤。

如果*mbstate*為 null，內部**mbstate_t**會使用轉換狀態。 如果字元包含在*wchar*沒有對應的多位元組字元，值*pReturnValue*是-1，此函數會傳回**errno**值**EILSEQ**。

**Wcrtomb_s**函式不同於[wctomb_s、 _wctomb_s_l](wctomb-s-wctomb-s-l.md)重新。 轉換狀態會儲存在*mbstate*的相同或其他可重新啟動的函式的後續呼叫。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如，應用程式會使用**wcsrlen**而**wcslen**，如果的後續呼叫**wcsrtombs_s**而不是使用**wcstombs_s**.

C++ 利用多載樣板簡化了此函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>例外狀況

**Wcrtomb_s**函式是多執行緒安全，只要在目前執行緒中的任何函式呼叫**setlocale**此函式執行時和*mbstate*為 null。

## <a name="example"></a>範例

```C
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
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
