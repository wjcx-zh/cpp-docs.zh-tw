---
title: __max
ms.date: 04/05/2018
apiname:
- __max
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
apitype: DLLExport
f1_keywords:
- max
- __max
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: 32e1207ea4bb030ac5303de32c0566f98e0596a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613755"
---
# <a name="max"></a>__max

傳回兩個值的較大的前置處理器巨集。

## <a name="syntax"></a>語法

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>參數

， *b*<br/>
要比較之任何數字類型的值。

## <a name="return-value"></a>傳回值

**__max**傳回其引數的較大。

## <a name="remarks"></a>備註

**__Max**巨集比較兩個值，並傳回較大的值。 引數可以是帶正負號或不帶正負號的任何數值資料類型。 引數和傳回值必須屬於相同的資料類型。

傳回引數會評估兩次由巨集。 這可能會導致非預期的結果引數是否會改變其值，其進行評估時，這類運算式`*p++`。

## <a name="requirements"></a>需求

|巨集|必要的標頭|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>範例

如需詳細資訊，請參閱 [__min](min.md) 的範例。

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>