---
title: c16rtomb，c32rtomb
ms.date: 01/22/2018
api_name:
- c16rtomb
- c32rtomb
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: a16effe48442ccbb5144b57ead2fb15c908fe898
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943421"
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
**Mbstate_t**物件的指標。

## <a name="return-value"></a>傳回值

儲存在陣列物件*mbchar*中的位元組數目，包括任何移位序列。 如果*wchar*不是有效的寬字元，則會傳回值（**size_t**）（-1）， **errno**會設定為**EILSEQ**，而*state*的值則為未指定。

## <a name="remarks"></a>備註

**C16rtomb**函數會將 utf-16 字元*wchar*轉換成目前地區設定中對等的多位元組窄字元序列。 如果*mbchar*不是 null 指標，函式會將轉換的序列儲存在*mbchar*所指向的陣列物件中。 最多**MB_CUR_MAX**個位元組會儲存在*mbchar*中，而*狀態*會設定為產生的多位元組移位狀態。    如果*wchar*是 null 寬字元，則會視需要儲存還原初始移位狀態所需的序列，後面接著 null 字元，並將*狀態*設定為初始轉換狀態。 **C32rtomb**函式完全相同，但會轉換 UTF-32 字元。

如果*mbchar*是 null 指標，此行為相當於呼叫函式，以替代*mbchar*的內部緩衝區和用於*wchar*的寬 null 字元。

*狀態*轉換狀態物件可讓您對此函式，以及維護多位元組輸出字元之移位狀態的其他可重新開機函數進行後續呼叫。 當您混合使用可重新開機和不可重新開機的函式，或在可重新開機的函式呼叫之間呼叫**setlocale**時，會產生未定義的結果。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**c16rtomb**、 **c32rtomb**|C、C++：\<uchar.h>|

如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtoc16、mbrtoc32](mbrtoc16-mbrtoc323.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
