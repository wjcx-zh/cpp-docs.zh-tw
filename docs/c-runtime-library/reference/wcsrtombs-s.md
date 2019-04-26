---
title: wcsrtombs_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: bd965271a65fa91b427c7af7bbd4173b129e1d8c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188567"
---
# <a name="wcsrtombss"></a>wcsrtombs_s

將寬字元字串轉換為其多位元組字元字串表示法。 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [wcsrtombs](wcsrtombs.md) 版本。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*pReturnValue*<br/>
大小 （位元組） 的已轉換的字串，包括 null 結束字元。

*mbstr*<br/>
所產生之已轉換的多位元組字串的緩衝區位址。

*sizeInBytes*<br/>
以位元組為單位的大小*mbstr*緩衝區。

*wcstr*<br/>
指向要轉換的寬字元字串。

*count*<br/>
要儲存在位元組的數目上限*mbstr*緩衝區，或是[_TRUNCATE](../../c-runtime-library/truncate.md)。

*mbstate*<br/>
指標**mbstate_t**轉換狀態物件。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。

|錯誤狀況|傳回值和**errno**|
|---------------------|------------------------------|
|*mbstr*已**NULL**並*sizeInBytes* > 0|**EINVAL**|
|*wcstr*是**NULL**|**EINVAL**|
|目的緩衝區太小而無法包含已轉換的字串 (除非*計數*是 **_TRUNCATE**; 請參閱下面的 < 備註 >)|**ERANGE**|

如果發生上述任何一種情況，則會叫用無效的參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回錯誤碼，並設定**errno**資料表中所示。

## <a name="remarks"></a>備註

**Wcsrtombs_s**函式會將所指向的寬字元字串轉換*wcstr*到儲存在緩衝區所指向的多位元組字元*mbstr*，並使用中包含的轉換狀態*mbstate*。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：

- 遇到 Null 寬字元

- 遇到無法轉換的寬字元

- 儲存在位元組的數目*mbstr*緩衝 equals*計數*。

目的字串一律會以 Null 結束 (即使發生錯誤亦然)。

如果*計數*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md)，然後**wcsrtombs_s**的字串會轉換符合目的緩衝區，同時仍留出空間給 null 值結束字元。

如果**wcsrtombs_s**成功轉換來源字串中，它會在將大小以位元組為單位的已轉換的字串，包括 null 結束字元，將放置 *&#42;pReturnValue* (提供*pReturnValue*不是**NULL**)。 發生這種情況即使*mbstr*引數是**NULL** ，並提供一個方式來判斷所需的緩衝區大小。 請注意，如果*mbstr*是**NULL**，*計數*會被忽略。

如果**wcsrtombs_s**遇到寬字元，它無法轉換成多位元組字元，它將-1 放入 *\*pReturnValue*，將目的緩衝區設為空字串，設定**errno**要**EILSEQ**，並傳回**EILSEQ**。

如果指向的序列所*wcstr*並*mbstr*重疊，就會有的行為**wcsrtombs_s**是未定義。 **wcsrtombs_s**會受到目前地區設定之 LC_TYPE 分類。

> [!IMPORTANT]
> 請確認*wcstr*並*mbstr*未重疊時，且*計數*正確反映要轉換的寬字元數目。

**Wcsrtombs_s**函式與不同[wcstombs_s、 _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)重新。 轉換狀態會儲存在*mbstate*的後續呼叫相同或其他可重新啟動的函式。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如，應用程式會使用**wcsrlen**而非**wcslen**，如果後續呼叫**wcsrtombs_s**而不是使用**wcstombs_s**.

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>例外狀況

**Wcsrtombs_s**函式是多執行緒的安全，只要在目前的執行緒中的任何函式會呼叫**setlocale**執行此函式時， *mbstate*為 null。

## <a name="example"></a>範例

```cpp
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
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
