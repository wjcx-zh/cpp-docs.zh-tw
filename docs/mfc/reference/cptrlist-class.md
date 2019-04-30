---
title: CPtrList 類別
ms.date: 11/04/2016
f1_keywords:
- CPtrList
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
ms.openlocfilehash: 5b88b0950b3b46f9738bd26080883c00d46f8555
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372435"
---
# <a name="cptrlist-class"></a>CPtrList 類別

支援 void 指標的清單。

## <a name="syntax"></a>語法

```
class CPtrList : public CObject
```

## <a name="members"></a>成員

成員函式`CPtrList`類別的成員函式類似[CObList](../../mfc/reference/coblist-class.md)。 由於此相似性，您可以針對成員函式特性使用 `CObList` 參考文件。 無論在何處看到`CObject`指標做為函式參數或傳回值，取代指標**void**。

`CObject*& CObList::GetHead() const;`

例如，轉換為

`void*& CPtrList::GetHead() const;`

## <a name="remarks"></a>備註

`CPtrList` 併入 IMPLEMENT_DYNAMIC 巨集，以支援執行階段類型存取和傾印`CDumpContext`物件。 如果您需要個別指標清單項目傾印，您必須將傾印內容的深度設定為 1 (含) 以上。

指標清單不可序列化。

當 `CPtrList` 物件被刪除，或當它的項目被移除時，只會移除指標，而非它們參考的實體。

如需有關使用`CPtrList`，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CPtrList`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObList 類別](../../mfc/reference/coblist-class.md)
