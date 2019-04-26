---
title: offsetof 巨集
ms.date: 11/04/2016
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
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: a0f367dbe6fa2681a7d413304f32b5699b8f7cee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156058"
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

**offsetof**傳回以位元組為單位的指定成員的位移，從其父資料結構開頭。 位元欄位並未定義它。

## <a name="remarks"></a>備註

**Offsetof**巨集傳回以位元組為單位的位移*memberName*所指定結構開頭*structName*類型的值為**size_t**。 您可以指定具有類型**結構**關鍵字。

> [!NOTE]
> **offsetof**不是函式，而且不能使用 C 原型所述。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
