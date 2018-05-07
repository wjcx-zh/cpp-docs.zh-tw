---
title: COleDataSource 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4df2584bd9b74640266d8ddf87087e2820deaac8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="coledatasource-class"></a>COleDataSource 類別
做為快取，應用程式在此放置資料，以便在資料傳輸作業 (例如剪貼簿或拖放作業) 期間提供。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDataSource : public CCmdTarget  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDataSource::COleDataSource](#coledatasource)|建構 `COleDataSource` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDataSource::CacheData](#cachedata)|提供資料中指定的格式使用**STGMEDIUM**結構。|  
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|提供資料中指定的格式使用`HGLOBAL`。|  
|[COleDataSource::DelayRenderData](#delayrenderdata)|提供在指定的格式來延遲的轉譯的資料。|  
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|提供資料中的指定格式`CFile`指標。|  
|[COleDataSource::DelaySetData](#delaysetdata)|針對每一種支援的格式來呼叫`OnSetData`。|  
|[Coledatasource:: Dodragdrop](#dodragdrop)|執行拖放作業與資料來源。|  
|[COleDataSource::Empty](#empty)|清空`COleDataSource`資料物件。|  
|[COleDataSource::FlushClipboard](#flushclipboard)|將所有的資料呈現到剪貼簿。|  
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|確認放在剪貼簿的資料仍然存在。|  
|[COleDataSource::OnRenderData](#onrenderdata)|擷取資料做為延遲轉譯的一部分。|  
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|擷取資料到`CFile`延遲轉譯的一部分。|  
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|擷取資料到`HGLOBAL`延遲轉譯的一部分。|  
|[COleDataSource::OnSetData](#onsetdata)|呼叫以取代中的資料`COleDataSource`物件。|  
|[COleDataSource::SetClipboard](#setclipboard)|上的芳鄰`COleDataSource`剪貼簿上的物件。|  
  
## <a name="remarks"></a>備註  
 您可以直接建立 OLE 資料來源。 或者， [COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem](../../mfc/reference/coleserveritem-class.md)類別建立 OLE 資料來源，以回應其`CopyToClipboard`和`DoDragDrop`成員函式。 請參閱[COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard)的簡短描述。 覆寫`OnGetClipboardData`OLE 資料來源中的資料加入其他的剪貼簿格式您用戶端項目或伺服器項目類別成員函式建立`CopyToClipboard`或`DoDragDrop`成員函式。  
  
 每當您想要準備傳輸的資料，您應該建立這個類別的物件，並填入資料，可使用最適合的方法，為您的資料。 它會插入至資料來源的方式直接受到資料是否立即提供 （立即轉譯） 或依需求 （延遲轉譯）。 您可以在此提供藉由傳遞要使用的剪貼簿格式的資料每個剪貼簿格式 (和選擇性[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構)，呼叫[DelayRenderData](#delayrenderdata)。  
  
 如需有關資料來源和資料傳輸的詳細資訊，請參閱文章[資料物件和資料來源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。 此外，發行項[剪貼簿主題](../../mfc/clipboard.md)描述 OLE 剪貼簿機制。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDataSource`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="cachedata"></a>  COleDataSource::CacheData  
 呼叫此函式以指定的格式，在其中的資料期間提供的資料傳輸作業。  
  
```  
void CacheData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料為提供剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構，其中包含指定的格式中的資料。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述資料為提供的格式。 如果您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果是**NULL**，預設值會用於中的其他欄位**FORMATETC**結構。  
  
### <a name="remarks"></a>備註  
 您必須提供資料，因為此函式，提供它使用立即呈現。 資料會快取，直到需要為止。  
  
 提供使用資料[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構。 您也可以使用`CacheGlobalData`成員函式，如果您提供的資料量是夠小，無法有效率地使用傳送`HGLOBAL`。  
  
 在呼叫之後`CacheData` **ptd**隸屬`lpFormatEtc`和內容`lpStgMedium`資料物件，不是由呼叫者所擁有。  
  
 若要使用延遲的轉譯，呼叫[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源： 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的結構。  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="cacheglobaldata"></a>  COleDataSource::CacheGlobalData  
 呼叫此函式以指定的格式，在其中的資料期間提供的資料傳輸作業。  
  
```  
void CacheGlobalData(
    CLIPFORMAT cfFormat,  
    HGLOBAL hGlobal,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料為提供剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 *hGlobal*  
 包含指定的格式資料的全域記憶體區塊的控制代碼。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述資料為提供的格式。 如果您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果是**NULL**，預設值會用於中的其他欄位**FORMATETC**結構。  
  
### <a name="remarks"></a>備註  
 此函式提供使用直接呈現，因此呼叫函式; 時，您必須提供資料的資料資料會快取，直到需要為止。 使用`CacheData`成員函式，如果您提供的大量資料，或如果您需要的結構化儲存體。  
  
 若要使用延遲的轉譯，呼叫[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源： 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的結構。  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="coledatasource"></a>  COleDataSource::COleDataSource  
 建構 `COleDataSource` 物件。  
  
```  
COleDataSource();
```  
  
##  <a name="delayrenderdata"></a>  COleDataSource::DelayRenderData  
 呼叫此函式以指定的格式，在其中的資料期間提供的資料傳輸作業。  
  
```  
void DelayRenderData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料為提供剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述資料為提供的格式。 如果您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果是**NULL**，預設值會用於中的其他欄位**FORMATETC**結構。  
  
### <a name="remarks"></a>備註  
 此函式提供的資料，使用延遲的轉譯，所以不會立即提供的資料。 [OnRenderData](#onrenderdata)或[OnRenderGlobalData](#onrenderglobaldata)呼叫成員函式會要求資料。  
  
 如果您不打算提供透過您的資料，請使用此函式`CFile`物件。 如果您要提供的資料，透過`CFile`物件，呼叫[DelayRenderFileData](#delayrenderfiledata)成員函式。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源： 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 若要使用立即轉譯，呼叫[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成員函式。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的結構。  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="delayrenderfiledata"></a>  COleDataSource::DelayRenderFileData  
 呼叫此函式以指定的格式，在其中的資料期間提供的資料傳輸作業。  
  
```  
void DelayRenderFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料為提供剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述資料為提供的格式。 如果您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果是**NULL**，預設值會用於中的其他欄位**FORMATETC**結構。  
  
### <a name="remarks"></a>備註  
 此函式提供的資料，使用延遲的轉譯，所以不會立即提供的資料。 [OnRenderFileData](#onrenderfiledata)呼叫成員函式會要求資料。  
  
 使用此函式，如果您要使用`CFile`來提供資料的物件。 如果您不打算使用`CFile`物件，呼叫[DelayRenderData](#delayrenderdata)成員函式。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源： 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 若要使用立即轉譯，呼叫[CacheData](#cachedata)或[CacheGlobalData](#cacheglobaldata)成員函式。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的結構。  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="delaysetdata"></a>  COleDataSource::DelaySetData  
 呼叫此函式來支援變更資料來源的內容。  
  
```  
void DelaySetData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 中的資料是放到剪貼簿格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述中的資料是要被取代的格式。 如果您想要指定所指定的剪貼簿格式之外的其他格式資訊，請為此參數提供值`cfFormat`。 如果是**NULL**，預設值會用於中的其他欄位**FORMATETC**結構。  
  
### <a name="remarks"></a>備註  
 [OnSetData](#onsetdata)會在發生此情況時由架構呼叫。 這只用於架構傳回的資料來源時[COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)。 如果`DelaySetData`未呼叫您`OnSetData`永遠不會呼叫函式。 `DelaySetData` 應該針對每個剪貼簿呼叫或**FORMATETC**您支援的格式。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的結構。  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="dodragdrop"></a>  Coledatasource:: Dodragdrop  
 呼叫`DoDragDrop`成員函式來執行拖放作業，此資料來源，通常在[CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)處理常式。  
  
```  
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,  
    LPCRECT lpRectStartDrag = NULL,  
    COleDropSource* pDropSource = NULL);
```  
  
### <a name="parameters"></a>參數  
 `dwEffects`  
 拖放作業所允許在此資料來源。 可以是下列一或多個項目：  
  
- `DROPEFFECT_COPY` 無法執行複製作業。  
  
- `DROPEFFECT_MOVE` 無法執行移動作業。  
  
- `DROPEFFECT_LINK` 無法建立已卸除的資料從原始資料的連結。  
  
- `DROPEFFECT_SCROLL` 表示可能發生拖曳捲軸作業。  
  
 `lpRectStartDrag`  
 實際開始拖曳所定義的矩形的指標。 如需詳細資訊，請參閱接下來的＜備註＞一節。  
  
 *pDropSource*  
 要卸除來源點。 如果**NULL**然後的預設實作[COleDropSource](../../mfc/reference/coledropsource-class.md)將使用。  
  
### <a name="return-value"></a>傳回值  
 卸除拖放作業，所產生的效果否則`DROPEFFECT_NONE`如果作業永遠不會開始因為使用者放開滑鼠按鈕，然後退出提供的矩形。  
  
### <a name="remarks"></a>備註  
 拖放作業不會立即啟動。 它會等候直到滑鼠游標離開所指定的矩形`lpRectStartDrag`，或是直到已通過指定的毫秒數。 如果`lpRectStartDrag`是**NULL**，矩形的大小是一個像素。  
  
 登錄機碼設定所指定的延遲時間。 您可以藉由呼叫變更的延遲時間[CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)或[cwinapp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint)。 如果您未指定延遲時間，會使用預設值是 200 毫秒。 拖放到延遲時間會儲存，如下所示：  
  
-   Windows NT 拖曳延遲時間會儲存在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay。  
  
-   Win 儲存 Windows 3.x 拖曳延遲時間。INI 檔案，底下的 [Windows} 一節。  
  
-   Windows 95/98 拖曳延遲時間會儲存在 WIN 的快取版本。INI。  
  
 如需有關如何將延遲的資訊會儲存在登錄或。INI 檔案，請參閱[WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) Windows SDK 中。  
  
 如需詳細資訊，請參閱文章[將拖放： 實作置放來源](../../mfc/drag-and-drop-implementing-a-drop-source.md)。  
  
##  <a name="empty"></a>  COleDataSource::Empty  
 呼叫此函式可空白`COleDataSource`資料物件。  
  
```  
void Empty();
```  
  
### <a name="remarks"></a>備註  
 兩者都快取，而延遲的轉譯格式會清空，以便之後可以重複使用。  
  
 如需詳細資訊，請參閱[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) Windows SDK 中。  
  
##  <a name="flushclipboard"></a>  COleDataSource::FlushClipboard  
 將剪貼簿，並再貼上剪貼簿的資料，您的應用程式關閉後的資料呈現。  
  
```  
static void PASCAL FlushClipboard();
```  
  
### <a name="remarks"></a>備註  
 使用[SetClipboard](#setclipboard)將資料放在剪貼簿。  
  
##  <a name="getclipboardowner"></a>  COleDataSource::GetClipboardOwner  
 決定是否變更過資料到剪貼簿上的[SetClipboard](#setclipboard)上次呼叫，若是如此，識別目前的擁有者。  
  
```  
static COleDataSource* PASCAL GetClipboardOwner();
```  
  
### <a name="return-value"></a>傳回值  
 資料來源目前在剪貼簿，或**NULL**如果沒有任何剪貼簿上，或呼叫應用程式不屬於剪貼簿。  
  
##  <a name="onrenderdata"></a>  COleDataSource::OnRenderData  
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
 指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](#delayrenderdata)或[DelayRenderFileData](#delayrenderfiledata)延遲轉譯的成員函式。 此函式的預設實作會呼叫[OnRenderFileData](#onrenderfiledata)或[OnRenderGlobalData](#onrenderglobaldata)是否提供的儲存體中的檔案或記憶體，分別。 如果這些格式都不提供，預設實作會傳回 0，然後會執行任何動作。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源： 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如果`lpStgMedium` ->  *tymed*是**TYMED_NULL**、 **STGMEDIUM**應該配置，並填入所指定*lpFormatEtc->tymed*。 如果不是**TYMED_NULL**、 **STGMEDIUM**應填入資料的位置。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可以改為覆寫這個函式的其他版本的其中一個。 如果您的資料是小型且固定的大小，會覆寫`OnRenderGlobalData`。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構[TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227)列舉型別和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)在 Windows SDK。  
  
##  <a name="onrenderfiledata"></a>  COleDataSource::OnRenderFileData  
 由架構呼叫以指定的儲存體中為檔案時，擷取指定的格式中的資料。  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，指定用來要求資訊的格式。  
  
 `pFile`  
 指向[CFile](../../mfc/reference/cfile-class.md)資料為呈現的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回**FALSE**。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可以改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存媒體，覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫`OnRenderFileData`。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源： 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431) Windows SDK 中。  
  
##  <a name="onrenderglobaldata"></a>  COleDataSource::OnRenderGlobalData  
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
 指向全域記憶體資料所要傳回的控制代碼。 如果其中一個具有尚未配置，這個參數可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 指定的格式是其中一個先前置於`COleDataSource`物件使用[DelayRenderData](#delayrenderdata)延遲轉譯的成員函式。 此函式的預設實作只會傳回**FALSE**。  
  
 如果`phGlobal`是**NULL**，然後新`HGLOBAL`應該配置並傳回`phGlobal`。 否則，`HGLOBAL`所指定`phGlobal`應填入資料。 資料量置於`HGLOBAL`不能超過目前的記憶體區塊大小。 此外，無法重新配置較大的區塊。  
  
 這是進階可覆寫。 覆寫此函式可提供您要求的格式和 「 中 」 的資料。 根據您的資料，您可以改為覆寫這個函式的其他版本的其中一個。 如果您想要處理多個儲存媒體，覆寫[OnRenderData](#onrenderdata)。 如果您在檔案中，或資料的大小不固定，覆寫[OnRenderFileData](#onrenderfiledata)。 如需有關延遲轉譯為 mfc 已處理，請參閱文章[資料物件和資料來源： 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431) Windows SDK 中。  
  
##  <a name="onsetdata"></a>  COleDataSource::OnSetData  
 由架構呼叫以設定或取代中的資料`COleDataSource`物件中指定的格式。  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構，指定要取代的資料格式。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構，其中包含的資料，將會取代目前的內容`COleDataSource`物件。  
  
 `bRelease`  
 指出誰完成函式呼叫後之儲存媒體的擁有權。 呼叫端決定誰負責釋放之儲存媒體代表配置的資源。 呼叫端會藉由設定`bRelease`。 如果`bRelease`為非零，資料來源取得擁有權，使用它完成時釋放媒體。 當`bRelease`為 0、 呼叫端保留擁有權和資料來源可以只針對在呼叫期間使用之儲存媒體。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 資料來源不會擁有權的資料，直到它成功取得它。 也就是說，它不會擁有權如果`OnSetData`傳回 0。 如果資料來源取得擁有權，才會釋出儲存媒體藉由呼叫[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)函式。  
  
 預設實作不做任何動作。 覆寫這個函式來取代指定的格式中的資料。 這是進階可覆寫。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構和[ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491)和[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)Windows SDK 中的函式。  
  
##  <a name="setclipboard"></a>  COleDataSource::SetClipboard  
 將中所包含的資料放`COleDataSource`物件上呼叫下列函數的其中一個之後剪貼簿： [CacheData](#cachedata)， [CacheGlobalData](#cacheglobaldata)， [DelayRenderData](#delayrenderdata)，或[DelayRenderFileData](#delayrenderfiledata)。  
  
```  
void SetClipboard();
```  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDataObject 類別](../../mfc/reference/coledataobject-class.md)
