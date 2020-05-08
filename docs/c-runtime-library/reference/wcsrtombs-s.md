---
title: wcsrtombs_s
ms.date: 4/2/2020
api_name:
- wcsrtombs_s
- _o_wcsrtombs_s
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: c804d232dbcce67b8d467eaa37ccf2b15282881a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910589"
---
# <a name="wcsrtombs_s"></a>wcsrtombs_s

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
已轉換字串的大小（以位元組為單位），包括 null 結束字元。

*mbstr*<br/>
所產生之已轉換的多位元組字串的緩衝區位址。

*sizeInBytes*<br/>
*Mbstr*緩衝區的大小（以位元組為單位）。

*wcstr*<br/>
指向要轉換的寬字元字串。

*計數*<br/>
要儲存在*mbstr*緩衝區中的最大位元組數目，或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*mbstate*<br/>
**Mbstate_t**轉換狀態物件的指標。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。

|錯誤狀況|傳回值和**errno**|
|---------------------|------------------------------|
|*mbstr*是**Null** ，而*sizeInBytes* > 0|**EINVAL**|
|*wcstr*為**Null**|**EINVAL**|
|目的緩衝區太小，無法包含已轉換的字串（除非*count*是 **_TRUNCATE**，請參閱下面的備註）|**ERANGE**|

如果發生上述任何一種情況，則會叫用無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回錯誤碼並設定**errno** ，如下表所示。

## <a name="remarks"></a>備註

**Wcsrtombs_s**函式會使用*mbstate*中包含的轉換狀態，將*wcstr*所指向的寬字元字串轉換為儲存在*mbstr*所指向的緩衝區中的多位元組字元。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：

- 遇到 Null 寬字元

- 遇到無法轉換的寬字元

- 儲存在*mbstr*緩衝區中的位元組數目等於*count*。

目的字串一律會以 Null 結束 (即使發生錯誤亦然)。

如果*count*是[_TRUNCATE](../../c-runtime-library/truncate.md)的特殊值，則**wcsrtombs_s**會盡可能將字串轉換為符合目的地緩衝區的大小，同時仍留出空間給 null 結束字元。

如果**wcsrtombs_s**成功轉換來源字串，則會將已轉換字串的大小（包括 null 結束字元）放入 *&#42;pReturnValue* （提供的*pReturnValue*不是**null**）。 即使*mbstr*引數為**Null** ，也會提供方法來判斷所需的緩衝區大小。 請注意，如果*mbstr*為**Null**，則會忽略*count* 。

如果**wcsrtombs_s**遇到無法轉換成多位元組字元的寬字元，會將-1 放在* \*pReturnValue*中，將目的緩衝區設定為空字串，將**errno**設為**EILSEQ**，並傳回**EILSEQ**。

如果*wcstr*和*mbstr*所指向的序列重迭， **wcsrtombs_s**的行為會是未定義的。 **wcsrtombs_s**會受到目前地區設定的 LC_TYPE 分類所影響。

> [!IMPORTANT]
> 請確定*wcstr*和*mbstr*不會重迭，而且該*計數*會正確反映要轉換的寬字元數。

**Wcsrtombs_s**函式與[wcstombs_s、_wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)的重新開機功能不同。 轉換狀態會儲存在*mbstate*中，以供後續呼叫相同或其他可重新開機的函式。 混合使用可重新啟動和不可重新啟動之函式的結果不明。 例如，如果使用了**wcsrtombs_s**的後續呼叫，而不是**wcstombs_s**，應用程式就會使用**wcsrlen**而非**wcslen**。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="exceptions"></a>例外狀況

只要在執行此函式時，目前線程中的函式不會呼叫**setlocale** ，而且*mbstate*為 null， **wcsrtombs_s**函式就是多執行緒安全。

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

int main()
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
[語言](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
