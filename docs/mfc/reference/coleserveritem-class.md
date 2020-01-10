---
title: COleServerItem 類別
ms.date: 11/04/2016
f1_keywords:
- COleServerItem
- AFXOLE/COleServerItem
- AFXOLE/COleServerItem::COleServerItem
- AFXOLE/COleServerItem::AddOtherClipboardData
- AFXOLE/COleServerItem::CopyToClipboard
- AFXOLE/COleServerItem::DoDragDrop
- AFXOLE/COleServerItem::GetClipboardData
- AFXOLE/COleServerItem::GetDocument
- AFXOLE/COleServerItem::GetEmbedSourceData
- AFXOLE/COleServerItem::GetItemName
- AFXOLE/COleServerItem::GetLinkSourceData
- AFXOLE/COleServerItem::GetObjectDescriptorData
- AFXOLE/COleServerItem::IsConnected
- AFXOLE/COleServerItem::IsLinkedItem
- AFXOLE/COleServerItem::NotifyChanged
- AFXOLE/COleServerItem::OnDoVerb
- AFXOLE/COleServerItem::OnDraw
- AFXOLE/COleServerItem::OnDrawEx
- AFXOLE/COleServerItem::OnGetClipboardData
- AFXOLE/COleServerItem::OnGetExtent
- AFXOLE/COleServerItem::OnInitFromData
- AFXOLE/COleServerItem::OnQueryUpdateItems
- AFXOLE/COleServerItem::OnRenderData
- AFXOLE/COleServerItem::OnRenderFileData
- AFXOLE/COleServerItem::OnRenderGlobalData
- AFXOLE/COleServerItem::OnSetColorScheme
- AFXOLE/COleServerItem::OnSetData
- AFXOLE/COleServerItem::OnSetExtent
- AFXOLE/COleServerItem::OnUpdate
- AFXOLE/COleServerItem::OnUpdateItems
- AFXOLE/COleServerItem::SetItemName
- AFXOLE/COleServerItem::GetDataSource
- AFXOLE/COleServerItem::OnHide
- AFXOLE/COleServerItem::OnOpen
- AFXOLE/COleServerItem::OnShow
- AFXOLE/COleServerItem::m_sizeExtent
helpviewer_keywords:
- COleServerItem [MFC], COleServerItem
- COleServerItem [MFC], AddOtherClipboardData
- COleServerItem [MFC], CopyToClipboard
- COleServerItem [MFC], DoDragDrop
- COleServerItem [MFC], GetClipboardData
- COleServerItem [MFC], GetDocument
- COleServerItem [MFC], GetEmbedSourceData
- COleServerItem [MFC], GetItemName
- COleServerItem [MFC], GetLinkSourceData
- COleServerItem [MFC], GetObjectDescriptorData
- COleServerItem [MFC], IsConnected
- COleServerItem [MFC], IsLinkedItem
- COleServerItem [MFC], NotifyChanged
- COleServerItem [MFC], OnDoVerb
- COleServerItem [MFC], OnDraw
- COleServerItem [MFC], OnDrawEx
- COleServerItem [MFC], OnGetClipboardData
- COleServerItem [MFC], OnGetExtent
- COleServerItem [MFC], OnInitFromData
- COleServerItem [MFC], OnQueryUpdateItems
- COleServerItem [MFC], OnRenderData
- COleServerItem [MFC], OnRenderFileData
- COleServerItem [MFC], OnRenderGlobalData
- COleServerItem [MFC], OnSetColorScheme
- COleServerItem [MFC], OnSetData
- COleServerItem [MFC], OnSetExtent
- COleServerItem [MFC], OnUpdate
- COleServerItem [MFC], OnUpdateItems
- COleServerItem [MFC], SetItemName
- COleServerItem [MFC], GetDataSource
- COleServerItem [MFC], OnHide
- COleServerItem [MFC], OnOpen
- COleServerItem [MFC], OnShow
- COleServerItem [MFC], m_sizeExtent
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
ms.openlocfilehash: dcae304e8571ecb5743002638ea23f13c3e21517
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741350"
---
# <a name="coleserveritem-class"></a>COleServerItem 類別

提供 OLE 項目的伺服器介面。

## <a name="syntax"></a>語法

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|說明|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|建構 `COleServerItem` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|將`COleDataSource`簡報和轉換格式放在物件中。|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|將專案複製到剪貼簿。|
|[COleServerItem::DoDragDrop](#dodragdrop)|執行拖放作業。|
|[COleServerItem::GetClipboardData](#getclipboarddata)|取得要用於資料傳輸（拖放或剪貼簿）的資料來源。|
|[COleServerItem::GetDocument](#getdocument)|傳回包含專案的伺服器檔。|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|取得 OLE 專案的 CF_EMBEDSOURCE 資料。|
|[COleServerItem::GetItemName](#getitemname)|傳回專案的名稱。 僅用於連結專案。|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|取得 OLE 專案的 CF_LINKSOURCE 資料。|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|取得 OLE 專案的 CF_OBJECTDESCRIPTOR 資料。|
|[COleServerItem::IsConnected](#isconnected)|指出專案目前是否附加至作用中的容器。|
|[COleServerItem::IsLinkedItem](#islinkeditem)|指出專案是否代表連結的 OLE 專案。|
|[COleServerItem::NotifyChanged](#notifychanged)|使用自動連結更新來更新所有容器。|
|[COleServerItem::OnDoVerb](#ondoverb)|呼叫以執行動詞。|
|[COleServerItem::OnDraw](#ondraw)|當容器要求繪製專案時呼叫;需要執行。|
|[COleServerItem::OnDrawEx](#ondrawex)|針對特製化專案繪製呼叫。|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|由架構呼叫，以取得要複製到剪貼簿的資料。|
|[COleServerItem::OnGetExtent](#ongetextent)|由架構呼叫以取得 OLE 專案的大小。|
|[COleServerItem::OnInitFromData](#oninitfromdata)|由架構呼叫，使用指定的資料傳輸物件的內容來初始化 OLE 專案。|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|呼叫以判斷是否有任何連結的專案需要更新。|
|[COleServerItem::OnRenderData](#onrenderdata)|將資料當做延遲轉譯的一部分來抓取。|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|將`CFile`資料當做延遲轉譯的一部分，抓取至物件中。|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|將資料當做延遲轉譯的一部分，捕獲到 HGLOBAL 中。|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|呼叫以設定專案的色彩配置。|
|[COleServerItem::OnSetData](#onsetdata)|呼叫以設定專案的資料。|
|[COleServerItem::OnSetExtent](#onsetextent)|由架構呼叫以設定 OLE 專案的大小。|
|[COleServerItem::OnUpdate](#onupdate)|當專案所屬的部分檔已變更時呼叫。|
|[COleServerItem::OnUpdateItems](#onupdateitems)|呼叫以補救伺服器檔中所有專案的呈現快取。|
|[COleServerItem::SetItemName](#setitemname)|設定專案的名稱。 僅用於連結專案。|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|取得用來儲存轉換格式的物件。|
|[COleServerItem::OnHide](#onhide)|由架構呼叫以隱藏 OLE 專案。|
|[COleServerItem::OnOpen](#onopen)|由架構呼叫，以在它自己的最上層視窗中顯示 OLE 專案。|
|[COleServerItem::OnShow](#onshow)|當容器要求顯示專案時呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|通知伺服器有多少 OLE 專案可見。|

## <a name="remarks"></a>備註

連結的專案可以代表部分或所有的伺服器檔。 內嵌專案一律代表整個伺服器檔。

`COleServerItem`類別會定義數個 OLE 系統動態連結程式庫（dll）所呼叫的可覆寫成員函式，通常是為了回應來自容器應用程式的要求。 這些成員函式可讓容器應用程式以各種不同的方式間接管理專案，例如藉由顯示、執行其動詞命令，或以各種格式來抓取其資料。

若要`COleServerItem`使用，請從它衍生一個類別，並執行[OnDraw](#ondraw)並[序列化](../../mfc/reference/cobject-class.md#serialize)成員函式。 `OnDraw`函式會提供專案的中繼檔標記法，讓它能夠在容器應用程式開啟複合檔案時顯示。 的函式會提供專案的原生標記法，允許在伺服器和容器應用程式之間傳送內嵌專案。 `CObject` `Serialize` [OnGetExtent](#ongetextent)會將專案的自然大小提供給容器，讓容器能夠調整專案的大小。

如需有關伺服器和相關主題的詳細資訊，請[參閱伺服器：在文章](../../mfc/servers-implementing-a-server.md) [容器中執行伺服器和「建立容器/伺服器應用程式」：先進的](../../mfc/containers-advanced-features.md)功能。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>需求

**標頭：** afxole。h

##  <a name="addotherclipboarddata"></a>COleServerItem：： AddOtherClipboardData

呼叫此函式可將 OLE 專案的呈現和轉換格式放在指定`COleDataSource`的物件中。

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>參數

*pDataSource*<br/>
應放置資料`COleDataSource`之物件的指標。

### <a name="remarks"></a>備註

您必須已實作為[OnDraw](#ondraw)成員函式，才能提供專案的呈現格式（中繼檔圖片）。 若要支援其他轉換格式，請使用[GetDataSource](#getdatasource)所傳回的[COleDataSource](../../mfc/reference/coledatasource-class.md)物件來進行註冊，然後覆寫[OnRenderData](#onrenderdata)成員函式，以提供您想要支援的格式的資料。

##  <a name="coleserveritem"></a>COleServerItem：： COleServerItem

會建立`COleServerItem`物件，並將它加入至伺服器檔的檔專案集合。

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>參數

*pServerDoc*<br/>
將包含新專案之檔的指標。

*bAutoDelete*<br/>
旗標，指出當物件的連結已釋放時，是否可以刪除它。 如果`COleServerItem`物件是您必須刪除的檔資料中不可或缺的一部分，請將此設為 FALSE。 如果物件是用來識別檔資料中可由架構刪除之範圍的次要結構，請將此值設定為 TRUE。

##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard

呼叫此函式可將 OLE 專案複製到剪貼簿。

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>參數

*bIncludeLink*<br/>
如果應該將連結資料複製到剪貼簿，請將此設為 TRUE。 如果您的伺服器應用程式不支援連結，請將此設定為 FALSE。

### <a name="remarks"></a>備註

函式會使用[OnGetClipboardData](#ongetclipboarddata)成員函式，以支援的格式來建立包含 OLE 專案資料的[COleDataSource](../../mfc/reference/coledatasource-class.md)物件。 函式會使用`COleDataSource` [COleDataSource：： SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函式，將物件放在剪貼簿上。 `COleDataSource`物件包含專案的原生資料，以及其在 CF_METAFILEPICT 格式中的標記法，以及您選擇支援的任何轉換格式的資料。 您必須已執行[序列化](../../mfc/reference/cobject-class.md#serialize)和[OnDraw](#ondraw) ，此成員函式才能運作。

##  <a name="dodragdrop"></a>  COleServerItem::DoDragDrop

`DoDragDrop`呼叫成員函式以執行拖放作業。

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>參數

*lpRectItem*<br/>
螢幕上的專案矩形（以圖元為單位），相對於工作區。

*ptOffset*<br/>
*LpItemRect*的位移，其中滑鼠位置位於拖曳時。

*bIncludeLink*<br/>
如果應該將連結資料複製到剪貼簿，請將此設為 TRUE。 如果您的應用程式不支援連結，請將它設定為 FALSE。

*dwEffects*<br/>
決定拖曳作業在拖曳作業中允許的效果（複製、移動和連結的組合）。

*lpRectStartDrag*<br/>
定義拖曳實際開始位置之矩形的指標。 如需詳細資訊，請參閱接下來的＜備註＞一節。

### <a name="return-value"></a>傳回值

來自 DROPEFFECT 列舉的值。 如果已 DROPEFFECT_MOVE，則應該移除原始資料。

### <a name="remarks"></a>備註

拖放作業不會立即啟動。 它會等到滑鼠游標離開*lpRectStartDrag*所指定的矩形，或直到經過指定的毫秒數為止。 如果*lpRectStartDrag*為 Null，則會使用預設矩形，以便在滑鼠游標移動一個圖元時開始拖曳。

延遲時間是由登錄機碼設定所指定。 您可以藉由呼叫[CWinApp：： WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[CWinApp：： WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint)來變更延遲時間。 如果您未指定延遲時間，則會使用預設值200毫秒。 拖曳延遲時間的儲存方式如下：

- Windows NT 拖曳延遲時間儲存在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay. 中

- Windows 3.x 拖曳延遲時間會儲存在 WIN 中。INI 檔案，位於 [Windows}] 區段底下。

- Windows 95/98 拖曳延遲時間會儲存在 WIN 的快取版本中.INI.

如需如何將拖曳延遲資訊儲存在登錄或中的詳細資訊。INI 檔，請參閱 Windows SDK 中的[WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) 。

##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData

呼叫此函式，以在您呼叫[CopyToClipboard](#copytoclipboard)時，將所有要複製到剪貼簿的資料填入指定的[COleDataSource](../../mfc/reference/coledatasource-class.md)物件（如果您呼叫[DoDragDrop](#dodragdrop)，也會傳送相同的資料）。

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>參數

*pDataSource*<br/>
`COleDataSource`物件的指標，會以所有支援的格式接收 OLE 專案的資料。

*bIncludeLink*<br/>
如果應該將連結資料複製到剪貼簿，則為 TRUE。 如果您的伺服器應用程式不支援連結，則為 FALSE。

*lpOffset*<br/>
滑鼠游標從物件原點開始的位移（以圖元為單位）。

*lpSize*<br/>
物件的大小（以圖元為單位）。

### <a name="remarks"></a>備註

此函式會呼叫[GetEmbedSourceData](#getembedsourcedata)成員函式來取得 OLE 專案的原生資料，並呼叫[AddOtherClipboardData](#addotherclipboarddata)成員函式以取得呈現格式和任何支援的轉換格式。 如果*bIncludeLink*為 TRUE，函數也會呼叫[GetLinkSourceData](#getlinksourcedata)來取得專案的連結資料。

如果您想要在所`COleDataSource` `CopyToClipboard`提供的格式之前或之後，將格式放在物件中，請覆寫此函數。

##  <a name="getdatasource"></a>COleServerItem：： GetDataSource

呼叫此函式可取得用來儲存伺服器應用程式所支援之轉換格式的[COleDataSource](../../mfc/reference/coledatasource-class.md)物件。

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>傳回值

用來儲存轉換`COleDataSource`格式之物件的指標。

### <a name="remarks"></a>備註

如果您想要讓伺服器應用程式在資料傳輸作業期間提供各種格式的資料，請使用此函數所`COleDataSource`傳回的物件來註冊這些格式。 例如，如果您想要為剪貼簿或拖放作業提供 OLE 專案的 CF_TEXT 標記法，您會使用此函式所傳回的`COleDataSource`物件來註冊格式，然後將`OnRenderXxxData`成員函式覆寫為提供資料。

##  <a name="getdocument"></a>COleServerItem：： GetDocument

呼叫此函式可取得包含專案之檔的指標。

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>傳回值

包含專案之檔的指標;如果專案不是檔的一部分，則為 Null。

### <a name="remarks"></a>備註

這可讓您存取當做引數傳遞給此`COleServerItem`函式的伺服器檔。

##  <a name="getembedsourcedata"></a>COleServerItem：： GetEmbedSourceData

呼叫此函式可取得 OLE 專案的 CF_EMBEDSOURCE 資料。

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpStgMedium*<br/>
[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構的指標，會接收 OLE 專案的 CF_EMBEDSOURCE 資料。

### <a name="remarks"></a>備註

此格式包含專案的原生資料。 您必須已`Serialize`實作為此函式的成員函式，才能正常運作。

然後，您可以使用[COleDataSource：： CacheData](../../mfc/reference/coledatasource-class.md#cachedata)，將結果新增至資料來源。 此函式是由[COleServerItem：： OnGetClipboardData](#ongetclipboarddata)自動呼叫。

如需詳細資訊，請參閱 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) 。

##  <a name="getitemname"></a>COleServerItem：： GetItemName

呼叫此函式可取得專案的名稱。

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>傳回值

項目的名稱。

### <a name="remarks"></a>備註

您通常只會針對連結的專案呼叫此函式。

##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData

呼叫此函式可取得 OLE 專案的 CF_LINKSOURCE 資料。

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpStgMedium*<br/>
[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構的指標，會接收 OLE 專案的 CF_LINKSOURCE 資料。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此格式包含描述 OLE 專案類型的 CLSID，以及尋找包含 OLE 專案之檔所需的資訊。

然後，您可以使用[COleDataSource：： CacheData](../../mfc/reference/coledatasource-class.md#cachedata)將結果新增至資料來源。 [OnGetClipboardData](#ongetclipboarddata)會自動呼叫此函式。

如需詳細資訊，請參閱 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) 。

##  <a name="getobjectdescriptordata"></a>COleServerItem：： GetObjectDescriptorData

呼叫此函式可取得 OLE 專案的 CF_OBJECTDESCRIPTOR 資料。

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpOffset*<br/>
滑鼠點擊的位移，從 OLE 專案的左上角開始。 可以是 Null。

*lpSize*<br/>
OLE 專案的大小。 可以是 Null。

*lpStgMedium*<br/>
[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構的指標，會接收 OLE 專案的 CF_OBJECTDESCRIPTOR 資料。

### <a name="remarks"></a>備註

資訊會複製到*lpStgMedium*所`STGMEDIUM`指向的結構中。 此格式包含 [貼上特殊] 對話方塊所需的資訊。

如需詳細資訊，請參閱 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) 。

##  <a name="isconnected"></a>COleServerItem：： Connectionmultiplexer.isconnected

呼叫此函式，以查看 OLE 專案是否已連接。

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>傳回值

如果專案已連接，則為非零值;否則為0。

### <a name="remarks"></a>備註

如果一或多個容器有專案的參考，則會將 OLE 專案視為已連接。 如果專案的參考計數大於0，或如果它是內嵌專案，則會連接。

##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem

呼叫此函式，以查看 OLE 專案是否為連結的專案。

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>傳回值

如果專案是連結的專案，則為非零值;否則為0。

### <a name="remarks"></a>備註

如果專案是有效的，而且不會在檔的內嵌專案清單中傳回，則會連結專案。 連結的專案不一定會連接到容器。

連結和內嵌的專案通常會使用相同的類別。 `IsLinkedItem`可讓您讓連結專案的行為與內嵌專案不同，雖然程式碼很常見。

##  <a name="m_sizeextent"></a>COleServerItem：： m_sizeExtent

這個成員會告訴伺服器，在容器檔案中可以看到多少物件。

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>備註

[OnSetExtent](#onsetextent)的預設執行會設定這個成員。

##  <a name="notifychanged"></a>COleServerItem：： NotifyChanged

在連結的專案變更後呼叫此函式。

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>參數

*nDrawAspect*<br/>
DVASPECT 列舉中的值，指出 OLE 專案的哪些層面已變更。 這個參數可以具有下列任何值：

- DVASPECT_CONTENT 專案的表示方式，可以在其容器內顯示為内嵌物件。

- DVASPECT_THUMBNAIL 專案會以「縮圖」標記法呈現，以便在流覽工具中顯示。

- DVASPECT_ICON 專案是以圖示表示。

- DVASPECT_DOCPRINT 專案的表示方式，就如同使用 [檔案] 功能表中的 [列印] 命令來列印一樣。

### <a name="remarks"></a>備註

如果容器專案已連結至具有自動連結的檔，則會更新專案以反映變更。 在使用 MFC 程式庫所寫入的容器應用程式中，會在回應中呼叫[COleClientItem：： OnChange](../../mfc/reference/coleclientitem-class.md#onchange) 。

##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb

由架構呼叫以執行指定的動詞。

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
指定要執行的指令動詞。 它可以是下列任何一項：

|值|意義|符號|
|-----------|-------------|------------|
|0|主動詞命令|OLEIVERB_PRIMARY|
|1|次要動詞|(無)|
|- 1|顯示要編輯的專案|OLEIVERB_SHOW|
|- 2|在個別視窗中編輯專案|OLEIVERB_OPEN|
|- 3|隱藏專案|OLEIVERB_HIDE|

-1 值通常是另一個動詞的別名。 如果不支援開啟編輯，-2 的效果會與-1 相同。 如需其他值，請參閱 Windows SDK 中的[IOleObject：:D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 。

### <a name="remarks"></a>備註

如果容器應用程式是以 MFC 程式庫撰寫，則在呼叫對應`COleClientItem`物件的[COleClientItem：： Activate](../../mfc/reference/coleclientitem-class.md#activate)成員函式時，會呼叫這個函式。 如果指定了主要動詞或 OLEIVERB_SHOW，則預設的實值會呼叫[OnShow](#onshow)成員函式，如果指定了次要動詞或 OLEIVERB_OPEN，則為[OnOpen](#onopen) ，而如果指定 OLEIVERB_HIDE，則為[OnHide](#onhide) 。 如果 iVerb 不是`OnShow`以上所列的其中一個動詞，則預設的實值會呼叫。

如果您的主要動詞不會顯示專案，請覆寫此函式。 例如，如果專案是錄音，而且其主要動詞為播放，您就不需要顯示伺服器應用程式來播放專案。

如需詳細資訊，請參閱 Windows SDK 中的[IOleObject：:D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 。

##  <a name="ondraw"></a>  COleServerItem::OnDraw

由架構呼叫，以將 OLE 專案轉譯為中繼檔。

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>參數

*pDC*<br/>
要在其上繪製專案之[CDC](../../mfc/reference/cdc-class.md)物件的指標。 顯示內容會自動連接到屬性顯示內容，因此您可以呼叫屬性函式，雖然這樣做會讓中繼檔成為裝置特定的。

*rSize*<br/>
要在其中繪製中繼檔的大小（以 HIMETRIC 單位表示）。

### <a name="return-value"></a>傳回值

如果成功繪製專案，則為非零。否則為0。

### <a name="remarks"></a>備註

OLE 專案的中繼檔標記法是用來顯示容器應用程式中的專案。 如果容器應用程式是以 MFC 程式庫撰寫，則對應[COleClientItem](../../mfc/reference/coleclientitem-class.md)物件的[Draw](../../mfc/reference/coleclientitem-class.md#draw)成員函式會使用中繼檔。 沒有預設的實作。 您必須覆寫這個函式，才能將專案繪製到指定的裝置內容中。

##  <a name="ondrawex"></a>COleServerItem：： OnDrawEx

由架構針對所有繪圖呼叫。

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>參數

*pDC*<br/>
要在其上繪製專案之[CDC](../../mfc/reference/cdc-class.md)物件的指標。 DC 會自動連接到屬性 DC，讓您可以呼叫屬性函式，雖然這樣做會讓中繼檔成為裝置特定的。

*nDrawAspect*<br/>
來自 DVASPECT 列舉的值。 這個參數可以具有下列任何值：

- DVASPECT_CONTENT 專案的表示方式，可以在其容器內顯示為内嵌物件。

- DVASPECT_THUMBNAIL 專案會以「縮圖」標記法呈現，以便在流覽工具中顯示。

- DVASPECT_ICON 專案是以圖示表示。

- DVASPECT_DOCPRINT 專案的表示方式，就如同使用 [檔案] 功能表中的 [列印] 命令來列印一樣。

*rSize*<br/>
專案的大小（以 HIMETRIC 單位表示）。

### <a name="return-value"></a>傳回值

如果成功繪製專案，則為非零。否則為0。

### <a name="remarks"></a>備註

當 DVASPECT 等於 DVASPECT_CONTENT `OnDraw`時，預設的實作為呼叫，否則會失敗。

覆寫此函數以提供 DVASPECT_CONTENT 以外層面的呈現資料，例如 DVASPECT_ICON 或 DVASPECT_THUMBNAIL。

##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData

由架構呼叫以取得`COleDataSource`物件，其中包含的所有資料都將會藉由呼叫[CopyToClipboard](#copytoclipboard)成員函式放在剪貼簿上。

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>參數

*bIncludeLink*<br/>
如果應該將連結資料複製到剪貼簿，請將此設為 TRUE。 如果您的伺服器應用程式不支援連結，請將此設定為 FALSE。

*lpOffset*<br/>
滑鼠游標從物件原點開始的位移（以圖元為單位）。

*lpSize*<br/>
物件的大小（以圖元為單位）。

### <a name="return-value"></a>傳回值

包含剪貼簿資料之[COleDataSource](../../mfc/reference/coledatasource-class.md)物件的指標。

### <a name="remarks"></a>備註

此函式的預設實作用會呼叫[GetClipboardData](#getclipboarddata)。

##  <a name="ongetextent"></a>COleServerItem：： OnGetExtent

由架構呼叫，以取得 OLE 專案的大小（以 HIMETRIC 單位表示）。

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>參數

*nDrawAspect*<br/>
指定要抓取其界限的 OLE 專案的層面。 這個參數可以具有下列任何值：

- DVASPECT_CONTENT 專案的表示方式，可以在其容器內顯示為内嵌物件。

- DVASPECT_THUMBNAIL 專案會以「縮圖」標記法呈現，以便在流覽工具中顯示。

- DVASPECT_ICON 專案是以圖示表示。

- DVASPECT_DOCPRINT 專案的表示方式，就如同使用 [檔案] 功能表中的 [列印] 命令來列印一樣。

*rSize*<br/>
`CSize`物件的參考，將會接收 OLE 專案的大小。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果容器應用程式是以 MFC 程式庫撰寫，則在呼叫對應`COleClientItem`物件的[GetExtent](../../mfc/reference/coleclientitem-class.md#getextent)成員函式時，會呼叫這個函式。 預設實作不做任何動作。 您必須自行執行。 如果您想要在處理 OLE 專案大小的要求時執行特殊處理，請覆寫這個函式。

##  <a name="onhide"></a>COleServerItem：： OnHide

由架構呼叫以隱藏 OLE 專案。

```
virtual void OnHide();
```

### <a name="remarks"></a>備註

預設的呼叫`COleServerDoc::OnShowDocument( FALSE )`。 函式也會通知容器，OLE 專案已隱藏。 如果您想要在隱藏 OLE 專案時執行特殊處理，請覆寫此函數。

##  <a name="oninitfromdata"></a>COleServerItem：： OnInitFromData

由架構呼叫，以使用*pDataObject*的內容初始化 OLE 專案。

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
OLE 資料物件的指標，其中包含用來初始化 OLE 專案之各種格式的資料。

*bCreation*<br/>
如果呼叫函式以初始化由容器應用程式新建立的 OLE 專案，則為 TRUE。 如果呼叫函式來取代已存在的 OLE 專案內容，則為 FALSE。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果*bCreation*為 TRUE，則如果容器根據目前的選取範圍來執行插入新物件，就會呼叫這個函式。 當您建立新的 OLE 專案時，會使用選取的資料。 例如，選取試算表程式中的儲存格範圍，然後使用 [插入新物件]，根據所選範圍中的值建立圖表。 預設實作不做任何動作。 覆寫此函式，從*pDataObject*所提供的格式選擇可接受的格式，並根據提供的資料將 OLE 專案初始化。 這是一個先進的可覆寫。

如需詳細資訊，請參閱 Windows SDK 中的[IOleObject：： InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) 。

##  <a name="onopen"></a>COleServerItem：： OnOpen

由架構呼叫，以在伺服器應用程式的個別實例中顯示 OLE 專案，而不是就地。

```
virtual void OnOpen();
```

### <a name="remarks"></a>備註

預設的執行會啟動第一個框架視窗，其中顯示包含 OLE 專案的檔;如果應用程式是迷你伺服器，則預設的執行會顯示主視窗。 函式也會通知容器，OLE 專案已開啟。

如果您想要在開啟 OLE 專案時執行特殊處理，請覆寫此函數。 這特別適用于您想要在開啟連結時，將選取範圍設定為連結的連結專案。

如需詳細資訊，請參閱 Windows SDK 中的[IOleClientSite：： OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) 。

##  <a name="onqueryupdateitems"></a>COleServerItem：： OnQueryUpdateItems

由架構呼叫以判斷目前伺服器檔中的任何連結專案是否已過期。

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>傳回值

如果檔包含需要更新的專案，則為非零。如果所有專案都是最新的，則為0。

### <a name="remarks"></a>備註

如果專案的來源文件已變更，但連結的專案尚未更新以反映檔中的變更，則專案已過期。

##  <a name="onrenderdata"></a>COleServerItem：： OnRenderData

由架構呼叫，以取得指定格式的資料。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構，指定要求資訊的格式。

*lpStgMedium*<br/>
指向要傳回資料的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是先前`COleDataSource`使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)或[DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)成員函式來呈現延遲轉譯的物件。 如果所提供的儲存媒體是檔案或記憶體，此函式的預設實作為分別會呼叫[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)。 如果未提供上述任何一種格式，則預設的執行會傳回0，而且不會執行任何操作。

如果*lpStgMedium* ->  *tymed*為 TYMED_Null，則 STGMEDIUM 應配置並填入*lpFormatEtc-> tymed*所指定的。 如果未 TYMED_Null，就應該使用資料來填入 STGMEDIUM。

這是一個先進的可覆寫。 覆寫此函式，以要求的格式和媒體提供您的資料。 根據您的資料而定，您可能會想要改為覆寫此函式的其中一個其他版本。 如果您的資料大小很小且固定，請`OnRenderGlobalData`覆寫。 如果您的資料位於檔案中，或屬於變數大小，請覆`OnRenderFileData`寫。

如需詳細資訊，請參閱 Windows SDK 中的[IDataObject：：](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)、 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)和[TYMED](/windows/win32/api/objidl/ne-objidl-tymed) 。

##  <a name="onrenderfiledata"></a>COleServerItem：： OnRenderFileData

由架構呼叫，以在儲存媒體為檔案時，以指定的格式抓取資料。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構，指定要求資訊的格式。

*pFile*<br/>
指向要在其中呈現資料的物件。`CFile`

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是先前`COleDataSource`使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)成員函式來呈現延遲轉譯的物件。 此函式的預設實作用只會傳回 FALSE。

這是一個先進的可覆寫。 覆寫此函式，以要求的格式和媒體提供您的資料。 根據您的資料而定，您可能會想要改為覆寫此函式的其中一個其他版本。 如果您想要處理多個儲存媒體，請覆寫[OnRenderData](#onrenderdata)。 如果您的資料位於檔案中，或屬於變數大小，請覆寫[OnRenderFileData](#onrenderfiledata)。

如需詳細資訊，請參閱 Windows SDK 中的[IDataObject：：執行](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)程式和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

##  <a name="onrenderglobaldata"></a>COleServerItem：： OnRenderGlobalData

由架構呼叫，以在指定的儲存媒體為全域記憶體時，以指定的格式抓取資料。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構，指定要求資訊的格式。

*phGlobal*<br/>
指向要傳回資料之全域記憶體的控制碼。 如果未配置記憶體，這個參數可以是 Null。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是先前`COleDataSource`使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)成員函式來呈現延遲轉譯的物件。 此函式的預設實作用只會傳回 FALSE。

如果*phGlobal*為 Null，則應該在*phGlobal*中配置並傳回新的 HGLOBAL。 否則， *phGlobal*所指定的 HGLOBAL 應該填入資料。 放在 HGLOBAL 中的資料量不得超過記憶體區塊的目前大小。 此外，區塊也無法重新配置為較大的大小。

這是一個先進的可覆寫。 覆寫此函式，以要求的格式和媒體提供您的資料。 根據您的資料而定，您可能會想要改為覆寫此函式的其中一個其他版本。 如果您想要處理多個儲存媒體，請覆寫[OnRenderData](#onrenderdata)。 如果您的資料位於檔案中，或屬於變數大小，請覆寫[OnRenderFileData](#onrenderfiledata)。

如需詳細資訊，請參閱 Windows SDK 中的[IDataObject：：執行](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)程式和[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 。

##  <a name="onsetcolorscheme"></a>COleServerItem：： OnSetColorScheme

由架構呼叫，以指定在編輯 OLE 專案時要使用的調色板。

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>參數

*lpLogPalette*<br/>
Windows [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)結構的指標。

### <a name="return-value"></a>傳回值

如果使用色調色板，則為非零。否則為0。

### <a name="remarks"></a>備註

如果容器應用程式是使用 MFC 程式庫所撰寫，則在呼叫對應`COleClientItem`物件的[IOleObject：： SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme)函式時，會呼叫這個函式。 預設的實值會傳回 FALSE。 如果您想要使用建議的調色板，請覆寫此函數。 不需要伺服器應用程式就可以使用建議的調色板。

如需詳細資訊，請參閱 Windows SDK 中的[IOleObject：： SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) 。

##  <a name="onsetdata"></a>COleServerItem：： OnSetData

由架構呼叫，以指定的資料取代 OLE 專案的資料。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指定資料格式之[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構的指標。

*lpStgMedium*<br/>
資料所在之[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構的指標。

*bRelease*<br/>
指出在完成函數呼叫之後，誰擁有儲存媒體的擁有權。 呼叫者會決定誰負責釋放代表儲存媒體所配置的資源。 呼叫者會藉由設定*bRelease*來執行這項工作。 如果*bRelease*為非零值，則伺服器專案會取得擁有權，並在完成使用時釋放媒體。 當*bRelease*為0時，呼叫端會保留擁有權，而伺服器專案只能在呼叫期間使用儲存媒體。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

伺服器專案在成功取得資料之前，不會取得其擁有權。 也就是說，如果傳回0，則不會取得擁有權。 如果資料來源取得擁有權，它會藉由呼叫[ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium)函數來釋放儲存媒體。

預設實作不做任何動作。 覆寫這個函式，以指定的資料取代 OLE 專案的資料。 這是一個先進的可覆寫。

如需詳細資訊，請參閱 Windows SDK 中的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)、 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)和[ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 。

##  <a name="onsetextent"></a>COleServerItem：： OnSetExtent

由架構呼叫，告訴 OLE 專案容器檔案中有多少可用空間。

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>參數

*nDrawAspect*<br/>
指定要指定其界限的 OLE 專案的層面。 這個參數可以具有下列任何值：

- DVASPECT_CONTENT 專案的表示方式，可以在其容器內顯示為内嵌物件。

- DVASPECT_THUMBNAIL 專案會以「縮圖」標記法呈現，以便在流覽工具中顯示。

- DVASPECT_ICON 專案是以圖示表示。

- DVASPECT_DOCPRINT 專案的表示方式，就如同使用 [檔案] 功能表中的 [列印] 命令來列印一樣。

*size*<br/>
[CSize](../../atl-mfc-shared/reference/csize-class.md)結構，指定 OLE 專案的新大小。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果容器應用程式是以 MFC 程式庫撰寫，則在呼叫對應`COleClientItem`物件的[SetExtent](../../mfc/reference/coleclientitem-class.md#setextent)成員函式時，會呼叫這個函式。 如果*nDrawAspect*為 DVASPECT_CONTENT，則預設的執行會將[m_sizeExtent](#m_sizeextent)成員設定為指定的大小;否則，它會傳回0。 當您變更專案的大小時，請覆寫此函式以執行特殊處理。

##  <a name="onshow"></a>COleServerItem：： OnShow

由架構呼叫，指示伺服器應用程式就地顯示 OLE 專案。

```
virtual void OnShow();
```

### <a name="remarks"></a>備註

當容器應用程式的使用者建立專案或執行需要顯示專案的動詞（例如編輯）時，通常會呼叫這個函式。 預設的執行會嘗試就地啟用。 如果失敗，函式會呼叫`OnOpen`成員函式，將 OLE 專案顯示在另一個視窗中。

如果您想要在顯示 OLE 專案時執行特殊處理，請覆寫這個函式。

##  <a name="onupdate"></a>COleServerItem：： OnUpdate

當專案已修改時由架構呼叫。

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>參數

*pSender*<br/>
修改檔之專案的指標。 可以是 Null。

*lHint*<br/>
包含修改的相關資訊。

*pHint*<br/>
物件的指標，儲存修改的相關資訊。

*nDrawAspect*<br/>
來自 DVASPECT 列舉的值。 這個參數可以具有下列任何一個值：

- DVASPECT_CONTENT 專案的表示方式，可以在其容器內顯示為内嵌物件。

- DVASPECT_THUMBNAIL 專案會以「縮圖」標記法呈現，以便在流覽工具中顯示。

- DVASPECT_ICON 專案是以圖示表示。

- DVASPECT_DOCPRINT 專案的表示方式，就如同使用 [檔案] 功能表中的 [列印] 命令來列印一樣。

### <a name="remarks"></a>備註

無論提示或寄件者為何，預設的實[NotifyChanged](#notifychanged)都會呼叫。

##  <a name="onupdateitems"></a>COleServerItem：： OnUpdateItems

由架構呼叫以補救伺服器檔中的所有專案。

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>備註

預設的執行會呼叫檔中`COleClientItem`所有物件的 [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)。

##  <a name="setitemname"></a>COleServerItem：： SetItemName

當您建立連結的專案來設定其名稱時，請呼叫此函式。

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>參數

*lpszItemName*<br/>
專案之新名稱的指標。

### <a name="remarks"></a>備註

此名稱在檔中必須是唯一的。 呼叫伺服器應用程式來編輯連結的專案時，應用程式會使用這個名稱來尋找專案。 您不需要為內嵌專案呼叫此函式。

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem 類別](../../mfc/reference/cdocitem-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)
