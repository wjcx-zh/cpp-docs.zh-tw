---
title: CDocObjectServerItem 類別
ms.date: 03/27/2019
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnDoVerb
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnDoVerb
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
ms.openlocfilehash: 1f0f5cf93aab35a17f7174b2beee0d1398564a3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375532"
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem 類別

實作 DocObject 伺服器專屬的 OLE 伺服器動詞命令。

## <a name="syntax"></a>語法

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CDocObjectServer 專案:CDocObjectServer專案](#cdocobjectserveritem)|建構 `CDocObjectServerItem` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDocObjectServer 專案:取得文件](#getdocument)|檢索指向包含項的文件的指標。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CDocObjectServer專案::OnDoVerb](#ondoverb)|被調用以執行動詞。|
|[CDocObjectServer 專案::開啟隱藏](#onhide)|如果框架嘗試隱藏 DocObject 項,則引發異常。|
|[CDocObjectServer專案::在展會上](#onshow)|由框架調用以使 DocObject 項就地處於活動狀態。 如果專案不是 DocObject,請呼叫[COleServerItem::onShow。](../../mfc/reference/coleserveritem-class.md#onshow)|

## <a name="remarks"></a>備註

`CDocObjectServerItem`定義可重寫的成員函數[:OnHide、OnDoVerb](#onhide)和[OnDoVerb](#ondoverb)[OnShow](#onshow)。

要使用`CDocObjectServerItem`,`COleServerDoc`確保派生類`CDocObjectServerItem`中的[OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)重寫傳回新物件。 如果需要更改專案中的任何功能,可以創建自己的`CDocObjectServerItem`派生類的新實例。

有關文件物件的詳細資訊,請參閱*MFC 參考*中的[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[COleCmdUI。](../../mfc/reference/colecmdui-class.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>需求

**標題:** afxdocob.h

## <a name="cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a>CDocObjectServer 專案:CDocObjectServer專案

建構 `CDocObjectServerItem` 物件。

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>參數

*pServerDoc*<br/>
指向將包含新 DocObject 項的文件的指標。

*b 自動刪除*<br/>
指示在釋放指向該物件的連結時是否可以刪除該物件。 如果物件是文件資料的組成部分,`CDocObjectServerItem`則將參數設置為 FALSE。 如果對像是用於識別文件資料中可由框架刪除的範圍的輔助結構,則將其設置為 TRUE。

## <a name="cdocobjectserveritemgetdocument"></a><a name="getdocument"></a>CDocObjectServer 專案:取得文件

檢索指向包含項的文件的指標。

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>傳回值

指向包含項的文檔的指標;如果專案不是文件的一部分,則 NULL。

### <a name="remarks"></a>備註

這允許造訪為參數傳遞給[CDocObjectServerItem](#cdocobjectserveritem)建構函數的伺服器文件。

## <a name="cdocobjectserveritemondoverb"></a><a name="ondoverb"></a>CDocObjectServer專案::OnDoVerb

由框架調用以執行指定的謂詞。

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
指定要執行的謂詞。 有關可能的值,請參閱 Windows SDK 中的[IOleObject::DoVerb。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)

### <a name="remarks"></a>備註

如果專案是 DocObject 並指定了OLEIVERB_INPLACEACTIVATE或OLEIVERB_SHOW,則預設實現將調用[OnShow](#onshow)成員函數。 如果項不是 DocObject 或指定了其他謂詞,則預設實現將呼叫[COleServerItem::OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb)。

## <a name="cdocobjectserveritemonhide"></a><a name="onhide"></a>CDocObjectServer 專案::開啟隱藏

由框架調用以隱藏項。

```
virtual void OnHide();
```

### <a name="remarks"></a>備註

如果項是 DocObject,則默認實現將引發異常。 不能隱藏活動文檔物件項,因為它佔用整個檢視。 您必須停用 DocObject 項才能將其消失。 如果專案不是 DocObject,則預設實現將調用[COleServerItem::onHide。](../../mfc/reference/coleserveritem-class.md#onhide)

## <a name="cdocobjectserveritemonshow"></a><a name="onshow"></a>CDocObjectServer專案::在展會上

由框架呼叫,指示伺服器應用程式使 DocObject 項就地處於活動狀態。

```
virtual void OnShow();
```

### <a name="remarks"></a>備註

如果專案不是 DocObject,則預設實現將調用[COleServerItem::onShow。](../../mfc/reference/coleserveritem-class.md#onopen) 如果要在打開 DocObject 項時執行特殊處理,則重寫此函數。

## <a name="see-also"></a>另請參閱

[COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer 類別](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem 類別](../../mfc/reference/coledocobjectitem-class.md)
