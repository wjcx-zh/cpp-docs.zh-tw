---
title: offsetof 巨集
ms.date: 11/04/2016
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
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: ee6d5e56bb9f41a842e53984f754c7c07d58a125
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213498"
---
# <a name="offsetof-macro"></a>offsetof 巨集

從其父結構開頭擷取成員的位移。

## <a name="syntax"></a>語法

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>參數

*structName*<br/>
父資料結構的名稱。

*基*<br/>
要判斷其位移之父資料結構中成員的名稱。

## <a name="return-value"></a>傳回值

**offsetof**會從其父資料結構的開頭，傳回指定成員的位移（以位元組為單位）。 位元欄位並未定義它。

## <a name="remarks"></a>備註

**Offsetof**宏會以位元組為單位，從*structname 類型*所指定的結構開頭，傳回*成員*的位移，以**size_t**的類型。 您可以使用關鍵字指定類型 **`struct`** 。

> [!NOTE]
> **offsetof**不是函式，而且無法使用 C 原型加以描述。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
