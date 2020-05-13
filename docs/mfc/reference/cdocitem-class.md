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
ms.openlocfilehash: 438bc2a03239946dbfca53d5f2989c731b682ab0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375615"
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
|[CDocItem:取得文件](#getdocument)|返回包含該項目的文檔。|
|[CDocItem::是空白](#isblank)|確定該專案是否包含任何資訊。|

## <a name="remarks"></a>備註

`CDocItem`物件用於表示客戶端和伺服器文件中的 OLE 項。

有關詳細資訊,請參閱文章[「容器:實現容器](../../mfc/containers-implementing-a-container.md)」。。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="cdocitemgetdocument"></a><a name="getdocument"></a>CDocItem:取得文件

呼叫此函數以獲取包含項的文件。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>傳回值

指向包含項的文檔的指標;NULL,如果項不是文檔的一部分。

### <a name="remarks"></a>備註

此函數在派生類[COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem](../../mfc/reference/coleserveritem-class.md)中重寫,傳回指向[COleDocument、COle](../../mfc/reference/coledocument-class.md)[連結文件](../../mfc/reference/colelinkingdoc-class.md)或[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)物件的指標。

## <a name="cdocitemisblank"></a><a name="isblank"></a>CDocItem::是空白

當發生預設序列化時,由框架調用。

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>傳回值

如果專案不包含任何資訊,則非零;否則 0。

### <a name="remarks"></a>備註

預設情況下,`CDocItem`物件不為空。 [COleClientItem 物件](../../mfc/reference/coleclientitem-class.md)有時為空,因為它們直接`CDocItem`派生 自 。 但是[,COleServerItem 對象](../../mfc/reference/coleserveritem-class.md)始終為空。 預設情況下,包含`COleClientItem`沒有 x 或 y 範圍物件的 OLE 應用程式將序列化。 這是通過從項目沒有 x`IsBlank`或 y 範圍時從重寫返回 TRUE 來實現的。

如果要在序列化期間實現其他操作,則重寫此函數。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDocument 類別](../../mfc/reference/coledocument-class.md)<br/>
[COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)
