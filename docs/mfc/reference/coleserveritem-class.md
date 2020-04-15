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
ms.openlocfilehash: 5373075cf6dfc54e6e2368e46f48f317fcec64d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376120"
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
|[COleServer 專案:COleServer專案](#coleserveritem)|建構 `COleServerItem` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleServer 專案:新增其他剪貼簿資料](#addotherclipboarddata)|在`COleDataSource`物件中放置表示和轉換格式。|
|[COleServer 專案::複製到剪貼簿](#copytoclipboard)|將專案複製到剪貼簿。|
|[COleServer專案::DoDragDrop](#dodragdrop)|執行拖放操作。|
|[COleServer 專案:取得剪貼簿資料](#getclipboarddata)|獲取用於數據傳輸(拖放或剪貼簿)的數據源。|
|[COleServer 專案:取得文件](#getdocument)|返回包含該項目的伺服器文檔。|
|[COleServer 專案:取得嵌入來源資料](#getembedsourcedata)|獲取 OLE 項的CF_EMBEDSOURCE數據。|
|[COleServer 專案:取得項目名稱](#getitemname)|返回項的名稱。 僅用於連結專案。|
|[COleServer 專案:取得連結來源資料](#getlinksourcedata)|獲取 OLE 項CF_LINKSOURCE數據。|
|[COleServer 專案:取得物件描述資料](#getobjectdescriptordata)|獲取 OLE 項CF_OBJECTDESCRIPTOR數據。|
|[COleServer 專案:已連接](#isconnected)|指示專案當前是否附加到活動容器。|
|[COleServer 專案:是連結專案](#islinkeditem)|指示專案是否表示連結的 OLE 項。|
|[COleServer 專案:通知已變更](#notifychanged)|使用自動連結更新更新所有容器。|
|[COleServer專案:OnDoVerb](#ondoverb)|被調用以執行動詞。|
|[COleServer專案:在畫上](#ondraw)|當容器請求繪製項時調用;需要實現。|
|[COleServer專案:OnDrawEx](#ondrawex)|調用專用項目繪圖。|
|[COleServer 專案:在取得剪貼簿資料](#ongetclipboarddata)|由框架呼叫,獲取將複製到剪貼簿的資料。|
|[COleServerItem::OnGetExtent](#ongetextent)|由框架調用以檢索 OLE 項的大小。|
|[COleServer 專案:從資料開啟](#oninitfromdata)|框架呼叫使用指定的資料傳輸物件的內容初始化 OLE 項。|
|[COleServer 專案:開啟查詢更新專案](#onqueryupdateitems)|調用 以確定是否有任何連結的專案需要更新。|
|[COleServer 專案:在渲染資料上](#onrenderdata)|檢索數據作為延遲呈現的一部分。|
|[COleServer 專案:在渲染檔案資料上](#onrenderfiledata)|將數據檢索到物件中`CFile`作為延遲呈現的一部分。|
|[COleServer專案:在渲染全域資料上](#onrenderglobaldata)|將數據檢索到 HGLOBAL 中,作為延遲呈現的一部分。|
|[COleServer 專案:開啟顏色機制](#onsetcolorscheme)|調用以設置專案的色彩配置。|
|[COleServer專案:OnSetData](#onsetdata)|調用以設置項的數據。|
|[COleServerItem::OnSetExtent](#onsetextent)|由框架調用以設置 OLE 項的大小。|
|[COleServer專案:更新](#onupdate)|當項目所屬的文檔的某些部分已更改時調用。|
|[COleServer專案:更新專案](#onupdateitems)|呼叫 以更新伺服器文件中所有項的演示文稿快取。|
|[COleServer 專案:設定項目名稱](#setitemname)|設置項的名稱。 僅用於連結專案。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[COleServer 專案:取得資料來源](#getdatasource)|獲取用於存儲轉換格式的物件。|
|[COleServer 專案:開啟隱藏](#onhide)|由框架調用以隱藏 OLE 項。|
|[COleServer 專案:開啟](#onopen)|由框架調用以在其自己的頂級視窗中顯示 OLE 項。|
|[COleServer專案:在展會上](#onshow)|當容器請求顯示項時調用。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleServer專案:m_sizeExtent](#m_sizeextent)|通知伺服器有多少 OLE 項可見。|

## <a name="remarks"></a>備註

連結項可以表示部分或全部伺服器文檔。 嵌入的項目始終表示整個伺服器文檔。

該`COleServerItem`類定義由 OLE 系統動態連結庫 (DLL) 調用的多個可重寫成員函數,通常是為了回應來自容器應用程式的請求。 這些成員函數允許容器應用程式以各種方式間接操作專案,例如通過顯示專案、執行其謂詞或以各種格式檢索其數據。

要使用`COleServerItem`,從中派生類並實現[OnDraw](#ondraw)和[序列化](../../mfc/reference/cobject-class.md#serialize)成員函數。 該`OnDraw`函數提供項的元檔表示形式,允許在容器應用程式打開複合文件時顯示它。 提供`Serialize``CObject`項的本機表示形式,允許在伺服器和容器應用程式之間傳輸嵌入項。 [OnGetExtent](#ongetextent)向容器提供專案的自然大小,使容器能夠調整專案的大小。

關於伺服器與相關主題的詳細資訊,請參考文章伺服器伺服器[:實現伺服器'](../../mfc/servers-implementing-a-server.md)與'建立容器/伺服器應用程式"一文[:進階功能](../../mfc/containers-advanced-features.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="coleserveritemaddotherclipboarddata"></a><a name="addotherclipboarddata"></a>COleServer 專案:新增其他剪貼簿資料

呼叫此函數將 OLE 的表示格式和轉換格式放在`COleDataSource`指定 物件中。

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>參數

*pData 來源*<br/>
指向應放置`COleDataSource`數據的物件的指標。

### <a name="remarks"></a>備註

您必須已實現[OnDraw](#ondraw)成員函數,才能為專案提供表示格式(元檔圖片)。 要支援其他轉換格式,請使用[GetDataSource](#getdatasource)傳回的[COleDataSource](../../mfc/reference/coledatasource-class.md)物件註冊它們,並重寫[OnRenderData](#onrenderdata)成員函數以您想要支援的格式提供數據。

## <a name="coleserveritemcoleserveritem"></a><a name="coleserveritem"></a>COleServer 專案:COleServer專案

建構物件`COleServerItem`並將其添加到伺服器文件的文檔項集合中。

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>參數

*pServerDoc*<br/>
指向將包含新項目的文檔的指標。

*b 自動刪除*<br/>
指示在釋放指向物件的連結時是否可以刪除該物件的標誌。 如果對像是必須刪除的文件`COleServerItem`資料的組成部分,則將其設置為 FALSE。 如果對像是用於識別文件資料中可由框架刪除的範圍的輔助結構,則將其設置為 TRUE。

## <a name="coleserveritemcopytoclipboard"></a><a name="copytoclipboard"></a>COleServer 專案::複製到剪貼簿

呼叫此函數以將 OLE 複製到剪貼簿。

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>參數

*bInclude 連結*<br/>
如果連結數據應複製到剪貼簿,則將其設置為 TRUE。 如果伺服器應用程式不支援連結,請將此設置為 FALSE。

### <a name="remarks"></a>備註

該函數使用[OnGetClipboardData](#ongetclipboarddata)成員函數建立一個包含 OLE 項數據的[COleDataSource](../../mfc/reference/coledatasource-class.md)物件,該物件採用支援的格式。 然後,該函數使用`COleDataSource` [COleDataSource::setClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函數將物件放在剪貼簿上。 該`COleDataSource`物件包括專案的本機數據及其CF_METAFILEPICT格式的表示形式,以及您選擇的任何轉換格式的數據。 您必須已實現[序列化和](../../mfc/reference/cobject-class.md#serialize) [OnDraw,](#ondraw)才能讓此成員函數正常工作。

## <a name="coleserveritemdodragdrop"></a><a name="dodragdrop"></a>COleServer專案::DoDragDrop

調用`DoDragDrop`成員函數以執行拖放操作。

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>參數

*lprect 專案*<br/>
相對於工作區,螢幕上的專案矩形(以像素為單位)。

*pt 位移*<br/>
滑鼠位置在拖動時所在的*lpItemRect*的偏移量。

*bInclude 連結*<br/>
如果連結數據應複製到剪貼簿,則將其設置為 TRUE。 如果應用程式不支援連結,請將其設置為 FALSE。

*dwEffects*<br/>
確定拖動源在拖動操作中允許的效果(複製、移動和連結的組合)。

*lpRect 開始拖動*<br/>
指向定義拖動實際開始位置的矩形的指標。 如需詳細資訊，請參閱接下來的＜備註＞一節。

### <a name="return-value"></a>傳回值

DROPVALUE 枚舉中的值。 如果DROPEFFECT_MOVE,則應刪除原始數據。

### <a name="remarks"></a>備註

拖放操作不會立即啟動。 它等待滑鼠游標離開*lpRectStartDrag 指定的*矩形或直到經過指定數量的毫秒。 如果*lpRectStartDrag*為 NULL,則使用預設矩形,以便在滑鼠游標移動一個圖元時開始拖動。

延遲時間由註冊表鍵設置指定。 您可以通過調用[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint)來更改延遲時間。 如果不指定延遲時間,則使用預設值 200 毫秒。 拖動延遲時間儲存如下:

- Windows NT 拖動延遲時間存儲在HKEY_LOCAL_MACHINE_SOFTWARE_微軟\Windows_NT_當前版本\iniFile映射\win.ini_Windows_Dragdelay。

- Windows 3.x 拖動延遲時間存儲在 WIN 中。INI 檔,在 [Windows] 部分下。

- Windows 95/98 拖動延遲時間存儲在 WIN 的緩存版本中。Ini。

有關拖動延遲資訊如何存儲在註冊表或 中的詳細資訊。INI 檔案,請參閱 Windows SDK 中的[寫入設定檔字串](/windows/win32/api/winbase/nf-winbase-writeprofilestringw)。

## <a name="coleserveritemgetclipboarddata"></a><a name="getclipboarddata"></a>COleServer 專案:取得剪貼簿資料

呼叫此函數以填充指定的[COleDataSource](../../mfc/reference/coledatasource-class.md)物件,其中包含將複製到剪貼簿的所有資料(如果您[CopyToClipboard](#copytoclipboard)呼叫[DoDragDrop,](#dodragdrop)也會傳輸相同的數據)。

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>參數

*pData 來源*<br/>
指向將以`COleDataSource`所有受支援格式接收 OLE 項資料的物件的指標。

*bInclude 連結*<br/>
如果連結數據應複製到剪貼簿,則為 TRUE。 如果伺服器應用程式不支援連結,則 FALSE。

*lpOffset*<br/>
滑鼠游標與物件原點的偏移量(以像素為單位)。

*lpSize*<br/>
物件的大小(以像素為單位)。

### <a name="remarks"></a>備註

此函數調用[GetEmbedSourceData](#getembedsourcedata)成員函數獲取 OLE 專案的本機數據,並調用[AddOtherClipboard 資料](#addotherclipboarddata)成員函數來獲取表示格式和任何支援的轉換格式。 如果*bIncludeLink*為 TRUE,則函數還會調用[GetLinkSourceData](#getlinksourcedata)來獲取該專案的連結數據。

如果要在`CopyToClipboard`提供的格式之前或之後將`COleDataSource`格式 放在物件中,則重寫此函數。

## <a name="coleserveritemgetdatasource"></a><a name="getdatasource"></a>COleServer 專案:取得資料來源

呼叫此函數獲取用於儲存伺服器應用程式支援的轉換格式的[COleDataSource](../../mfc/reference/coledatasource-class.md)物件。

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>傳回值

指向用於儲存轉換`COleDataSource`格式的物件的指標。

### <a name="remarks"></a>備註

如果希望伺服器應用程式在數據傳輸操作期間以各種格式提供數據,請將這些格式註冊到此函數返回`COleDataSource`的物件中。 例如,如果要為剪貼簿或拖放操作提供 OLE 項的CF_TEXT表示形式,則需要將格式註冊到此函`COleDataSource`數返回的物件,`OnRenderXxxData`然後覆蓋成員函數以提供數據。

## <a name="coleserveritemgetdocument"></a><a name="getdocument"></a>COleServer 專案:取得文件

呼叫此函數以獲取指向包含項的文件的指標。

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>傳回值

指向包含項的文檔的指標;如果專案不是文件的一部分,則 NULL。

### <a name="remarks"></a>備註

這允許造訪作為參數傳遞給建構函數`COleServerItem`的伺服器文檔。

## <a name="coleserveritemgetembedsourcedata"></a><a name="getembedsourcedata"></a>COleServer 專案:取得嵌入來源資料

調用此函數以獲取 OLE 項CF_EMBEDSOURCE數據。

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpStg 中*<br/>
指向將接收 OLE 項CF_EMBEDSOURCE數據的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構的指標。

### <a name="remarks"></a>備註

此格式包括專案的本機數據。 您必須已實現`Serialize`成員函數,才能使此函數正常工作。

然後,可以使用[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)將結果添加到數據源中。 此函數由[COleServerItem 自動呼叫::::在GetClipboard資料上](#ongetclipboarddata)。

有關詳細資訊,請參閱 Windows SDK 中的[STGMEDIUM。](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)

## <a name="coleserveritemgetitemname"></a><a name="getitemname"></a>COleServer 專案:取得項目名稱

呼叫此函數以獲取項的名稱。

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>傳回值

項目的名稱。

### <a name="remarks"></a>備註

通常僅針對連結的專案調用此函數。

## <a name="coleserveritemgetlinksourcedata"></a><a name="getlinksourcedata"></a>COleServer 專案:取得連結來源資料

呼叫此函數以獲取 OLE 項的CF_LINKSOURCE資料。

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpStg 中*<br/>
指向將接收 OLE 項CF_LINKSOURCE數據的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此格式包括 CLSID,描述 OLE 項的類型以及查找包含 OLE 項的文件所需的資訊。

然後,可以使用[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)將結果添加到數據源中。 此功能由[OnGetClipboard 數據](#ongetclipboarddata)自動呼叫。

有關詳細資訊,請參閱 Windows SDK 中的[STGMEDIUM。](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)

## <a name="coleserveritemgetobjectdescriptordata"></a><a name="getobjectdescriptordata"></a>COleServer 專案:取得物件描述資料

調用此函數以獲取 OLE 項CF_OBJECTDESCRIPTOR數據。

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpOffset*<br/>
滑鼠按下從 OLE 專案的左上角偏移。 可以是 NULL。

*lpSize*<br/>
OLE 項的大小。 可以是 NULL。

*lpStg 中*<br/>
指向將接收 OLE 項CF_OBJECTDESCRIPTOR數據的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構的指標。

### <a name="remarks"></a>備註

資訊被複製到`STGMEDIUM`*lpStgMedia*指向的結構中。 此格式包括粘貼特殊對話方塊所需的資訊。

有關詳細資訊,請參閱 Windows SDK 中的[STGMEDIUM。](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)

## <a name="coleserveritemisconnected"></a><a name="isconnected"></a>COleServer 專案:已連接

呼叫此函數以查看 OLE 項是否已連接。

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>傳回值

如果專案已連接,則非零;否則 0。

### <a name="remarks"></a>備註

如果一個或多個容器對該專案具有引用,則 OLE 項被視為已連接。 如果項的引用計數大於 0 或是嵌入項,則連接該項。

## <a name="coleserveritemislinkeditem"></a><a name="islinkeditem"></a>COleServer 專案:是連結專案

呼叫此函數以查看 OLE 項是否為連結項。

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>傳回值

如果項是連結項,則非零;否則 0。

### <a name="remarks"></a>備註

如果項有效且未在文檔中的嵌入項清單中返回,則項將連結。 連結的項可能已連接到容器,也可能未連接到容器。

對於連結和嵌入項使用相同的類是很常見的。 `IsLinkedItem`允許您使連結項的行為方式與嵌入項不同,儘管代碼多次常見。

## <a name="coleserveritemm_sizeextent"></a><a name="m_sizeextent"></a>COleServer專案:m_sizeExtent

此成員告訴伺服器容器文檔中有多少物件可見。

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>備註

[OnSetA.的](#onsetextent)預設實現將設定此成員。

## <a name="coleserveritemnotifychanged"></a><a name="notifychanged"></a>COleServer 專案:通知已變更

更改連結項後調用此函數。

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>參數

*nDrawAspect*<br/>
DVASPECT 枚舉中的值,指示 OLE 項的哪個方面已更改。 這個參數可以有以下任何的值：

- DVASPECT_CONTENT項的表示方式可以將其顯示為容器內的嵌入物件。

- DVASPECT_THUMBNAIL專案以「縮略圖」表示形式呈現,以便它可以顯示在流覽工具中。

- DVASPECT_ICON項由圖示表示。

- DVASPECT_DOCPRINT項表示,就好像它是使用「檔」功能表中的「列印」命令一樣。

### <a name="remarks"></a>備註

如果容器項連結到具有自動連結的文檔,則該項將更新以反映更改。 在使用 Microsoft 基礎類庫編寫的容器應用程式中[,COleClientItem:onChange](../../mfc/reference/coleclientitem-class.md#onchange)是回應呼叫的。

## <a name="coleserveritemondoverb"></a><a name="ondoverb"></a>COleServer專案:OnDoVerb

由框架調用以執行指定的謂詞。

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
指定要執行的謂詞。 它可以是以下任一項:

|值|意義|符號|
|-----------|-------------|------------|
|0|主動詞命令|OLEIVERB_PRIMARY|
|1|次要動詞|(無)|
|- 1|顯示要編輯的項目|OLEIVERB_SHOW|
|- 2|在單獨視窗編輯項目|OLEIVERB_OPEN|
|- 3|隱藏項目|OLEIVERB_HIDE|

-1 值通常是另一個謂詞的別名。 如果不支援打開編輯,-2 的效果與 -1 相同。 有關其他值,請參閱 Windows SDK 中的[IOleObject::DoVerb。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)

### <a name="remarks"></a>備註

如果容器應用程式是使用 Microsoft 基礎類庫編寫的,則當調用相應物件的[COleClientItem::啟動](../../mfc/reference/coleclientitem-class.md#activate)相應`COleClientItem`物件的成員函數時,將調用此函數。 如果指定了主謂詞或OLEIVERB_SHOW,則預設實現將調用[OnShow](#onshow)成員函數;指定輔助謂詞或OLEIVERB_OPEN時[打開](#onopen);如果指定了OLEIVERB_HIDE,則[調用 OnHide。](#onhide) 如果`OnShow`*iVerb*不是上面列出的動詞之一,則默認實現將調用。

如果主動詞不顯示該專案,請覆蓋此函數。 例如,如果項是錄音,並且其主要謂詞是"播放",則不必顯示伺服器應用程式來播放該專案。

有關詳細資訊,請參閱 Windows SDK 中的[IOleObject::DoVerb。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)

## <a name="coleserveritemondraw"></a><a name="ondraw"></a>COleServer專案:在畫上

由框架呼叫,以將 OLE 選項呈現為元檔。

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向要在其中繪製項的[CDC](../../mfc/reference/cdc-class.md)物件的指標。 顯示上下文會自動連接到屬性顯示上下文,因此您可以調用屬性函數,儘管這樣做會使元文件設備特定於。

*rSize*<br/>
大小,以 HIMETRIC 單位表示,用於繪製元檔。

### <a name="return-value"></a>傳回值

如果專案已成功繪製,則非零;否則 0。

### <a name="remarks"></a>備註

OLE 項的元檔表示形式用於在容器應用程式中顯示該專案。 如果容器應用程式是使用 Microsoft 基礎類庫編寫的,則元檔由相應[COleClientItem](../../mfc/reference/coleclientitem-class.md)物件的[Draw](../../mfc/reference/coleclientitem-class.md#draw)成員函數使用。 沒有預設的實作。 必須重寫此函數才能將項繪製到指定的設備上下文中。

## <a name="coleserveritemondrawex"></a><a name="ondrawex"></a>COleServer專案:OnDrawEx

由所有繪圖的框架調用。

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向要在其中繪製項的[CDC](../../mfc/reference/cdc-class.md)物件的指標。 DC 會自動連接到屬性 DC,因此您可以調用屬性函數,儘管這樣做會使元檔設備特定於。

*nDrawAspect*<br/>
DVASPECT 枚舉中的值。 這個參數可以有以下任何的值：

- DVASPECT_CONTENT項的表示方式可以將其顯示為容器內的嵌入物件。

- DVASPECT_THUMBNAIL專案以「縮略圖」表示形式呈現,以便它可以顯示在流覽工具中。

- DVASPECT_ICON項由圖示表示。

- DVASPECT_DOCPRINT項表示,就好像它是使用「檔」功能表中的「列印」命令一樣。

*rSize*<br/>
物料的大小(以 HIMETRIC 單位為單位)。

### <a name="return-value"></a>傳回值

如果專案已成功繪製,則非零;否則 0。

### <a name="remarks"></a>備註

當 DVASPECT`OnDraw`等於DVASPECT_CONTENT時,默認實現調用;否則,它失敗。

重寫此函數以為DVASPECT_CONTENT以外的方面(如DVASPECT_ICON或DVASPECT_THUMBNAIL)提供表示數據。

## <a name="coleserveritemongetclipboarddata"></a><a name="ongetclipboarddata"></a>COleServer 專案:在取得剪貼簿資料

由框架調用,獲取一個`COleDataSource`物件,其中包含通過調用[CopyToClipboard](#copytoclipboard)成員函數在剪貼簿上放置的所有數據。

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>參數

*bInclude 連結*<br/>
如果連結數據應複製到剪貼簿,則將其設置為 TRUE。 如果伺服器應用程式不支援連結,請將此設置為 FALSE。

*lpOffset*<br/>
滑鼠游標與物件原點的偏移量(以像素為單位)。

*lpSize*<br/>
物件的大小(以像素為單位)。

### <a name="return-value"></a>傳回值

指向包含剪貼簿數據的[COleDataSource](../../mfc/reference/coledatasource-class.md)物件的指標。

### <a name="remarks"></a>備註

此函數的預設實現呼叫[GetClipboardData](#getclipboarddata)。

## <a name="coleserveritemongetextent"></a><a name="ongetextent"></a>COleServer 專案:在取得範圍

由框架調用以檢索 OLE 項的大小(以 HIMETRIC 單位為單位)。

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>參數

*nDrawAspect*<br/>
指定要檢索其邊界的 OLE 項的方面。 這個參數可以有以下任何的值：

- DVASPECT_CONTENT項的表示方式可以將其顯示為容器內的嵌入物件。

- DVASPECT_THUMBNAIL專案以「縮略圖」表示形式呈現,以便它可以顯示在流覽工具中。

- DVASPECT_ICON項由圖示表示。

- DVASPECT_DOCPRINT項表示,就好像它是使用「檔」功能表中的「列印」命令一樣。

*rSize*<br/>
引用將接收`CSize`OLE 項大小的物件。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果容器應用程式是使用 Microsoft 基礎類庫編寫的,則當調`COleClientItem`用相應 物件的[GetExtent](../../mfc/reference/coleclientitem-class.md#getextent)成員函數時,將調用此函數。 預設實作不做任何動作。 您必須自己實現它。 如果要在處理 OLE 項大小的請求時執行特殊處理,請覆蓋此函數。

## <a name="coleserveritemonhide"></a><a name="onhide"></a>COleServer 專案:開啟隱藏

由框架調用以隱藏 OLE 項。

```
virtual void OnHide();
```

### <a name="remarks"></a>備註

預設呼叫`COleServerDoc::OnShowDocument( FALSE )`。 該函數還會通知容器 OLE 項已隱藏。 如果要在隱藏 OLE 項時執行特殊處理,則重寫此函數。

## <a name="coleserveritemoninitfromdata"></a><a name="oninitfromdata"></a>COleServer 專案:從資料開啟

由框架呼叫,使用*pDataObject*的內容初始化 OLE 項。

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
指向包含各種格式資料的 OLE 資料物件,用於初始化 OLE 項。

*b創造*<br/>
如果調用函數來初始化容器應用程式新創建的 OLE 項,則為 TRUE。 如果調用函數以替換現有 OLE 項的內容,則 FALSE。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果*b創作*為 TRUE,則如果容器基於當前選擇實現「插入新物件」,則調用此函數。 創建新 OLE 項時,將使用所選數據。 例如,在電子表格程式中選擇單元格區域,然後使用"插入新物件"根據所選範圍內的值創建圖表時。 預設實作不做任何動作。 重寫此函數,從*pDataObject*提供的格式中選擇可接受的格式,並根據提供的數據初始化 OLE 項。 這是一個高級的可重寫。

有關詳細資訊,請參閱[IOleObject::Windows SDK 中的 InitfromData。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata)

## <a name="coleserveritemonopen"></a><a name="onopen"></a>COleServer 專案:開啟

由框架呼叫,以在伺服器應用程式的單獨實例中顯示 OLE 項,而不是就位。

```
virtual void OnOpen();
```

### <a name="remarks"></a>備註

默認實現啟動顯示包含 OLE 項的文件的第一個幀視窗;如果應用程式是微型伺服器,則默認實現將顯示主視窗。 該函數還會通知容器 OLE 項已打開。

如果要在打開 OLE 項時執行特殊處理,則重寫此函數。 這在連結項中尤其常見,您希望在連結打開時將所選內容設置為連結。

有關詳細資訊,請參閱[IOleClientSiteSite:Windows](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) SDK 中的「顯示視窗」。

## <a name="coleserveritemonqueryupdateitems"></a><a name="onqueryupdateitems"></a>COleServer 專案:開啟查詢更新專案

由框架調用以確定當前伺服器文檔中的任何連結項是否已過期。

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>傳回值

如果文檔具有需要更新的專案,則非零;如果所有專案都是最新的,則為 0。

### <a name="remarks"></a>備註

如果專案的源文檔已更改,但連結的項尚未更新以反映文檔中的更改,則項已過期。

## <a name="coleserveritemonrenderdata"></a><a name="onrenderdata"></a>COleServer 專案:在渲染資料上

框架調用以檢索指定格式的數據。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構,指定請求資訊的格式。

*lpStg 中*<br/>
指向要返回數據的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是以前使用`COleDataSource`[延遲渲染數據](../../mfc/reference/coledatasource-class.md#delayrenderdata)或[延遲渲染文件](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)成員函數放置在物件中的格式,用於延遲渲染。 如果提供的儲存媒體是檔案或記憶體,則此函數的預設實現分別調用[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData。](#onrenderglobaldata) 如果未提供這兩種格式,則默認實現返回 0,不執行任何操作。

如果*lpStg 中*-> *tymedTYMED_NULL,STGMEDIUM*應分配和填充,如*lpFormatEtc->tymed*指定。 如果不TYMED_NULL,則 STGMEDIUM 應隨數據一起填充。

這是一個高級的可重寫。 重寫此函數以請求的格式和媒體提供資料。 根據數據的不同,您可能希望重寫此函數的其他版本之一。 如果資料較小且大小固定,請重寫`OnRenderGlobalData`。 如果資料位於檔案中,或大小可變,請重寫`OnRenderFileData`。

有關詳細資訊,請參閱[IDataObject:獲取資料](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)[、STGMEDIUM、FORMATETC](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[TYMED](/windows/win32/api/objidl/ne-objidl-tymed)在 Windows SDK 中。 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)

## <a name="coleserveritemonrenderfiledata"></a><a name="onrenderfiledata"></a>COleServer 專案:在渲染檔案資料上

當存儲媒體是檔時,框架呼叫以指定格式檢索資料。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構,指定請求資訊的格式。

*pFile*<br/>
指向要呈現`CFile`數據的物件。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是以前使用`COleDataSource`[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)成員函數放置在物件中的格式,用於延遲渲染。 此函數的預設實現僅返回 FALSE。

這是一個高級的可重寫。 重寫此函數以請求的格式和媒體提供資料。 根據數據的不同,您可能希望重寫此函數的其他版本之一。 如果要處理多個儲存媒體,則重寫[OnRenderData](#onrenderdata)。 如果資料位於檔案中,或者大小可變,請覆[寫 OnRenderFileData](#onrenderfiledata)。

有關詳細資訊,請參閱[IDataObject:獲取 Windows](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) SDK 中的數據和[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

## <a name="coleserveritemonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleServer專案:在渲染全域資料上

當指定的存儲媒體是全域記憶體時,框架調用以指定格式檢索資料。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構,指定請求資訊的格式。

*phGlobal*<br/>
指向要返回數據的全域記憶體的句柄。 如果未分配記憶體,則此參數可以是 NULL。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

指定的格式是以前使用`COleDataSource`[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)成員函數放置在物件中的格式,用於延遲渲染。 此函數的預設實現僅返回 FALSE。

如果*phGlobal*為 NULL,則應在 phGLOBAL 中分配並返回新的*HGLOBAL。* 否則 *,phGLOBAL*指定的 HGLOBAL 應填充數據。 放置在 HGLOBAL 中的數據量不得超過記憶體區塊的當前大小。 此外,塊無法重新分配到更大的大小。

這是一個高級的可重寫。 重寫此函數以請求的格式和媒體提供資料。 根據數據的不同,您可能希望重寫此函數的其他版本之一。 如果要處理多個儲存媒體,則重寫[OnRenderData](#onrenderdata)。 如果資料位於檔案中,或者大小可變,請覆[寫 OnRenderFileData](#onrenderfiledata)。

有關詳細資訊,請參閱[IDataObject:獲取 Windows](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) SDK 中的數據和[FORMATETC。](/windows/win32/api/objidl/ns-objidl-formatetc)

## <a name="coleserveritemonsetcolorscheme"></a><a name="onsetcolorscheme"></a>COleServer 專案:開啟顏色機制

由框架呼叫以指定在編輯 OLE 項時使用的調色板。

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>參數

*lpLogPalette*<br/>
指向 Windows [LOGPALETTE 結構的指標](/windows/win32/api/wingdi/ns-wingdi-logpalette)。

### <a name="return-value"></a>傳回值

如果使用調色板,則非零;否則 0。

### <a name="remarks"></a>備註

如果容器應用程式是使用 Microsoft 基礎類庫編寫的,則當調`COleClientItem`用相應 物件的[IOleObject:setColorscheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme)函數時,將調用此函數。 預設實現返回 FALSE。 如果要使用建議的調色板,請按一下此函數。 伺服器應用程式不需要使用建議的調色板。

有關詳細資訊,請參閱[IOleObject::在](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme)Windows SDK 中設置顏色方案。

## <a name="coleserveritemonsetdata"></a><a name="onsetdata"></a>COleServer專案:OnSetData

框架調用以將 OLE 項的數據替換為指定數據。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>參數

*lpFormatEtc*<br/>
指向指定數據格式的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)結構的指標。

*lpStg 中*<br/>
指向數據所在的[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)結構的指標。

*b釋放*<br/>
指示誰在完成函數調用後擁有存儲介質的擁有權。 調用方決定由誰負責釋放代表存儲介質分配的資源。 調用方通過設置*bRelease*來進行此用。 如果*bRelease*是非零,則伺服器項將取得擁有權,在介質使用完畢後釋放介質。 當*bRelease*為 0 時,調用方將保留擁有權,並且伺服器項只能在調用期間使用存儲介質。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

伺服器項在成功獲取數據之前不會取得數據的擁有權。 也就是說,如果它返回 0,它不取得擁有權。 如果數據源擁有擁有權,則通過調用[ReleaseStgMedia](/windows/win32/api/ole2/nf-ole2-releasestgmedium)函數釋放存儲介質。

預設實作不做任何動作。 重寫此函數以將 OLE 項的數據替換為指定數據。 這是一個高級的可重寫。

有關詳細資訊,請參閱 Windows SDK 中的[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) [STGMEDIUM、FORMATETC](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)和[發佈StgMedia。](/windows/win32/api/ole2/nf-ole2-releasestgmedium)

## <a name="coleserveritemonsetextent"></a><a name="onsetextent"></a>COleServer 專案:在設定範圍

由框架呼叫,告訴 OLE 檔在容器文件中有多少可用空間。

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>參數

*nDrawAspect*<br/>
指定正在指定其邊界的 OLE 項的方面。 這個參數可以有以下任何的值：

- DVASPECT_CONTENT項的表示方式可以將其顯示為容器內的嵌入物件。

- DVASPECT_THUMBNAIL專案以「縮略圖」表示形式呈現,以便它可以顯示在流覽工具中。

- DVASPECT_ICON項由圖示表示。

- DVASPECT_DOCPRINT項表示,就好像它是使用「檔」功能表中的「列印」命令一樣。

*大小*<br/>
指定 OLE 項新大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果容器應用程式是使用 Microsoft 基礎類庫編寫的,則當調`COleClientItem`用相應 物件的[SetExtent](../../mfc/reference/coleclientitem-class.md#setextent)成員函數時,將調用此函數。 如果*DVASPECT_CONTENT,* 則默認實現將[m_sizeExtent](#m_sizeextent)成員設置為指定大小;否則它返回 0。 重寫此函數以在更改項目大小時執行特殊處理。

## <a name="coleserveritemonshow"></a><a name="onshow"></a>COleServer專案:在展會上

由框架調用,指示伺服器應用程式將 OLE 項顯示到位。

```
virtual void OnShow();
```

### <a name="remarks"></a>備註

當容器應用程式的使用者創建項或執行需要顯示項的謂詞(如 Edit)時,通常會調用此函數。 默認實現嘗試就地啟動。 如果失敗,該函數將調用`OnOpen`成員函數以在單獨的視窗中顯示 OLE 項。

如果要在顯示 OLE 項時執行特殊處理,則重寫此函數。

## <a name="coleserveritemonupdate"></a><a name="onupdate"></a>COleServer專案:更新

修改項時由框架調用。

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>參數

*pSender*<br/>
指向修改文件的項的指標。 可以是 NULL。

*lHint*<br/>
包含有關修改的資訊。

*pHint*<br/>
指向存儲有關修改資訊的物件的指標。

*nDrawAspect*<br/>
DVASPECT 枚舉中的值。 這個參數可以具有以下任一值:

- DVASPECT_CONTENT項的表示方式可以將其顯示為容器內的嵌入物件。

- DVASPECT_THUMBNAIL專案以「縮略圖」表示形式呈現,以便它可以顯示在流覽工具中。

- DVASPECT_ICON項由圖示表示。

- DVASPECT_DOCPRINT項表示,就好像它是使用「檔」功能表中的「列印」命令一樣。

### <a name="remarks"></a>備註

默認實現調用[Notify 更改](#notifychanged),無論提示或寄件者。

## <a name="coleserveritemonupdateitems"></a><a name="onupdateitems"></a>COleServer專案:更新專案

由框架調用以更新伺服器文件中的所有項。

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>備註

預設實現調用文件中所有`COleClientItem`物件的[UpdateLink。](../../mfc/reference/coleclientitem-class.md#updatelink)

## <a name="coleserveritemsetitemname"></a><a name="setitemname"></a>COleServer 專案:設定項目名稱

創建連結項以設置其名稱時調用此函數。

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>參數

*lpszItem名稱*<br/>
指向項的新名稱的指標。

### <a name="remarks"></a>備註

名稱在文檔中必須是唯一的。 當調用伺服器應用程式編輯連結項時,應用程式使用此名稱來查找該專案。 不需要為嵌入項調用此函數。

## <a name="see-also"></a>另請參閱

[MFC 樣品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem 類別](../../mfc/reference/cdocitem-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)
