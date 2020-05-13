---
title: MFC 類別物件的類型轉換
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
ms.openlocfilehash: 953acc32c3510b31c265f2d64d0a013f6dee06cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372885"
---
# <a name="type-casting-of-mfc-class-objects"></a>MFC 類別物件的類型轉換

類型轉換宏提供了一種將給定指標轉換為指向特定類對象的指標的方法,無論是否檢查強制轉換是否合法。

下表列出了 MFC 類型強制轉換宏。

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>向 MFC 類別強制轉換指標的巨集

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|在檢查強制轉換是否合法時,將指向類物件的指標強制轉換。|
|[STATIC_DOWNCAST](#static_downcast)|將指向物件的指標從一個類轉換為相關類型的指標。 在調試生成中,如果物件不是目標類型的"類型",則會導致 ASSERT。|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST

提供了一種方便的方法,用於在檢查強制轉換是否合法時,將指向類對象的指標轉換為指標。

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>參數

*class*<br/>
類的名稱。

*指標*<br/>
要轉換為指向類型*類*物件的指標的指標。

### <a name="remarks"></a>備註

宏將*指標*參數轉換為指向*類*參數類型物件的指標。

如果指標引用的對像是標識的類的"類型",則宏將返回相應的指標。 如果它不是法定強制轉換,宏將返回 NULL。

## <a name="static_downcast"></a><a name="static_downcast"></a>STATIC_DOWNCAST

將*pobject*投射到指向*class_name*物件的指標。

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>參數

*class_name*<br/>
要強制轉換到的類的名稱。

*pobject*<br/>
要轉換為指向*class_name*物件的指標。

### <a name="remarks"></a>備註

*pobject*必須是 NULL,或者指向直接從或間接派生自*class_name*的類的物件。 在定義了_DEBUG預處理器符號的應用程式的版本中,如果*pobject*不是 NULL,或者如果它指向不是*class_name*參數中指定的類的"類型"的物件(請參閱[CObject:IsKindOf),](../../mfc/reference/cobject-class.md#iskindof)宏將斷言。 在非 **_DEBUG**生成中,宏執行強制轉換,無需進行任何類型檢查。

*class_name*參數中指定的類必須派生`CObject`自 ,並且必須使用DECLARE_DYNAMIC和IMPLEMENT_DYNAMIC、DECLARE_DYNCREATE和IMPLEMENT_DYNCREATE,或者DECLARE_SERIAL和IMPLEMENT_SERIAL宏,如[CObject 類別中的說明:從 CObject 派生類](../../mfc/deriving-a-class-from-cobject.md)。

例如,您可以將指標轉換為`CMyDoc``pMyDoc`呼叫的指標,指向`CDocument`使用此表示式的指標:

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

如果不`pMyDoc`指向直接或間接派生的`CDocument`物件 ,宏將斷言。

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
