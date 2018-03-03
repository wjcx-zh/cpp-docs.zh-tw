---
title: "COleClientItem 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleClientItem
- AFXOLE/COleClientItem
- AFXOLE/COleClientItem::COleClientItem
- AFXOLE/COleClientItem::Activate
- AFXOLE/COleClientItem::ActivateAs
- AFXOLE/COleClientItem::AttachDataObject
- AFXOLE/COleClientItem::CanCreateFromData
- AFXOLE/COleClientItem::CanCreateLinkFromData
- AFXOLE/COleClientItem::CanPaste
- AFXOLE/COleClientItem::CanPasteLink
- AFXOLE/COleClientItem::Close
- AFXOLE/COleClientItem::ConvertTo
- AFXOLE/COleClientItem::CopyToClipboard
- AFXOLE/COleClientItem::CreateCloneFrom
- AFXOLE/COleClientItem::CreateFromClipboard
- AFXOLE/COleClientItem::CreateFromData
- AFXOLE/COleClientItem::CreateFromFile
- AFXOLE/COleClientItem::CreateLinkFromClipboard
- AFXOLE/COleClientItem::CreateLinkFromData
- AFXOLE/COleClientItem::CreateLinkFromFile
- AFXOLE/COleClientItem::CreateNewItem
- AFXOLE/COleClientItem::CreateStaticFromClipboard
- AFXOLE/COleClientItem::CreateStaticFromData
- AFXOLE/COleClientItem::Deactivate
- AFXOLE/COleClientItem::DeactivateUI
- AFXOLE/COleClientItem::Delete
- AFXOLE/COleClientItem::DoDragDrop
- AFXOLE/COleClientItem::DoVerb
- AFXOLE/COleClientItem::Draw
- AFXOLE/COleClientItem::GetActiveView
- AFXOLE/COleClientItem::GetCachedExtent
- AFXOLE/COleClientItem::GetClassID
- AFXOLE/COleClientItem::GetClipboardData
- AFXOLE/COleClientItem::GetDocument
- AFXOLE/COleClientItem::GetDrawAspect
- AFXOLE/COleClientItem::GetExtent
- AFXOLE/COleClientItem::GetIconFromRegistry
- AFXOLE/COleClientItem::GetIconicMetafile
- AFXOLE/COleClientItem::GetInPlaceWindow
- AFXOLE/COleClientItem::GetItemState
- AFXOLE/COleClientItem::GetLastStatus
- AFXOLE/COleClientItem::GetLinkUpdateOptions
- AFXOLE/COleClientItem::GetType
- AFXOLE/COleClientItem::GetUserType
- AFXOLE/COleClientItem::IsInPlaceActive
- AFXOLE/COleClientItem::IsLinkUpToDate
- AFXOLE/COleClientItem::IsModified
- AFXOLE/COleClientItem::IsOpen
- AFXOLE/COleClientItem::IsRunning
- AFXOLE/COleClientItem::OnActivate
- AFXOLE/COleClientItem::OnActivateUI
- AFXOLE/COleClientItem::OnChange
- AFXOLE/COleClientItem::OnDeactivate
- AFXOLE/COleClientItem::OnDeactivateUI
- AFXOLE/COleClientItem::OnGetClipboardData
- AFXOLE/COleClientItem::OnInsertMenus
- AFXOLE/COleClientItem::OnRemoveMenus
- AFXOLE/COleClientItem::OnSetMenu
- AFXOLE/COleClientItem::OnShowControlBars
- AFXOLE/COleClientItem::OnUpdateFrameTitle
- AFXOLE/COleClientItem::ReactivateAndUndo
- AFXOLE/COleClientItem::Release
- AFXOLE/COleClientItem::Reload
- AFXOLE/COleClientItem::Run
- AFXOLE/COleClientItem::SetDrawAspect
- AFXOLE/COleClientItem::SetExtent
- AFXOLE/COleClientItem::SetHostNames
- AFXOLE/COleClientItem::SetIconicMetafile
- AFXOLE/COleClientItem::SetItemRects
- AFXOLE/COleClientItem::SetLinkUpdateOptions
- AFXOLE/COleClientItem::SetPrintDevice
- AFXOLE/COleClientItem::UpdateLink
- AFXOLE/COleClientItem::CanActivate
- AFXOLE/COleClientItem::OnChangeItemPosition
- AFXOLE/COleClientItem::OnDeactivateAndUndo
- AFXOLE/COleClientItem::OnDiscardUndoState
- AFXOLE/COleClientItem::OnGetClipRect
- AFXOLE/COleClientItem::OnGetItemPosition
- AFXOLE/COleClientItem::OnGetWindowContext
- AFXOLE/COleClientItem::OnScrollBy
- AFXOLE/COleClientItem::OnShowItem
dev_langs:
- C++
helpviewer_keywords:
- COleClientItem [MFC], COleClientItem
- COleClientItem [MFC], Activate
- COleClientItem [MFC], ActivateAs
- COleClientItem [MFC], AttachDataObject
- COleClientItem [MFC], CanCreateFromData
- COleClientItem [MFC], CanCreateLinkFromData
- COleClientItem [MFC], CanPaste
- COleClientItem [MFC], CanPasteLink
- COleClientItem [MFC], Close
- COleClientItem [MFC], ConvertTo
- COleClientItem [MFC], CopyToClipboard
- COleClientItem [MFC], CreateCloneFrom
- COleClientItem [MFC], CreateFromClipboard
- COleClientItem [MFC], CreateFromData
- COleClientItem [MFC], CreateFromFile
- COleClientItem [MFC], CreateLinkFromClipboard
- COleClientItem [MFC], CreateLinkFromData
- COleClientItem [MFC], CreateLinkFromFile
- COleClientItem [MFC], CreateNewItem
- COleClientItem [MFC], CreateStaticFromClipboard
- COleClientItem [MFC], CreateStaticFromData
- COleClientItem [MFC], Deactivate
- COleClientItem [MFC], DeactivateUI
- COleClientItem [MFC], Delete
- COleClientItem [MFC], DoDragDrop
- COleClientItem [MFC], DoVerb
- COleClientItem [MFC], Draw
- COleClientItem [MFC], GetActiveView
- COleClientItem [MFC], GetCachedExtent
- COleClientItem [MFC], GetClassID
- COleClientItem [MFC], GetClipboardData
- COleClientItem [MFC], GetDocument
- COleClientItem [MFC], GetDrawAspect
- COleClientItem [MFC], GetExtent
- COleClientItem [MFC], GetIconFromRegistry
- COleClientItem [MFC], GetIconicMetafile
- COleClientItem [MFC], GetInPlaceWindow
- COleClientItem [MFC], GetItemState
- COleClientItem [MFC], GetLastStatus
- COleClientItem [MFC], GetLinkUpdateOptions
- COleClientItem [MFC], GetType
- COleClientItem [MFC], GetUserType
- COleClientItem [MFC], IsInPlaceActive
- COleClientItem [MFC], IsLinkUpToDate
- COleClientItem [MFC], IsModified
- COleClientItem [MFC], IsOpen
- COleClientItem [MFC], IsRunning
- COleClientItem [MFC], OnActivate
- COleClientItem [MFC], OnActivateUI
- COleClientItem [MFC], OnChange
- COleClientItem [MFC], OnDeactivate
- COleClientItem [MFC], OnDeactivateUI
- COleClientItem [MFC], OnGetClipboardData
- COleClientItem [MFC], OnInsertMenus
- COleClientItem [MFC], OnRemoveMenus
- COleClientItem [MFC], OnSetMenu
- COleClientItem [MFC], OnShowControlBars
- COleClientItem [MFC], OnUpdateFrameTitle
- COleClientItem [MFC], ReactivateAndUndo
- COleClientItem [MFC], Release
- COleClientItem [MFC], Reload
- COleClientItem [MFC], Run
- COleClientItem [MFC], SetDrawAspect
- COleClientItem [MFC], SetExtent
- COleClientItem [MFC], SetHostNames
- COleClientItem [MFC], SetIconicMetafile
- COleClientItem [MFC], SetItemRects
- COleClientItem [MFC], SetLinkUpdateOptions
- COleClientItem [MFC], SetPrintDevice
- COleClientItem [MFC], UpdateLink
- COleClientItem [MFC], CanActivate
- COleClientItem [MFC], OnChangeItemPosition
- COleClientItem [MFC], OnDeactivateAndUndo
- COleClientItem [MFC], OnDiscardUndoState
- COleClientItem [MFC], OnGetClipRect
- COleClientItem [MFC], OnGetItemPosition
- COleClientItem [MFC], OnGetWindowContext
- COleClientItem [MFC], OnScrollBy
- COleClientItem [MFC], OnShowItem
ms.assetid: 7f571b7c-2758-4839-847a-0cf1ef643128
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3732f23c2af429d0b5fc965b7f961af8400e2e42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="coleclientitem-class"></a>COleClientItem 類別
定義 OLE 項目的容器介面。  
  
## <a name="syntax"></a>語法  
  
```  
class COleClientItem : public CDocItem  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleClientItem::COleClientItem](#coleclientitem)|建構 `COleClientItem` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleClientItem::Activate](#activate)|開啟作業的 OLE 項目，然後執行指定的動詞命令。|  
|[COleClientItem::ActivateAs](#activateas)|啟動為其他類型的項目。|  
|[COleClientItem::AttachDataObject](#attachdataobject)|存取 OLE 物件中的資料。|  
|[COleClientItem::CanCreateFromData](#cancreatefromdata)|指出容器應用程式是否可以建立內嵌的物件。|  
|[COleClientItem::CanCreateLinkFromData](#cancreatelinkfromdata)|指出容器應用程式是否可以建立連結的物件。|  
|[COleClientItem::CanPaste](#canpaste)|指出是否剪貼簿包含內嵌或靜態 OLE 項目。|  
|[COleClientItem::CanPasteLink](#canpastelink)|指出是否剪貼簿包含連結的 OLE 項目。|  
|[COleClientItem::Close](#close)|關閉伺服器的連結，但不會終結 OLE 項目。|  
|[COleClientItem::ConvertTo](#convertto)|將項目轉換成另一種類型。|  
|[COleClientItem::CopyToClipboard](#copytoclipboard)|將 OLE 項目複製到剪貼簿。|  
|[COleClientItem::CreateCloneFrom](#createclonefrom)|建立現有項目的複本。|  
|[COleClientItem::CreateFromClipboard](#createfromclipboard)|從剪貼簿中建立內嵌項目。|  
|[COleClientItem::CreateFromData](#createfromdata)|建立內嵌項目從資料物件。|  
|[COleClientItem::CreateFromFile](#createfromfile)|從檔案建立內嵌項目。|  
|[COleClientItem::CreateLinkFromClipboard](#createlinkfromclipboard)|從剪貼簿中建立連結的項目。|  
|[COleClientItem::CreateLinkFromData](#createlinkfromdata)|建立連結的項目從資料物件。|  
|[COleClientItem::CreateLinkFromFile](#createlinkfromfile)|從檔案建立連結的項目。|  
|[COleClientItem::CreateNewItem](#createnewitem)|啟動伺服器應用程式建立新的內嵌項目。|  
|[COleClientItem::CreateStaticFromClipboard](#createstaticfromclipboard)|建立靜態項目從剪貼簿。|  
|[COleClientItem::CreateStaticFromData](#createstaticfromdata)|建立靜態項目從資料物件。|  
|[COleClientItem::Deactivate](#deactivate)|停用項目。|  
|[COleClientItem::DeactivateUI](#deactivateui)|將容器應用程式的使用者介面還原成原始狀態。|  
|[COleClientItem::Delete](#delete)|刪除或關閉 OLE 項目，如果它已連結的項目。|  
|[COleClientItem::DoDragDrop](#dodragdrop)|執行拖放作業。|  
|[COleClientItem::DoVerb](#doverb)|執行指定的動詞命令。|  
|[COleClientItem::Draw](#draw)|繪製 OLE 項目。|  
|[COleClientItem::GetActiveView](#getactiveview)|取得的檢視的就地啟動項目。|  
|[COleClientItem::GetCachedExtent](#getcachedextent)|傳回 OLE 項目的矩形界限。|  
|[COleClientItem::GetClassID](#getclassid)|取得目前項目的類別識別碼。|  
|[COleClientItem::GetClipboardData](#getclipboarddata)|取得會藉由呼叫放到剪貼簿的資料`CopyToClipboard`成員函式。|  
|[COleClientItem::GetDocument](#getdocument)|傳回`COleDocument`物件，其中包含出現的項目。|  
|[COleClientItem::GetDrawAspect](#getdrawaspect)|取得轉譯項目的目前檢視。|  
|[COleClientItem::GetExtent](#getextent)|傳回 OLE 項目的矩形界限。|  
|[COleClientItem::GetIconFromRegistry](#geticonfromregistry)|擷取特定的 CLSID 的伺服器相關聯的圖示的控制代碼。|  
|[COleClientItem::GetIconicMetafile](#geticonicmetafile)|取得用於繪製的項目圖示的中繼檔。|  
|[COleClientItem::GetInPlaceWindow](#getinplacewindow)|傳回的項目就地編輯視窗的指標。|  
|[COleClientItem::GetItemState](#getitemstate)|取得項目的目前狀態。|  
|[COleClientItem::GetLastStatus](#getlaststatus)|傳回最後一個 OLE 作業的狀態。|  
|[COleClientItem::GetLinkUpdateOptions](#getlinkupdateoptions)|傳回連結的項目 （進階功能） 的更新模式。|  
|[COleClientItem::GetType](#gettype)|傳回 OLE 項目類型 （內嵌、 連結或靜態）。|  
|[COleClientItem::GetUserType](#getusertype)|取得描述項目類型的字串。|  
|[COleClientItem::IsInPlaceActive](#isinplaceactive)|傳回`TRUE`如果就地啟用作用中的項目。|  
|[COleClientItem::IsLinkUpToDate](#islinkuptodate)|傳回**TRUE**如果連結的項目是最新狀態的來源文件。|  
|[COleClientItem::IsModified](#ismodified)|傳回`TRUE`如果自上次儲存後已修改的項目。|  
|[COleClientItem::IsOpen](#isopen)|傳回`TRUE`如果伺服器應用程式中目前開啟的項目。|  
|[COleClientItem::IsRunning](#isrunning)|傳回`TRUE`如果項目的伺服器應用程式正在執行。|  
|[COleClientItem::OnActivate](#onactivate)|由架構呼叫以通知已經啟用此項目。|  
|[COleClientItem::OnActivateUI](#onactivateui)|由架構呼叫以通知項目，它就會啟動，並且應顯示其使用者介面。|  
|[COleClientItem::OnChange](#onchange)|伺服器變更 OLE 項目時呼叫。 所需的實作。|  
|[COleClientItem::OnDeactivate](#ondeactivate)|停用項目時由架構呼叫。|  
|[COleClientItem::OnDeactivateUI](#ondeactivateui)|伺服器已移除其就地使用者介面時，由架構呼叫。|  
|[COleClientItem::OnGetClipboardData](#ongetclipboarddata)|由架構呼叫以取得要複製到剪貼簿的資料。|  
|[COleClientItem::OnInsertMenus](#oninsertmenus)|由架構呼叫以建立複合的功能表。|  
|[COleClientItem::OnRemoveMenus](#onremovemenus)|由架構呼叫以從組合功能表移除容器的功能表。|  
|[COleClientItem::OnSetMenu](#onsetmenu)|由架構呼叫以安裝和移除組合功能表。|  
|[COleClientItem::OnShowControlBars](#onshowcontrolbars)|由架構呼叫以顯示和隱藏控制列。|  
|[COleClientItem::OnUpdateFrameTitle](#onupdateframetitle)|由架構呼叫以更新框架視窗的標題列。|  
|[COleClientItem::ReactivateAndUndo](#reactivateandundo)|重新啟動此項目，最後一個就地編輯作業復原。|  
|[COleClientItem::Release](#release)|釋放連接至 OLE 連結的項目並將它關閉，如果它已開啟。 不會終結的用戶端項目。|  
|[COleClientItem::Reload](#reload)|若要在呼叫之後會重新載入項目`ActivateAs`。|  
|[COleClientItem::Run](#run)|執行應用程式相關聯的項目。|  
|[COleClientItem::SetDrawAspect](#setdrawaspect)|設定項目的目前檢視中的轉譯。|  
|[COleClientItem::SetExtent](#setextent)|設定 OLE 項目的週框矩形。|  
|[COleClientItem::SetHostNames](#sethostnames)|設定編輯 OLE 項目時，會顯示伺服器的名稱。|  
|[COleClientItem::SetIconicMetafile](#seticonicmetafile)|會快取的中繼檔，用來繪製項目的圖示。|  
|[COleClientItem::SetItemRects](#setitemrects)|設定項目的周框。|  
|[COleClientItem::SetLinkUpdateOptions](#setlinkupdateoptions)|設定連結的項目 （進階功能） 的更新模式。|  
|[COleClientItem::SetPrintDevice](#setprintdevice)|設定此用戶端項目的的列印目標裝置。|  
|[COleClientItem::UpdateLink](#updatelink)|更新簡報快取的項目。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleClientItem::CanActivate](#canactivate)|由架構呼叫以判斷是否允許就地啟用。|  
|[COleClientItem::OnChangeItemPosition](#onchangeitemposition)|項目的位置變更時由架構呼叫。|  
|[COleClientItem::OnDeactivateAndUndo](#ondeactivateandundo)|若要在啟用後才復原架構呼叫。|  
|[COleClientItem::OnDiscardUndoState](#ondiscardundostate)|由架構呼叫以捨棄的項目復原狀態資訊。|  
|[COleClientItem::OnGetClipRect](#ongetcliprect)|由架構呼叫以取得項目的裁剪矩形座標。|  
|[COleClientItem::OnGetItemPosition](#ongetitemposition)|由架構呼叫以取得項目的位置，相對於檢視。|  
|[COleClientItem::OnGetWindowContext](#ongetwindowcontext)|項目就地啟動時由架構呼叫。|  
|[COleClientItem::OnScrollBy](#onscrollby)|由架構呼叫以捲動檢視中的項目。|  
|[COleClientItem::OnShowItem](#onshowitem)|由架構呼叫以顯示 OLE 項目。|  
  
## <a name="remarks"></a>備註  
 OLE 項目代表伺服器應用程式，可以插入文件"順暢地 」 合併，使其顯示給使用者，以便能在單一文件所建立和維護的資料。 結果為 「 複合文件 」 由 OLE 項目與包含文件所組成。  
  
 OLE 項目可以內嵌或連結。 如果內嵌，其資料儲存複合文件的一部分。 如果連結，其資料會儲存為個別的檔案伺服器應用程式所建立的一部分，並只連結至該檔案會儲存在複合文件。 所有 OLE 項目都包含指定的伺服器應用程式應該呼叫來編輯這些資訊。  
  
 `COleClientItem`定義數個呼叫的可覆寫函式以回應要求，從伺服器應用程式。這些可覆寫通常做為通知。 這可讓伺服器應用程式通知編輯 OLE 項目時，可讓使用者變更的容器，或擷取在編輯期間所需的資訊。  
  
 `COleClientItem`可以使用其中一種[COleDocument](../../mfc/reference/coledocument-class.md)， [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)，或[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)類別。 若要使用`COleClientItem`、 衍生的類別和實作[OnChange](#onchange)成員函式，以定義容器的項目所做之變更的回應方式。 若要支援就地啟用，覆寫[OnGetItemPosition](#ongetitemposition)成員函式。 此函數會提供 OLE 項目顯示位置的相關資訊。  
  
 如需使用容器介面的詳細資訊，請參閱文章[容器： 實作容器](../../mfc/containers-implementing-a-container.md)和[啟用](../../mfc/activation-cpp.md)。  
  
> [!NOTE]
>  Windows SDK 的內嵌和連結項目，例如 「 物件 」 是指和參考類型的項目，例如 「 類別 」。 此參考會使用 「 項目 」 一詞來區別 OLE 實體從對應的 c + + 物件和詞彙來區別 OLE 類別目錄從 c + + 類別的 「 類型 」。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleClientItem`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="activate"></a>COleClientItem::Activate  
 呼叫此函式以執行指定的動詞，而不是[DoVerb](#doverb) ，讓您可以自己處理作業時擲回例外狀況。  
  
```  
void Activate(
    LONG nVerb,  
    CView* pView,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>參數  
 `nVerb`  
 指定要執行的指令動詞。 它可以是下列其中一項：  
  
|值|意義|符號|  
|-----------|-------------|------------|  
|- 0|主動詞命令|`OLEIVERB_PRIMARY`|  
|- 1|次要的動詞命令|(無)|  
|- 1|顯示編輯項目|`OLEIVERB_SHOW`|  
|- 2|編輯在個別視窗中的項目|`OLEIVERB_OPEN`|  
|- 3|隱藏項目|`OLEIVERB_HIDE`|  
  
 -1 值通常是另一個動詞命令的別名。 如果不支援開啟編輯，-2 會有相同的效果為-1。 如需其他值，請參閱[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) Windows SDK 中。  
  
 `pView`  
 容器檢視視窗，其中包含 OLE 項目; 的指標這用於伺服器應用程式就地啟用。 這個參數應該是**NULL**如果容器不支援就地啟用。  
  
 `lpMsg`  
 造成要啟動的項目之訊息的指標。  
  
### <a name="remarks"></a>備註  
 如果伺服器應用程式使用 Microsoft Foundation 類別庫所撰寫，這個函式會導致[OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb)成員函式對應`COleServerItem`来執行的物件。  
  
 如果主要動作是編輯和中指定零`nVerb`啟動參數，伺服器應用程式以允許編輯 OLE 項目。 如果容器應用程式支援就地啟用，編輯即可備妥。 如果容器不支援就地啟用 （或如果未指定 Open 動詞），伺服器會在個別視窗中啟動，並編輯即可那里。 一般而言，當容器應用程式使用者按兩下 OLE 項目中的主要動詞命令的值時，才`nVerb`參數會決定使用者可以採取哪些動作。 不過，如果伺服器支援只有一個動作，會在該動作，不論其中該值會以指定`nVerb`參數。  
  
 如需詳細資訊，請參閱[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) Windows SDK 中。  
  
##  <a name="activateas"></a>COleClientItem::ActivateAs  
 啟動項目，就好像是所指定之類型的項目會使用 OLE 的物件轉換設備`clsidNew`。  
  
```  
virtual BOOL ActivateAs(
    LPCTSTR lpszUserType,  
    REFCLSID clsidOld,  
    REFCLSID clsidNew);
```  
  
### <a name="parameters"></a>參數  
 *lpszUserType*  
 指向之字串表示的目標使用者類型，例如 「 Word 文件 」。  
  
 *clsidOld*  
 項目的目前類別的參考識別碼。 類別識別碼應該代表實際物件的類型儲存，除非它是連結。 在此情況下，它應該是 CLSID 的連結所參考的項目。 [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)自動提供項目的正確類別識別碼。  
  
 `clsidNew`  
 參考到目標類別識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 這稱為自動[COleConvertDialog::DoConvert](../../mfc/reference/coleconvertdialog-class.md#doconvert)。 它不通常會直接呼叫。  
  
##  <a name="attachdataobject"></a>COleClientItem::AttachDataObject  
 呼叫此函式來初始化[COleDataObject](../../mfc/reference/coledataobject-class.md)來存取 OLE 項目中的資料。  
  
```  
void AttachDataObject(COleDataObject& rDataObject) const;  
```  
  
### <a name="parameters"></a>參數  
 *rDataObject*  
 若要參考`COleDataObject`將會初始化為 OLE 項目中允許資料存取的物件。  
  
##  <a name="canactivate"></a>COleClientItem::CanActivate  
 使用者要求的 OLE 項目; 就地啟動時由架構呼叫此函式的傳回值會決定是否允許就地啟用。  
  
```  
virtual BOOL CanActivate();
```  
  
### <a name="return-value"></a>傳回值  
 如果允許就地啟用，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 預設實作允許就地啟用容器具有有效的視窗。 覆寫這個函式來實作特殊邏輯，接受或拒絕啟動要求。 例如，OLE 項目是否太小，或目前可見，可以拒絕啟用要求。  
  
 如需詳細資訊，請參閱[IOleInPlaceSite::CanInPlaceActivate](http://msdn.microsoft.com/library/windows/desktop/ms691236) Windows SDK 中。  
  
##  <a name="cancreatefromdata"></a>COleClientItem::CanCreateFromData  
 容器應用程式是否可以建立從內嵌的物件會檢查給定`COleDataObject`物件。  
  
```  
static BOOL PASCAL CanCreateFromData(const COleDataObject* pDataObject);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指標[COleDataObject](../../mfc/reference/coledataobject-class.md)從中 OLE 項目是要建立的物件。  
  
### <a name="return-value"></a>傳回值  
 如果容器可以建立從內嵌的物件則為非零`COleDataObject`物件; 否則為 0。  
  
### <a name="remarks"></a>備註  
 `COleDataObject`類別用於資料傳輸的剪貼簿、 拖放，透過作業或內嵌 OLE 項目擷取各種格式的資料。  
  
 容器可以使用此函式，來決定啟用或停用其編輯貼上] 和 [編輯選擇性貼上命令。  
  
 如需詳細資訊，請參閱文章[資料物件和資料來源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。  
  
##  <a name="cancreatelinkfromdata"></a>COleClientItem::CanCreateLinkFromData  
 檢查容器應用程式是否可以建立連結的物件，從給定`COleDataObject`物件。  
  
```  
static BOOL PASCAL CanCreateLinkFromData(const COleDataObject* pDataObject);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指標[COleDataObject](../../mfc/reference/coledataobject-class.md)從中 OLE 項目是要建立的物件。  
  
### <a name="return-value"></a>傳回值  
 如果容器可以建立連結的物件則為非零`COleDataObject`物件。  
  
### <a name="remarks"></a>備註  
 `COleDataObject`類別用於資料傳輸的剪貼簿、 拖放，透過作業或內嵌 OLE 項目擷取各種格式的資料。  
  
 容器可以使用此函式，來決定啟用或停用其編輯選擇性貼上及編輯貼上連結的命令。  
  
 如需詳細資訊，請參閱文章[資料物件和資料來源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。  
  
##  <a name="canpaste"></a>COleClientItem::CanPaste  
 呼叫此函式可看到內嵌的 OLE 項目是否可以從剪貼簿貼上。  
  
```  
static BOOL PASCAL CanPaste();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果內嵌的 OLE 項目可以貼上從 剪貼簿。否則便是 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[OleGetClipboard](http://msdn.microsoft.com/library/windows/desktop/ms692778)和[OleQueryCreateFromData](http://msdn.microsoft.com/library/windows/desktop/ms683739) Windows SDK 中。  
  
##  <a name="canpastelink"></a>COleClientItem::CanPasteLink  
 呼叫此函式，以查看連結的 OLE 項目是否可以從剪貼簿貼上。  
  
```  
static BOOL PASCAL CanPasteLink();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果連結的 OLE 項目可以貼上從 剪貼簿。否則便是 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[OleGetClipboard](http://msdn.microsoft.com/library/windows/desktop/ms692778)和[OleQueryLinkFromData](http://msdn.microsoft.com/library/windows/desktop/ms690244) Windows SDK 中。  
  
##  <a name="close"></a>COleClientItem::Close  
 呼叫此函式可載入其處理常式，在記憶體中使用，但伺服器未執行的執行狀態至載入的狀態，也就是從變更的 OLE 項目狀態。  
  
```  
void Close(OLECLOSE dwCloseOption = OLECLOSE_SAVEIFDIRTY);
```  
  
### <a name="parameters"></a>參數  
 `dwCloseOption`  
 旗標，指定當它傳回至載入的狀態，OLE 項目儲存在哪些情況之下。 它可以包含下列值之一：  
  
- `OLECLOSE_SAVEIFDIRTY`儲存 OLE 項目。  
  
- `OLECLOSE_NOSAVE`不要儲存 OLE 項目。  
  
- `OLECLOSE_PROMPTSAVE`提示使用者是否要儲存 OLE 項目。  
  
### <a name="remarks"></a>備註  
 OLE 項目不在執行時，此函式沒有任何作用。  
  
 如需詳細資訊，請參閱[IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922) Windows SDK 中。  
  
##  <a name="coleclientitem"></a>COleClientItem::COleClientItem  
 建構`COleClientItem`物件，並將它加入至容器文件的文件項目集合，其中建構 c + + 物件，並不會執行任何 OLE 初始化。  
  
```  
COleClientItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pContainerDoc`  
 容器文件會包含此項目的指標。 這可以是任何[COleDocument](../../mfc/reference/coledocument-class.md)衍生項目。  
  
### <a name="remarks"></a>備註  
 如果您要傳入**NULL**指標，沒有新增對容器文件。 您必須明確呼叫[COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem)。  
  
 使用 OLE 項目之前，您必須呼叫其中一個下建立成員函式：  
  
- [CreateFromClipboard](#createfromclipboard)  
  
- [CreateFromData](#createfromdata)  
  
- [CreateFromFile](#createfromfile)  
  
- [CreateStaticFromClipboard](#createstaticfromclipboard)  
  
- [CreateStaticFromData](#createstaticfromdata)  
  
- [CreateLinkFromClipboard](#createlinkfromclipboard)  
  
- [CreateLinkFromData](#createlinkfromdata)  
  
- [CreateLinkFromFile](#createlinkfromfile)  
  
- [CreateNewItem](#createnewitem)  
  
- [CreateCloneFrom](#createclonefrom)  
  
##  <a name="convertto"></a>COleClientItem::ConvertTo  
 呼叫此成員函式，將項目所指定之類型為`clsidNew`。  
  
```  
virtual BOOL ConvertTo(REFCLSID clsidNew);
```  
  
### <a name="parameters"></a>參數  
 `clsidNew`  
 目標類型的類別識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 這稱為自動[COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)。 您不需要直接呼叫它。  
  
##  <a name="copytoclipboard"></a>COleClientItem::CopyToClipboard  
 呼叫此函式可將 OLE 項目複製到剪貼簿。  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bIncludeLink`  
 **TRUE**如果連結資訊應該複製到剪貼簿，讓連結的項目貼上，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 一般而言，撰寫從 [編輯] 功能表的 [複製或剪下] 命令的訊息處理常式時呼叫此函式。 如果您想要實作 [複製或剪下] 命令，您必須實作應用程式容器中的項目選取。  
  
 如需詳細資訊，請參閱[OleSetClipboard](http://msdn.microsoft.com/library/windows/desktop/ms686623) Windows SDK 中。  
  
##  <a name="createclonefrom"></a>COleClientItem::CreateCloneFrom  
 呼叫此函式可建立指定之 OLE 項目的複本。  
  
```  
BOOL CreateCloneFrom(const COleClientItem* pSrcItem);
```  
  
### <a name="parameters"></a>參數  
 *pSrcItem*  
 要複製的 OLE 項目指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 是與來源項目相同的副本。 您可以使用此函式來支援復原作業。  
  
##  <a name="createfromclipboard"></a>COleClientItem::CreateFromClipboard  
 呼叫此函式可從剪貼簿的內容中建立內嵌項目。  
  
```  
BOOL CreateFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 *轉譯*  
 旗標，指定伺服器如何呈現 OLE 項目。 如需可能的值，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) Windows SDK 中。  
  
 `cfFormat`  
 指定要建立 OLE 項目時，快取的剪貼簿資料格式。  
  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，如果使用*呈現*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 只有當您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果您省略這個參數時，會使用中的其他欄位的預設值**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您通常呼叫此函式的訊息處理常式中的 [編輯] 功能表中的 [貼上] 命令。 (如果貼上 命令會啟用由架構[CanPaste](#canpaste)成員函式傳回非零值。)  
  
 如需詳細資訊，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="createfromdata"></a>COleClientItem::CreateFromData  
 呼叫此函式，建立內嵌項目從`COleDataObject`物件。  
  
```  
BOOL CreateFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指標[COleDataObject](../../mfc/reference/coledataobject-class.md)從中 OLE 項目是要建立的物件。  
  
 *轉譯*  
 旗標，指定伺服器如何呈現 OLE 項目。 如需可能的值，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) Windows SDK 中。  
  
 `cfFormat`  
 指定要建立 OLE 項目時，快取的剪貼簿資料格式。  
  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，如果使用*呈現*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 只有當您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果您省略這個參數時，會使用中的其他欄位的預設值**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 資料傳輸作業，例如貼上剪貼簿或拖放作業，從提供`COleDataObject`包含資訊的伺服器應用程式所提供的物件。 通常用於覆寫[CView::OnDrop](../../mfc/reference/cview-class.md#ondrop)。  
  
 如需詳細資訊，請參閱[OleCreateFromData](http://msdn.microsoft.com/library/windows/desktop/ms691211)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="createfromfile"></a>COleClientItem::CreateFromFile  
 呼叫此函式可從檔案建立內嵌的 OLE 項目。  
  
```  
BOOL CreateFromFile(
    LPCTSTR lpszFileName,  
    REFCLSID clsid = CLSID_NULL,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszFileName`  
 建立 OLE 項目檔案名稱的指標。  
  
 `clsid`  
 保留供未來使用。  
  
 *轉譯*  
 旗標，指定伺服器如何呈現 OLE 項目。 如需可能的值，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) Windows SDK 中。  
  
 `cfFormat`  
 指定要建立 OLE 項目時，快取的剪貼簿資料格式。  
  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，如果使用*呈現*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 只有當您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果您省略這個參數時，會使用中的其他欄位的預設值**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 架構會呼叫此函式從[COleInsertDialog::CreateItem](../../mfc/reference/coleinsertdialog-class.md#createitem)如果使用者會選擇 [插入物件] 對話方塊的 [確定] 時已選取 [檔案] 按鈕建立。  
  
 如需詳細資訊，請參閱[OleCreateFromFile](http://msdn.microsoft.com/library/windows/desktop/ms690116)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="createlinkfromclipboard"></a>COleClientItem::CreateLinkFromClipboard  
 呼叫此函式可從剪貼簿的內容中建立連結的項目。  
  
```  
BOOL CreateLinkFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 *轉譯*  
 旗標，指定伺服器如何呈現 OLE 項目。 如需可能的值，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) Windows SDK 中。  
  
 `cfFormat`  
 指定要建立 OLE 項目時，快取的剪貼簿資料格式。  
  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，如果使用*呈現*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 只有當您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果您省略這個參數時，會使用中的其他欄位的預設值**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您通常呼叫此函式的訊息處理常式從 [編輯] 功能表上貼上連結命令。 (貼上連結已啟用命令的預設實作中[COleDocument](../../mfc/reference/coledocument-class.md)如果剪貼簿包含可連結到 OLE 項目。)  
  
 如需詳細資訊，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="createlinkfromdata"></a>COleClientItem::CreateLinkFromData  
 呼叫此函式來建立連結的項目從`COleDataObject`物件。  
  
```  
BOOL CreateLinkFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指標[COleDataObject](../../mfc/reference/coledataobject-class.md)從中 OLE 項目是要建立的物件。  
  
 *轉譯*  
 旗標，指定伺服器如何呈現 OLE 項目。 如需可能的值，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) Windows SDK 中。  
  
 `cfFormat`  
 指定要建立 OLE 項目時，快取的剪貼簿資料格式。  
  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，如果使用*呈現*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 只有當您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果您省略這個參數時，會使用中的其他欄位的預設值**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 這在卸除作業期間時呼叫使用者指出應建立的連結。 它也可以用來處理編輯貼上 命令。 呼叫此方法中的 framework`COleClientItem::CreateLinkFromClipboard`和[COlePasteSpecialDialog::CreateItem](../../mfc/reference/colepastespecialdialog-class.md#createitem) Link 選項已選取時。  
  
 如需詳細資訊，請參閱[OleCreateLinkFromData](http://msdn.microsoft.com/library/windows/desktop/ms680731)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="createlinkfromfile"></a>COleClientItem::CreateLinkFromFile  
 呼叫此函式可從檔案建立連結的 OLE 項目。  
  
```  
BOOL CreateLinkFromFile(
    LPCTSTR lpszFileName,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszFileName`  
 建立 OLE 項目檔案名稱的指標。  
  
 *轉譯*  
 旗標，指定伺服器如何呈現 OLE 項目。 如需可能的值，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) Windows SDK 中。  
  
 `cfFormat`  
 指定要建立 OLE 項目時，快取的剪貼簿資料格式。  
  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，如果使用*呈現*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 只有當您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果您省略這個參數時，會使用中的其他欄位的預設值**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果使用者會選擇 [插入物件] 對話方塊的 [確定] 時已選取 [檔案] 按鈕建立和連結核取方塊已核取，架構會呼叫此函式。 它從呼叫[COleInsertDialog::CreateItem](../../mfc/reference/coleinsertdialog-class.md#createitem)。  
  
 如需詳細資訊，請參閱[OleCreateLinkToFile](http://msdn.microsoft.com/library/windows/desktop/ms678434)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="createnewitem"></a>COleClientItem::CreateNewItem  
 呼叫此函式，建立內嵌項目。此函式會啟動伺服器應用程式，可讓使用者建立 OLE 項目。  
  
```  
BOOL CreateNewItem(
    REFCLSID clsid,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 唯一識別要建立的 OLE 項目類型的識別碼。  
  
 *轉譯*  
 旗標，指定伺服器如何呈現 OLE 項目。 如需可能的值，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) Windows SDK 中。  
  
 `cfFormat`  
 指定要建立 OLE 項目時，快取的剪貼簿資料格式。  
  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，如果使用*呈現*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 只有當您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果您省略這個參數時，會使用中的其他欄位的預設值**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果使用者從選擇選擇 [確定] 插入物件對話方塊中選取建立新的按鈕時，架構會呼叫此函式。  
  
 如需詳細資訊，請參閱[OleCreate](http://msdn.microsoft.com/library/windows/desktop/ms678409)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="createstaticfromclipboard"></a>COleClientItem::CreateStaticFromClipboard  
 呼叫此函式可從剪貼簿的內容建立靜態項目。  
  
```  
BOOL CreateStaticFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 *轉譯*  
 旗標，指定伺服器如何呈現 OLE 項目。 如需可能的值，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) Windows SDK 中。  
  
 `cfFormat`  
 指定要建立 OLE 項目時，快取的剪貼簿資料格式。  
  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，如果使用*呈現*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 只有當您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果您省略這個參數時，會使用中的其他欄位的預設值**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 靜態項目包含展示檔資料，但不是原生資料;因此它不能編輯。 您通常呼叫此函式，如果[CreateFromClipboard](#createfromclipboard)成員函式會失敗。  
  
 如需詳細資訊，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="createstaticfromdata"></a>COleClientItem::CreateStaticFromData  
 呼叫此函式，建立靜態項目從`COleDataObject`物件。  
  
```  
BOOL CreateStaticFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指標[COleDataObject](../../mfc/reference/coledataobject-class.md)從中 OLE 項目是要建立的物件。  
  
 *轉譯*  
 旗標，指定伺服器如何呈現 OLE 項目。 如需可能的值，請參閱[OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) Windows SDK 中。  
  
 `cfFormat`  
 指定要建立 OLE 項目時，快取的剪貼簿資料格式。  
  
 `lpFormatEtc`  
 指標[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，如果使用*呈現*是**OLERENDER_FORMAT**或**OLERENDER_DRAW**。 只有當您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果您省略這個參數時，會使用中的其他欄位的預設值**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 靜態項目包含展示檔資料，但不是原生資料;因此，它不能編輯。 基本上，這是與相同[CreateStaticFromClipboard](#createstaticfromclipboard)不同之處在於您可以從任意建立靜態項目`COleDataObject`，而不只是從剪貼簿。  
  
 用於[COlePasteSpecialDialog::CreateItem](../../mfc/reference/colepastespecialdialog-class.md#createitem)選取靜態時。  
  
 如需詳細資訊，請參閱[OleCreateStaticFromData](http://msdn.microsoft.com/library/windows/desktop/ms687290)， [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
##  <a name="deactivate"></a>COleClientItem::Deactivate  
 呼叫此函式可停用 OLE 項目，並釋放任何相關聯的資源。  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>備註  
 當使用者按一下滑鼠的項目範圍外的用戶端區域上，您通常停用使用中就地 OLE 項目。 請注意，停用 OLE 項目將會捨棄其復原狀態，無法呼叫[ReactivateAndUndo](#reactivateandundo)成員函式。  
  
 如果您的應用程式支援復原，請勿呼叫`Deactivate`; 相反地，呼叫[DeactivateUI](#deactivateui)。  
  
 如需詳細資訊，請參閱[IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700) Windows SDK 中。  
  
##  <a name="deactivateui"></a>COleClientItem::DeactivateUI  
 當使用者停用就地啟動時的項目時，請呼叫此函式。  
  
```  
void DeactivateUI();
```  
  
### <a name="remarks"></a>備註  
 此函式會還原到其原始狀態，隱藏任何功能表和其他控制項，可建立就地啟用的容器應用程式的使用者介面。  
  
 此函式不會清除復原的狀態資訊項目。 資訊會保留，讓[ReactivateAndUndo](#reactivateandundo)稍後可用來執行復原命令在伺服器應用程式，以防容器的 [復原] 命令會停用項目之後，立即選擇。  
  
 如需詳細資訊，請參閱[IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700) Windows SDK 中。  
  
##  <a name="delete"></a>COleClientItem::Delete  
 呼叫此函式可從容器文件刪除 OLE 項目。  
  
```  
void Delete(BOOL bAutoDelete = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bAutoDelete`  
 指定是否要從文件中移除項目。  
  
### <a name="remarks"></a>備註  
 此函數會呼叫[發行](#release)成員函式，依次刪除項目，永久移除 OLE 項目文件的 c + + 物件。 如果內嵌 OLE 項目，會刪除原生資料的項目。 它一律會關閉執行中的伺服器。因此，如果項目是開啟的連結，此函式會關閉它。  
  
##  <a name="dodragdrop"></a>COleClientItem::DoDragDrop  
 呼叫`DoDragDrop`成員函式來執行拖放作業。  
  
```  
DROPEFFECT DoDragDrop(
    LPCRECT lpItemRect,  
    CPoint ptOffset,  
    BOOL bIncludeLink = FALSE,  
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,  
    LPCRECT lpRectStartDrag = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpItemRect`  
 在工作區座標 （像素） 的螢幕上項目的矩形。  
  
 `ptOffset`  
 從位移`lpItemRect`滑鼠位置在拖曳時的所在。  
  
 `bIncludeLink`  
 將此設**TRUE**如果連結資料應該複製到剪貼簿。 將它設定為**FALSE**如果伺服器應用程式不支援的連結。  
  
 `dwEffects`  
 決定拖曳來源會允許在拖曳作業的效果。  
  
 `lpRectStartDrag`  
 實際開始拖曳所定義的矩形的指標。 如需詳細資訊，請參閱接下來的＜備註＞一節。  
  
### <a name="return-value"></a>傳回值  
 `DROPEFFECT` 值。 如果是`DROPEFFECT_MOVE`，應該移除原始的資料。  
  
### <a name="remarks"></a>備註  
 拖放作業不會立即啟動。 它會等候直到滑鼠游標離開所指定的矩形`lpRectStartDrag`，或是直到已通過指定的毫秒數。 如果`lpRectStartDrag`是**NULL**，矩形的大小是一個像素。  
  
 登錄機碼設定所指定的延遲時間。 您可以藉由呼叫變更的延遲時間[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果您未指定延遲時間，會使用預設值是 200 毫秒。 拖放到延遲時間會儲存，如下所示：  
  
-   Windows NT 拖曳延遲時間會儲存在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。  
  
-   Win 儲存 Windows 3.x 拖曳延遲時間。INI 檔案，底下的 [Windows} 一節。  
  
-   Windows 95/98 拖曳延遲時間會儲存在 WIN 的快取版本。INI。  
  
 如需有關如何將延遲的資訊會儲存在登錄或。INI 檔案，請參閱[WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) Windows SDK 中。  
  
##  <a name="doverb"></a>COleClientItem::DoVerb  
 呼叫`DoVerb`執行指定的動詞命令。  
  
```  
virtual BOOL DoVerb(
    LONG nVerb,  
    CView* pView,
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>參數  
 `nVerb`  
 指定要執行的指令動詞。 它可以包含下列其中一項：  
  
|值|意義|符號|  
|-----------|-------------|------------|  
|- 0|主動詞命令|`OLEIVERB_PRIMARY`|  
|- 1|次要的動詞命令|(無)|  
|- 1|顯示編輯項目|`OLEIVERB_SHOW`|  
|- 2|編輯在個別視窗中的項目|`OLEIVERB_OPEN`|  
|- 3|隱藏項目|`OLEIVERB_HIDE`|  
  
 -1 值通常是另一個動詞命令的別名。 如果不支援開啟編輯，-2 會有相同的效果為-1。 如需其他值，請參閱[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) Windows SDK 中。  
  
 `pView`  
 指向 [檢視] 視窗中。這用於伺服器就地啟用。 這個參數應該是**NULL**如果容器應用程式不允許就地啟用。  
  
 `lpMsg`  
 造成要啟動的項目之訊息的指標。  
  
### <a name="return-value"></a>傳回值  
 如果動詞命令執行成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函數會呼叫[Activate](#activate)成員函式來執行的指令動詞。 它也會攔截例外狀況，並向使用者顯示訊息方塊，如果其中一個會擲回。  
  
 如果主要動作是編輯和中指定零`nVerb`啟動參數，伺服器應用程式以允許編輯 OLE 項目。 如果容器應用程式支援就地啟用，編輯即可備妥。 如果容器不支援就地啟用 （或如果未指定 Open 動詞），伺服器會在個別視窗中啟動，並編輯即可那里。 一般而言，當容器應用程式使用者按兩下 OLE 項目中的主要動詞命令的值時，才`nVerb`參數會決定使用者可以採取哪些動作。 不過，如果伺服器支援只有一個動作，會在該動作，不論其中該值會以指定`nVerb`參數。  
  
##  <a name="draw"></a>COleClientItem::Draw  
 呼叫此函式可使用指定的裝置內容指定的週框矩形內繪製 OLE 項目。  
  
```  
BOOL Draw(
    CDC* pDC,  
    LPCRECT lpBounds,  
    DVASPECT nDrawAspect = (DVASPECT)-1);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指標[CDC](../../mfc/reference/cdc-class.md)物件用來繪製 OLE 項目。  
  
 `lpBounds`  
 指標[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或`RECT`結構，定義要在其中繪製 OLE 項目 （以邏輯單位，取決於裝置內容） 的周框。  
  
 `nDrawAspect`  
 指定層面的 OLE 項目，也就是它應如何顯示。 如果`nDrawAspect`為-1，上次使用設定的外觀[SetDrawAspect](#setdrawaspect)用。 如需可能的值，這個旗標的詳細資訊，請參閱[SetDrawAspect](#setdrawaspect)。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 函式可能會使用 OLE 項目所建立的中繼檔表示[OnDraw](../../mfc/reference/coleserveritem-class.md#ondraw)成員函式`COleServerItem`。  
  
 通常您會使用**繪製**螢幕顯示將傳遞做為螢幕裝置內容`pDC`。 在此情況下，您需要指定只有前兩個參數。  
  
 `lpBounds`參數會識別 （相對於其目前的對應模式） 的目標裝置內容中的矩形。 呈現可能牽涉到將圖片的比例，以及可以由容器應用程式用來強制顯示的檢視之間列印的最後一個影像縮放比例的檢視。  
  
 如需詳細資訊，請參閱[iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655) Windows SDK 中。  
  
##  <a name="getactiveview"></a>COleClientItem::GetActiveView  
 傳回在其的項目是就地啟用的檢視。  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 檢視; 指標否則**NULL**如果項目不是就地啟動。  
  
##  <a name="getcachedextent"></a>COleClientItem::GetCachedExtent  
 呼叫此函式可擷取 OLE 項目的大小。  
  
```  
BOOL GetCachedExtent(
    LPSIZE lpSize,  
    DVASPECT nDrawAspect = (DVASPECT)-1);
```  
  
### <a name="parameters"></a>參數  
 `lpSize`  
 指標**大小**結構或[CSize](../../atl-mfc-shared/reference/csize-class.md)將會收到大小資訊的物件。  
  
 `nDrawAspect`  
 指定要擷取其界限的 OLE 項目的外觀。 可能的值，請參閱[SetDrawAspect](#setdrawaspect)。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零0，表示 OLE 項目是空白。  
  
### <a name="remarks"></a>備註  
 此函式會提供相同的資訊[GetExtent](#getextent)。 不過，您可以呼叫`GetCachedExtent`取得在處理期間的範圍資訊的其他 OLE 處理常式，例如[OnChange](#onchange)。 維度是在`MM_HIMETRIC`單位。  
  
 這可能是因為`GetCachedExtent`使用[IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)介面，而不是使用[IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709)介面，以取得此項目的範圍。 **IViewObject2** COM 物件會快取前一個呼叫中使用的範圍資訊[iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)。  
  
 如需詳細資訊，請參閱[IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032) Windows SDK 中。  
  
##  <a name="getclassid"></a>COleClientItem::GetClassID  
 傳回的類別識別碼的項目至所指向的記憶體`pClassID`。  
  
```  
void GetClassID(CLSID* pClassID) const;  
```  
  
### <a name="parameters"></a>參數  
 `pClassID`  
 指標類型的應用程式識別項[CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424)擷取的類別識別碼。 如需有關詳細**CLSID**，請參閱 Windows SDK。  
  
### <a name="remarks"></a>備註  
 類別識別碼是 128 位元數字，可唯一識別的應用程式的編輯項目。  
  
 如需詳細資訊，請參閱[ipersist:: Getclassid](http://msdn.microsoft.com/library/windows/desktop/ms688664) Windows SDK 中。  
  
##  <a name="getclipboarddata"></a>COleClientItem::GetClipboardData  
 呼叫此函式可取得`COleDataSource`物件，其中包含會將呼叫放置在剪貼簿的所有資料[CopyToClipboard](#copytoclipboard)成員函式。  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDataSource`  
 指標[COleDataSource](../../mfc/reference/coledatasource-class.md)將 OLE 項目中接收資料所包含的物件。  
  
 `bIncludeLink`  
 **TRUE**連結資料應該包含，否則如果**FALSE**。  
  
 `lpOffset`  
 從原點的物件，像素為單位的滑鼠游標的位移。  
  
 `lpSize`  
 物件，像素為單位的大小。  
  
### <a name="remarks"></a>備註  
 `GetClipboardData`預設實作稱為[ongetclipboarddata 而自動發生](#ongetclipboarddata)。 覆寫`OnGetClipboardData`只有當您想要提供除了所提供的資料格式`CopyToClipboard`。 將放在這些格式`COleDataSource`物件之前或之後呼叫`CopyToClipboard`，然後將傳遞`COleDataSource`物件[COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard)函式。 例如，如果您想隨附剪貼簿上其容器文件中的 OLE 項目的位置，您會定義您自己的格式來傳遞該資訊並將它放在`COleDataSource`之前先呼叫`CopyToClipboard`。  
  
##  <a name="getdocument"></a>COleClientItem::GetDocument  
 呼叫此函式可取得包含 OLE 項目的文件的指標。  
  
```  
COleDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 文件，其中包含 OLE 項目指標。 **NULL**如果項目不是文件的一部分。  
  
### <a name="remarks"></a>備註  
 此指標可讓您存取`COleDocument`物件做為引數傳遞`COleClientItem`建構函式。  
  
##  <a name="getdrawaspect"></a>COleClientItem::GetDrawAspect  
 呼叫`GetDrawAspect`成員函式，以判斷目前 「 外觀 」 或項目的檢視。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 中的值`DVASPECT`列舉型別，其值列的參考中[SetDrawAspect](#setdrawaspect)。  
  
### <a name="remarks"></a>備註  
 層面指定的項目是要轉譯的方式。  
  
##  <a name="getextent"></a>COleClientItem::GetExtent  
 呼叫此函式可擷取 OLE 項目的大小。  
  
```  
BOOL GetExtent(
    LPSIZE lpSize,  
    DVASPECT nDrawAspect = (DVASPECT)- 1);
```  
  
### <a name="parameters"></a>參數  
 `lpSize`  
 指標**大小**結構或`CSize`將會收到大小資訊的物件。  
  
 `nDrawAspect`  
 指定要擷取其界限的 OLE 項目的外觀。 可能的值，請參閱[SetDrawAspect](#setdrawaspect)。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零0，表示 OLE 項目是空白。  
  
### <a name="remarks"></a>備註  
 如果伺服器應用程式使用 Microsoft Foundation 類別庫所撰寫，這個函式會導致[OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)成員函式對應`COleServerItem`来呼叫的物件。 請注意擷取的大小可能不同於上次所設定的大小[SetExtent](#setextent)成員函式，則為所指定的大小`SetExtent`會被視為建議。 維度是在`MM_HIMETRIC`單位。  
  
> [!NOTE]
>  請勿呼叫`GetExtent`OLE 處理常式處理這類[OnChange](#onchange)。 呼叫[GetCachedExtent](#getcachedextent)改為。  
  
 如需詳細資訊，請參閱[IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325) Windows SDK 中。  
  
##  <a name="geticonfromregistry"></a>COleClientItem::GetIconFromRegistry  
 呼叫此成員函式可擷取特定的 CLSID 的伺服器相關聯的圖示資源的控制代碼。  
  
```  
HICON GetIconFromRegistry() const;  
  
static HICON GetIconFromRegistry(CLSID& clsid);
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 參考的 CLSID 與圖示相關聯的伺服器。  
  
### <a name="return-value"></a>傳回值  
 有效的控制代碼的圖示資源，或**NULL**如果找不到伺服器的圖示或預設的圖示。  
  
### <a name="remarks"></a>備註  
 此成員函式不會啟動伺服器或取得圖示，以動態方式，即使伺服器已在執行。 相反地，此成員函式開啟伺服器的可執行映像，並擷取靜態與已註冊的伺服器相關的圖示。  
  
##  <a name="geticonicmetafile"></a>COleClientItem::GetIconicMetafile  
 擷取用來繪製的項目圖示的中繼檔。  
  
```  
HGLOBAL GetIconicMetafile();
```  
  
### <a name="return-value"></a>傳回值  
 中繼檔成功; 如果控制代碼否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果沒有目前的圖示，則會傳回預設圖示。 這會自動呼叫由 MFC/OLE 對話，和通常不會直接呼叫。  
  
 此函式也會呼叫[SetIconicMetafile](#seticonicmetafile)快取供稍後使用中繼檔。  
  
##  <a name="getinplacewindow"></a>COleClientItem::GetInPlaceWindow  
 呼叫`GetInPlaceWindow`成員函式來進行就地編輯的視窗中開啟項目取得的指標。  
  
```  
CWnd* GetInPlaceWindow();
```  
  
### <a name="return-value"></a>傳回值  
 指標的項目就地編輯視窗。**NULL**項目是否不在作用中或它的伺服器無法使用。  
  
### <a name="remarks"></a>備註  
 只能針對就地啟用作用中的項目應該呼叫此函式。  
  
##  <a name="getitemstate"></a>COleClientItem::GetItemState  
 呼叫此函式可取得 OLE 項目的目前狀態。  
  
```  
UINT GetItemState() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A **COleClientItem::ItemState**列舉值，它可以是下列其中之一： `emptyState`， **loadedState**， `openState`， `activeState`， `activeUIState`。 如需這些狀態資訊，請參閱文章[容器： 用戶端項目狀態](../../mfc/containers-client-item-states.md)。  
  
### <a name="remarks"></a>備註  
 若要將 OLE 項目的狀態變更時，會收到通知，請使用[OnChange](#onchange)成員函式。  
  
 如需詳細資訊，請參閱文章[容器： 用戶端項目狀態](../../mfc/containers-client-item-states.md)。  
  
##  <a name="getlaststatus"></a>COleClientItem::GetLastStatus  
 傳回最後一個 OLE 作業的狀態碼。  
  
```  
SCODE GetLastStatus() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `SCODE` 值。  
  
### <a name="remarks"></a>備註  
 成員函式，會傳回**BOOL**值**FALSE**，或其他成員函式，會傳回**NULL**，`GetLastStatus`傳回更詳細的失敗資訊。 請注意，大部分 OLE 成員函式會擲回例外狀況的更嚴重的錯誤。 在解譯的特定資訊`SCODE`取決於上次傳回的基礎 OLE 呼叫`SCODE`值。  
  
 如需有關`SCODE`，請參閱[結構 COM 錯誤碼的](http://msdn.microsoft.com/library/windows/desktop/ms690088)Windows SDK 文件中。  
  
##  <a name="getlinkupdateoptions"></a>COleClientItem::GetLinkUpdateOptions  
 呼叫此函式可取得 OLE 項目連結更新選項的目前值。  
  
```  
OLEUPDATE GetLinkUpdateOptions();
```  
  
### <a name="return-value"></a>傳回值  
 下列其中一個值：  
  
- `OLEUPDATE_ALWAYS`更新連結的項目，請盡可能。 此選項會支援連結 對話方塊中的自動連結更新選項按鈕。  
  
- `OLEUPDATE_ONCALL`更新連結的項目，只能從容器應用程式的要求上 (當[UpdateLink](#updatelink)成員函式呼叫)。 此選項會支援連結 對話方塊中手動連結更新選項按鈕。  
  
### <a name="remarks"></a>備註  
 這是進階的操作。  
  
 此函式就會呼叫自動[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)類別。  
  
 如需詳細資訊，請參閱[IOleLink::GetUpdateOptions](http://msdn.microsoft.com/library/windows/desktop/ms680100) Windows SDK 中。  
  
##  <a name="gettype"></a>COleClientItem::GetType  
 呼叫此函式可判斷是否 OLE 項目是內嵌或連結，或靜態。  
  
```  
OLE_OBJTYPE GetType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 不帶正負號的整數的下列值之一：  
  
- `OT_LINK`OLE 項目是一個連結。  
  
- `OT_EMBEDDED`內嵌 OLE 項目。  
  
- `OT_STATIC`OLE 項目是靜態的也就是說，它只包含呈現的資料，不原生資料，並因此無法編輯。  
  
##  <a name="getusertype"></a>COleClientItem::GetUserType  
 呼叫此函式可取得使用者可見的字串描述 OLE 項目類型，例如 「 Word 文件 」。  
  
```  
void GetUserType(
    USERCLASSTYPE nUserClassType,  
    CString& rString);
```  
  
### <a name="parameters"></a>參數  
 *nUserClassType*  
 值，指出所需的 variant 描述 OLE 項目類型的字串。 這可以有下列值之一：  
  
- `USERCLASSTYPE_FULL`完整的型別名稱顯示給使用者。  
  
- `USERCLASSTYPE_SHORT`使用快顯功能表和 [編輯連結] 對話方塊中指定簡短名稱 （最多 15 個字元）。  
  
- `USERCLASSTYPE_APPNAME`服務類別的應用程式名稱。  
  
 `rString`  
 若要參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)所要傳回的字串描述 OLE 項目的型別物件。  
  
### <a name="remarks"></a>備註  
 這通常是系統註冊資料庫中的項目。  
  
 如果要求，但無法使用的完整類型名稱，會改用簡短名稱。 如果沒有 OLE 項目類型的項目是在資料庫中找到註冊，或如果沒有註冊的 OLE 項目類型的使用者型別，則使用者類型目前儲存在會使用 OLE 項目。 如果該使用者的類型名稱為空字串，則會使用 「 未知的物件 」。  
  
 如需詳細資訊，請參閱[IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643) Windows SDK 中。  
  
##  <a name="isinplaceactive"></a>COleClientItem::IsInPlaceActive  
 呼叫此函式的 OLE 項目就地啟用作用中。  
  
```  
BOOL IsInPlaceActive() const;  
```  
  
### <a name="return-value"></a>傳回值  
 OLE 項目就地啟用作用中; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 通常會執行不同的邏輯，根據是否正在就地編輯項目。 函式會檢查目前的項目狀態是否等於 `activeState`或`activeUIState`。  
  
##  <a name="islinkuptodate"></a>COleClientItem::IsLinkUpToDate  
 呼叫此函式可查看 OLE 項目是否為最新狀態。  
  
```  
BOOL IsLinkUpToDate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 OLE 項目是最新狀態; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 連結的項目可以是過期如果已更新它的來源文件。 內嵌項目，其中包含連結，其中可以同樣地會變成過期。 此函式會遞迴核取的 OLE 項目。 請注意，判斷是否已過期的 OLE 項目可能成本實際上正在執行更新。  
  
 這稱為自動[COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)實作。  
  
 如需詳細資訊，請參閱[IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624) Windows SDK 中。  
  
##  <a name="ismodified"></a>COleClientItem::IsModified  
 呼叫此函式，以查看是否 OLE 項目是已損毀 （修改自上次儲存後）。  
  
```  
BOOL IsModified() const;  
```  
  
### <a name="return-value"></a>傳回值  
 OLE 項目是已損毀; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[IPersistStorage::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms683910) Windows SDK 中。  
  
##  <a name="isopen"></a>COleClientItem::IsOpen  
 呼叫此函式，以查看 OLE 項目是否為開啟。也就是說，在個別視窗中執行的伺服器應用程式的執行個體中開啟。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 OLE 項目開啟; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 它用來判斷何時要繪製的物件與影線圖樣。 開啟的物件應該規劃圖樣，該物件之上繪製。 您可以使用[CRectTracker](../../mfc/reference/crecttracker-class.md)物件來完成這項作業。  
  
##  <a name="isrunning"></a>COleClientItem::IsRunning  
 呼叫此函式，以查看是否正在執行的 OLE 項目。也就是項目是否已載入及執行伺服器應用程式中。  
  
```  
BOOL IsRunning() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果正在執行的 OLE 項目; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[OleIsRunning](http://msdn.microsoft.com/library/windows/desktop/ms688705) Windows SDK 中。  
  
##  <a name="onactivate"></a>COleClientItem::OnActivate  
 由架構呼叫以通知，只要啟用後就地項目。  
  
```  
virtual void OnActivate();
```  
  
### <a name="remarks"></a>備註  
 請注意，呼叫此函式指示伺服器正在執行，不是用來表示容器應用程式中確認已安裝使用者介面。 此時，該物件沒有作用中使用者介面 (不是`activeUIState`)。 不安裝其功能表或工具列。 [OnActivateUI](#onactivateui)發生此情況時，呼叫成員函式。  
  
 預設實作會呼叫[OnChange](#onchange)成員函式**OLE_CHANGEDSTATE**做為參數。 覆寫這個函式來執行自訂處理項目時就地啟用作用中。  
  
##  <a name="onactivateui"></a>COleClientItem::OnActivateUI  
 這個架構會呼叫`OnActivateUI`當物件已進入作用中的 UI 狀態。  
  
```  
virtual void OnActivateUI();
```  
  
### <a name="remarks"></a>備註  
 物件現在已安裝的工具列和功能表。  
  
 預設實作會記住伺服器`HWND`稍後**GetServerWindow**呼叫。  
  
##  <a name="onchange"></a>COleClientItem::OnChange  
 在使用者修改、 儲存，或關閉 OLE 項目時由架構呼叫。  
  
```  
virtual void OnChange(
    OLE_NOTIFICATION nCode,  
    DWORD dwParam);
```  
  
### <a name="parameters"></a>參數  
 `nCode`  
 伺服器的原因會變更此項目。 它可以包含下列值之一：  
  
- `OLE_CHANGED`OLE 項目的外觀已變更。  
  
- `OLE_SAVED`已儲存 OLE 項目。  
  
- `OLE_CLOSED`OLE 項目已關閉。  
  
- `OLE_CHANGED_STATE`OLE 項目已從某個狀態變更為另一個。  
  
 `dwParam`  
 如果`nCode`是`OLE_SAVED`或`OLE_CLOSED`，未使用此參數。 如果`nCode`是`OLE_CHANGED`，此參數指定的 OLE 項目已變更外觀。 可能的值，請參閱`dwParam`參數[COleClientItem::Draw](#draw)。 如果`nCode`是`OLE_CHANGED_STATE`，這個參數是**COleClientItem::ItemState**列舉值，並說明所輸入的狀態。 它可以有下列值之一： `emptyState`， **loadedState**， `openState`， `activeState`，或`activeUIState`。  
  
### <a name="remarks"></a>備註  
 (如果使用 Mfc 程式庫來撰寫伺服器應用程式，以回應呼叫此函式`Notify`的成員函式`COleServerDoc`或`COleServerItem`。)預設實作會將標示容器文件為，如果修改`nCode`是`OLE_CHANGED`或`OLE_SAVED`。  
  
 如`OLE_CHANGED_STATE`，從傳回的目前狀態[GetItemState](#getitemstate)仍會舊的狀態，表示目前在這個狀態變更之前的狀態。  
  
 覆寫此函式以回應中的 OLE 項目狀態變更。 通常您會藉由讓失效的區域中顯示的項目更新項目的外觀。 呼叫基底類別實作您的覆寫的開頭。  
  
##  <a name="onchangeitemposition"></a>COleClientItem::OnChangeItemPosition  
 由架構呼叫以告知就地啟用期間變更 OLE 項目範圍的容器。  
  
```  
virtual BOOL OnChangeItemPosition(const CRect& rectPos);
```  
  
### <a name="parameters"></a>參數  
 *rectPos*  
 表示相對於容器應用程式的用戶端區域的項目位置。  
  
### <a name="return-value"></a>傳回值  
 如果已成功變更項目的位置，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 預設實作會決定新的顯示矩形的 OLE 項目並呼叫[SetItemRects](#setitemrects)含有新值。 預設實作會計算項目的可見的矩形，並將該資訊傳遞至伺服器。  
  
 覆寫此函式可調整大小/移動作業套用特殊規則。 如果應用程式撰寫 MFC 中，此呼叫結果，因為伺服器呼叫[COleServerDoc::RequestPositionChange](../../mfc/reference/coleserverdoc-class.md#requestpositionchange)。  
  
##  <a name="ondeactivate"></a>COleClientItem::OnDeactivate  
 當 OLE 項目轉換從就地使用中狀態時，由架構呼叫 ( `activeState`) 至載入的狀態，這表示它已停用就地啟動之後。  
  
```  
virtual void OnDeactivate();
```  
  
### <a name="remarks"></a>備註  
 請注意，呼叫此函式指出 OLE 項目已關閉，無法從容器應用程式已移除其使用者介面。 當發生這種情況時， [OnDeactivateUI](#ondeactivateui)呼叫成員函式。  
  
 預設實作會呼叫[OnChange](#onchange)成員函式**OLE_CHANGEDSTATE**做為參數。 覆寫這個函式來執行自訂處理停用就地使用中的項目時。 例如，如果您在容器應用程式中支援復原命令，您可以覆寫此函式可捨棄復原狀態，表示上次執行的 OLE 項目上的作業無法復原，當停用項目。  
  
##  <a name="ondeactivateandundo"></a>COleClientItem::OnDeactivateAndUndo  
 當使用者叫用復原命令啟動就地 OLE 項目之後，由架構呼叫。  
  
```  
virtual void OnDeactivateAndUndo();
```  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫[DeactivateUI](#deactivateui)停用伺服器的使用者介面。 如果容器應用程式中實作 [復原] 命令，請覆寫這個函式。 在您的覆寫呼叫此函式的基底類別版本，然後復原您的應用程式中執行的最後一個命令。  
  
 如需詳細資訊，請參閱[IOleInPlaceSite::DeactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms683743) Windows SDK 中。  
  
##  <a name="ondeactivateui"></a>COleClientItem::OnDeactivateUI  
 當使用者停用就地啟動時的項目時呼叫。  
  
```  
virtual void OnDeactivateUI(BOOL bUndoable);
```  
  
### <a name="parameters"></a>參數  
 `bUndoable`  
 指定編輯變更是否可復原。  
  
### <a name="remarks"></a>備註  
 此函式會還原到其原始狀態，隱藏任何功能表和其他控制項，可建立就地啟用的容器應用程式的使用者介面。  
  
 如果`bUndoable`是**FALSE**容器應該停用復原命令，實際上並捨棄復原狀態的容器，因為它會指出伺服器所執行最後一項作業是無法復原。  
  
##  <a name="ondiscardundostate"></a>COleClientItem::OnDiscardUndoState  
 當使用者執行動作可捨棄復原狀態編輯 OLE 項目時由架構呼叫。  
  
```  
virtual void OnDiscardUndoState();
```  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。 如果容器應用程式中實作 [復原] 命令，請覆寫這個函式。 在您覆寫時，捨棄容器應用程式的復原狀態。  
  
 如果伺服器使用 Microsoft Foundation 類別庫所撰寫，伺服器可能會導致呼叫藉由呼叫這個函式[COleServerDoc::DiscardUndoState](../../mfc/reference/coleserverdoc-class.md#discardundostate)。  
  
 如需詳細資訊，請參閱[IOleInPlaceSite::DiscardUndoState](http://msdn.microsoft.com/library/windows/desktop/ms688642) Windows SDK 中。  
  
##  <a name="ongetclipboarddata"></a>COleClientItem::OnGetClipboardData  
 由架構呼叫以取得`COleDataSource`物件，其中包含會將呼叫放置在剪貼簿的所有資料[CopyToClipboard](#copytoclipboard)或[DoDragDrop](#dodragdrop)成員函式。  
  
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
 從原點的像素為單位的物件的指標，滑鼠游標的位移。  
  
 `lpSize`  
 物件，像素為單位的大小指標。  
  
### <a name="return-value"></a>傳回值  
 指標[COleDataSource](../../mfc/reference/coledatasource-class.md)包含剪貼簿資料物件。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會呼叫[GetClipboardData](#getclipboarddata)。  
  
##  <a name="ongetcliprect"></a>COleClientItem::OnGetClipRect  
 這個架構會呼叫`OnGetClipRect`成員函式來取得的裁剪方框座標正在編輯的項目中的位置。  
  
```  
virtual void OnGetClipRect(CRect& rClipRect);
```  
  
### <a name="parameters"></a>參數  
 *rClipRect*  
 類別的物件指標[CRect](../../atl-mfc-shared/reference/crect-class.md)將保留項目的裁剪矩形座標。  
  
### <a name="remarks"></a>備註  
 座標是相對於容器應用程式視窗的用戶端區域的像素為單位。  
  
 預設實作只會傳回在其的項目是就地啟用作用中的檢視之用戶端矩形。  
  
##  <a name="ongetitemposition"></a>COleClientItem::OnGetItemPosition  
 這個架構會呼叫`OnGetItemPosition`成員函式來取得就地正在編輯之項目的座標。  
  
```  
virtual void OnGetItemPosition(CRect& rPosition);
```  
  
### <a name="parameters"></a>參數  
 `rPosition`  
 若要參考[CRect](../../atl-mfc-shared/reference/crect-class.md)將包含的項目位置座標的物件。  
  
### <a name="remarks"></a>備註  
 座標是相對於容器應用程式視窗的用戶端區域的像素為單位。  
  
 此函式的預設實作不做任何動作。 支援就地編輯的應用程式需要它的實作。  
  
##  <a name="ongetwindowcontext"></a>COleClientItem::OnGetWindowContext  
 項目就地啟動時由架構呼叫。  
  
```  
virtual BOOL OnGetWindowContext(
    CFrameWnd** ppMainFrame,  
    CFrameWnd** ppDocFrame,  
    LPOLEINPLACEFRAMEINFO lpFrameInfo);
```  
  
### <a name="parameters"></a>參數  
 `ppMainFrame`  
 主框架視窗的指標的指標。  
  
 `ppDocFrame`  
 指向文件框架視窗的指標。  
  
 `lpFrameInfo`  
 指標[OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737)結構，將會收到框架視窗資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式用來擷取 OLE 項目的父視窗的相關資訊。  
  
 如果容器是 MDI 應用程式，預設實作會傳回指標[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)物件存放至`ppMainFrame`和作用中的指標[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)中物件`ppDocFrame`. 如果容器是 SDI 應用程式，預設實作會傳回指標[CFrameWnd](../../mfc/reference/cframewnd-class.md)物件存放至`ppMainFrame`並傳回**NULL**中`ppDocFrame`。 預設實作也會填入的成員`lpFrameInfo`。  
  
 預設實作不符合應用程式; 時，才會覆寫這個函式例如，如果您的應用程式具有不同於 SDI 或 MDI 使用者介面典範。 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[IOleInPlaceSite::GetWindowContext](http://msdn.microsoft.com/library/windows/desktop/ms694366)和[OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737) Windows SDK 中的結構。  
  
##  <a name="oninsertmenus"></a>COleClientItem::OnInsertMenus  
 在就地啟用容器應用程式的功能表插入空的功能表時由架構呼叫。  
  
```  
virtual void OnInsertMenus(
    CMenu* pMenuShared,  
    LPOLEMENUGROUPWIDTHS lpMenuWidths);
```  
  
### <a name="parameters"></a>參數  
 `pMenuShared`  
 指向空的功能表。  
  
 `lpMenuWidths`  
 指向陣列的六**長**指出多少功能表在每個下列功能表群組中的值： 檔案、 編輯、 容器物件，視窗中，說明。 容器應用程式會負責檔、 容器和視窗功能表群組，對應至 0、 2 和 4，這個陣列的項目。  
  
### <a name="remarks"></a>備註  
 這個功能表，然後會傳遞到伺服器，它會插入其本身的功能表，建立複合的功能表。 可以重複呼叫這個函式來建立數個複合功能表。  
  
 預設實作插入`pMenuShared`就地容器功能表; 也就是檔案、 容器和視窗功能表的群組。 [CDocTemplate::SetContainerInfo](../../mfc/reference/cdoctemplate-class.md#setcontainerinfo)用來設定此功能表資源。 預設實作也會將適當的值指派給 0、 2 和 4 中的項目`lpMenuWidths`，取決於功能表資源。 覆寫的預設實作不是適用於您的應用程式; 此函式例如，如果您的應用程式不會使用文件範本關聯的文件類型的資源。 如果您覆寫這個函式，您也應該覆寫[OnSetMenu](#onsetmenu)和[OnRemoveMenus](#onremovemenus)。 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[ioleinplaceframe:: Insertmenus](http://msdn.microsoft.com/library/windows/desktop/ms683987) Windows SDK 中。  
  
##  <a name="onremovemenus"></a>COleClientItem::OnRemoveMenus  
 由架構呼叫以就地啟用結束時，從指定的組合功能表移除容器的功能表。  
  
```  
virtual void OnRemoveMenus(CMenu* pMenuShared);
```  
  
### <a name="parameters"></a>參數  
 `pMenuShared`  
 指向建構所呼叫的複合功能表[OnInsertMenus](#oninsertmenus)成員函式。  
  
### <a name="remarks"></a>備註  
 預設實作會移除`pMenuShared`，不是就地容器功能表、 檔案、 容器和視窗功能表的群組。 覆寫的預設實作不是適用於您的應用程式; 此函式例如，如果您的應用程式不會使用文件範本關聯的文件類型的資源。 如果您覆寫這個函式，您應該可能覆寫[OnInsertMenus](#oninsertmenus)和[OnSetMenu](#onsetmenu)以及。 這是進階可覆寫。  
  
 在子功能表`pMenuShared`可能會由一個以上的複合功能表所共用，如果伺服器具有重複呼叫`OnInsertMenus`。 因此，請勿刪除任何子功能表中的覆寫`OnRemoveMenus`; 您應該只中斷。  
  
 如需詳細資訊，請參閱[IOleInPlaceFrame::RemoveMenus](http://msdn.microsoft.com/library/windows/desktop/ms688685) Windows SDK 中。  
  
##  <a name="onscrollby"></a>COleClientItem::OnScrollBy  
 由架構呼叫以捲動 OLE 項目，以從伺服器回應要求。  
  
```  
virtual BOOL OnScrollBy(CSize sizeExtent);
```  
  
### <a name="parameters"></a>參數  
 *sizeExtent*  
 指定距離，單位為像素 x 和 y 方向捲動。  
  
### <a name="return-value"></a>傳回值  
 如果此項目已捲動; 非零，0，表示捲動不到項目。  
  
### <a name="remarks"></a>備註  
 比方說，如果 OLE 項目是部分可見的使用者移到可見區域外執行就地編輯時，呼叫此函式會將資料指標保持可見。 預設實作不做任何動作。 覆寫此函式可捲軸項目，以指定的數量。 請注意結果向下捲動，可以變更的可見部分的 OLE 項目。 呼叫[SetItemRects](#setitemrects)更新項目的顯示矩形。  
  
 如需詳細資訊，請參閱[IOleInPlaceSite::Scroll](http://msdn.microsoft.com/library/windows/desktop/ms690291) Windows SDK 中。  
  
##  <a name="onsetmenu"></a>COleClientItem::OnSetMenu  
 由架構呼叫兩次就地啟用開始和結束。安裝組合功能表和第二次第一次 (與`holemenu`等於**NULL**) 將它移除。  
  
```  
virtual void OnSetMenu(
    CMenu* pMenuShared,  
    HOLEMENU holemenu,  
    HWND hwndActiveObject);
```  
  
### <a name="parameters"></a>參數  
 `pMenuShared`  
 建構函式所呼叫，以組合功能表指向[OnInsertMenus](#oninsertmenus)成員函式和`InsertMenu`函式。  
  
 `holemenu`  
 所傳回的功能表描述元的控制代碼**OleCreateMenuDescriptor**函式，或**NULL**分派的程式碼是否要移除。  
  
 *hwndActiveObject*  
 OLE 項目的編輯視窗的控制代碼。 這是會從 OLE 接收編輯命令視窗。  
  
### <a name="remarks"></a>備註  
 預設實作會安裝或移除組合功能表，然後呼叫[OleSetMenuDescriptor](http://msdn.microsoft.com/library/windows/desktop/ms692831)函式來安裝或移除分派的程式碼。 如果預設實作不適合您的應用程式，請覆寫這個函式。 如果您覆寫這個函式，您應該可能覆寫[OnInsertMenus](#oninsertmenus)和[OnRemoveMenus](#onremovemenus)以及。 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[OleCreateMenuDescriptor](http://msdn.microsoft.com/library/windows/desktop/ms691415)， [OleSetMenuDescriptor](http://msdn.microsoft.com/library/windows/desktop/ms692831)，和[ioleinplaceframe:: Setmenu](http://msdn.microsoft.com/library/windows/desktop/ms693713) Windows SDK 中。  
  
##  <a name="onshowcontrolbars"></a>COleClientItem::OnShowControlBars  
 由架構呼叫以顯示和隱藏容器應用程式的控制列。  
  
```  
virtual BOOL OnShowControlBars(
    CFrameWnd* pFrameWnd,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 `pFrameWnd`  
 容器應用程式的框架視窗的指標。 這可以是主框架視窗或 MDI 子視窗。  
  
 `bShow`  
 指定是否要顯示或隱藏控制列。  
  
### <a name="return-value"></a>傳回值  
 如果函式呼叫會造成控制列的狀態; 變更為非零0 如果呼叫會不造成任何變更，或如果`pFrameWnd`未指向容器的框架視窗。  
  
### <a name="remarks"></a>備註  
 如果控制列已在所指定的狀態，此函數會傳回 0 *bShow。* 這會發生，例如，如果隱藏的控制列和`bShow`是**FALSE**。  
  
 預設實作會移除最上層框架視窗中的工具列。  
  
##  <a name="onshowitem"></a>COleClientItem::OnShowItem  
 由架構呼叫以顯示 OLE 項目，以便完全看到它在編輯期間。  
  
```  
virtual void OnShowItem();
```  
  
### <a name="remarks"></a>備註  
 當容器應用程式支援內嵌項目的連結時使用 (亦即，如果您有衍生您的文件類別，從[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md))。 就地啟動或 OLE 項目連結來源而且使用者想對其進行編輯期間，會呼叫此函式。 預設實作會啟動容器文件上的第一個檢視。 覆寫此函式可將文件捲動，如此才能看到 OLE 項目。  
  
##  <a name="onupdateframetitle"></a>COleClientItem::OnUpdateFrameTitle  
 由架構呼叫以更新框架視窗的標題列的就地啟用期間。  
  
```  
virtual BOOL OnUpdateFrameTitle();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果這個函式已成功更新框架標題，否則為零。  
  
### <a name="remarks"></a>備註  
 預設實作不會變更的框架視窗標題。 覆寫這個函式，如果您想要不同的畫面格標題您的應用程式，例如"*伺服器應用程式* - *項目*中*docname*」 （如所示，「 MicrosoftExcel-在報表中的試算表。文件 」）。 這是進階可覆寫。  
  
##  <a name="reactivateandundo"></a>COleClientItem::ReactivateAndUndo  
 呼叫此函式以重新啟動 OLE 項目，並復原上次由使用者執行期間就地編輯作業。  
  
```  
BOOL ReactivateAndUndo();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果容器應用程式支援 [復原] 命令，呼叫此函式，如果使用者選擇 [復原] 命令後立即停用 OLE 項目。  
  
 如果伺服器應用程式寫入與 Microsoft Foundation 類別庫，此函式會導致伺服器呼叫[COleServerDoc::OnReactivateAndUndo](../../mfc/reference/coleserverdoc-class.md#onreactivateandundo)。  
  
 如需詳細資訊，請參閱[IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372) Windows SDK 中。  
  
##  <a name="release"></a>COleClientItem::Release  
 呼叫此函式來清除 OLE 項目所使用的資源。  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>參數  
 `dwCloseOption`  
 旗標，指定當它傳回至載入的狀態，OLE 項目儲存在哪些情況之下。 如需可能值的清單，請參閱[COleClientItem::Close](#close)。  
  
### <a name="remarks"></a>備註  
 **發行**稱為`COleClientItem`解構函式。  
  
 如需詳細資訊，請參閱[Iunknown](http://msdn.microsoft.com/library/windows/desktop/ms682317) Windows SDK 中。  
  
##  <a name="reload"></a>COleClientItem::Reload  
 關閉並重新載入項目。  
  
```  
BOOL Reload();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 呼叫`Reload`函式呼叫，為另一種類型的項目啟動項目之後[ActivateAs](#activateas)。  
  
##  <a name="run"></a>COleClientItem::Run  
 執行此項目相關聯的應用程式。  
  
```  
void Run();
```  
  
### <a name="remarks"></a>備註  
 呼叫**執行**成員函式來啟動伺服器應用程式，然後再啟動項目。 這是自動由[Activate](#activate)和[DoVerb](#doverb)，因此通常不需要呼叫此函式。 呼叫此函式，如果需要執行的伺服器，才能設定項目屬性，例如[SetExtent](#setextent)，然後再執行[DoVerb](#doverb)。  
  
##  <a name="setdrawaspect"></a>COleClientItem::SetDrawAspect  
 呼叫`SetDrawAspect`成員函式來設定 「 外觀 」 或項目的檢視。  
  
```  
virtual void SetDrawAspect(DVASPECT nDrawAspect);
```  
  
### <a name="parameters"></a>參數  
 `nDrawAspect`  
 `DVASPECT` 列舉中的值。 這個參數的值可以是下列其中一個：  
  
- `DVASPECT_CONTENT`項目表示的方式，它可以顯示為其容器內部內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目會以圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [列印] 命令，從 [檔案] 功能表來列印。  
  
### <a name="remarks"></a>備註  
 層面可讓您指定的項目所要呈現的是如何[繪製](#draw)時的預設值為該函式`nDrawAspect`使用引數。  
  
 變更圖示 （以及其他直接呼叫 [變更圖示] 對話方塊的對話） 會自動呼叫此函式以啟用由使用者要求時的圖示顯示外觀。  
  
##  <a name="setextent"></a>COleClientItem::SetExtent  
 呼叫此函式可指定多少空間可供 OLE 項目。  
  
```  
void SetExtent(
    const CSize& size,  
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>參數  
 `size`  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，其中包含大小資訊。  
  
 `nDrawAspect`  
 指定的界限所設定的 OLE 項目的外觀。 可能的值，請參閱[SetDrawAspect](#setdrawaspect)。  
  
### <a name="remarks"></a>備註  
 如果伺服器應用程式使用 Microsoft Foundation 類別庫所撰寫，這會導致[OnSetExtent](../../mfc/reference/coleserveritem-class.md#onsetextent)成員函式對應`COleServerItem`来呼叫的物件。 OLE 項目然後可以跟著調整它的顯示畫面。 維度必須是在`MM_HIMETRIC`單位。 當使用者調整大小時 OLE 項目，或支援某種形式的配置交涉，請呼叫此函式。  
  
 如需詳細資訊，請參閱[IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330) Windows SDK 中。  
  
##  <a name="sethostnames"></a>COleClientItem::SetHostNames  
 呼叫此函式可指定容器應用程式的名稱和內嵌 OLE 項目容器的名稱。  
  
```  
void SetHostNames(
    LPCTSTR lpszHost,  
    LPCTSTR lpszHostObj);
```  
  
### <a name="parameters"></a>參數  
 `lpszHost`  
 使用者顯示的容器應用程式名稱的指標。  
  
 `lpszHostObj`  
 識別字串，包含 OLE 項目之容器的指標。  
  
### <a name="remarks"></a>備註  
 如果伺服器應用程式使用 Microsoft Foundation 類別庫所撰寫，此函數會呼叫[OnSetHostNames](../../mfc/reference/coleserverdoc-class.md#onsethostnames)成員函式`COleServerDoc`文件，其中包含 OLE 項目。 當正在編輯 OLE 項目，這項資訊用於視窗的標題。 每次載入容器文件時，架構會呼叫此函式的文件中的所有 OLE 項目。 `SetHostNames`只會套用於內嵌的項目。 您不需要在啟動內嵌的 OLE 項目每次呼叫此函式，進行編輯。  
  
 這也稱為自動的應用程式名稱和文件名稱或不同的名稱儲存檔案時已載入物件。 因此，它通常不需要直接呼叫此函式。  
  
 如需詳細資訊，請參閱[IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642) Windows SDK 中。  
  
##  <a name="seticonicmetafile"></a>COleClientItem::SetIconicMetafile  
 會快取的中繼檔，用來繪製項目的圖示。  
  
```  
BOOL SetIconicMetafile(HGLOBAL hMetaPict);
```  
  
### <a name="parameters"></a>參數  
 `hMetaPict`  
 用於繪製的項目圖示的中繼檔的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用[GetIconicMetafile](#geticonicmetafile)擷取中繼檔。  
  
 `hMetaPict`參數複製到項目; 因此，`hMetaPict`必須由呼叫者釋放。  
  
##  <a name="setitemrects"></a>COleClientItem::SetItemRects  
 呼叫此函式可設定之周框或 OLE 項目顯示矩形。  
  
```  
BOOL SetItemRects(
    LPCRECT lpPosRect = NULL,  
    LPCRECT lpClipRect = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lprcPosRect*  
 指標，該矩形包含 OLE 項目相對於其父視窗，在用戶端座標中的界限。  
  
 *lprcClipRect*  
 指標，包含 OLE 項目相對於其父視窗，在用戶端座標中的可見部分界限的矩形。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫此函式[OnChangeItemPosition](#onchangeitemposition)成員函式。 位置的可見部分 OLE 項目變更時，您應該呼叫此函式。 通常這表示它呼叫從您的檢視[OnSize](../../mfc/reference/cwnd-class.md#onsize)和[OnScrollBy](../../mfc/reference/cview-class.md#onscrollby)成員函式。  
  
 如需詳細資訊，請參閱[IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767) Windows SDK 中。  
  
##  <a name="setlinkupdateoptions"></a>COleClientItem::SetLinkUpdateOptions  
 呼叫此函式可設定指定的連結項目呈現的連結更新選項。  
  
```  
void SetLinkUpdateOptions(OLEUPDATE dwUpdateOpt);
```  
  
### <a name="parameters"></a>參數  
 *dwUpdateOpt*  
 此項目的連結更新選項的值。 此值必須是下列其中一項：  
  
- `OLEUPDATE_ALWAYS`更新連結的項目，請盡可能。 此選項會支援連結 對話方塊中的自動連結更新選項按鈕。  
  
- `OLEUPDATE_ONCALL`更新連結的項目，只能從容器應用程式的要求上 (當[UpdateLink](#updatelink)成員函式呼叫)。 此選項會支援連結 對話方塊中手動連結更新選項按鈕。  
  
### <a name="remarks"></a>備註  
 一般而言，您不應該變更連結 對話方塊中的使用者所選擇的更新選項。  
  
 如需詳細資訊，請參閱[IOleLink::SetUpdateOptions](http://msdn.microsoft.com/library/windows/desktop/ms680120) Windows SDK 中。  
  
##  <a name="setprintdevice"></a>COleClientItem::SetPrintDevice  
 呼叫此函式來變更此項目的列印目標裝置。  
  
```  
BOOL SetPrintDevice(const DVTARGETDEVICE* ptd);  
BOOL SetPrintDevice(const PRINTDLG* ppd);
```  
  
### <a name="parameters"></a>參數  
 `ptd`  
 指標[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)資料結構，其中包含新的列印目標裝置的相關資訊。 可以是**NULL**。  
  
 `ppd`  
 指標[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646940)資料結構，其中包含新的列印目標裝置的相關資訊。 可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函式會更新列印目標裝置的項目，但是不會重新整理簡報快取。 若要更新簡報快取中的項目，呼叫[UpdateLink](#updatelink)。  
  
 此函式的引數包含 OLE 系統用來識別目標裝置的資訊。 **PRINTDLG**結構包含 Windows 用來初始化一般的 [列印] 對話方塊的資訊。 使用者關閉對話方塊之後，Windows 會傳回這個結構中的相關使用者的選取項目資訊。 `m_pd`隸屬[CPrintDialog](../../mfc/reference/cprintdialog-class.md)物件是**PRINTDLG**結構。  
  
 如需此結構的詳細資訊，請參閱[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) Windows SDK 中。  
  
 如需詳細資訊，請參閱[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) Windows SDK 中。  
  
##  <a name="updatelink"></a>COleClientItem::UpdateLink  
 呼叫此函式可立即更新的 OLE 項目展示資料。  
  
```  
BOOL UpdateLink();
```  
  
### <a name="return-value"></a>傳回值  
 非零成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 針對連結的項目，函式會尋找連結來源，以取得新的簡報的 OLE 項目。 此程序可能需要執行一或多個伺服器應用程式，這可能會相當耗時。 針對內嵌的項目，此函數操作以遞迴方式檢查內嵌項目是否包含可能是過期的連結，以及更新它們。 使用者也可以手動更新個別使用 [連結] 對話方塊的連結。  
  
 如需詳細資訊，請參閱[IOleLink::Update](http://msdn.microsoft.com/library/windows/desktop/ms692660) Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例 MFCBIND](../../visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [CDocItem 類別](../../mfc/reference/cdocitem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)
