---
title: CDocItem 類別
ms.date: 11/04/2016
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
ms.openlocfilehash: 6c1c1da14d732b6aff6ae07f86ae7b9c1b690b84
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291310"
---
# <a name="cdocitem-class"></a>CDocItem 類別

文件項目的基底類別，這些項目是文件資料的元件。

## <a name="syntax"></a>語法

```
class CDocItem : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDocItem::GetDocument](#getdocument)|傳回包含之項目的文件。|
|[CDocItem::IsBlank](#isblank)|判斷項目是否包含任何資訊。|

## <a name="remarks"></a>備註

`CDocItem` 物件用來代表用戶端和伺服器的文件中的 OLE 項目。

如需詳細資訊，請參閱文章[容器：實作容器](../../mfc/containers-implementing-a-container.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>需求

**標頭：** afxole.h

##  <a name="getdocument"></a>  CDocItem::GetDocument

呼叫此函式可取得包含項目的文件。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>傳回值

包含項目; 的文件指標NULL，如果項目不是文件的一部分。

### <a name="remarks"></a>備註

此函式會在衍生類別中覆寫[COleClientItem](../../mfc/reference/coleclientitem-class.md)並[COleServerItem](../../mfc/reference/coleserveritem-class.md)，將指標傳回至[COleDocument](../../mfc/reference/coledocument-class.md)、 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)，或有[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)物件。

##  <a name="isblank"></a>  CDocItem::IsBlank

預設的序列化發生時，由架構呼叫。

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>傳回值

非零值，如果項目不包含任何資訊;否則為 0。

### <a name="remarks"></a>備註

根據預設，`CDocItem`物件不是空白。 [COleClientItem](../../mfc/reference/coleclientitem-class.md)物件是有時空白因為它們直接衍生自`CDocItem`。 不過， [COleServerItem](../../mfc/reference/coleserveritem-class.md)物件永遠為空白。 根據預設，OLE 應用程式包含`COleClientItem`沒有 x 或 y 的物件範圍會序列化。 這是藉由傳回 TRUE 的覆寫從`IsBlank`項目時有任何 x 或 y 的範圍。

如果您想要在序列化期間實作其他動作，請覆寫這個函式。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDocument 類別](../../mfc/reference/coledocument-class.md)<br/>
[COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)
