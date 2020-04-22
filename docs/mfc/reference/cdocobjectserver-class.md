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
ms.openlocfilehash: f415df35b13e50eee092f87eca0627e5cf143720
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753290"
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
|[CDocObject 伺服器:CDocObjectServer](#cdocobjectserver)|建構 `CDocObjectServer` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDocObject 伺服器:啟用文件物件](#activatedocobject)|激活文檔物件伺服器,但不顯示它。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CDocObject 伺服器:開啟啟動檢視](#onactivateview)|顯示文件物件檢視。|
|[CDocObject 伺服器:在應用檢視狀態](#onapplyviewstate)|還原文件物件視圖的狀態。|
|[CDocObject 伺服器::儲存檢視狀態](#onsaveviewstate)|保存文檔物件檢視的狀態。|

## <a name="remarks"></a>備註

`CDocObjectServer`派生自`CCmdTarget`並緊密地`COleServerDoc`與 公開介面。

DocObject 伺服器文件可以包含[CDocObjectServerItem 物件](../../mfc/reference/cdocobjectserveritem-class.md),這些物件表示文件物件項的伺服器介面。

要自訂文件物件伺服器,`CDocObjectServer`請從其檢視設定功能[「啟用」、應用程式](#onactivateview)[檢視](#onapplyviewstate)狀態和[OnSaveViewState](#onsaveviewstate)派生您自己的類並重寫其檢視設定功能。 您需要提供類的新實例來回應框架調用。

有關文件物件的詳細資訊,請參閱*MFC 參考*中的[CDocObjectServerItem 專案和](../../mfc/reference/cdocobjectserveritem-class.md) [COleCmdUI。](../../mfc/reference/colecmdui-class.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>需求

**標題:** afxdocob.h

## <a name="cdocobjectserveractivatedocobject"></a><a name="activatedocobject"></a>CDocObject 伺服器:啟用文件物件

呼叫此函數以啟動(但不顯示)文件物件伺服器。

```cpp
void ActivateDocObject();
```

### <a name="remarks"></a>備註

`ActivateDocObject`呼叫`IOleDocumentSite`的方法`ActivateMe`,但不顯示檢視,因為它等待有關如何設定和顯示檢視的特定說明,在呼叫[CDocObjectServer 時給出::OnActivateView](#onactivateview)。

一起`ActivateDocObject`,`OnActivateView`並啟動和顯示文件物件檢視。 DocObject 啟動不同於其他類型的 OLE 就地啟動。 DocObject 啟動繞過顯示就地填充邊框和物件修飾(如大小調整控點),忽略物件範圍函數,並在檢視矩形中繪製滾動條,而不是將其繪製到該矩形之外(如正常就地啟動)。

## <a name="cdocobjectservercdocobjectserver"></a><a name="cdocobjectserver"></a>CDocObject 伺服器:CDocObjectServer

建構並初始化 `CDocObjectServer` 物件。

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>參數

*pOwner*<br/>
指向用戶端網站文件的指標,該文檔是 DocObject 伺服器的用戶端。

*pDocSite*<br/>
指向容器實現的`IOleDocumentSite`介面的指標。

### <a name="remarks"></a>備註

當 DocObject 處於活動狀態時,用戶端網站`IOleDocumentSite`OLE 介面 ( ) 是允許 DocObject 伺服器與其用戶端(容器)通信的原因。 啟動 DocObject 伺服器時,它首先檢查容器`IOleDocumentSite`是否實現了介面。 如果是這樣,則調用[COleServerDoc:getDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver)以檢視容器是否支援文件物件。 預設情況下,`GetDocObjectServer`傳回 NULL。 必須重寫`COleServerDoc::GetDocObjectServer`以建構自己的`CDocObjectServer`新 物件或派生物件,`COleServerDoc`並將指向`IOleDocumentSite`容器及其 介面的指標作為構造函數的參數。

## <a name="cdocobjectserveronactivateview"></a><a name="onactivateview"></a>CDocObject 伺服器:開啟啟動檢視

呼叫此函數以顯示文件物件檢視。

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>傳回值

返回錯誤或警告值。 默認情況下,如果成功,則返回 NOERROR;否則,E_FAIL。

### <a name="remarks"></a>備註

此函數創建一個就地框架視窗,在檢視中繪製滾動條,設置伺服器與其容器共用的功能表,添加幀控制件,設置活動物件,最後顯示就地框架視窗並設置焦點。

## <a name="cdocobjectserveronapplyviewstate"></a><a name="onapplyviewstate"></a>CDocObject 伺服器:在應用檢視狀態

重寫此函數以還原文件物件檢視的狀態。

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
用於`CArchive`序列化檢視狀態的物件。

### <a name="remarks"></a>備註

當視圖在實例化後首次顯示時,將調用此功能。 `OnApplyViewState`指示檢視根據以前與[OnSaveViewState](#onsaveviewstate)一起保存的`CArchive`對象 中的數據重新初始化自身。 視圖必須驗證物件中`CArchive`的數據,因為容器不會嘗試以任何方式解釋視圖狀態數據。

可以使用`OnSaveViewState`來存儲特定於視圖狀態的持久資訊。 如果重寫`OnSaveViewState`以存儲資訊,則需要重`OnApplyViewState`寫 以讀取該資訊,並在視圖新啟動時將其應用於視圖。

## <a name="cdocobjectserveronsaveviewstate"></a><a name="onsaveviewstate"></a>CDocObject 伺服器::儲存檢視狀態

重寫此函數以保存有關 DocObject 檢視的額外狀態資訊。

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
視圖`CArchive`狀態序列化的物件。

### <a name="remarks"></a>備註

您的狀態可能包括檢視類型、縮放係數、插入和選擇點等屬性。 容器通常在停用檢視之前調用此函數。 保存的狀態稍後可以通過[OnApplyViewState](#onapplyviewstate)還原。

可以使用`OnSaveViewState`來存儲特定於視圖狀態的持久資訊。 如果重寫`OnSaveViewState`以存儲資訊,則需要重`OnApplyViewState`寫 以讀取該資訊,並在視圖新啟動時將其應用於視圖。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServerItem 類別](../../mfc/reference/cdocobjectserveritem-class.md)
