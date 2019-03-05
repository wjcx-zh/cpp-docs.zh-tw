---
title: CDocObjectServer 類別
ms.date: 09/12/2018
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
ms.openlocfilehash: f4b1a352a9fa62dfcb46d1c1cb0784661e66e5b4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289893"
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer 類別

實作可讓一般 `COleDocument` 伺服器融入完整 DocObject 伺服器所需的其他 OLE 介面： `IOleDocument`、 `IOleDocumentView`、 `IOleCommandTarget`和 `IPrint`。

## <a name="syntax"></a>語法

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|建構 `CDocObjectServer` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|會啟用文件物件的伺服器，但不會顯示。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CDocObjectServer::OnActivateView](#onactivateview)|顯示 DocObject 檢視表。|
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|還原 DocObject 檢視表的狀態。|
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|儲存 DocObject 檢視表的狀態。|

## <a name="remarks"></a>備註

`CDocObjectServer` 衍生自`CCmdTarget`與密切`COleServerDoc`公開的介面。

DocObject 伺服器文件可以包含[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) DocObject 項目代表的伺服器介面的物件。

若要自訂您的 DocObject 伺服器，衍生您自己的類別，從`CDocObjectServer`，並覆寫其檢視設定函式中， [OnActivateView](#onactivateview)， [OnApplyViewState](#onapplyviewstate)，和[OnSaveViewState](#onsaveviewstate). 您必須提供來回架構會呼叫您類別的新執行個體。

如需 DocObjects 的詳細資訊，請參閱[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)並[COleCmdUI](../../mfc/reference/colecmdui-class.md)中*MFC 參考 》*。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>需求

**標頭：** afxdocob.h

##  <a name="activatedocobject"></a>  CDocObjectServer::ActivateDocObject

呼叫此函式可啟用 （但不是顯示） 的文件物件的伺服器。

```
void ActivateDocObject();
```

### <a name="remarks"></a>備註

`ActivateDocObject` 呼叫`IOleDocumentSite`的`ActivateMe`方法，但不會顯示檢視，因為它會等候特定的指示，有關如何設定及顯示檢視中，指定在呼叫[CDocObjectServer::OnActivateView](#onactivateview)。

共同`ActivateDocObject`和`OnActivateView`啟動並顯示 DocObject 檢視表。 DocObject 啟用不同於其他類型的 OLE 就地啟用。 DocObject 啟用會略過顯示就地規劃框線和物件 （例如調整大小控點） 的裝飾，忽略物件範圍函式，並繪製捲軸 檢視相對於該矩形 （如同一般外繪製它們之矩形內在就地啟用）。

##  <a name="cdocobjectserver"></a>  CDocObjectServer::CDocObjectServer

建構並初始化 `CDocObjectServer` 物件。

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>參數

*pOwner*<br/>
是 DocObject 伺服器的用戶端的用戶端站台文件指標。

*pDocSite*<br/>
指標`IOleDocumentSite`容器所實作的介面。

### <a name="remarks"></a>備註

DocObject 作用中時，用戶端站台 OLE 介面 ( `IOleDocumentSite`) 可讓 DocObject 伺服器通訊使用其用戶端 （容器）。 DocObject 伺服器啟動時，它會先檢查容器實作`IOleDocumentSite`介面。 如果是的話[COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver)稱為容器是否支援 DocObjects。 根據預設，`GetDocObjectServer`會傳回 NULL。 您必須覆寫`COleServerDoc::GetDocObjectServer`用以建構新`CDocObjectServer`物件或衍生您自己的資源，以指向的物件`COleServerDoc`容器並將其`IOleDocumentSite`做為建構函式的引數的介面。

##  <a name="onactivateview"></a>  CDocObjectServer::OnActivateView

呼叫此函式可顯示 DocObject 檢視表。

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>傳回值

會傳回錯誤或警告的值。 根據預設，會傳回 NOERROR 如果登錄成功。否則，E_FAIL。

### <a name="remarks"></a>備註

此函式建立的就地框架視窗、 繪製捲軸檢視內、 設定伺服器以其容器的共用、 加入框架控制項、 設定作用中的物件，則最後的就地框架視窗會顯示，並將焦點設定功能表。

##  <a name="onapplyviewstate"></a>  CDocObjectServer::OnApplyViewState

覆寫這個函式來還原 DocObject 檢視表的狀態。

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
A`CArchive`要序列化的檢視狀態的物件。

### <a name="remarks"></a>備註

當第一次在其執行個體化之後顯示的檢視時，會呼叫此函數。 `OnApplyViewState` 會指示檢視，以重新初始化本身中的資料根據`CArchive`先前所儲存的物件[OnSaveViewState](#onsaveviewstate)。 檢視必須驗證中的資料`CArchive`物件，因為容器並不會嘗試解譯以任何方式的檢視狀態資料。

您可以使用`OnSaveViewState`來儲存您的檢視狀態的特定的持續性資訊。 如果您覆寫`OnSaveViewState`來儲存資訊，您會想要覆寫`OnApplyViewState`讀取該資訊，並將它套用至您的檢視中，新啟動時。

##  <a name="onsaveviewstate"></a>  CDocObjectServer::OnSaveViewState

覆寫這個函式，以儲存您 DocObject 檢視表的額外狀態資訊。

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
A`CArchive`来序列化的檢視狀態的物件。

### <a name="remarks"></a>備註

您的狀態可能包含屬性，例如檢視類型、 比例、 插入和選取範圍點，依此類推。 通常，容器會呼叫此函式之前停用檢視。 稍後可以透過還原的已儲存的狀態[OnApplyViewState](#onapplyviewstate)。

您可以使用`OnSaveViewState`來儲存您的檢視狀態的特定的持續性資訊。 如果您覆寫`OnSaveViewState`來儲存資訊，您會想要覆寫`OnApplyViewState`讀取該資訊，並將它套用至您的檢視中，新啟動時。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServerItem 類別](../../mfc/reference/cdocobjectserveritem-class.md)
