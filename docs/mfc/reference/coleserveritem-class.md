---
title: "COleServerItem 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleServerItem
dev_langs:
- C++
helpviewer_keywords:
- servers, OLE
- OLE server applications, managing server documents
- OLE server applications, server interfaces
- OLE server documents
- COleServerItem class
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 49dd8cc258ebf96c91ac8ff1190f9a830b6bb5ec
ms.lasthandoff: 02/24/2017

---
# <a name="coleserveritem-class"></a>COleServerItem 類別
提供 OLE 項目的伺服器介面。  
  
## <a name="syntax"></a>語法  
  
```  
class COleServerItem : public CDocItem  
```  
  
## <a name="members"></a>Members  
  
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
|[COleServerItem::GetClipboardData](#getclipboarddata)|取得用於資料傳輸 （拖曳和拖放或剪貼簿） 中的資料來源。|  
|[COleServerItem::GetDocument](#getdocument)|傳回包含之項目的伺服器文件。|  
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|取得**CF_EMBEDSOURCE** OLE 項目的資料。|  
|[COleServerItem::GetItemName](#getitemname)|傳回項目的名稱。 用於連結項目。|  
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|取得`CF_LINKSOURCE`OLE 項目的資料。|  
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|取得**CF_OBJECTDESCRIPTOR** OLE 項目的資料。|  
|[COleServerItem::IsConnected](#isconnected)|表示項目目前連接至使用中的容器。|  
|[COleServerItem::IsLinkedItem](#islinkeditem)|表示項目是否表示連結的 OLE 項目。|  
|[COleServerItem::NotifyChanged](#notifychanged)|更新自動連結更新所有容器。|  
|[COleServerItem::OnDoVerb](#ondoverb)|呼叫來執行動作。|  
|[Coleserveritem](#ondraw)|若要繪製項目; 要求的容器時呼叫所需的實作。|  
|[COleServerItem::OnDrawEx](#ondrawex)|針對特定的項目繪製呼叫。|  
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|若要取得的資料，將會複製到剪貼簿架構呼叫。|  
|[COleServerItem::OnGetExtent](#ongetextent)|若要擷取的 OLE 項目大小架構呼叫。|  
|[COleServerItem::OnInitFromData](#oninitfromdata)|呼叫以初始化 OLE 項目使用指定的資料傳輸物件的內容架構。|  
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|呼叫以判斷是否需要更新任何連結的項目。|  
|[COleServerItem::OnRenderData](#onrenderdata)|擷取資料延遲轉譯的一部分。|  
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|擷取資料到`CFile`一部分延遲轉譯的物件。|  
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|擷取資料到`HGLOBAL`延遲轉譯的一部分。|  
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|呼叫以設定項目的色彩配置。|  
|[COleServerItem::OnSetData](#onsetdata)|呼叫以設定項目的資料。|  
|[COleServerItem::OnSetExtent](#onsetextent)|若要設定的 OLE 項目大小架構呼叫。|  
|[COleServerItem::OnUpdate](#onupdate)|呼叫中的某些部分的文件項目所屬時已變更。|  
|[COleServerItem::OnUpdateItems](#onupdateitems)|呼叫更新簡報快取伺服器文件中所有項目。|  
|[COleServerItem::SetItemName](#setitemname)|設定項目的名稱。 用於連結項目。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleServerItem::GetDataSource](#getdatasource)|取得用來儲存轉換格式的物件。|  
|[COleServerItem::OnHide](#onhide)|若要隱藏 OLE 項目架構呼叫。|  
|[COleServerItem::OnOpen](#onopen)|若要在其最上層視窗中顯示 OLE 項目架構呼叫。|  
|[COleServerItem::OnShow](#onshow)|當容器要求顯示項目時呼叫。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[COleServerItem::m_sizeExtent](#m_sizeextent)|OLE 項目中有多少會顯示有關通知伺服器。|  
  
## <a name="remarks"></a>備註  
 部分或所有的伺服器文件，可以表示連結的項目。 內嵌項目永遠代表整個伺服器文件。  
  
 `COleServerItem`類別會定義數個可覆寫成員函式會呼叫 OLE 系統動態連結程式庫 (Dll)，通常以回應要求，從容器應用程式。 這些成員函式可讓容器應用程式，來顯示它、 執行其動詞，或者擷取各種格式的資料，例如操作間接地以各種方式的項目。  
  
 若要使用`COleServerItem`、 衍生的類別和實作[OnDraw](#ondraw)和[序列化](../../mfc/reference/cobject-class.md#serialize)成員函式。 `OnDraw`函式提供的項目，讓它可以開啟 複合文件容器應用程式時所要顯示的中繼檔表示法。 `Serialize`函式的`CObject`提供項目，讓內嵌項目要在伺服器和容器應用程式之間傳輸的原生表示法。 [OnGetExtent](#ongetextent)提供自然的容器，啟用調整大小之項目的容器項目大小。  
  
 如需有關伺服器和相關的主題的詳細資訊，請參閱文章[伺服器︰ 實作伺服器](../../mfc/servers-implementing-a-server.md)和 「 建立容器/伺服器應用程式 > 一文中[容器︰ 進階功能](../../mfc/containers-advanced-features.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleServerItem`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="a-nameaddotherclipboarddataa--coleserveritemaddotherclipboarddata"></a><a name="addotherclipboarddata"></a>COleServerItem::AddOtherClipboardData  
 呼叫此函式，將 OLE 項目展示和轉換格式中指定`COleDataSource`物件。  
  
```  
void AddOtherClipboardData(COleDataSource* pDataSource);
```  
  
### <a name="parameters"></a>參數  
 `pDataSource`  
 指標`COleDataSource`中應該放置資料的物件。  
  
### <a name="remarks"></a>備註  
 您必須實作[OnDraw](#ondraw)提供項目的呈現格式 （中繼檔圖片） 的成員函式。 若要支援其他轉換格式，註冊它們使用[COleDataSource](../../mfc/reference/coledatasource-class.md)所傳回的物件[GetDataSource](#getdatasource)並覆寫[OnRenderData](#onrenderdata)成員函式，以提供您想要支援的格式中的資料。  
  
##  <a name="a-namecoleserveritema--coleserveritemcoleserveritem"></a><a name="coleserveritem"></a>COleServerItem::COleServerItem  
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
 旗標，指出物件是否可刪除的連結時，會釋放。 請設為**FALSE**如果`COleServerItem`物件是您必須刪除文件的資料中不可或缺的一部分。 請設為**TRUE**如果物件是用來識別文件的資料可以刪除架構中某個範圍的第二個結構。  
  
##  <a name="a-namecopytoclipboarda--coleserveritemcopytoclipboard"></a><a name="copytoclipboard"></a>COleServerItem::CopyToClipboard  
 呼叫此函式可將 OLE 項目複製到剪貼簿。  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bIncludeLink`  
 請設為**TRUE**如果連結資料應該複製到剪貼簿。 請設為**FALSE**如果伺服器應用程式不支援的連結。  
  
### <a name="remarks"></a>備註  
 此函數會使用[OnGetClipboardData](#ongetclipboarddata)成員函式來建立[COleDataSource](../../mfc/reference/coledatasource-class.md)物件，其中包含支援的格式中的 OLE 項目的資料。 然後將函數放`COleDataSource`物件使用剪貼簿上的[COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函式。 `COleDataSource`物件包含的項目原生資料和其表示`CF_METAFILEPICT`格式，以及任何您選擇支援的轉換格式的資料。 您必須實作[序列化](../../mfc/reference/cobject-class.md#serialize)和[OnDraw](#ondraw)用於此成員函式。  
  
##  <a name="a-namedodragdropa--coleserveritemdodragdrop"></a><a name="dodragdrop"></a>COleServerItem::DoDragDrop  
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
 項目的矩形在畫面上，單位為像素，相對於用戶端區域。  
  
 `ptOffset`  
 從位移`lpItemRect`在拖曳時所在的滑鼠位置。  
  
 `bIncludeLink`  
 請設為**TRUE**如果連結資料應該複製到剪貼簿。 將它設定為**FALSE**如果您的應用程式不支援的連結。  
  
 `dwEffects`  
 判斷拖曳來源允許在拖曳作業 （複製、 移動和連結的組合） 的效果。  
  
 `lpRectStartDrag`  
 實際開始拖曳所定義的矩形的指標。 如需詳細資訊，請參閱接下來的＜備註＞一節。  
  
### <a name="return-value"></a>傳回值  
 `DROPEFFECT` 列舉中的值。 如果是`DROPEFFECT_MOVE`，應該移除原始的資料。  
  
### <a name="remarks"></a>備註  
 拖放作業不會立即啟動。 將滑鼠游標離開所指定的矩形等到`lpRectStartDrag`，或是直到經過指定的毫秒數。 如果`lpRectStartDrag`是**NULL**，會使用預設矩形，以便拖曳開始，當滑鼠游標移動一個像素。  
  
 登錄機碼設定為指定的延遲時間。 您可以變更的延遲時間，藉由呼叫[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果未指定的延遲時間，會使用預設值是 200 毫秒。 拖曳的延遲時間會儲存，如下所示︰  
  
-   Windows NT 拖曳延遲時間會儲存在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。  
  
-   Windows 3.x 拖曳延遲時間會儲存在獲得。INI 檔案，底下的 [Windows} 一節。  
  
-   Windows 95/98 拖曳延遲時間會儲存在快取的 WIN 版本。INI。  
  
 如需有關如何將拖曳的延遲資訊會儲存在登錄或。INI 檔案，請參閱[WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetclipboarddataa--coleserveritemgetclipboarddata"></a><a name="getclipboarddata"></a>COleServerItem::GetClipboardData  
 呼叫此函式，以填滿指定[COleDataSource](../../mfc/reference/coledatasource-class.md)物件會複製到剪貼簿中，如果您呼叫的所有資料[CopyToClipboard](#copytoclipboard) (如果您呼叫，就也傳送相同的資料[DoDragDrop](#dodragdrop))。  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDataSource`  
 指標`COleDataSource`會接收所有支援的格式中的 OLE 項目資料的物件。  
  
 `bIncludeLink`  
 **TRUE**如果連結資料應該複製到剪貼簿。 **FALSE**如果伺服器應用程式不支援的連結。  
  
 `lpOffset`  
 單位為像素滑鼠游標的原始物件的位移。  
  
 `lpSize`  
 像素為單位的物件大小。  
  
### <a name="remarks"></a>備註  
 此函數會呼叫[GetEmbedSourceData](#getembedsourcedata)成員函式來取得原生資料的 OLE 項目並呼叫[AddOtherClipboardData](#addotherclipboarddata)成員函式可取得的呈現格式，以及任何支援的轉換格式。 如果`bIncludeLink`是**TRUE**，函式也會呼叫[GetLinkSourceData](#getlinksourcedata)來取得項目的連結資料。  
  
 覆寫這個函式，如果您想要置於格式`COleDataSource`物件之前或之後所提供的這些格式`CopyToClipboard`。  
  
##  <a name="a-namegetdatasourcea--coleserveritemgetdatasource"></a><a name="getdatasource"></a>COleServerItem::GetDataSource  
 呼叫此函式可取得[COleDataSource](../../mfc/reference/coledatasource-class.md)物件用來儲存伺服器應用程式支援的轉換格式。  
  
```  
COleDataSource* GetDataSource();
```  
  
### <a name="return-value"></a>傳回值  
 指標`COleDataSource`物件用來儲存轉換格式。  
  
### <a name="remarks"></a>備註  
 如果想讓伺服器應用程式期間資料傳輸作業提供各種格式的資料，註冊這些格式與`COleDataSource`此函數所傳回的物件。 例如，如果您想要提供**CF_TEXT**剪貼簿或拖放作業的 OLE 項目表示，您會註冊與格式`COleDataSource`此函式傳回的物件，然後再覆寫**OnRenderXxxData**成員函式提供的資料。  
  
##  <a name="a-namegetdocumenta--coleserveritemgetdocument"></a><a name="getdocument"></a>COleServerItem::GetDocument  
 呼叫此函式可取得包含項目的文件的指標。  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指向文件，其中包含項目;**NULL**如果項目不是文件的一部分。  
  
### <a name="remarks"></a>備註  
 這樣可允許存取做為引數傳遞給您的伺服器文件`COleServerItem`建構函式。  
  
##  <a name="a-namegetembedsourcedataa--coleserveritemgetembedsourcedata"></a><a name="getembedsourcedata"></a>COleServerItem::GetEmbedSourceData  
 呼叫此函式可取得**CF_EMBEDSOURCE** OLE 項目的資料。  
  
```  
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>參數  
 `lpStgMedium`  
 指標[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構，將會收到**CF_EMBEDSOURCE** OLE 項目的資料。  
  
### <a name="remarks"></a>備註  
 這個格式中包含的項目原生資料。 您必須實作`Serialize`成員函式，此功能才能正常運作。  
  
 結果可以再加入資料來源使用[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 會自動呼叫此函數[COleServerItem::OnGetClipboardData](#ongetclipboarddata)。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetitemnamea--coleserveritemgetitemname"></a><a name="getitemname"></a>COleServerItem::GetItemName  
 呼叫此函式可取得的項目名稱。  
  
```  
const CString& GetItemName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 項目的名稱。  
  
### <a name="remarks"></a>備註  
 您通常會呼叫此函式只會針對連結的項目。  
  
##  <a name="a-namegetlinksourcedataa--coleserveritemgetlinksourcedata"></a><a name="getlinksourcedata"></a>COleServerItem::GetLinkSourceData  
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
 此格式包含描述的 OLE 項目並尋找文件包含 OLE 項目所需的資訊類型的 CLSID。  
  
 結果可以再加入至資料來源與[COleDataSource::CacheData](../../mfc/reference/coledatasource-class.md#cachedata)。 會自動呼叫此函數[OnGetClipboardData](#ongetclipboarddata)。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetobjectdescriptordataa--coleserveritemgetobjectdescriptordata"></a><a name="getobjectdescriptordata"></a>COleServerItem::GetObjectDescriptorData  
 呼叫此函式可取得**CF_OBJECTDESCRIPTOR** OLE 項目的資料。  
  
```  
void GetObjectDescriptorData(
    LPPOINT lpOffset,  
    LPSIZE lpSize,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>參數  
 `lpOffset`  
 滑鼠點選的 OLE 項目左上角的位移。 可以是**NULL**。  
  
 `lpSize`  
 OLE 項目的大小。 可以是**NULL**。  
  
 `lpStgMedium`  
 指標[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構，將會收到**CF_OBJECTDESCRIPTOR** OLE 項目的資料。  
  
### <a name="remarks"></a>備註  
 資訊複製到**STGMEDIUM**指向結構`lpStgMedium`。 此格式包含所需的 [選擇性貼上] 對話方塊中的資訊。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisconnecteda--coleserveritemisconnected"></a><a name="isconnected"></a>COleServerItem::IsConnected  
 呼叫此函式，以查看是否已連接的 OLE 項目。  
  
```  
BOOL IsConnected() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果項目都會連接;否則為 0。  
  
### <a name="remarks"></a>備註  
 OLE 項目會被視為已連接一或多個容器有項目的參考。 如果參考計數大於 0，或者它是內嵌的項目，被連接項目。  
  
##  <a name="a-nameislinkeditema--coleserveritemislinkeditem"></a><a name="islinkeditem"></a>COleServerItem::IsLinkedItem  
 呼叫此函式的 OLE 項目是否為連結的項目。  
  
```  
BOOL IsLinkedItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果項目連結的項目。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果項目有效，而且不會傳回文件的內嵌項目清單中，會連結項目。 連結的項目可能會或可能無法連線至容器。  
  
 通常會使用相同的類別，如連結和內嵌項目。 `IsLinkedItem`可讓您進行的行為不同於內嵌的項目連結的項目，雖然許多次的程式碼是很常見。  
  
##  <a name="a-namemsizeextenta--coleserveritemmsizeextent"></a><a name="m_sizeextent"></a>COleServerItem::m_sizeExtent  
 這個成員會要求伺服器物件中有多少會顯示在容器文件中。  
  
```  
CSize m_sizeExtent;  
```  
  
### <a name="remarks"></a>備註  
 預設實作[OnSetExtent](#onsetextent)設定這個成員。  
  
##  <a name="a-namenotifychangeda--coleserveritemnotifychanged"></a><a name="notifychanged"></a>COleServerItem::NotifyChanged  
 變更連結的項目之後，請呼叫此函式。  
  
```  
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>參數  
 `nDrawAspect`  
 介於`DVASPECT`列舉，指出哪些方面的 OLE 項目已變更。 這個參數可以具有下列值之一︰  
  
- `DVASPECT_CONTENT`項目表示的方式，可以顯示為其容器內的內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目是以一個圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [檔案] 功能表的 [列印] 命令來列印。  
  
### <a name="remarks"></a>備註  
 如果容器項目自動連結至文件，以反映所做的變更更新項目。 在容器應用程式使用 Microsoft Foundation 類別庫中，撰寫[COleClientItem::OnChange](../../mfc/reference/coleclientitem-class.md#onchange)呼叫回應中。  
  
##  <a name="a-nameondoverba--coleserveritemondoverb"></a><a name="ondoverb"></a>COleServerItem::OnDoVerb  
 若要執行指定的動詞架構呼叫。  
  
```  
virtual void OnDoVerb(LONG iVerb);
```  
  
### <a name="parameters"></a>參數  
 `iVerb`  
 指定要執行的動詞。 它可以是下列其中一項動作︰  
  
|值|意義|符號|  
|-----------|-------------|------------|  
|0|主動詞命令|`OLEIVERB_PRIMARY`|  
|1|第二個動詞命令|(無)|  
|– 1|編輯顯示項目|`OLEIVERB_SHOW`|  
|– 2|編輯在個別視窗中的項目|`OLEIVERB_OPEN`|  
|– 3|隱藏項目|`OLEIVERB_HIDE`|  
  
 -1 值通常是其他的動詞命令的別名。 如果不支援開啟編輯，–&2; 會有相同的效果，為 –&1;。 其他值，請參閱[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 如果容器應用程式寫入與 Mfc 程式庫，此函式時，會呼叫[COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate)成員函式對應`COleClientItem`稱為物件。 預設實作會呼叫[OnShow](#onshow)成員函式，如果主動作或`OLEIVERB_SHOW`指定，則[OnOpen](#onopen)如果第二個動詞或`OLEIVERB_OPEN`指定，則和[OnHide](#onhide)如果`OLEIVERB_HIDE`指定。 預設實作會呼叫`OnShow`如果`iVerb`不是其中一個以上所列的動詞命令。  
  
 如果您主要的動詞命令不會顯示此項目，請覆寫這個函式。 比方說，如果項目是錄音，其主要動作是播放，您就沒有顯示伺服器應用程式播放該項目。  
  
 如需詳細資訊，請參閱[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameondrawa--coleserveritemondraw"></a><a name="ondraw"></a>Coleserveritem  
 由框架呼叫將 OLE 項目呈現在中繼檔中。  
  
```  
virtual BOOL OnDraw(
    CDC* pDC,  
    CSize& rSize) = 0;  
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指標[CDC](../../mfc/reference/cdc-class.md)物件在其上繪製項目。 顯示內容會自動連接到屬性顯示內容，您可以呼叫屬性的函式，雖然這樣做會限制中繼檔裝置特有。  
  
 `rSize`  
 調整大小，請在**HIMETRIC**單位，在其中繪製中繼檔。  
  
### <a name="return-value"></a>傳回值  
 已經成功地繪製項目; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 中繼檔表示的 OLE 項目用來在容器應用程式中顯示的項目。 如果撰寫 Mfc 程式庫容器應用程式時，便會使用中繼檔[繪製](../../mfc/reference/coleclientitem-class.md#draw)成員函式對應[COleClientItem](../../mfc/reference/coleclientitem-class.md)物件。 沒有預設的實作。 您必須覆寫這個函式來繪製到指定的裝置內容的項目。  
  
##  <a name="a-nameondrawexa--coleserveritemondrawex"></a><a name="ondrawex"></a>COleServerItem::OnDrawEx  
 所有的繪圖架構呼叫。  
  
```  
virtual BOOL OnDrawEx(
    CDC* pDC,  
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指標[CDC](../../mfc/reference/cdc-class.md)物件在其上繪製項目。 DC 會自動連接到 DC 的屬性，您可以呼叫屬性的函式，雖然這樣做會限制中繼檔裝置特有。  
  
 `nDrawAspect`  
 `DVASPECT` 列舉中的值。 這個參數可以具有下列值之一︰  
  
- `DVASPECT_CONTENT`項目表示的方式，可以顯示為其容器內的內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目是以一個圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [檔案] 功能表的 [列印] 命令來列印。  
  
 `rSize`  
 在項目的大小**HIMETRIC**單位。  
  
### <a name="return-value"></a>傳回值  
 已經成功地繪製項目; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`OnDraw`時`DVASPECT`等於`DVASPECT_CONTENT`; 否則會失敗。  
  
 覆寫這個函式以外的其他層面提供展示資料`DVASPECT_CONTENT`，例如`DVASPECT_ICON`或`DVASPECT_THUMBNAIL`。  
  
##  <a name="a-nameongetclipboarddataa--coleserveritemongetclipboarddata"></a><a name="ongetclipboarddata"></a>COleServerItem::OnGetClipboardData  
 若要取得架構呼叫`COleDataSource`物件，其中包含會呼叫放在剪貼簿的所有資料[CopyToClipboard](#copytoclipboard)成員函式。  
  
```  
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,  
    LPPOINT lpOffset,  
    LPSIZE lpSize);
```  
  
### <a name="parameters"></a>參數  
 `bIncludeLink`  
 請設為**TRUE**如果連結資料應該複製到剪貼簿。 請設為**FALSE**如果伺服器應用程式不支援的連結。  
  
 `lpOffset`  
 滑鼠游標從物件像素為單位的原點位移。  
  
 `lpSize`  
 像素為單位的物件大小。  
  
### <a name="return-value"></a>傳回值  
 指標[COleDataSource](../../mfc/reference/coledatasource-class.md)物件，其中包含剪貼簿的資料。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會呼叫[GetClipboardData](#getclipboarddata)。  
  
##  <a name="a-nameongetextenta--coleserveritemongetextent"></a><a name="ongetextent"></a>COleServerItem::OnGetExtent  
 擷取大小，在架構呼叫**HIMETRIC**個 OLE 項目。  
  
```  
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>參數  
 `nDrawAspect`  
 指定要擷取其界限的 OLE 項目的外觀。 這個參數可以具有下列值之一︰  
  
- `DVASPECT_CONTENT`項目表示的方式，可以顯示為其容器內的內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目是以一個圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [檔案] 功能表的 [列印] 命令來列印。  
  
 `rSize`  
 若要參考`CSize`物件，將會收到 OLE 項目的大小。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果容器應用程式寫入與 Mfc 程式庫，此函式時，會呼叫[GetExtent](../../mfc/reference/coleclientitem-class.md#getextent)成員函式對應`COleClientItem`稱為物件。 預設實作不做任何動作。 您必須實作它自己。 如果您想要處理的要求大小的 OLE 項目時執行特殊處理，覆寫這個函式。  
  
##  <a name="a-nameonhidea--coleserveritemonhide"></a><a name="onhide"></a>COleServerItem::OnHide  
 若要隱藏 OLE 項目架構呼叫。  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>備註  
 預設會呼叫**COleServerDoc::OnShowDocument (FALSE)**。 函式也會告知容器已隱藏 OLE 項目。 如果您想要隱藏 OLE 項目時執行特殊處理，覆寫這個函式。  
  
##  <a name="a-nameoninitfromdataa--coleserveritemoninitfromdata"></a><a name="oninitfromdata"></a>COleServerItem::OnInitFromData  
 初始化 OLE 項目使用的內容架構呼叫`pDataObject`。  
  
```  
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,  
    BOOL bCreation);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 OLE 資料物件，其中包含各種格式來初始化 OLE 項目中的資料指標。  
  
 `bCreation`  
 **TRUE**如果呼叫的函式初始化新容器應用程式建立 OLE 項目。 **FALSE**如果呼叫的函式取代現有的 OLE 項目內容。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`bCreation`是**TRUE**，如果容器實作插入新根據目前的選取範圍的物件，會呼叫此函數。 建立新的 OLE 項目時，會使用選取的資料。 例如，試算表程式中選取資料格範圍，然後使用 建立一張圖表的 插入新物件基礎時選取的範圍中的值。 預設實作不做任何動作。 此函式可從所提供的選擇可接受的格式會覆寫`pDataObject`和初始化 OLE 項目，根據提供的資料。 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonopena--coleserveritemonopen"></a><a name="onopen"></a>COleServerItem::OnOpen  
 若要在伺服器應用程式的個別執行個體，而不是就地顯示 OLE 項目架構呼叫。  
  
```  
virtual void OnOpen();
```  
  
### <a name="remarks"></a>備註  
 預設實作會啟動第一個框架視窗顯示文件，其中包含 OLE 項目。迷你伺服應用程式時，預設實作會顯示在主視窗。 函式也會告知容器已開啟的 OLE 項目。  
  
 如果您想要開啟 OLE 項目時執行特殊處理，覆寫這個函式。 這是您要將選項設定為連結時開啟連結的項目上特別常發生。  
  
 如需詳細資訊，請參閱[IOleClientSite::OnShowWindow](http://msdn.microsoft.com/library/windows/desktop/ms688658)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonqueryupdateitemsa--coleserveritemonqueryupdateitems"></a><a name="onqueryupdateitems"></a>COleServerItem::OnQueryUpdateItems  
 若要判斷目前的伺服器文件中任何連結的項目是否已過期，架構呼叫。  
  
```  
virtual BOOL OnQueryUpdateItems();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果文件項目需要更新。0，如果所有項目是最新狀態。  
  
### <a name="remarks"></a>備註  
 如果已變更其來源文件，但尚未連結的項目更新以反映變更文件中的，項目已過期。  
  
##  <a name="a-nameonrenderdataa--coleserveritemonrenderdata"></a><a name="onrenderdata"></a>COleServerItem::OnRenderData  
 擷取指定之格式的資料架構所呼叫。  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)指定要求資訊的格式結構。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)資料所要傳回的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前放置在`COleDataSource`物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)或[DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)延遲轉譯的成員函式。 此函式的預設實作會呼叫[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)分別，如果提供的儲存體中的檔案或記憶體。 如果這些格式都未提供，預設實作會傳回 0，而且不執行任何動作。  
  
 如果`lpStgMedium` ->  *tymed*是**TYMED_NULL**、 **STGMEDIUM**應該配置及填入所指定*-> tymed lpFormatEtc*。 如果不是**TYMED_NULL**、 **STGMEDIUM**應填入的資料的位置。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可能要改為覆寫這個函式的其他版本的其中一個。 如果您的資料是小型且固定的大小，覆寫`OnRenderGlobalData`。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。  
  
 如需詳細資訊，請參閱[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)， [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)， [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)，和[TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonrenderfiledataa--coleserveritemonrenderfiledata"></a><a name="onrenderfiledata"></a>COleServerItem::OnRenderFileData  
 擷取指定之格式的資料儲存媒體檔案時架構呼叫。  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)指定要求資訊的格式結構。  
  
 `pFile`  
 指向`CFile`裡面的資料是要呈現的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前放置在`COleDataSource`物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回**FALSE**。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可能要改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存媒體，覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫[OnRenderFileData](#onrenderfiledata)。  
  
 如需詳細資訊，請參閱[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonrenderglobaldataa--coleserveritemonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleServerItem::OnRenderGlobalData  
 擷取指定的格式中的資料，當指定的儲存體中的全域記憶體架構所呼叫。  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)指定要求資訊的格式結構。  
  
 `phGlobal`  
 指向資料所要傳回的全域記憶體的控制代碼。 如果已不配置任何記憶體，這個參數可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前放置在`COleDataSource`物件使用[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回**FALSE**。  
  
 如果`phGlobal`是**NULL**，然後新`HGLOBAL`應該配置並傳回`phGlobal`。 否則，`HGLOBAL`所指定`phGlobal`應該填入資料。 資料量放在`HGLOBAL`不能超過目前的記憶體區塊大小。 此外，無法重新配置較大的區塊。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可能要改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存媒體，覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫[OnRenderFileData](#onrenderfiledata)。  
  
 如需詳細資訊，請參閱[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonsetcolorschemea--coleserveritemonsetcolorscheme"></a><a name="onsetcolorscheme"></a>COleServerItem::OnSetColorScheme  
 若要指定編輯 OLE 項目時要使用的調色盤架構呼叫。  
  
```  
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```  
  
### <a name="parameters"></a>參數  
 `lpLogPalette`  
 Windows 指標[LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)結構。  
  
### <a name="return-value"></a>傳回值  
 非零，如果使用的色彩調色盤。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果使用 Mfc 程式庫寫入容器應用程式，此函式時，會呼叫[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971)函式對應`COleClientItem`稱為物件。 預設實作會傳回**FALSE**。 如果您想要使用建議的調色盤，請覆寫這個函式。 伺服器應用程式不需要使用建議的調色盤。  
  
 如需詳細資訊，請參閱[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonsetdataa--coleserveritemonsetdata"></a><a name="onsetdata"></a>COleServerItem::OnSetData  
 將指定的資料取代成 OLE 項目的資料架構呼叫。  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構指定的資料格式。  
  
 `lpStgMedium`  
 指標[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)資料所在的結構。  
  
 `bRelease`  
 指出可完成函式呼叫之後儲存媒體的擁有權。 呼叫端將決定誰負責釋放配置代表儲存體中的資源。 呼叫端的做法是設定`bRelease`。 如果`bRelease`是零，伺服器項目會取得擁有權，使用它完成時釋放媒體。 當`bRelease`為 0、 呼叫端保留擁有權和伺服器項目可用於儲存媒體只能在呼叫期間。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 它已成功取得它的伺服器項目才會擁有權的資料。 也就是說，它不會擁有權如果它傳回 0。 如果資料來源會取得擁有權，它會藉由呼叫釋放儲存媒體[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)函式。  
  
 預設實作不做任何動作。 覆寫這個函式，以取代指定之資料的 OLE 項目的資料。 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)， [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)，和[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameonsetextenta--coleserveritemonsetextent"></a><a name="onsetextent"></a>COleServerItem::OnSetExtent  
 告訴 OLE 項目多少空間是它可以在容器文件中使用的架構所呼叫。  
  
```  
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,  
    const CSize& size);
```  
  
### <a name="parameters"></a>參數  
 `nDrawAspect`  
 指定的 OLE 項目會指定其繫結的外觀。 這個參數可以具有下列值之一︰  
  
- `DVASPECT_CONTENT`項目表示的方式，可以顯示為其容器內的內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目是以一個圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [檔案] 功能表的 [列印] 命令來列印。  
  
 `size`  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)結構，指定新的 OLE 項目大小。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果容器應用程式寫入與 Mfc 程式庫，此函式時，會呼叫[SetExtent](../../mfc/reference/coleclientitem-class.md#setextent)成員函式對應`COleClientItem`稱為物件。 預設實作集[m_sizeExtent](#m_sizeextent)成員，才能指定大小如果`nDrawAspect`是`DVASPECT_CONTENT`; 否則便傳回 0。 覆寫這個函式來執行特殊處理，當您變更項目的大小。  
  
##  <a name="a-nameonshowa--coleserveritemonshow"></a><a name="onshow"></a>COleServerItem::OnShow  
 指示伺服器應用程式就地顯示 OLE 項目架構呼叫。  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>備註  
 當容器應用程式的使用者建立的項目，或執行指令動詞，例如編輯，通常會呼叫此函數需要顯示的項目。 預設實作會在就地啟動。 如果失敗，函式呼叫`OnOpen`成員函式可在個別視窗中顯示 OLE 項目。  
  
 如果您想要執行特殊處理，而顯示 OLE 項目時，覆寫這個函式。  
  
##  <a name="a-nameonupdatea--coleserveritemonupdate"></a><a name="onupdate"></a>COleServerItem::OnUpdate  
 由架構呼叫時已修改的項目。  
  
```  
virtual void OnUpdate(
    COleServerItem* pSender,  
    LPARAM lHint,  
    CObject* pHint,  
    DVASPECT nDrawAspect);
```  
  
### <a name="parameters"></a>參數  
 `pSender`  
 修改文件項目的指標。 可以是**NULL**。  
  
 `lHint`  
 包含有關修改資訊。  
  
 `pHint`  
 儲存修改的相關資訊的物件指標。  
  
 `nDrawAspect`  
 `DVASPECT` 列舉中的值。 這個參數可以具有下列值之一︰  
  
- `DVASPECT_CONTENT`項目表示的方式，可以顯示為其容器內的內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目是以一個圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [檔案] 功能表的 [列印] 命令來列印。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫[NotifyChanged](#notifychanged)、 提示和寄件者。  
  
##  <a name="a-nameonupdateitemsa--coleserveritemonupdateitems"></a><a name="onupdateitems"></a>COleServerItem::OnUpdateItems  
 更新伺服器文件中的所有項目架構所呼叫。  
  
```  
virtual void OnUpdateItems();
```  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫[UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)所有`COleClientItem`文件中的物件。  
  
##  <a name="a-namesetitemnamea--coleserveritemsetitemname"></a><a name="setitemname"></a>COleServerItem::SetItemName  
 當您建立連結的項目，可將它的名稱，請呼叫此函式。  
  
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

