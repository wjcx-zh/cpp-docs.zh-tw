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
ms.openlocfilehash: 4d44791415626f1a94500b9c3885581d67e8fe42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506825"
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem 類別

實作 DocObject 伺服器專屬的 OLE 伺服器動詞命令。

## <a name="syntax"></a>語法

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|說明|
|----------|-----------------|
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|建構 `CDocObjectServerItem` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDocObjectServerItem::GetDocument](#getdocument)|抓取包含專案之檔的指標。|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|呼叫以執行動詞。|
|[CDocObjectServerItem::OnHide](#onhide)|如果架構嘗試隱藏 DocObject 專案, 則會擲回例外狀況。|
|[CDocObjectServerItem::OnShow](#onshow)|由架構呼叫, 讓 DocObject 專案就地啟用。 如果專案不是 DocObject, 則會呼叫[COleServerItem:: OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。|

## <a name="remarks"></a>備註

`CDocObjectServerItem`定義可覆寫的成員函式:[OnHide](#onhide)、 [OnDoVerb](#ondoverb)和[OnShow](#onshow)。

若要`CDocObjectServerItem`使用, 請確保衍生類別中`COleServerDoc`的[OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)覆寫會傳回新`CDocObjectServerItem`的物件。 如果您需要變更專案中的任何功能, 您可以為自己`CDocObjectServerItem`的衍生類別建立新的實例。

如需 DocObjects 的詳細資訊, 請參閱*MFC 參考*中的[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[COleCmdUI](../../mfc/reference/colecmdui-class.md) 。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>需求

**標頭:** afxdocob。h

##  <a name="cdocobjectserveritem"></a>CDocObjectServerItem:: CDocObjectServerItem

建構 `CDocObjectServerItem` 物件。

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>參數

*pServerDoc*<br/>
將包含新 DocObject 專案之檔的指標。

*bAutoDelete*<br/>
指出當物件的連結已釋放時, 是否可以刪除它。 如果`CDocObjectServerItem`物件是檔資料不可或缺的一部分, 請將引數設定為 FALSE。 如果物件是用來識別檔資料中可由架構刪除之範圍的次要結構, 請將它設定為 TRUE。

##  <a name="getdocument"></a>CDocObjectServerItem:: GetDocument

抓取包含專案之檔的指標。

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>傳回值

包含專案之檔的指標;如果專案不是檔的一部分, 則為 Null。

### <a name="remarks"></a>備註

這可讓您存取當做引數傳遞至[CDocObjectServerItem](#cdocobjectserveritem)函數的伺服器檔。

##  <a name="ondoverb"></a>  CDocObjectServerItem::OnDoVerb

由架構呼叫以執行指定的動詞。

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
指定要執行的指令動詞。 如需可能的值, 請參閱 Windows SDK 中的[IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 。

### <a name="remarks"></a>備註

如果專案是 DocObject, 而且已指定 OLEIVERB_INPLACEACTI加值稅E 或 OLEIVERB_SHOW, 則預設的執行會呼叫[OnShow](#onshow)成員函式。 如果專案不是 DocObject, 或指定了不同的動詞, 則預設的執行會呼叫[COleServerItem:: OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb)。

##  <a name="onhide"></a>CDocObjectServerItem:: OnHide

由架構呼叫以隱藏專案。

```
virtual void OnHide();
```

### <a name="remarks"></a>備註

如果專案是 DocObject, 則預設的執行會擲回例外狀況。 您無法隱藏作用中的 DocObject 專案, 因為它會取得整個視圖。 您必須停用 DocObject 專案, 使其消失。 如果專案不是 DocObject, 則預設的執行會呼叫[COleServerItem:: OnHide](../../mfc/reference/coleserveritem-class.md#onhide)。

##  <a name="onshow"></a>CDocObjectServerItem:: OnShow

由架構呼叫以指示伺服器應用程式將 DocObject 專案設為現用。

```
virtual void OnShow();
```

### <a name="remarks"></a>備註

如果專案不是 DocObject, 則預設的執行會呼叫[COleServerItem:: OnShow](../../mfc/reference/coleserveritem-class.md#onopen)。 如果您想要在開啟 DocObject 專案時執行特殊處理, 請覆寫此函數。

## <a name="see-also"></a>另請參閱

[COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer 類別](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem 類別](../../mfc/reference/coledocobjectitem-class.md)
