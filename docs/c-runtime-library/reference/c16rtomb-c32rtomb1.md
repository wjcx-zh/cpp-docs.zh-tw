---
title: c16rtomb，c32rtomb
ms.date: 01/22/2018
apiname:
- c16rtomb
- c32rtomb
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
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: ad58184c7bab6f95a842bda5f9eb545f09434a3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341752"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb，c32rtomb

將 UTF-16 或 UTF-32 寬字元轉換成目前地區設定的多位元組字元。

## <a name="syntax"></a>語法

```C
size_t c16rtomb(
    char *mbchar,
    char16_t wchar,
    mbstate_t *state
);
size_t c32rtomb(
    char *mbchar,
    char32_t wchar,
    mbstate_t *state
);
```

### <a name="parameters"></a>參數

*mbchar*<br/>
儲存多位元組轉換字元陣列的指標。

*wchar*<br/>
要轉換的寬字元。

*state*<br/>
指標**mbstate_t**物件。

## <a name="return-value"></a>傳回值

陣列物件中儲存的位元組數目*mbchar*，包括任何移位序列。 如果*wchar*不是有效的寬字元，值 (**size_t**傳回)(-1) **errno**設定為**EILSEQ**，的值*狀態*未指定。

## <a name="remarks"></a>備註

**C16rtomb**函式會將轉換的 utf-16 字元*wchar*目前的地區設定中的對等的多位元組窄字元序列。 如果*mbchar*不是 null 指標所指向的陣列物件中已轉換的序列的函式存放區*mbchar*。 最多**MB_CUR_MAX**位元組會儲存在*mbchar*，並*狀態*設為產生的多位元組移位狀態。    如果*wchar*是 null 寬字元序列，才能的還原初始移位狀態會儲存，如有需要後面接著 null 字元，並*狀態*設為初始轉換狀態。 **C32rtomb**函式相同，但轉換 UTF-32 字元。

如果*mbchar*為 null 指標，行為相當於呼叫替代的內部緩衝區的函式*mbchar*和 寬 null 字元*wchar*。

*狀態*轉換狀態物件可讓您進行後續呼叫此函式和其他可重新啟動的函式所維護的多位元組輸出字元移位狀態。 當您混合使用可重新啟動和非可重新啟動的函式，或如果呼叫，結果便未定義**setlocale**之間可重新啟動的函式呼叫。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**c16rtomb**， **c32rtomb**|C、C++：\<uchar.h>|

如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtoc16、mbrtoc32](mbrtoc16-mbrtoc323.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
