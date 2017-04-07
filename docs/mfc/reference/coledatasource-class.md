---
title: "COleDataSource 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [C++], MFC support
- Clipboard [C++], OLE support
- uniform data transfer
- OLE [C++], uniform data transfer
- Clipboard [C++], MFC support
- OLE Clipboard [C++], support
- IDataObject, MFC encapsulation
- data transfer [C++], OLE
- COleDataSource class
- OLE data transfer [C++]
- uniform data transfer, OLE
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: cd8f30c3edd7d26b254e7f4a6f153ab0b2fc96da
ms.lasthandoff: 02/24/2017

---
# <a name="coledatasource-class"></a>COleDataSource 類別
做為快取，應用程式在此放置資料，以便在資料傳輸作業 (例如剪貼簿或拖放作業) 期間提供。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDataSource : public CCmdTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDataSource::COleDataSource](#coledatasource)|建構 `COleDataSource` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDataSource::CacheData](#cachedata)|提供資料中指定的格式使用**STGMEDIUM**結構。|  
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|提供資料中指定的格式使用`HGLOBAL`。|  
|[COleDataSource::DelayRenderData](#delayrenderdata)|提供指定的格式來延遲的轉譯中的資料。|  
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|提供在指定之格式的資料`CFile`指標。|  
|[COleDataSource::DelaySetData](#delaysetdata)|針對每一種支援的格式來呼叫`OnSetData`。|  
|[COleDataSource::DoDragDrop](#dodragdrop)|執行拖放作業與資料來源。|  
|[COleDataSource::Empty](#empty)|清空`COleDataSource`資料物件。|  
|[COleDataSource::FlushClipboard](#flushclipboard)|將所有的資料呈現到剪貼簿。|  
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|確認放在剪貼簿上的資料還在那裡。|  
|[COleDataSource::OnRenderData](#onrenderdata)|擷取資料延遲轉譯的一部分。|  
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|擷取資料到`CFile`延遲轉譯的一部分。|  
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|擷取資料到`HGLOBAL`延遲轉譯的一部分。|  
|[COleDataSource::OnSetData](#onsetdata)|要取代的資料呼叫`COleDataSource`物件。|  
|[COleDataSource::SetClipboard](#setclipboard)|數位`COleDataSource`剪貼簿上的物件。|  
  
## <a name="remarks"></a>備註  
 您可以直接建立 OLE 資料來源。 或者， [COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem](../../mfc/reference/coleserveritem-class.md)類別建立 OLE 資料來源，以回應其`CopyToClipboard`和`DoDragDrop`成員函式。 請參閱[COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard)的簡短描述。 覆寫`OnGetClipboardData`OLE 資料來源中的資料中加入額外的剪貼簿格式您用戶端項目或伺服器項目類別的成員函式建立`CopyToClipboard`或`DoDragDrop`成員函式。  
  
 每當您想要準備傳輸的資料，您應該建立這個類別的物件，並填入您使用最適合的方法，為您的資料的資料。 插入資料來源的方式直接受到資料是否立即提供 （立即轉譯） 或依需求 （延遲轉譯）。 每個剪貼簿格式，您可以在此提供藉由傳遞要使用的剪貼簿格式的資料 (以及選用性[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構)，呼叫[DelayRenderData](#delayrenderdata)。  
  
 如需有關資料來源和資料傳輸的詳細資訊，請參閱文章[資料物件和資料來源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。 此外，本文[剪貼簿主題](../../mfc/clipboard.md)描述 OLE 剪貼簿機制。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDataSource`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="cachedata"></a>COleDataSource::CacheData  
 呼叫此函式以指定的格式，在其中的資料期間提供的資料傳輸作業。  
  
```  
void CacheData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料可提供剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構，其中包含指定的格式中的資料。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述提供資料格式。 如果您想要指定其他的格式資訊所指定的剪貼簿格式之外，此參數提供的值`cfFormat`。 如果是**NULL**，會使用預設值中的其他欄位**FORMATETC**結構。  
  
### <a name="remarks"></a>備註  
 您必須提供資料，因為此函數會提供其使用立即轉譯。 資料會快取，直到需要為止。  
  
 提供使用資料[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構。 您也可以使用`CacheGlobalData`成員函式，如果您所提供的資料量是夠小，無法有效地使用傳送`HGLOBAL`。  
  
 在呼叫之後`CacheData` **ptd**成員`lpFormatEtc`和內容`lpStgMedium`資料物件，不是由呼叫者所擁有。  
  
 若要使用延遲的轉譯，呼叫[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源︰ 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="cacheglobaldata"></a>COleDataSource::CacheGlobalData  
 呼叫此函式以指定的格式，在其中的資料期間提供的資料傳輸作業。  
  
```  
void CacheGlobalData(
    CLIPFORMAT cfFormat,  
    HGLOBAL hGlobal,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料可提供剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 *hGlobal*  
 包含指定的格式資料的全域記憶體區塊的控制代碼。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述提供資料格式。 如果您想要指定其他的格式資訊所指定的剪貼簿格式之外，此參數提供的值`cfFormat`。 如果是**NULL**，會使用預設值中的其他欄位**FORMATETC**結構。  
  
### <a name="remarks"></a>備註  
 此函數會提供使用立即呈現，因此呼叫函式; 時，您必須提供資料的資料資料會快取，直到需要為止。 使用`CacheData`如果提供大量的資料，或如果您需要的結構化儲存體中的成員函式。  
  
 若要使用延遲的轉譯，呼叫[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源︰ 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="coledatasource"></a>COleDataSource::COleDataSource  
 建構 `COleDataSource` 物件。  
  
```  
COleDataSource();
```  
  
##  <a name="delayrenderdata"></a>COleDataSource::DelayRenderData  
 呼叫此函式以指定的格式，在其中的資料期間提供的資料傳輸作業。  
  
```  
void DelayRenderData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料可提供剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述提供資料格式。 如果您想要指定其他的格式資訊所指定的剪貼簿格式之外，此參數提供的值`cfFormat`。 如果是**NULL**，會使用預設值中的其他欄位**FORMATETC**結構。  
  
### <a name="remarks"></a>備註  
 此函數會提供使用資料轉譯的延遲，因此不會立即提供的資料。 [OnRenderData](#onrenderdata)或[OnRenderGlobalData](#onrenderglobaldata)呼叫成員函式會要求資料。  
  
 使用此函式，如果您不打算提供您的資料透過`CFile`物件。 如果您要提供的資料透過`CFile`物件，請呼叫[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源︰ 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 若要使用立即呈現，呼叫[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成員函式。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="delayrenderfiledata"></a>COleDataSource::DelayRenderFileData  
 呼叫此函式以指定的格式，在其中的資料期間提供的資料傳輸作業。  
  
```  
void DelayRenderFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料可提供剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述提供資料格式。 如果您想要指定其他的格式資訊所指定的剪貼簿格式之外，此參數提供的值`cfFormat`。 如果是**NULL**，會使用預設值中的其他欄位**FORMATETC**結構。  
  
### <a name="remarks"></a>備註  
 此函數會提供使用資料轉譯的延遲，因此不會立即提供的資料。 [OnRenderFileData](#onrenderfiledata)呼叫成員函式會要求資料。  
  
 使用此函式，如果您要使用`CFile`來提供資料的物件。 如果您不打算使用`CFile`物件，請呼叫[DelayRenderData](#delayrenderdata)成員函式。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源︰ 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 若要使用立即呈現，呼叫[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成員函式。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="delaysetdata"></a>COleDataSource::DelaySetData  
 呼叫此函式來支援變更資料來源的內容。  
  
```  
void DelaySetData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料可放到剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，描述要被取代的資料格式。 如果您想要指定其他的格式資訊所指定的剪貼簿格式之外，此參數提供的值`cfFormat`。 如果是**NULL**，會使用預設值中的其他欄位**FORMATETC**結構。  
  
### <a name="remarks"></a>備註  
 [OnSetData](#onsetdata)會由架構呼叫，在這種情況。 這才會使用架構傳回的資料來源時[COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)。 如果`DelaySetData`，不會呼叫您`OnSetData`絕不會呼叫函式。 `DelaySetData`應該針對每個剪貼簿呼叫或**FORMATETC**您支援的格式。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="dodragdrop"></a>COleDataSource::DoDragDrop  
 呼叫`DoDragDrop`成員函式來執行這個資料來源的拖放作業通常在[CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)處理常式。  
  
```  
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,  
    LPCRECT lpRectStartDrag = NULL,  
    COleDropSource* pDropSource = NULL);
```  
  
### <a name="parameters"></a>參數  
 `dwEffects`  
 拖放作業可以在此資料來源。 可以是下列一或多項動作︰  
  
- `DROPEFFECT_COPY`無法執行複製作業。  
  
- `DROPEFFECT_MOVE`您可以執行移動作業。  
  
- `DROPEFFECT_LINK`無法建立已卸除的資料的原始資料的連結。  
  
- `DROPEFFECT_SCROLL`表示可能發生的拖曳捲動作業。  
  
 `lpRectStartDrag`  
 實際開始拖曳所定義的矩形的指標。 如需詳細資訊，請參閱接下來的＜備註＞一節。  
  
 *pDropSource*  
 要卸除來源點。 如果**NULL**然後的預設實作[COleDropSource](../../mfc/reference/coledropsource-class.md)並用。  
  
### <a name="return-value"></a>傳回值  
 卸除拖放作業中，所產生的效果否則`DROPEFFECT_NONE`如果因為使用者放開滑鼠按鈕，然後退出提供的矩形，則作業永遠不會開始。  
  
### <a name="remarks"></a>備註  
 拖放作業不會立即啟動。 將滑鼠游標離開所指定的矩形等到`lpRectStartDrag`，或是直到經過指定的毫秒數。 如果`lpRectStartDrag`是**NULL**，矩形的大小為一個像素。  
  
 登錄機碼設定為指定的延遲時間。 您可以變更的延遲時間，藉由呼叫[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果未指定的延遲時間，會使用預設值是 200 毫秒。 拖曳的延遲時間會儲存，如下所示︰  
  
-   Windows NT 拖曳延遲時間會儲存在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。  
  
-   Windows 3.x 拖曳延遲時間會儲存在獲得。INI 檔案，底下的 [Windows} 一節。  
  
-   Windows 95/98 拖曳延遲時間會儲存在快取的 WIN 版本。INI。  
  
 如需有關如何將拖曳的延遲資訊會儲存在登錄或。INI 檔案，請參閱[WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需詳細資訊，請參閱文章[將拖放︰ 實作置放來源](../../mfc/drag-and-drop-implementing-a-drop-source.md)。  
  
##  <a name="empty"></a>COleDataSource::Empty  
 呼叫此函式，以空`COleDataSource`資料物件。  
  
```  
void Empty();
```  
  
### <a name="remarks"></a>備註  
 兩者都快取和延遲的轉譯格式會清空，因此可以重複使用。  
  
 如需詳細資訊，請參閱[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="flushclipboard"></a>COleDataSource::FlushClipboard  
 將剪貼簿，然後接著可讓您貼上剪貼簿的資料，您的應用程式關閉後資料的呈現。  
  
```  
static void PASCAL FlushClipboard();
```  
  
### <a name="remarks"></a>備註  
 使用[SetClipboard](#setclipboard) ，將資料放在剪貼簿上。  
  
##  <a name="getclipboardowner"></a>COleDataSource::GetClipboardOwner  
 判斷自從是否已變更的資料到剪貼簿上[SetClipboard](#setclipboard)上次呼叫，如果是的話，識別目前的擁有者。  
  
```  
static COleDataSource* PASCAL GetClipboardOwner();
```  
  
### <a name="return-value"></a>傳回值  
 目前的剪貼簿，資料來源或**NULL**如果沒有任何在剪貼簿上，或呼叫應用程式不屬於剪貼簿。  
  
##  <a name="onrenderdata"></a>COleDataSource::OnRenderData  
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
 指定的格式是其中一個先前放置在`COleDataSource`物件使用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)延遲轉譯的成員函式。 此函式的預設實作會呼叫[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)如果提供的儲存體中的檔案或記憶體，分別為。 如果這些格式都不提供，然後預設實作會傳回 0，並不執行任何動作。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源︰ 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如果`lpStgMedium` ->  *tymed*是**TYMED_NULL**、 **STGMEDIUM**應該配置及所指定的填滿*-> tymed lpFormatEtc*。 如果不是**TYMED_NULL**、 **STGMEDIUM**應填入的資料的位置。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可能要改為覆寫這個函式的其他版本的其中一個。 如果您的資料是小型且固定的大小，覆寫`OnRenderGlobalData`。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構[TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227)列舉型別和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
##  <a name="onrenderfiledata"></a>COleDataSource::OnRenderFileData  
 指定的儲存體中的檔案時，擷取指定的格式中的資料架構所呼叫。  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)指定要求資訊的格式結構。  
  
 `pFile`  
 指向[CFile](../../mfc/reference/cfile-class.md)裡面的資料是要呈現的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前放置在`COleDataSource`物件使用[DelayRenderData](#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回**FALSE**。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可能要改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存媒體，覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源︰ 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
##  <a name="onrenderglobaldata"></a>COleDataSource::OnRenderGlobalData  
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
 指向資料所要傳回的全域記憶體的控制代碼。 如果其中一個具有尚未配置，這個參數可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前放置在`COleDataSource`物件使用[DelayRenderData](#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回**FALSE**。  
  
 如果`phGlobal`是**NULL**，然後新`HGLOBAL`應該配置並傳回`phGlobal`。 否則，`HGLOBAL`所指定`phGlobal`應該填入資料。 資料量放在`HGLOBAL`不能超過目前的記憶體區塊大小。 此外，無法重新配置較大的區塊。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可能要改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存媒體，覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫[OnRenderFileData](#onrenderfiledata)。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源︰ 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
##  <a name="onsetdata"></a>COleDataSource::OnSetData  
 若要設定或取代的資料架構呼叫`COleDataSource`物件中指定的格式。  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)指定取代資料的格式結構。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構，其中包含的資料將會取代目前的內容，`COleDataSource`物件。  
  
 `bRelease`  
 指出可完成函式呼叫之後儲存媒體的擁有權。 呼叫端將決定誰負責釋放配置代表儲存體中的資源。 呼叫端的做法是設定`bRelease`。 如果`bRelease`是零，資料來源取得擁有權，使用它完成時釋放媒體。 當`bRelease`為 0、 呼叫端保留擁有權和資料來源可用於儲存媒體只能在呼叫期間。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 它已成功取得它的資料來源才會擁有權的資料。 也就是說，它不會擁有權如果`OnSetData`會傳回 0。 如果資料來源會取得擁有權，它會藉由呼叫釋放儲存媒體[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)函式。  
  
 預設實作不做任何動作。 覆寫這個函式來取代指定的格式中的資料。 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構和[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)函式的[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
##  <a name="setclipboard"></a>COleDataSource::SetClipboard  
 將所包含的資料`COleDataSource`物件之後呼叫下列函式的其中一個剪貼簿︰ [CacheData](#cachedata)， [CacheGlobalData](#cacheglobaldata)， [DelayRenderData](#delayrenderdata)，或[DelayRenderFileData](#delayrenderfiledata)。  
  
```  
void SetClipboard();
```  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDataObject 類別](../../mfc/reference/coledataobject-class.md)

