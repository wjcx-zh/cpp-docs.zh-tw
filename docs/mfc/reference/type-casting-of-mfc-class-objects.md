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
ms.openlocfilehash: e3702ced83021e42ac6bf71a78efc51fa07b8be9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840488"
---
# <a name="type-casting-of-mfc-class-objects"></a>MFC 類別物件的類型轉換

類型轉換宏提供一種方法，可將指定指標轉型為指向特定類別之物件的指標，而不會檢查轉換是否合法。

下表列出 MFC 型別轉換宏。

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>將指標轉換成 MFC 類別物件的宏

|名稱|描述|
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|將指標轉換成類別物件的指標，同時檢查轉換是否合法。|
|[STATIC_DOWNCAST](#static_downcast)|將物件的指標從某個類別轉換成相關型別的指標。 在 debug 組建中，如果物件不是目標型別的「種類」，則會導致判斷提示。|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a> DYNAMIC_DOWNCAST

提供一個便利的方式，將指標轉換成類別物件的指標，同時檢查轉換是否合法。

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>參數

*class*<br/>
類別的名稱。

*指標*<br/>
要轉換成 *類別*型別物件之指標的指標。

### <a name="remarks"></a>備註

宏會將 *指標* 參數轉換為 *類別* 參數類型之物件的指標。

如果指標所參考的物件是已識別之類別的「種類」，則該宏會傳回適當的指標。 如果它不是合法的轉換，則宏會傳回 Null。

## <a name="static_downcast"></a><a name="static_downcast"></a> STATIC_DOWNCAST

將 *pobject* 轉換為 *class_name* 物件的指標。

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>參數

*class_name*<br/>
要轉換成的類別名稱。

*pobject*<br/>
要轉換成 *class_name* 物件之指標的指標。

### <a name="remarks"></a>備註

*pobject* 必須是 Null，或指向類別的物件，而該物件是直接或間接衍生自 *class_name*。 在已定義 _DEBUG 預處理器符號的應用程式組建中，如果 *pobject* 不是 Null，宏就會判斷提示，如果它指向的物件不是 *class_name* 參數中指定之類別的「種類」 (請參閱 [CObject：： IsKindOf](../../mfc/reference/cobject-class.md#iskindof)) 。 在非 **_DEBUG** 組建中，宏會在沒有任何類型檢查的情況下執行轉換。

在 *class_name* 參數中指定的類別必須衍生自 `CObject` ，而且必須使用 DECLARE_DYNAMIC 和 IMPLEMENT_DYNAMIC、DECLARE_DYNCREATE 和 IMPLEMENT_DYNCREATE，或 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏，如文章 [CObject 類別：從 cobject 衍生類別](../../mfc/deriving-a-class-from-cobject.md)中所述。

例如，您可能會將名為的指標轉換為 `CMyDoc` `pMyDoc` `CDocument` 使用這個運算式的指標：

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

如果沒有 `pMyDoc` 指向直接或間接衍生自的物件 `CDocument` ，宏將會判斷提示。

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
