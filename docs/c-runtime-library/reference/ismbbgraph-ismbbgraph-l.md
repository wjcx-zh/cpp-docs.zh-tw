---
title: _ismbbgraph、_ismbbgraph_l
ms.date: 11/04/2016
api_name:
- _ismbbgraph_l
- _ismbbgraph
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
- api-ms-win-crt-multibyte-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbbgraph
- _ismbbgraph_l
- ismbbgraph
- ismbbgraph_l
helpviewer_keywords:
- _ismbbgraph_l function
- ismbbgraph_l function
- _ismbbgraph function
- ismbbgraph function
ms.assetid: b60db718-134f-4796-acc1-592d0b9efbb7
ms.openlocfilehash: 096450869f9a150585b3102cea155ecd948c5751
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954193"
---
# <a name="_ismbbgraph-_ismbbgraph_l"></a>_ismbbgraph、_ismbbgraph_l

判斷某個多位元組字元是否為圖形字元。

## <a name="syntax"></a>語法

```C
int _ismbbgraph (
   unsigned int c
);
int _ismbbgraph_l (
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>參數

*C*<br/>
待測試整數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回非零值表示運算式：

`isctype(c, ( _PUNCT | _UPPER | _LOWER | _DIGIT )) || _ismbbkprint(c)`

*c*為非零值; 如果不是，則為0。 **_ismbbgraph**會針對任何與地區設定相關的行為使用目前的地區設定。 **_ismbbgraph_l**相同，不同之處在于它會改為使用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_ismbbgraph**|\<mbctype.h>|
|**_ismbbgraph_l**|\<mbctype.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[位元組分類](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 常式](../../c-runtime-library/ismbb-routines.md)<br/>
