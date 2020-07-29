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
ms.openlocfilehash: d7da4fe52d25d9ffdf6371aa40f41d7082f1165c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226837"
---
# <a name="cptrlist-class"></a>CPtrList 類別

支援 void 指標的清單。

## <a name="syntax"></a>語法

```
class CPtrList : public CObject
```

## <a name="members"></a>成員

的成員函式 `CPtrList` 類似于[CObList](../../mfc/reference/coblist-class.md)類別的成員函式。 由於此相似性，您可以針對成員函式特性使用 `CObList` 參考文件。 只要您看到 `CObject` 指標做為函式參數或傳回值，請將指標替換為 **`void`** 。

`CObject*& CObList::GetHead() const;`

例如，轉換為

`void*& CPtrList::GetHead() const;`

## <a name="remarks"></a>備註

`CPtrList`併入 IMPLEMENT_DYNAMIC 宏，以支援執行時間類型存取和傾印至 `CDumpContext` 物件。 如果您需要個別指標清單項目傾印，您必須將傾印內容的深度設定為 1 (含) 以上。

指標清單不可序列化。

當 `CPtrList` 物件被刪除，或當它的項目被移除時，只會移除指標，而非它們參考的實體。

如需有關使用的詳細資訊 `CPtrList` ，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CPtrList`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObList 類別](../../mfc/reference/coblist-class.md)
