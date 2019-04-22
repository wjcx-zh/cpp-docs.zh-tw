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
ms.openlocfilehash: c4c026975e9884ac2a0e6aaef31e799c2b5b09bf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777372"
---
# <a name="coleserveritem-class"></a>COleServerItem 類別

提供 OLE 項目的伺服器介面。

## <a name="syntax"></a>語法

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[COleServerItem::COleServerItem](#coleserveritem)|建構 `COleServerItem` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|放置中的簡報和轉換格式`COleDataSource`物件。|
|[COleServerItem::CopyToClipboard](#copytoclipboard)|將項目複製到剪貼簿。|
|[COleServerItem::DoDragDrop](#dodragdrop)|執行拖放作業。|
|[COleServerItem::GetClipboardData](#getclipboarddata)|取得用於資料傳輸 （拖曳和卸除或剪貼簿） 中的資料來源。|
|[COleServerItem::GetDocument](#getdocument)|傳回包含之項目的伺服器文件。|
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|取得 OLE 項目 CF_EMBEDSOURCE 資料。|
|[COleServerItem::GetItemName](#getitemname)|傳回項目的名稱。 用於連結項目。|
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|取得 OLE 項目 CF_LINKSOURCE 資料。|
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|取得 OLE 項目 CF_OBJECTDESCRIPTOR 資料。|
|[COleServerItem::IsConnected](#isconnected)|表示是否項目目前已連結至使用中的容器。|
|[COleServerItem::IsLinkedItem](#islinkeditem)|表示項目是否表示連結的 OLE 項目。|
|[COleServerItem::NotifyChanged](#notifychanged)|使用自動連結更新來更新所有容器。|
|[COleServerItem::OnDoVerb](#ondoverb)|呼叫以執行動詞命令。|
|[COleServerItem::OnDraw](#ondraw)|繪製項目; 要求的容器時呼叫所需的實作。|
|[COleServerItem::OnDrawEx](#ondrawex)|針對特定的項目繪製呼叫。|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|由架構呼叫以取得的資料，將會複製到剪貼簿。|
|[COleServerItem::OnGetExtent](#ongetextent)|由架構呼叫以擷取 OLE 項目的大小。|
|[COleServerItem::OnInitFromData](#oninitfromdata)|由架構呼叫以初始化 OLE 項目使用指定的資料傳輸物件的內容。|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|呼叫以判斷是否需要更新任何連結的項目。|
|[COleServerItem::OnRenderData](#onrenderdata)|擷取資料做為延遲轉譯的一部分。|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|擷取資料到`CFile`一部分延遲轉譯的物件。|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|擷取資料到 HGLOBAL 延遲轉譯的一部分。|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|呼叫以設定項目的色彩配置。|
|[COleServerItem::OnSetData](#onsetdata)|呼叫以設定項目的資料。|
|[COleServerItem::OnSetExtent](#onsetextent)|由架構呼叫以設定的 OLE 項目大小。|
|[COleServerItem::OnUpdate](#onupdate)|呼叫中之項目的文件的一部分則歸屬時已變更。|
|[COleServerItem::OnUpdateItems](#onupdateitems)|呼叫以更新簡報的快取伺服器文件中的所有項目。|
|[COleServerItem::SetItemName](#setitemname)|設定項目的名稱。 用於連結項目。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[COleServerItem::GetDataSource](#getdatasource)|取得用來將轉換的格式儲存的物件。|
|[COleServerItem::OnHide](#onhide)|由架構呼叫以隱藏 OLE 項目。|
|[COleServerItem::OnOpen](#onopen)|由架構呼叫以顯示其最上層的視窗中的 OLE 項目。|
|[COleServerItem::OnShow](#onshow)|當容器要求顯示項目時呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleServerItem::m_sizeExtent](#m_sizeextent)|告知伺服器有多少 OLE 項目可見。|

## <a name="remarks"></a>備註

部分或所有的伺服器文件，可以表示連結的項目。 內嵌項目一律會代表整個伺服器文件。

`COleServerItem`類別會定義數個可覆寫成員函式呼叫的 OLE 系統動態連結程式庫 (Dll)，通常是從容器應用程式回應要求。 這些成員函式可讓容器應用程式，例如操作間接以各種方式的項目，顯示它、 執行其動詞命令，或者以各種格式資料擷取。

若要使用`COleServerItem`，從它衍生的類別並實作[OnDraw](#ondraw)並[序列化](../../mfc/reference/cobject-class.md#serialize)成員函式。 `OnDraw`函式會提供項目，讓它可以將容器應用程式會開啟 複合文件時要顯示的中繼檔表示。 `Serialize`函式的`CObject`提供項目，讓內嵌項目之間的伺服器和容器應用程式傳輸的原生表示法。 [OnGetExtent](#ongetextent)提供自然的容器，並啟用調整大小的項目容器的項目大小。

如需有關伺服器和相關的主題的詳細資訊，請參閱文章[伺服器：實作伺服器](../../mfc/servers-implementing-a-server.md)和 「 建立容器/伺服器應用程式 」 一文中[容器：進階功能](../../mfc/containers-advanced-features.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>需求

**標頭：** afxole.h

##  <a name="addotherclipboarddata"></a>  COleServerItem::AddOtherClipboardData

呼叫此函式可放置在指定的 OLE 項目展示和轉換格式`COleDataSource`物件。

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>參數

*pDataSource*<br/>
指標`COleDataSource`物件應放置資料。

### <a name="remarks"></a>備註

您必須實作[OnDraw](#ondraw)提供項目的呈現格式 （中繼檔圖片） 的成員函式。 若要支援其他轉換格式，將它們註冊使用[COleDataSource](../../mfc/reference/coledatasource-class.md)所傳回的物件[GetDataSource](#getdatasource)並覆寫[OnRenderData](#onrenderdata)成員函式提供您想要支援的格式資料。

##  <a name="coleserveritem"></a>  COleServerItem::COleServerItem

建構`COleServerItem`物件，並將它加入至文件項目伺服器文件的集合。

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>參數

*pServerDoc*<br/>
將包含新的項目文件的指標。

*bAutoDelete*<br/>
表示發行它的連結時，是否可以刪除物件的旗標。 將此設為 false`COleServerItem`物件是您必須刪除您的文件資料中不可或缺的一部分。 將此設為 true 的物件是用來識別架構來刪除您的文件資料中某個範圍的第二個結構。

##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard

呼叫此函式可將 OLE 項目複製到剪貼簿。

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>參數

*bIncludeLink*<br/>
將此設為 true 連結資料應該複製到剪貼簿。 將此設為 false 您的伺服器應用程式不支援連結。

### <a name="remarks"></a>備註

此函數會使用[ongetclipboarddata 而自動發生](#ongetclipboarddata)成員函式來建立[COleDataSource](../../mfc/reference/coledatasource-class.md)物件，其中包含支援的格式中的 OLE 項目的資料。 函式接著會放置`COleDataSource`使用剪貼簿上的物件[COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函式。 `COleDataSource` CF_METAFILEPICT 格式，以及任何您選擇支援的轉換格式的資料物件包含的項目原生資料，其表示法。 您必須實作[Serialize](../../mfc/reference/cobject-class.md#serialize)並[OnDraw](#ondraw)運作此成員函式。

##  <a name="dodragdrop"></a>  COleServerItem::DoDragDrop

呼叫`DoDragDrop`成員函式來執行拖放作業。

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
在畫面上，以像素為單位，相對於用戶端區域中的項目矩形。

*ptOffset*<br/>
從位移*lpItemRect*滑鼠位置的拖曳時。

*bIncludeLink*<br/>
將此設為 true 連結資料應該複製到剪貼簿。 請將它設定為 FALSE，如果您的應用程式不支援連結。

*dwEffects*<br/>
判斷拖曳來源會允許在拖曳作業 （複製、 移動和連結的組合） 的效果。

*lpRectStartDrag*<br/>
定義實際開始拖曳的矩形的指標。 如需詳細資訊，請參閱接下來的＜備註＞一節。

### <a name="return-value"></a>傳回值

從 DROPEFFECT 列舉的值。 如果是 DROPEFFECT_MOVE，應該移除原始的資料。

### <a name="remarks"></a>備註

拖放作業不會立即啟動。 它會等到滑鼠游標離開所指定的矩形*lpRectStartDrag*或直到經過指定的毫秒數。 如果*lpRectStartDrag*是 NULL，預設矩形使用，讓拖曳開始時將滑鼠游標移一個像素。

登錄機碼設定所指定的延遲時間。 您可以變更的延遲時間，藉由呼叫[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或是[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果您未指定延遲時間，則會使用預設值是 200 毫秒。 拖曳延遲時間會儲存，如下所示：

- Windows NT 拖曳延遲時間會儲存在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。

- Windows 3.x 拖曳延遲時間會儲存在獲得。INI 檔案，底下的 [Windows} 一節。

- Windows 95/98 拖曳延遲時間會儲存在成交的快取版本。INI。

如需有關如何將拖曳的延遲資訊會儲存在登錄或。INI 檔案，請參閱[WriteProfileString](/windows/desktop/api/winbase/nf-winbase-writeprofilestringa) Windows SDK 中。

##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData

呼叫此函式，以指定的填滿[COleDataSource](../../mfc/reference/coledatasource-class.md)物件會複製到剪貼簿中，如果您呼叫的所有資料[CopyToClipboard](#copytoclipboard) (會也會傳送相同的資料，如果您呼叫[DoDragDrop](#dodragdrop))。

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>參數

*pDataSource*<br/>
指標`COleDataSource`會在所有支援的格式收到 OLE 項目資料的物件。

*bIncludeLink*<br/>
連結資料應該複製到剪貼簿，其值為 TRUE。 如果您的伺服器應用程式不支援的連結，則為 FALSE。

*lpOffset*<br/>
以像素為單位，滑鼠資料指標，從物件的原始來源中的位移。

*lpSize*<br/>
像素為單位的物件大小。

### <a name="remarks"></a>備註

此函式會呼叫[GetEmbedSourceData](#getembedsourcedata)成員函式來取得原生資料的 OLE 項目並呼叫[AddOtherClipboardData](#addotherclipboarddata)取得的呈現格式，以及任何的成員函式支援的轉換格式。 如果*bIncludeLink*呼叫也為 TRUE 時，此函式[GetLinkSourceData](#getlinksourcedata)取得項目連結的資料。

覆寫這個函式，如果您想要置於格式`COleDataSource`之前或之後所提供的這些格式的物件`CopyToClipboard`。

##  <a name="getdatasource"></a>  COleServerItem::GetDataSource

呼叫此函式可取得[COleDataSource](../../mfc/reference/coledatasource-class.md)用來儲存伺服器應用程式支援的轉換格式的物件。

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>傳回值

指標`COleDataSource`用來儲存轉換格式的物件。

### <a name="remarks"></a>備註

如果您想您的伺服器應用程式提供各種格式的資料，資料傳輸期間作業時，註冊與這些格式`COleDataSource`此函數所傳回的物件。 例如，如果您想要提供 OLE 項目的 CF_TEXT 表示剪貼簿或拖放作業，您會註冊與格式`COleDataSource`此函式傳回的物件，然後覆寫`OnRenderXxxData`成員函式提供的資料。

##  <a name="getdocument"></a>  COleServerItem::GetDocument

呼叫此函式可取得包含項目的文件的指標。

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>傳回值

包含項目; 的文件指標如果項目不是文件的一部分，則為 NULL。

### <a name="remarks"></a>備註

這可讓您存取伺服器文件做為引數傳遞`COleServerItem`建構函式。

##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData

呼叫此函式可取得的 CF_EMBEDSOURCE 資料 OLE 項目。

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpStgMedium*<br/>
指標[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)會收到 OLE 項目的 CF_EMBEDSOURCE 資料的結構。

### <a name="remarks"></a>備註

此格式包含的項目原生資料。 您必須實作`Serialize`成員函式，此函式才能正常運作。

結果可以再加入資料來源使用[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 會自動呼叫此函數[COleServerItem::OnGetClipboardData](#ongetclipboarddata)。

如需詳細資訊，請參閱 < [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) Windows SDK 中。

##  <a name="getitemname"></a>  COleServerItem::GetItemName

呼叫此函式可取得項目的名稱。

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>傳回值

項目的名稱。

### <a name="remarks"></a>備註

您通常會呼叫此函式只會針對連結的項目。

##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData

呼叫此函式可取得的 CF_LINKSOURCE 資料 OLE 項目。

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpStgMedium*<br/>
指標[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)會收到 OLE 項目的 CF_LINKSOURCE 資料的結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此格式包含描述 OLE 項目和尋找文件，內含 OLE 項目所需的資訊類型的 CLSID。

結果可以新增至資料來源[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 會自動呼叫此函數[ongetclipboarddata 而自動發生](#ongetclipboarddata)。

如需詳細資訊，請參閱 < [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) Windows SDK 中。

##  <a name="getobjectdescriptordata"></a>  COleServerItem::GetObjectDescriptorData

呼叫此函式可取得的 CF_OBJECTDESCRIPTOR 資料 OLE 項目。

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpOffset*<br/>
從 OLE 項目左上角，按一下的滑鼠所造成的位移。 可以是 NULL。

*lpSize*<br/>
OLE 項目的大小。 可以是 NULL。

*lpStgMedium*<br/>
指標[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)會收到 OLE 項目的 CF_OBJECTDESCRIPTOR 資料的結構。

### <a name="remarks"></a>備註

資訊都會複製到`STGMEDIUM`結構所指*lpStgMedium*。 此格式包含貼上 對話方塊所需的資訊。

如需詳細資訊，請參閱 < [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) Windows SDK 中。

##  <a name="isconnected"></a>  COleServerItem::IsConnected

呼叫此函式，以查看是否已連接的 OLE 項目。

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>傳回值

非零值，如果項目都會連接;否則為 0。

### <a name="remarks"></a>備註

OLE 項目會被視為已連接一或多個容器有項目的參考。 如果參考計數大於 0，或者它是內嵌的項目，被連接項目。

##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem

呼叫此函式的 OLE 項目是否為連結的項目。

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>傳回值

非零值，如果項目連結的項目;否則為 0。

### <a name="remarks"></a>備註

項目連結的項目有效，且不會傳回在文件的清單中的內嵌項目。 連結的項目可能會或可能未連線至容器。

它會連結和內嵌的項目所使用相同的類別。 `IsLinkedItem` 可讓您進行連結的行為與內嵌的項目，不同的項目，雖然許多次的程式碼很常見。

##  <a name="m_sizeextent"></a>  COleServerItem::m_sizeExtent

這個成員會要求伺服器多少物件會顯示在容器文件。

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>備註

預設實作[OnSetExtent](#onsetextent)設定這個成員。

##  <a name="notifychanged"></a>  COleServerItem::NotifyChanged

變更連結的項目之後，請呼叫此函式。

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>參數

*nDrawAspect*<br/>
從 DVASPECT 列舉，指出哪些層面 OLE 項目已變更的值。 這個參數可以具有下列值之一：

- DVASPECT_CONTENT 項目表示的方式，它可以顯示為其容器內部的內嵌物件。

- 「 縮圖 」 表示法呈現 DVASPECT_THUMBNAIL 項目，以便它可以顯示在瀏覽工具。

- DVASPECT_ICON 項目是以圖示表示。

- DVASPECT_DOCPRINT 項目被表示，如同它已列印使用從 [檔案] 功能表的 [列印] 命令。

### <a name="remarks"></a>備註

如果自動連結的容器項目連結至文件，此項目會更新以反映所做的變更。 在容器應用程式中使用 Microsoft Foundation 類別庫中，撰寫[COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange)呼叫回應中。

##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb

由架構呼叫以執行指定的動詞命令。

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
指定要執行的動詞命令。 它可以是下列其中一項動作：

|值|意義|符號|
|-----------|-------------|------------|
|0|主動詞命令|OLEIVERB_PRIMARY|
|1|次要的動詞命令|(無)|
|- 1|顯示項目進行編輯|OLEIVERB_SHOW|
|- 2|編輯在個別視窗中的項目|OLEIVERB_OPEN|
|- 3|隱藏項目|OLEIVERB_HIDE|

-1 值通常是另一個動詞命令的別名。 如果不支援開啟編輯，-2 會有相同的效果，為-1。 其他值，請參閱[IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) Windows SDK 中。

### <a name="remarks"></a>備註

如果容器應用程式使用 Microsoft Foundation 類別庫所撰寫，此函式時，會呼叫[COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate)成員函式對應`COleClientItem`呼叫物件。 預設實作會呼叫[OnShow](#onshow)成員函式，如果指定 OLEIVERB_SHOW 或主要的動詞命令，則[OnOpen](#onopen)如果指定了次要動作或 OLEIVERB_OPEN，和[OnHide](#onhide)如果 OLEIVERB_HIDE 指定。 預設實作會呼叫`OnShow`如果*iVerb*不是其中一個上面所列的動詞命令。

如果您主要的動詞命令不會顯示此項目，請覆寫這個函式。 比方說，如果項目是錄音，其主要動作是播放，您就沒有顯示伺服器應用程式播放該項目。

如需詳細資訊，請參閱 < [IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) Windows SDK 中。

##  <a name="ondraw"></a>  COleServerItem::OnDraw

由架構呼叫以轉譯 OLE 項目為中繼檔。

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>參數

*pDC*<br/>
指標[CDC](../../mfc/reference/cdc-class.md)物件在其上繪製項目。 顯示內容會自動連接到的屬性顯示的內容讓您可以呼叫屬性的函式，雖然這樣做會限制之中繼檔裝置特有。

*rSize*<br/>
以 himetric 為單位，在其中繪製中繼檔的大小。

### <a name="return-value"></a>傳回值

如果已經成功地繪製項目; 非零值否則為 0。

### <a name="remarks"></a>備註

OLE 項目之中繼檔表示用來顯示容器應用程式中的項目。 如果容器應用程式使用 Microsoft Foundation 類別庫所撰寫，會使用中繼檔[繪製](../../mfc/reference/coleclientitem-class.md#draw)成員函式的對應[COleClientItem](../../mfc/reference/coleclientitem-class.md)物件。 沒有預設的實作。 您必須覆寫此函式可繪製到指定的裝置內容的項目。

##  <a name="ondrawex"></a>  COleServerItem::OnDrawEx

由架構呼叫的所有繪圖。

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指標[CDC](../../mfc/reference/cdc-class.md)物件在其上繪製項目。 DC 會自動連接到 DC 的屬性讓您可以呼叫屬性的函式，雖然這樣做會限制之中繼檔裝置特有。

*nDrawAspect*<br/>
從 DVASPECT 列舉的值。 這個參數可以具有下列值之一：

- DVASPECT_CONTENT 項目表示的方式，它可以顯示為其容器內部的內嵌物件。

- 「 縮圖 」 表示法呈現 DVASPECT_THUMBNAIL 項目，以便它可以顯示在瀏覽工具。

- DVASPECT_ICON 項目是以圖示表示。

- DVASPECT_DOCPRINT 項目被表示，如同它已列印使用從 [檔案] 功能表的 [列印] 命令。

*rSize*<br/>
項目，以 himetric 為單位的大小。

### <a name="return-value"></a>傳回值

如果已經成功地繪製項目; 非零值否則為 0。

### <a name="remarks"></a>備註

預設實作會呼叫`OnDraw`時 DVASPECT 等於 DVASPECT_CONTENT; 否則會失敗。

覆寫此函式可提供 DVASPECT_CONTENT，例如 DVASPECT_ICON 或 DVASPECT_THUMBNAIL 以外的層面呈現資料。

##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData

由架構呼叫以取得`COleDataSource`物件，包含會呼叫放到剪貼簿的所有資料[CopyToClipboard](#copytoclipboard)成員函式。

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>參數

*bIncludeLink*<br/>
將此設為 true 連結資料應該複製到剪貼簿。 將此設為 false 您的伺服器應用程式不支援連結。

*lpOffset*<br/>
滑鼠資料指標原點的像素為單位的物件的位移。

*lpSize*<br/>
像素為單位的物件大小。

### <a name="return-value"></a>傳回值

指標[COleDataSource](../../mfc/reference/coledatasource-class.md)物件，其中包含剪貼簿的資料。

### <a name="remarks"></a>備註

此函式的預設實作會呼叫[GetClipboardData](#getclipboarddata)。

##  <a name="ongetextent"></a>  COleServerItem::OnGetExtent

由架構呼叫以擷取的大小，以 himetric 為單位，OLE 項目。

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>參數

*nDrawAspect*<br/>
指定要擷取其界限的 OLE 項目的外觀。 這個參數可以具有下列值之一：

- DVASPECT_CONTENT 項目表示的方式，它可以顯示為其容器內部的內嵌物件。

- 「 縮圖 」 表示法呈現 DVASPECT_THUMBNAIL 項目，以便它可以顯示在瀏覽工具。

- DVASPECT_ICON 項目是以圖示表示。

- DVASPECT_DOCPRINT 項目被表示，如同它已列印使用從 [檔案] 功能表的 [列印] 命令。

*rSize*<br/>
若要參考`CSize`物件，將會收到 OLE 項目的大小。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果容器應用程式使用 Microsoft Foundation 類別庫所撰寫，此函式時，會呼叫[GetExtent](../../mfc/reference/coleclientitem-class.md#getextent)成員函式對應`COleClientItem`呼叫物件。 預設實作不做任何動作。 您必須實作它自己。 如果您想要處理的 OLE 項目大小的要求時執行特殊處理，請覆寫這個函式。

##  <a name="onhide"></a>  COleServerItem::OnHide

由架構呼叫以隱藏 OLE 項目。

```
virtual void OnHide();
```

### <a name="remarks"></a>備註

預設會呼叫`COleServerDoc::OnShowDocument( FALSE )`。 函式也會告知容器已隱藏 OLE 項目。 如果您想要隱藏 OLE 項目會執行特殊處理，請覆寫這個函式。

##  <a name="oninitfromdata"></a>  COleServerItem::OnInitFromData

由架構呼叫以初始化 OLE 項目使用的內容*pDataObject*。

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
OLE 資料物件，包含各種格式來初始化 OLE 項目中的資料指標。

*bCreation*<br/>
如果函式呼叫來初始化新建立的容器應用程式的 OLE 項目，則為 TRUE。 如果呼叫此函式來取代現有的 OLE 項目的內容，則為 FALSE。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果*bCreation*為 TRUE，如果容器實作插入新物件根據目前的選取項目，會呼叫此函數。 建立新的 OLE 項目時，會使用選取的資料。 比方說，當在試算表程式中選取資料格範圍，然後使用 建立圖表的 插入新物件基礎的選取範圍中的值。 預設實作不做任何動作。 覆寫此函式可從所提供的選擇可接受的格式*pDataObject*和初始化 OLE 項目，根據提供的資料。 這是一種進階可覆寫。

如需詳細資訊，請參閱 < [IOleObject::InitFromData](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-initfromdata) Windows SDK 中。

##  <a name="onopen"></a>  COleServerItem::OnOpen

由架構呼叫以個別的執行個體的伺服器應用程式，而不是就地顯示 OLE 項目。

```
virtual void OnOpen();
```

### <a name="remarks"></a>備註

預設實作啟動顯示文件，其中包含 OLE 項目; 的第一個框架視窗迷你伺服器應用程式時，預設實作會顯示在主視窗。 函式也會告知容器已開啟的 OLE 項目。

如果您想要開啟 OLE 項目時執行特殊處理，請覆寫這個函式。 這是您想要用來開啟時，設定選取項目連結的連結項目上特別常發生。

如需詳細資訊，請參閱 < [IOleClientSite::OnShowWindow](/windows/desktop/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) Windows SDK 中。

##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems

由架構呼叫以判斷目前的伺服器文件中任何連結的項目是否已過期。

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>傳回值

如果文件沒有需要更新; 的項目，非零值。0，表示所有項目是最新狀態。

### <a name="remarks"></a>備註

如果已變更其來源文件，但連結的項目尚未更新以反映文件中的變更，項目已過期。

##  <a name="onrenderdata"></a>  COleServerItem::OnRenderData

由架構呼叫以擷取指定格式的資料。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構，指定用來要求資訊的格式。

*lpStgMedium*<br/>
指向[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)資料所要傳回的結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)或是[DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)延遲轉譯的成員函式。 此函式的預設實作會呼叫[OnRenderFileData](#onrenderfiledata)或是[OnRenderGlobalData](#onrenderglobaldata)分別，如果提供的存放媒體是檔案或記憶體。 如果一種格式都未提供，預設實作會傳回 0，且沒有任何作用。

如果*lpStgMedium*-> *tymed*是 TYMED_NULL，STGMEDIUM 應該配置，而且所指定的填滿*lpFormatEtc]-> [tymed*。 如果不是在與資料的位置，則應該填入 TYMED_NULL、 STGMEDIUM。

這是一種進階可覆寫。 覆寫此函式可提供您要求的格式和媒體中的資料。 根據您的資料，您可能想要改為覆寫這個函式的其他版本的其中一個。 如果您的資料是小型且固定的大小，會覆寫`OnRenderGlobalData`。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。

如需詳細資訊，請參閱 < [idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata)， [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)， [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)，以及[TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed) Windows SDK 中。

##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData

由架構呼叫以擷取指定之格式的資料儲存體中的檔案時。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構，指定用來要求資訊的格式。

*pFile*<br/>
指向`CFile`所在的資料是要轉譯的物件。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回 FALSE。

這是一種進階可覆寫。 覆寫此函式可提供您要求的格式和媒體中的資料。 根據您的資料，您可能想要改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存體媒介中轉移，覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫[OnRenderFileData](#onrenderfiledata)。

如需詳細資訊，請參閱 < [idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata)並[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中。

##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData

由架構呼叫以指定的存放媒體是全域記憶體時，擷取指定之格式的資料。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構，指定用來要求資訊的格式。

*phGlobal*<br/>
指向要傳回之資料的全域記憶體控制代碼。 如果已不配置任何記憶體，則這個參數可以是 NULL。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回 FALSE。

如果*phGlobal*是 NULL，則應該配置並傳回新 HGLOBAL *phGlobal*。 HGLOBAL 所指定的否則為*phGlobal*應該填入資料。 資料放在 HGLOBAL 數量不得超過目前的記憶體區塊大小。 此外，無法重新配置較大的區塊。

這是一種進階可覆寫。 覆寫此函式可提供您要求的格式和媒體中的資料。 根據您的資料，您可能想要改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存體媒介中轉移，覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫[OnRenderFileData](#onrenderfiledata)。

如需詳細資訊，請參閱 < [idataobject:: Getdata](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata)並[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中。

##  <a name="onsetcolorscheme"></a>  COleServerItem::OnSetColorScheme

由架構呼叫以指定編輯 OLE 項目時要使用的調色盤。

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>參數

*lpLogPalette*<br/>
Windows 指標[LOGPALETTE](/windows/desktop/api/wingdi/ns-wingdi-taglogpalette)結構。

### <a name="return-value"></a>傳回值

如果色彩調色盤則為非零值否則為 0。

### <a name="remarks"></a>備註

如果容器應用程式使用 Microsoft Foundation 類別庫所撰寫，此函式時，會呼叫[IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme)函式對應`COleClientItem`呼叫物件。 預設實作會傳回 FALSE。 如果您想要使用建議的調色盤，請覆寫這個函式。 伺服器應用程式不需要使用建議的調色盤。

如需詳細資訊，請參閱 < [IOleObject::SetColorScheme](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) Windows SDK 中。

##  <a name="onsetdata"></a>  COleServerItem::OnSetData

由架構呼叫以指定的資料取代 OLE 項目的資料。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指標[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)結構，指定資料的格式。

*lpStgMedium*<br/>
指標[STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)結構，位在其中的資料。

*bRelease*<br/>
表示誰完成函式呼叫之後儲存媒體的擁有權。 呼叫端將決定誰負責釋放配置的存放媒體代表的資源。 呼叫端會藉由設定*bRelease*。 如果*bRelease*為非零值，伺服器項目取得擁有權，使用它完成時釋放媒體。 當*bRelease*為 0，呼叫端保留擁有權，且伺服器項目只能針對在呼叫期間使用的存放媒體。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

它已成功取得它的伺服器項目才會將資料的擁有權。 也就是說，它不會擁有權如果它傳回 0。 如果資料來源會取得擁有權，它會藉由呼叫釋放儲存媒體[ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium)函式。

預設實作不做任何動作。 覆寫這個函式來取代指定的資料中的 OLE 項目的資料。 這是一種進階可覆寫。

如需詳細資訊，請參閱 < [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium)， [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc)，並[ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) Windows SDK 中。

##  <a name="onsetextent"></a>  COleServerItem::OnSetExtent

由架構呼叫以告知 OLE 項目多少空間可用，在容器文件中。

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>參數

*nDrawAspect*<br/>
指定 OLE 項目會指定其界限的外觀。 這個參數可以具有下列值之一：

- DVASPECT_CONTENT 項目表示的方式，它可以顯示為其容器內部的內嵌物件。

- 「 縮圖 」 表示法呈現 DVASPECT_THUMBNAIL 項目，以便它可以顯示在瀏覽工具。

- DVASPECT_ICON 項目是以圖示表示。

- DVASPECT_DOCPRINT 項目被表示，如同它已列印使用從 [檔案] 功能表的 [列印] 命令。

*size*<br/>
A [CSize](../../atl-mfc-shared/reference/csize-class.md)結構，指定新的 OLE 項目大小。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果容器應用程式使用 Microsoft Foundation 類別庫所撰寫，此函式時，會呼叫[SetExtent](../../mfc/reference/coleclientitem-class.md#setextent)成員函式對應`COleClientItem`呼叫物件。 預設實作集[m_sizeExtent](#m_sizeextent)成員所指定大小時如果*nDrawAspect*是 DVASPECT_CONTENT; 否則會傳回 0。 覆寫這個函式來執行特殊處理，當您變更項目的大小。

##  <a name="onshow"></a>  COleServerItem::OnShow

由架構呼叫以指示伺服器應用程式，以就地顯示 OLE 項目。

```
virtual void OnShow();
```

### <a name="remarks"></a>備註

當容器應用程式的使用者建立項目，或執行的指令動詞，例如編輯、 通常會呼叫此函數所要顯示的項目。 預設實作會嘗試在就地啟用。 如果失敗，函式呼叫`OnOpen`成員函式，以在個別視窗中顯示 OLE 項目。

如果您想要執行特殊處理，當顯示 OLE 項目時，請覆寫這個函式。

##  <a name="onupdate"></a>  COleServerItem::OnUpdate

已修改的項目時，由架構呼叫。

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>參數

*pSender*<br/>
修改文件項目的指標。 可以是 NULL。

*lHint*<br/>
包含修改的相關資訊。

*pHint*<br/>
儲存修改的相關資訊的物件指標。

*nDrawAspect*<br/>
從 DVASPECT 列舉的值。 這個參數可以具有下列值之一：

- DVASPECT_CONTENT 項目表示的方式，它可以顯示為其容器內部的內嵌物件。

- 「 縮圖 」 表示法呈現 DVASPECT_THUMBNAIL 項目，以便它可以顯示在瀏覽工具。

- DVASPECT_ICON 項目是以圖示表示。

- DVASPECT_DOCPRINT 項目被表示，如同它已列印使用從 [檔案] 功能表的 [列印] 命令。

### <a name="remarks"></a>備註

預設實作會呼叫[NotifyChanged](#notifychanged)不論提示或寄件者。

##  <a name="onupdateitems"></a>  COleServerItem::OnUpdateItems

由架構呼叫以更新伺服器文件中的所有項目。

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>備註

預設實作會呼叫[UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)所有`COleClientItem`文件中的物件。

##  <a name="setitemname"></a>  COleServerItem::SetItemName

當您建立連結的項目，可將它的名稱，請呼叫此函式。

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>參數

*lpszItemName*<br/>
項目的新名稱的指標。

### <a name="remarks"></a>備註

名稱必須是唯一的文件中。 若要編輯連結的項目呼叫伺服器應用程式時，應用程式會使用此名稱尋找項目。 您不需要呼叫此函式的內嵌項目。

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem 類別](../../mfc/reference/cdocitem-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)
