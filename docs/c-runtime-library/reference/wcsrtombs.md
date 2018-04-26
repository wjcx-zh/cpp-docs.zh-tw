---
title: wcsrtombs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: ea3544c9d6d84ab4671e505f7389f72dbb25095a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="wcsrtombs"></a>wcsrtombs

將寬字元字串轉換為其多位元組字元字串表示法。 此函式已有更安全的版本，請參閱 [wcsrtombs_s](wcsrtombs-s.md)。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*mbstr*<br/>
產生的已轉換多位元組字串的位址位置。

*wcstr*<br/>
間接指向要轉換的寬字元字串位置。

*count*<br/>
要轉換的字元數。

*mbstate*<br/>
指標**mbstate_t**轉換狀態物件。

## <a name="return-value"></a>傳回值

傳回成功轉換的位元組數，不含 Null 終止 Null 位元組 (如果有的話)，如果發生錯誤則為 -1。

## <a name="remarks"></a>備註

**Wcsrtombs**函式中指定的轉換狀態中包含開頭的寬字元字串，轉換為*mbstate*，在指向的值間接*wcstr*，插入的地址*mbstr*。 針對每個字元，才會繼續進行轉換： 之後遇到 null 終止的寬字元時，發生非對應的字元時，或下一個字元會超過限制包含在*計數*。 如果**wcsrtombs**之前或期間遇到寬字元的 null 字元 (L '\0')*計數*發生時，會將它轉換成 8 位元 0 而停止。

因此，在多位元組字元字串*mbstr*是以 null 終止才**wcsrtombs**在轉換期間所遇到的寬字元的 null 字元。 如果指向的序列*wcstr*和*mbstr*重疊，行為**wcsrtombs**是未定義。 **wcsrtombs**會受到目前地區設定之 LC_TYPE 分類。

**Wcsrtombs**函式不同於[wcstombs、 _wcstombs_l](wcstombs-wcstombs-l.md)重新。 轉換狀態會儲存在*mbstate*的相同或其他可重新啟動的函式的後續呼叫。 混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，應用程式會使用**wcsrlen**而**wcsnlen**，如果的後續呼叫**wcsrtombs**而不是使用**wcstombs**.

如果*mbstr*引數是**NULL**， **wcsrtombs**傳回目的地字串位元組中的所需的大小。 如果*mbstate*為 null，內部**mbstate_t**會使用轉換狀態。 如果字元序列*wchar*沒有對應的多位元組字元表示法，則傳回-1 和**errno**設**EILSEQ**。

在 C++ 中，這個函式具有樣板多載，可以叫用比這個函式更新且更安全的相對版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>例外狀況

**Wcsrtombs**函式是多執行緒安全，只要在目前執行緒中的任何函式呼叫**setlocale**此函式執行時和*mbstate*不是 null。

## <a name="example"></a>範例

```cpp
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
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
