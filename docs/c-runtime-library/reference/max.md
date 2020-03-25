---
title: __max
ms.date: 04/05/2018
api_name:
- __max
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- max
- __max
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: 4cdfd99ec344cd357900d76dfc7f9400046e448a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170185"
---
# <a name="__max"></a>__max

預處理器宏，它會傳回兩個值中較大的一個。

## <a name="syntax"></a>語法

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>參數

*a*、 *b*<br/>
要比較之任何數字類型的值。

## <a name="return-value"></a>傳回值

**__max**會傳回其引數中較大的一個。

## <a name="remarks"></a>備註

**__Max**宏比較兩個值，並傳回較大的值。 引數可以是帶正負號或不帶正負號的任何數值資料類型。 引數和傳回值必須屬於相同的資料類型。

傳回的引數會透過宏進行兩次評估。 如果引數是在評估時改變其值的運算式，例如 `*p++`，這可能會導致非預期的結果。

## <a name="requirements"></a>需求

|巨集|必要的標頭|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>範例

如需詳細資訊，請參閱 [__min](min.md) 的範例。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>
