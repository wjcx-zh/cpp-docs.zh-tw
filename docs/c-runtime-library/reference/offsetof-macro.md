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
ms.openlocfilehash: 278fca89046fcfc98e8c3ff726918cb4319e4ab0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951254"
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

*memberName*<br/>
要判斷其位移之父資料結構中成員的名稱。

## <a name="return-value"></a>傳回值

**offsetof**會從其父資料結構的開頭，傳回指定成員的位移（以位元組為單位）。 位元欄位並未定義它。

## <a name="remarks"></a>備註

**Offsetof**宏會從*structname 類型*所指定的結構開頭以*位元組為單位*，傳回值為**size_t**的位移。 您可以使用**struct**關鍵字來指定類型。

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
