---
title: "COleServerItem 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f56f356de8cb85bb919469a189618220c0843f3d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
  
|名稱|說明|  
|----------|-----------------|  
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|將放在簡報和轉換格式`COleDataSource`物件。|  
|[COleServerItem::CopyToClipboard](#copytoclipboard)|將項目複製到剪貼簿。|  
|[COleServerItem::DoDragDrop](#dodragdrop)|執行拖放作業。|  
|[COleServerItem::GetClipboardData](#getclipboarddata)|取得用於資料傳輸 （拖曳和卸除或剪貼簿） 中的資料來源。|  
|[COleServerItem::GetDocument](#getdocument)|傳回包含之項目的伺服器文件。|  
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|取得**CF_EMBEDSOURCE** OLE 項目的資料。|  
|[COleServerItem::GetItemName](#getitemname)|傳回項目的名稱。 用於連結項目。|  
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|取得`CF_LINKSOURCE`OLE 項目的資料。|  
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|取得**CF_OBJECTDESCRIPTOR** OLE 項目的資料。|  
|[COleServerItem::IsConnected](#isconnected)|指出是否此項目目前已連結至使用中的容器。|  
|[COleServerItem::IsLinkedItem](#islinkeditem)|指出項目是否代表連結的 OLE 項目。|  
|[COleServerItem::NotifyChanged](#notifychanged)|使用自動連結更新，更新所有容器。|  
|[COleServerItem::OnDoVerb](#ondoverb)|呼叫以執行動詞命令。|  
|[Coleserveritem:: Ondraw](#ondraw)|若要繪製項目; 要求的容器時呼叫所需的實作。|  
|[COleServerItem::OnDrawEx](#ondrawex)|針對特定的項目繪製呼叫。|  
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|由架構呼叫以取得的資料，將會複製到剪貼簿。|  
|[COleServerItem::OnGetExtent](#ongetextent)|由架構呼叫以擷取 OLE 項目的大小。|  
|[COleServerItem::OnInitFromData](#oninitfromdata)|由架構呼叫以初始化 OLE 項目使用指定的資料傳輸物件的內容。|  
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|呼叫以判斷是否需要更新任何連結的項目。|  
|[COleServerItem::OnRenderData](#onrenderdata)|擷取資料做為延遲轉譯的一部分。|  
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|擷取資料到`CFile`一部分延遲轉譯的物件。|  
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|擷取資料到`HGLOBAL`延遲轉譯的一部分。|  
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|呼叫以設定項目的色彩配置。|  
|[COleServerItem::OnSetData](#onsetdata)|呼叫以設定項目的資料。|  
|[COleServerItem::OnSetExtent](#onsetextent)|由架構呼叫以設定的 OLE 項目大小。|  
|[COleServerItem::OnUpdate](#onupdate)|呼叫中的某些部分的文件項目所屬時已變更。|  
|[COleServerItem::OnUpdateItems](#onupdateitems)|呼叫以更新簡報的快取伺服器文件中的所有項目。|  
|[COleServerItem::SetItemName](#setitemname)|設定項目的名稱。 用於連結項目。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleServerItem::GetDataSource](#getdatasource)|取得用來儲存轉換格式的物件。|  
|[COleServerItem::OnHide](#onhide)|由架構呼叫以隱藏 OLE 項目。|  
|[COleServerItem::OnOpen](#onopen)|由架構呼叫以其最上層的視窗中顯示 OLE 項目。|  
|[COleServerItem::OnShow](#onshow)|當容器要求顯示項目時呼叫。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[COleServerItem::m_sizeExtent](#m_sizeextent)|告知伺服器有多少 OLE 項目可見。|  
  
## <a name="remarks"></a>備註  
 部分或所有的伺服器文件，可以表示連結的項目。 內嵌項目永遠代表整個伺服器文件。  
  
 `COleServerItem`類別會定義由 OLE 系統動態連結程式庫 (Dll)，所呼叫的幾個可覆寫成員函式通常是為了回應容器應用程式要求。 這些成員函式可讓容器應用程式，來顯示它、 執行其動詞命令，或者以各種格式資料擷取，例如操作間接地以各種方式的項目。  
  
 若要使用`COleServerItem`、 衍生的類別和實作[OnDraw](#ondraw)和[序列化](../../mfc/reference/cobject-class.md#serialize)成員函式。 `OnDraw`函式提供的項目，讓它可以開啟 複合文件容器應用程式時，會顯示中繼檔表示法。 `Serialize`函式的`CObject`提供項目，讓內嵌項目之間的伺服器和容器應用程式傳輸的原生表示法。 [OnGetExtent](#ongetextent)提供自然的容器，啟用 調整大小之項目的容器項目大小。  
  
 如需伺服器和相關的主題的詳細資訊，請參閱文章[伺服器： 實作伺服器](../../mfc/servers-implementing-a-server.md)和 「 建立容器/伺服器應用程式 」 文章中[容器： 進階功能](../../mfc/containers-advanced-features.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleServerItem`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="addotherclipboarddata"></a>COleServerItem::AddOtherClipboardData  
 呼叫此函式，將 OLE 項目展示和轉換格式中指定`COleDataSource`物件。  
  
```  
void AddOtherClipboardData(COleDataSource* pDataSource);
```  
  
### <a name="parameters"></a>參數  
 `pDataSource`  
 指標`COleDataSource`物件存放至應放置資料。  
  
### <a name="remarks"></a>備註  
 您必須實作[OnDraw](#ondraw)提供項目的呈現格式 （中繼檔圖片） 的成員函式。 若要支援其他轉換格式，註冊它們使用[COleDataSource](../../mfc/reference/coledatasource-class.md)所傳回物件[GetDataSource](#getdatasource)並覆寫[OnRenderData](#onrenderdata)成員函式提供您想要支援的格式資料。  
  
##  <a name="coleserveritem"></a>COleServerItem::COleServerItem  
 建構`COleServerItem`物件，並將它加入至伺服器文件的文件項目集合。  
  
```  
COleServerItem(
    COleServerDoc* pServerDoc,  
    BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>參數  
 `pServerDoc`  
 文件會包含新項目的指標。  
  
 `bAutoDelete`  
 表示在發行的連結時，是否可以刪除物件旗標。 將此設**FALSE**如果`COleServerItem`物件是您必須刪除您的文件資料中不可或缺的一部分。 將此設**TRUE**如果物件是用來識別文件的資料可以刪除架構中的範圍的第二個結構。  
  
##  <a name="copytoclipboard"></a>COleServerItem::CopyToClipboard  
 呼叫此函式可將 OLE 項目複製到剪貼簿。  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bIncludeLink`  
 將此設**TRUE**如果連結資料應該複製到剪貼簿。 將此設**FALSE**如果伺服器應用程式不支援的連結。  
  
### <a name="remarks"></a>備註  
 此函數會使用[ongetclipboarddata 而自動發生](#ongetclipboarddata)成員函式來建立[COleDataSource](../../mfc/reference/coledatasource-class.md)物件，其中包含支援的格式中的 OLE 項目的資料。 然後將函數放`COleDataSource`物件上使用剪貼簿[COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函式。 `COleDataSource`物件包含的項目原生資料及它在中的表示`CF_METAFILEPICT`格式，以及任何您選擇支援的轉換格式的資料。 您必須實作[序列化](../../mfc/reference/cobject-class.md#serialize)和[OnDraw](#ondraw)運作此成員函式。  
  
##  <a name="dodragdrop"></a>COleServerItem::DoDragDrop  
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
 *lpRectItem*  
 在畫面上，以像素為單位，相對於用戶端區域中的項目矩形。  
  
 `ptOffset`  
 從位移`lpItemRect`滑鼠位置在拖曳時的所在。  
  
 `bIncludeLink`  
 將此設**TRUE**如果連結資料應該複製到剪貼簿。 將它設定為**FALSE**如果您的應用程式不支援的連結。  
  
 `dwEffects`  
 決定拖曳來源將允許在拖曳作業 （複製、 移動和連結的組合） 中的效果。  
  
 `lpRectStartDrag`  
 實際開始拖曳所定義的矩形的指標。 如需詳細資訊，請參閱接下來的＜備註＞一節。  
  
### <a name="return-value"></a>傳回值  
 `DROPEFFECT` 列舉中的值。 如果是`DROPEFFECT_MOVE`，應該移除原始的資料。  
  
### <a name="remarks"></a>備註  
 拖放作業不會立即啟動。 它會等候直到滑鼠游標離開所指定的矩形`lpRectStartDrag`，或是直到已通過指定的毫秒數。 如果`lpRectStartDrag`是**NULL**，使用預設矩形，因此拖曳開始，當滑鼠游標移一個像素。  
  
 登錄機碼設定所指定的延遲時間。 您可以藉由呼叫變更的延遲時間[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果您未指定延遲時間，會使用預設值是 200 毫秒。 拖放到延遲時間會儲存，如下所示：  
  
-   Windows NT 拖曳延遲時間會儲存在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。  
  
-   Win 儲存 Windows 3.x 拖曳延遲時間。INI 檔案，底下的 [Windows} 一節。  
  
-   Windows 95/98 拖曳延遲時間會儲存在 WIN 的快取版本。INI。  
  
 如需有關如何將延遲的資訊會儲存在登錄或。INI 檔案，請參閱[WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) Windows SDK 中。  
  
##  <a name="getclipboarddata"></a>COleServerItem::GetClipboardData  
 呼叫此函式，以填滿指定[COleDataSource](../../mfc/reference/coledatasource-class.md)物件會複製到剪貼簿中，如果您呼叫的所有資料[CopyToClipboard](#copytoclipboard) (會也會傳送相同的資料，如果您呼叫[DoDragDrop](#dodragdrop))。  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDataSource`  
 指標`COleDataSource`會在所有支援的格式接收 OLE 項目資料的物件。  
  
 `bIncludeLink`  
 **TRUE**如果連結資料應該複製到剪貼簿。 **FALSE**如果伺服器應用程式不支援的連結。  
  
 `lpOffset`  
 以像素的原始物件的滑鼠游標的位移。  
  
 `lpSize`  
 物件，像素為單位的大小。  
  
### <a name="remarks"></a>備註  
 此函數會呼叫[GetEmbedSourceData](#getembedsourcedata)成員函式來取得原生資料的 OLE 項目並呼叫[AddOtherClipboardData](#addotherclipboarddata)成員函式可取得的呈現格式，以及任何支援的轉換格式。 如果`bIncludeLink`是**TRUE**，函式也會呼叫[GetLinkSourceData](#getlinksourcedata)取得項目的連結資料。  
  
 覆寫這個函式，如果您想要放入格式`COleDataSource`物件之前或之後所提供的這些格式`CopyToClipboard`。  
  
##  <a name="getdatasource"></a>COleServerItem::GetDataSource  
 呼叫此函式可取得[COleDataSource](../../mfc/reference/coledatasource-class.md)用來儲存伺服器應用程式支援的轉換格式的物件。  
  
```  
COleDataSource* GetDataSource();
```  
  
### <a name="return-value"></a>傳回值  
 指標`COleDataSource`用來儲存轉換格式的物件。  
  
### <a name="remarks"></a>備註  
 如果您想伺服器應用程式的作業資料傳輸期間提供各種格式的資料時，註冊這些格式與`COleDataSource`此函數所傳回的物件。 例如，如果您想要提供**CF_TEXT**剪貼簿或拖放作業的 OLE 項目表示，您會註冊與格式`COleDataSource`此函數會傳回的物件，然後再覆寫**OnRenderXxxData**成員函式提供的資料。  
  
##  <a name="getdocument"></a>COleServerItem::GetDocument  
 呼叫此函式可取得包含項目的文件的指標。  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指向文件，其中包含項目。**NULL**如果項目不是文件的一部分。  
  
### <a name="remarks"></a>備註  
 這可讓您傳遞的引數為伺服器文件的存取`COleServerItem`建構函式。  
  
##  <a name="getembedsourcedata"></a>COleServerItem::GetEmbedSourceData  
 呼叫此函式可取得**CF_EMBEDSOURCE** OLE 項目的資料。  
  
```  
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>參數  
 `lpStgMedium`  
 指標[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構，將會收到**CF_EMBEDSOURCE** OLE 項目的資料。  
  
### <a name="remarks"></a>備註  
 此格式包含的項目原生資料。 您必須實作`Serialize`成員函式，這個函式才能正常運作。  
  
 結果可以再加入至資料來源使用[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 此函式就會呼叫自動[COleServerItem::OnGetClipboardData](#ongetclipboarddata)。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) Windows SDK 中。  
  
##  <a name="getitemname"></a>COleServerItem::GetItemName  
 呼叫此函式可取得的項目名稱。  
  
```  
const CString& GetItemName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 項目的名稱。  
  
### <a name="remarks"></a>備註  
 您通常會呼叫此函式僅為連結的項目。  
  
##  <a name="getlinksourcedata"></a>COleServerItem::GetLinkSourceData  
 呼叫此函式可取得`CF_LINKSOURCE`OLE 項目的資料。  
  
```  
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>參數  
 `lpStgMedium`  
 指標[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構，將會收到`CF_LINKSOURCE`OLE 項目的資料。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此格式包含描述 OLE 項目和尋找文件包含 OLE 項目所需的資訊類型的 CLSID。  
  
 結果可以再加入至資料來源與[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 此函式就會呼叫自動[ongetclipboarddata 而自動發生](#ongetclipboarddata)。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) Windows SDK 中。  
  
##  <a name="getobjectdescriptordata"></a>COleServerItem::GetObjectDescriptorData  
 呼叫此函式可取得**CF_OBJECTDESCRIPTOR** OLE 項目的資料。  
  
```  
void GetObjectDescriptorData(
    LPPOINT lpOffset,  
    LPSIZE lpSize,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>參數  
 `lpOffset`  
 從 OLE 項目左上角，按一下滑鼠的位移。 可以是**NULL**。  
  
 `lpSize`  
 OLE 項目的大小。 可以是**NULL**。  
  
 `lpStgMedium`  
 指標[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構，將會收到**CF_OBJECTDESCRIPTOR** OLE 項目的資料。  
  
### <a name="remarks"></a>備註  
 將資訊複製到**STGMEDIUM**結構所指`lpStgMedium`。 此格式包含貼上 對話方塊所需的資訊。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) Windows SDK 中。  
  
##  <a name="isconnected"></a>COleServerItem::IsConnected  
 呼叫此函式，以查看是否已連接 OLE 項目。  
  
```  
BOOL IsConnected() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果項目都會連接;否則便是 0。  
  
### <a name="remarks"></a>備註  
 OLE 項目會被視為已連接一或多個容器有項目的參考。 如果參考計數大於 0，或者它是內嵌的項目，項目都會連接。  
  
##  <a name="islinkeditem"></a>COleServerItem::IsLinkedItem  
 呼叫此函式的 OLE 項目是否為連結的項目。  
  
```  
BOOL IsLinkedItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果項目連結的項目。否則便是 0。  
  
### <a name="remarks"></a>備註  
 項目會連結項目有效，且不會傳回文件的內嵌項目清單中。 連結的項目可能會或可能未連線至容器。  
  
 它會使用相同的類別連結和內嵌的項目。 `IsLinkedItem`可讓您進行的行為模式不同內嵌的項目連結的項目，雖然許多次的程式碼很常見。  
  
##  <a name="m_sizeextent"></a>COleServerItem::m_sizeExtent  
 這個成員會要求伺服器物件中有多少會顯示在容器文件中。  
  
```  
CSize m_sizeExtent;  
```  
  
### <a name="remarks"></a>備註  
 預設實作[OnSetExtent](#onsetextent)設定這個成員。  
  
##  <a name="notifychanged"></a>COleServerItem::NotifyChanged  
 變更連結的項目之後，請呼叫此函式。  
  
```  
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>參數  
 `nDrawAspect`  
 中的值`DVASPECT`列舉，指出哪些方面的 OLE 項目已變更。 這個參數可以具有下列值之一：  
  
- `DVASPECT_CONTENT`項目表示的方式，它可以顯示為其容器內部內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目會以圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [列印] 命令，從 [檔案] 功能表來列印。  
  
### <a name="remarks"></a>備註  
 如果容器項目連結至文件之自動連結，則項目會更新以反映變更。 在容器應用程式中使用 Microsoft Foundation 類別庫中，撰寫[COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange)呼叫以回應。  
  
##  <a name="ondoverb"></a>COleServerItem::OnDoVerb  
 由架構呼叫以執行指定的動詞。  
  
```  
virtual void OnDoVerb(LONG iVerb);
```  
  
### <a name="parameters"></a>參數  
 `iVerb`  
 指定要執行的指令動詞。 它可以是下列其中一項動作：  
  
|值|意義|符號|  
|-----------|-------------|------------|  
|0|主動詞命令|`OLEIVERB_PRIMARY`|  
|1|次要的動詞命令|(無)|  
|- 1|顯示編輯項目|`OLEIVERB_SHOW`|  
|- 2|編輯在個別視窗中的項目|`OLEIVERB_OPEN`|  
|- 3|隱藏項目|`OLEIVERB_HIDE`|  
  
 -1 值通常是另一個動詞命令的別名。 如果不支援開啟編輯，-2 會有相同的效果為-1。 如需其他值，請參閱[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) Windows SDK 中。  
  
### <a name="remarks"></a>備註  
 如果容器應用程式已撰寫與 Mfc 程式庫，此函式時，會呼叫[COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate)成員函式對應`COleClientItem`稱為物件。 預設實作會呼叫[OnShow](#onshow)成員函式，如果主要動詞或`OLEIVERB_SHOW`指定，則[OnOpen](#onopen)如果次要動作或`OLEIVERB_OPEN`指定，則和[OnHide](#onhide)如果`OLEIVERB_HIDE`指定。 預設實作會呼叫`OnShow`如果`iVerb`不是其中一個上面所列的動詞命令。  
  
 如果您主要的動詞命令不會顯示項目，請覆寫這個函式。 例如，如果項目是音效錄製，而且其主要動作是播放，您會沒有顯示伺服器應用程式播放該項目。  
  
 如需詳細資訊，請參閱[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) Windows SDK 中。  
  
##  <a name="ondraw"></a>Coleserveritem:: Ondraw  
 由架構呼叫以在中繼檔轉譯 OLE 項目。  
  
```  
virtual BOOL OnDraw(
    CDC* pDC,  
    CSize& rSize) = 0;  
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指標[CDC](../../mfc/reference/cdc-class.md)物件在其上繪製項目。 顯示內容會自動連接到的屬性顯示的內容讓您可以呼叫屬性函式，雖然這樣做會讓中繼檔裝置特定。  
  
 `rSize`  
 調整大小，請在**HIMETRIC**單位，在其中繪製中繼檔。  
  
### <a name="return-value"></a>傳回值  
 如果已經成功地繪製項目; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 OLE 項目的中繼檔表示法用來顯示容器應用程式中的項目。 如果容器應用程式使用 Microsoft Foundation 類別庫所撰寫，便會使用中繼檔[繪製](../../mfc/reference/coleclientitem-class.md#draw)成員函式對應[COleClientItem](../../mfc/reference/coleclientitem-class.md)物件。 沒有預設的實作。 您必須覆寫此函式可繪製到指定的裝置內容的項目。  
  
##  <a name="ondrawex"></a>COleServerItem::OnDrawEx  
 所有的繪圖架構呼叫。  
  
```  
virtual BOOL OnDrawEx(
    CDC* pDC,  
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指標[CDC](../../mfc/reference/cdc-class.md)物件在其上繪製項目。 DC 會自動連接到 DC 的屬性，您可以呼叫屬性函式，雖然這樣做會讓中繼檔裝置特定。  
  
 `nDrawAspect`  
 `DVASPECT` 列舉中的值。 這個參數可以具有下列值之一：  
  
- `DVASPECT_CONTENT`項目表示的方式，它可以顯示為其容器內部內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目會以圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [列印] 命令，從 [檔案] 功能表來列印。  
  
 `rSize`  
 中的項目大小**HIMETRIC**單位。  
  
### <a name="return-value"></a>傳回值  
 如果已經成功地繪製項目; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`OnDraw`時`DVASPECT`等於`DVASPECT_CONTENT`; 否則會失敗。  
  
 覆寫此函數來提供簡報資料層面以外`DVASPECT_CONTENT`，例如`DVASPECT_ICON`或`DVASPECT_THUMBNAIL`。  
  
##  <a name="ongetclipboarddata"></a>COleServerItem::OnGetClipboardData  
 由架構呼叫以取得`COleDataSource`物件，其中包含會將呼叫放置在剪貼簿的所有資料[CopyToClipboard](#copytoclipboard)成員函式。  
  
```  
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,  
    LPPOINT lpOffset,  
    LPSIZE lpSize);
```  
  
### <a name="parameters"></a>參數  
 `bIncludeLink`  
 將此設**TRUE**如果連結資料應該複製到剪貼簿。 將此設**FALSE**如果伺服器應用程式不支援的連結。  
  
 `lpOffset`  
 從原點的物件，像素為單位的滑鼠游標的位移。  
  
 `lpSize`  
 物件，像素為單位的大小。  
  
### <a name="return-value"></a>傳回值  
 指標[COleDataSource](../../mfc/reference/coledatasource-class.md)包含剪貼簿資料物件。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會呼叫[GetClipboardData](#getclipboarddata)。  
  
##  <a name="ongetextent"></a>COleServerItem::OnGetExtent  
 由架構呼叫以擷取中的大小， **HIMETRIC**單位 OLE 項目。  
  
```  
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>參數  
 `nDrawAspect`  
 指定要擷取其界限的 OLE 項目的外觀。 這個參數可以具有下列值之一：  
  
- `DVASPECT_CONTENT`項目表示的方式，它可以顯示為其容器內部內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目會以圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [列印] 命令，從 [檔案] 功能表來列印。  
  
 `rSize`  
 若要參考`CSize`將會收到的 OLE 項目大小的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果容器應用程式已撰寫與 Mfc 程式庫，此函式時，會呼叫[GetExtent](../../mfc/reference/coleclientitem-class.md#getextent)成員函式對應`COleClientItem`稱為物件。 預設實作不做任何動作。 您必須實作它自己。 如果您想要執行特殊處理，當處理要求的 OLE 項目的大小，請覆寫這個函式。  
  
##  <a name="onhide"></a>COleServerItem::OnHide  
 由架構呼叫以隱藏 OLE 項目。  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>備註  
 預設會呼叫**COleServerDoc::OnShowDocument (FALSE)**。 此函式也會告知容器已隱藏 OLE 項目。 如果您想要隱藏 OLE 項目會執行特殊處理，請覆寫這個函式。  
  
##  <a name="oninitfromdata"></a>COleServerItem::OnInitFromData  
 由架構呼叫以初始化 OLE 項目使用的內容`pDataObject`。  
  
```  
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,  
    BOOL bCreation);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 OLE 資料物件包含各種格式來初始化 OLE 項目中的資料指標。  
  
 `bCreation`  
 **TRUE**如果函式會呼叫以初始化 OLE 項目所新建立的容器應用程式。 **FALSE**如果呼叫的函式取代現有的 OLE 項目內容。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`bCreation`是**TRUE**，如果容器實作插入新根據目前的選取範圍的物件，呼叫此函式。 建立新的 OLE 項目時，會使用選取的資料。 比方說，當在試算表程式中選取資料格範圍，然後使用 建立圖表的 插入新物件基礎的選取範圍中的值。 預設實作不做任何動作。 覆寫此函式可從所提供的選擇可接受的格式`pDataObject`和初始化 OLE 項目，根據提供的資料。 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) Windows SDK 中。  
  
##  <a name="onopen"></a>COleServerItem::OnOpen  
 由架構呼叫以顯示 OLE 項目，個別的執行個體的伺服器應用程式中，而不是就地。  
  
```  
virtual void OnOpen();
```  
  
### <a name="remarks"></a>備註  
 預設實作會啟動第一個框架視窗顯示文件，其中包含 OLE 項目。如果迷你伺服器應用程式，預設實作會顯示在主視窗。 函式也會告知容器已開啟 OLE 項目。  
  
 如果您想要開啟 OLE 項目時執行特殊處理，請覆寫這個函式。 這是使用連結的項目，您要將選項設定為連結開啟時特別常見。  
  
 如需詳細資訊，請參閱[IOleClientSite::OnShowWindow](http://msdn.microsoft.com/library/windows/desktop/ms688658) Windows SDK 中。  
  
##  <a name="onqueryupdateitems"></a>COleServerItem::OnQueryUpdateItems  
 由架構呼叫以判斷目前的伺服器文件中任何連結的項目是否已過期。  
  
```  
virtual BOOL OnQueryUpdateItems();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果文件項目需要更新。如果所有項目是最新狀態是 0。  
  
### <a name="remarks"></a>備註  
 如果已變更其來源文件，但連結的項目尚未更新來反映文件中的變更，項目已過期。  
  
##  <a name="onrenderdata"></a>COleServerItem::OnRenderData  
 由架構呼叫以擷取指定格式的資料。  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，指定用來要求資訊的格式。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)資料所要傳回的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)或[DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)延遲轉譯的成員函式。 此函式的預設實作會呼叫[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)分別，如果提供的儲存體中的檔案或記憶體。 如果這些格式都不提供，預設會傳回 0 與實作不做任何動作。  
  
 如果`lpStgMedium` ->  *tymed*是**TYMED_NULL**、 **STGMEDIUM**應該配置，以及所指定的填滿*lpFormatEtc->tymed*。 如果沒有**TYMED_NULL**、 **STGMEDIUM**應填入資料的位置。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可以改為覆寫這個函式的其他版本的其中一個。 如果您的資料是小型且固定的大小，會覆寫`OnRenderGlobalData`。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。  
  
 如需詳細資訊，請參閱[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)， [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)， [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)，和[TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) Windows SDK 中。  
  
##  <a name="onrenderfiledata"></a>COleServerItem::OnRenderFileData  
 由架構呼叫以擷取指定的格式中的資料儲存媒體為檔案時。  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，指定用來要求資訊的格式。  
  
 `pFile`  
 指向`CFile`資料為呈現的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回**FALSE**。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可以改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存媒體，覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫[OnRenderFileData](#onrenderfiledata)。  
  
 如需詳細資訊，請參閱[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="onrenderglobaldata"></a>COleServerItem::OnRenderGlobalData  
 由架構呼叫以時指定的儲存體中是全域記憶體擷取資料，以指定的格式。  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，指定用來要求資訊的格式。  
  
 `phGlobal`  
 指向全域記憶體資料所要傳回的控制代碼。 如果已不配置任何記憶體，這個參數可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回**FALSE**。  
  
 如果`phGlobal`是**NULL**，然後新`HGLOBAL`應該配置並傳回`phGlobal`。 否則，`HGLOBAL`所指定`phGlobal`應填入資料。 資料量置於`HGLOBAL`不能超過目前的記憶體區塊大小。 此外，無法重新配置較大的區塊。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可以改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存媒體，覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫[OnRenderFileData](#onrenderfiledata)。  
  
 如需詳細資訊，請參閱[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="onsetcolorscheme"></a>COleServerItem::OnSetColorScheme  
 由架構呼叫以指定編輯 OLE 項目時所要使用的色彩調色盤。  
  
```  
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```  
  
### <a name="parameters"></a>參數  
 `lpLogPalette`  
 指標的 windows [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)結構。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果使用的色彩調色盤。否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果容器應用程式使用 Microsoft Foundation 類別庫所撰寫，此函式時，會呼叫[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971)函式對應`COleClientItem`稱為物件。 預設實作會傳回**FALSE**。 如果您想要使用建議的調色盤，請覆寫這個函式。 伺服器應用程式不需要使用建議的調色盤。  
  
 如需詳細資訊，請參閱[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) Windows SDK 中。  
  
##  <a name="onsetdata"></a>COleServerItem::OnSetData  
 由架構呼叫以將 OLE 項目的資料取代為指定的資料。  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，指定資料的格式。  
  
 `lpStgMedium`  
 指標[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構中資料的所在。  
  
 `bRelease`  
 指出誰完成函式呼叫後之儲存媒體的擁有權。 呼叫端決定誰負責釋放之儲存媒體代表配置的資源。 呼叫端會藉由設定`bRelease`。 如果`bRelease`為非零，伺服器項目取得擁有權，使用它完成時釋放媒體。 當`bRelease`是 0，呼叫端保留擁有權，伺服器項目可以只針對在呼叫期間使用之儲存媒體。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 伺服器項目不會擁有權的資料，直到它成功取得它。 也就是說，它不會擁有權如果它會傳回 0。 如果資料來源取得擁有權，才會釋出儲存媒體藉由呼叫[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)函式。  
  
 預設實作不做任何動作。 覆寫此函式可將 OLE 項目的資料取代為指定的資料。 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)， [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)，和[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) Windows SDK 中。  
  
##  <a name="onsetextent"></a>COleServerItem::OnSetExtent  
 由架構呼叫以告知 OLE 項目多少空間是在容器文件中可。  
  
```  
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,  
    const CSize& size);
```  
  
### <a name="parameters"></a>參數  
 `nDrawAspect`  
 指定其界限所指定的 OLE 項目的外觀。 這個參數可以具有下列值之一：  
  
- `DVASPECT_CONTENT`項目表示的方式，它可以顯示為其容器內部內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目會以圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [列印] 命令，從 [檔案] 功能表來列印。  
  
 `size`  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)結構，指定新的 OLE 項目大小。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果容器應用程式已撰寫與 Mfc 程式庫，此函式時，會呼叫[SetExtent](../../mfc/reference/coleclientitem-class.md#setextent)成員函式對應`COleClientItem`稱為物件。 預設實作集[m_sizeExtent](#m_sizeextent)成員為指定的大小如果`nDrawAspect`是`DVASPECT_CONTENT`; 否則它會傳回 0。 覆寫此函式以執行特殊處理，當您變更項目的大小。  
  
##  <a name="onshow"></a>COleServerItem::OnShow  
 由架構呼叫以指示伺服器應用程式，以就地顯示 OLE 項目。  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>備註  
 當容器應用程式使用者建立的項目或執行動作，例如編輯、 通常呼叫此函式要求要顯示的項目。 預設實作會嘗試在就地啟用。 如果這個作業失敗，函式呼叫`OnOpen`成員函式，在個別視窗中顯示 OLE 項目。  
  
 如果您想要執行特殊處理顯示 OLE 項目時，覆寫這個函式。  
  
##  <a name="onupdate"></a>COleServerItem::OnUpdate  
 已修改的項目時由架構呼叫。  
  
```  
virtual void OnUpdate(
    COleServerItem* pSender,  
    LPARAM lHint,  
    CObject* pHint,  
    DVASPECT nDrawAspect);
```  
  
### <a name="parameters"></a>參數  
 `pSender`  
 修改文件的項目指標。 可以是**NULL**。  
  
 `lHint`  
 包含有關修改資訊。  
  
 `pHint`  
 儲存修改的相關資訊的物件指標。  
  
 `nDrawAspect`  
 `DVASPECT` 列舉中的值。 這個參數可以具有下列值之一：  
  
- `DVASPECT_CONTENT`項目表示的方式，它可以顯示為其容器內部內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目會以圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [列印] 命令，從 [檔案] 功能表來列印。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫[NotifyChanged](#notifychanged)，不論提示或寄件者。  
  
##  <a name="onupdateitems"></a>COleServerItem::OnUpdateItems  
 由架構呼叫以更新伺服器文件中的所有項目。  
  
```  
virtual void OnUpdateItems();
```  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫[UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)所有`COleClientItem`文件中的物件。  
  
##  <a name="setitemname"></a>COleServerItem::SetItemName  
 當您建立連結的項目，可將其名稱時，請呼叫此函式。  
  
```  
void SetItemName(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>參數  
 `lpszItemName`  
 項目的新名稱的指標。  
  
### <a name="remarks"></a>備註  
 名稱必須是唯一的文件中。 若要編輯連結的項目呼叫伺服器應用程式時，應用程式會使用此名稱尋找項目。 您不需要呼叫此函式的內嵌項目。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [CDocItem 類別](../../mfc/reference/cdocitem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)   
 [COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)   
 [COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)
