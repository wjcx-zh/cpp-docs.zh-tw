---
title: "CView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CView
- AFXWIN/CView
- AFXWIN/CView::CView
- AFXWIN/CView::DoPreparePrinting
- AFXWIN/CView::GetDocument
- AFXWIN/CView::IsSelected
- AFXWIN/CView::OnDragEnter
- AFXWIN/CView::OnDragLeave
- AFXWIN/CView::OnDragOver
- AFXWIN/CView::OnDragScroll
- AFXWIN/CView::OnDrop
- AFXWIN/CView::OnDropEx
- AFXWIN/CView::OnInitialUpdate
- AFXWIN/CView::OnPrepareDC
- AFXWIN/CView::OnScroll
- AFXWIN/CView::OnScrollBy
- AFXWIN/CView::OnActivateFrame
- AFXWIN/CView::OnActivateView
- AFXWIN/CView::OnBeginPrinting
- AFXWIN/CView::OnDraw
- AFXWIN/CView::OnEndPrinting
- AFXWIN/CView::OnEndPrintPreview
- AFXWIN/CView::OnPreparePrinting
- AFXWIN/CView::OnPrint
- AFXWIN/CView::OnUpdate
dev_langs:
- C++
helpviewer_keywords:
- CView [MFC], CView
- CView [MFC], DoPreparePrinting
- CView [MFC], GetDocument
- CView [MFC], IsSelected
- CView [MFC], OnDragEnter
- CView [MFC], OnDragLeave
- CView [MFC], OnDragOver
- CView [MFC], OnDragScroll
- CView [MFC], OnDrop
- CView [MFC], OnDropEx
- CView [MFC], OnInitialUpdate
- CView [MFC], OnPrepareDC
- CView [MFC], OnScroll
- CView [MFC], OnScrollBy
- CView [MFC], OnActivateFrame
- CView [MFC], OnActivateView
- CView [MFC], OnBeginPrinting
- CView [MFC], OnDraw
- CView [MFC], OnEndPrinting
- CView [MFC], OnEndPrintPreview
- CView [MFC], OnPreparePrinting
- CView [MFC], OnPrint
- CView [MFC], OnUpdate
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 843417508fc43f99b0027873988746d03a7863cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cview-class"></a>CView 類別
提供使用者定義的檢視類別的基本功能。  
  
## <a name="syntax"></a>語法  
  
```  
class AFX_NOVTABLE CView : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CView::CView](#cview)|建構 `CView` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CView::DoPreparePrinting](#doprepareprinting)|顯示 [列印] 對話方塊並建立印表機裝置內容。覆寫時，呼叫`OnPreparePrinting`成員函式。|  
|[CView::GetDocument](#getdocument)|傳回與檢視相關聯的文件。|  
|[CView::IsSelected](#isselected)|測試是否已選取文件項目。 OLE 支援的必要項。|  
|[CView::OnDragEnter](#ondragenter)|當項目第一次拖曳到檢視的拖放區時呼叫。|  
|[CView::OnDragLeave](#ondragleave)|拖曳的項目離開檢視拖放區域時呼叫。|  
|[CView::OnDragOver](#ondragover)|當項目拖曳至檢視的拖放區域上方時呼叫。|  
|[CView::OnDragScroll](#ondragscroll)|呼叫以判斷是否要將資料指標拖曳至視窗的捲軸區域。|  
|[CView::OnDrop](#ondrop)|已經卸除到檢視中，預設處理常式的拖放區域的項目時呼叫。|  
|[CView::OnDropEx](#ondropex)|已經卸除到檢視中，主要的處理常式的拖放區域的項目時呼叫。|  
|[Cview:: Oninitialupdate](#oninitialupdate)|檢視第一次連接至文件後呼叫。|  
|[CView::OnPrepareDC](#onpreparedc)|之前呼叫`OnDraw`螢幕上顯示呼叫成員函式或`OnPrint`列印或預覽列印呼叫成員函式。|  
|[CView::OnScroll](#onscroll)|當 OLE 項目拖曳超出檢視的邊界時呼叫。|  
|[CView::OnScrollBy](#onscrollby)|捲動檢視，其中包含使用中就地 OLE 項目時呼叫。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CView::OnActivateFrame](#onactivateframe)|包含檢視的框架視窗是啟用或停用時呼叫。|  
|[CView::OnActivateView](#onactivateview)|當檢視啟動時呼叫。|  
|[CView::OnBeginPrinting](#onbeginprinting)|列印工作開始; 時呼叫覆寫，以配置圖形裝置介面 (GDI) 資源。|  
|[Cview:: Ondraw](#ondraw)|呼叫以呈現在螢幕上顯示、 列印或預覽列印的文件的映像。 所需的實作。|  
|[CView::OnEndPrinting](#onendprinting)|當列印工作結束; 時呼叫若要解除配置 GDI 資源覆寫。|  
|[CView::OnEndPrintPreview](#onendprintpreview)|預覽模式結束時呼叫。|  
|[CView::OnPreparePrinting](#onprepareprinting)|在列印或預覽; 文件之前呼叫覆寫以初始化 [列印] 對話方塊。|  
|[CView::OnPrint](#onprint)|呼叫以列印或預覽文件的頁面。|  
|[CView::OnUpdate](#onupdate)|呼叫以通知的檢視，其文件已被修改。|  
  
## <a name="remarks"></a>備註  
 檢視附加至文件，並且會做為文件與使用者之間的媒介： 的檢視會呈現在螢幕或印表機的文件的映像和使用者輸入中解譯作業。  
  
 檢視是框架視窗的子系。 多個檢視可以共用框架視窗中，如同分隔視窗的情況。 檢視類別、 框架視窗類別，與文件類別之間的關聯性由建立`CDocTemplate`物件。 當使用者開啟新視窗或分割現有架構，其中建構新的檢視，並將其附加至文件。  
  
 檢視可以附加到單一文件，但文件可以有多個檢視一次附加 — 比方說，如果文件會顯示在分隔視窗中，或在多個文件介面 (MDI) 應用程式中的多個子視窗中。 您的應用程式可支援不同類型的檢視給定文件類型。例如，文書處理程式可能會提供文件的完整文字檢視和大綱檢視會顯示區段標題。 這些不同類型的檢視表可以放在個別的框架視窗中，或在個別的單一框架視窗的窗格如果您使用分隔視窗。  
  
 檢視可能會負責處理多種不同類型的輸入，例如鍵盤、 滑鼠輸入或透過拖放，以及命令的功能表、 工具列或捲軸的輸入。 檢視接收轉送其框架視窗的命令。 如果檢視不會處理指定的命令，會轉送至其相關聯的文件命令。 像所有的命令目標，檢視會處理透過訊息對應的訊息。  
  
 檢視其負責顯示和修改文件的資料，而不是用於儲存它。 文件會提供有關其資料與必要的詳細資料檢視。 您可以讓文件的資料成員，或者您可以提供要呼叫的檢視類別的文件類別中的成員函式檢視存取權。  
  
 當文件的資料變更時，負責將變更檢視通常會呼叫[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)文件，就會通知其他檢視，藉由呼叫的函式`OnUpdate`成員函式每個。 預設實作`OnUpdate`使檢視的整個工作區失效。 您可以覆寫它使只有這些區域的工作區對應至文件已修改的部分。  
  
 若要使用`CView`、 衍生的類別和實作`OnDraw`成員函式來執行螢幕顯示。 您也可以使用`OnDraw`執行列印和預覽列印。 架構會處理列印和文件預覽列印迴圈。  
  
 檢視會處理具有捲軸訊息[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成員函式。 您可以實作捲軸訊息處理的這些函式，或者您可以使用`CView`衍生的類別[CScrollView](../../mfc/reference/cscrollview-class.md)來處理您的捲動。  
  
 除了`CScrollView`，Mfc 程式庫提供九個衍生自其他類別`CView`:  
  
- [CCtrlView](../../mfc/reference/cctrlview-class.md)，允許文件-架構與樹狀目錄、 清單和 rich edit 控制項的檢視的使用方式的檢視。  
  
- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)，在對話方塊控制項中顯示資料庫記錄的檢視。  
  
- [CEditView](../../mfc/reference/ceditview-class.md)，提供簡單的多行文字編輯器的檢視。 您可以使用`CEditView`做為控制項的對話方塊與文件的檢視中的物件。  
  
- [CFormView](../../mfc/reference/cformview-class.md)，包含對話方塊控制項和對話方塊範本資源為基礎的可捲動檢視。  
  
- [CListView](../../mfc/reference/clistview-class.md)，允許文件-與清單控制項的檢視架構的使用方式的檢視。  
  
- [CRecordView](../../mfc/reference/crecordview-class.md)，在對話方塊控制項中顯示資料庫記錄的檢視。  
  
- [CRichEditView](../../mfc/reference/cricheditview-class.md)，允許文件-架構與 rich edit 控制項的檢視的使用方式的檢視。  
  
- [CScrollView](../../mfc/reference/cscrollview-class.md)，會自動支援捲動檢視。  
  
- [CTreeView](../../mfc/reference/ctreeview-class.md)，允許文件-與樹狀目錄控制項的檢視架構的使用方式的檢視。  
  
 `CView`類別也具有名為衍生的實作類別**CPreviewView**，這用來執行預覽列印時由架構。 這個類別會提供支援特有的功能 [預覽列印] 視窗中，例如工具列、 單一或雙頁面預覽及縮放的，放大的預覽的影像。 您不需要呼叫或覆寫任何**CPreviewView**的成員函式，除非您想要實作您自己的預覽列印的介面 （例如，如果您想要支援在預覽列印模式中編輯）。 如需有關使用`CView`，請參閱[文件/檢視架構](../../mfc/document-view-architecture.md)和[列印](../../mfc/printing.md)。 此外，請參閱[技術附註 30](../../mfc/tn030-customizing-printing-and-print-preview.md)如需有關自訂列印預覽。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CView`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cview"></a>CView::CView  
 建構 `CView` 物件。  
  
```  
CView();
```  
  
### <a name="remarks"></a>備註  
 建立新的框架視窗或分隔視窗時，架構會呼叫建構函式。 覆寫[OnInitialUpdate](#oninitialupdate)成員函式來初始化之後附加文件的檢視。  
  
##  <a name="doprepareprinting"></a>CView::DoPreparePrinting  
 呼叫此函式的覆寫從[OnPreparePrinting](#onprepareprinting)叫用 [列印] 對話方塊，並建立印表機裝置內容。  
  
```  
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述目前列印工作的結構。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果可以開始列印或預覽列印。0，表示作業已取消。  
  
### <a name="remarks"></a>備註  
 此函式的行為取決於是否呼叫它的列印或預覽列印 (所指定**m_bPreview**隸屬`pInfo`參數)。 如果列印檔案時，此函式會叫用 [列印] 對話方塊，使用中的值[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構`pInfo`指向; 使用者已關閉對話方塊之後，函式會建立印表機裝置內容根據設定的對話方塊中指定的使用者，並傳回透過這個裝置內容`pInfo`參數。 這個裝置內容用來列印文件。  
  
 如果預覽檔案時，此函式會建立印表機裝置內容中使用目前的印表機設定。這個裝置內容可以用來模擬在預覽期間的印表機。  
  
##  <a name="getdocument"></a>CView::GetDocument  
 呼叫此函式可取得檢視的文件的指標。  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CDocument](../../mfc/reference/cdocument-class.md)與檢視相關聯的物件。 **NULL**如果檢視未附加至文件。  
  
### <a name="remarks"></a>備註  
 這可讓您呼叫文件的成員函式。  
  
##  <a name="isselected"></a>CView::IsSelected  
 由架構呼叫以檢查是否已選取指定的文件項目。  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `pDocItem`  
 指向要測試的文件項目。  
  
### <a name="return-value"></a>傳回值  
 如果已選取指定的文件項目; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會傳回**FALSE**。 覆寫這個函式，如果您實作選取項目使用[CDocItem](../../mfc/reference/cdocitem-class.md)物件。 如果您的檢視包含 OLE 項目，您必須覆寫這個函式。  
  
##  <a name="onactivateframe"></a>CView::OnActivateFrame  
 框架視窗包含檢視已啟用或停用時由架構呼叫。  
  
```  
virtual void OnActivateFrame(
    UINT nState,  
    CFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>參數  
 `nState`  
 指定是否要被框架視窗啟用或停用。 它可以是下列值之一：  
  
- **WA_INACTIVE**框架視窗正在停用。  
  
- **WA_ACTIVE**框架視窗正在被啟動透過某些方法以外 （例如，藉由使用的鍵盤介面，以選取的視窗） 中按一下滑鼠。  
  
- **WA_CLICKACTIVE**正在啟用滑鼠點按的框架視窗  
  
 `pFrameWnd`  
 啟動會在框架視窗的指標。  
  
### <a name="remarks"></a>備註  
 如果您想要執行特殊處理與檢視相關聯的框架視窗啟用或停用時，覆寫此成員函式。 例如， [CFormView](../../mfc/reference/cformview-class.md)執行此覆寫時，它會將儲存並還原具有焦點的控制項。  
  
##  <a name="onactivateview"></a>CView::OnActivateView  
 啟用或停用檢視時由架構呼叫。  
  
```  
virtual void OnActivateView(
    BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView);
```  
  
### <a name="parameters"></a>參數  
 `bActivate`  
 代表是否要檢視啟用或停用。  
  
 `pActivateView`  
 檢視物件的啟動點。  
  
 `pDeactiveView`  
 正在停用的檢視物件的點。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會將焦點設定至啟動的檢視。 如果您想要執行特殊處理，啟用或停用檢視時，覆寫這個函式。 例如，如果您想要提供特殊視覺提示以區別現用檢視從非作用中的檢視，您會檢查`bActivate`參數並據此更新的檢視外觀。  
  
 `pActivateView`和`pDeactiveView`參數指向相同的檢視應用程式的主框架視窗啟動現用檢視表中沒有任何變更如果 — 比方說，如果焦點從另一個應用程式到這其中一個，而不是從一個傳輸檢視，以另一個應用程式中，或在 MDI 子視窗之間切換時。 這可讓檢視，以重新了解其調色盤，如有需要。  
  
 這些參數與不同時[CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview)呼叫時所使用的不同功能的檢視[CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview)會傳回。 發生這種情況最常與分隔視窗。  
  
##  <a name="onbeginprinting"></a>CView::OnBeginPrinting  
 在呼叫 `OnPreparePrinting` 之後，由架構在列印或預覽列印工作開始時呼叫。  
  
```  
virtual void OnBeginPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指向印表機裝置內容。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述目前列印工作的結構。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 覆寫此函式以配置列印特別需要的任何 GDI 資源，例如畫筆或字型。 選取的 GDI 物件到裝置內容中[OnPrint](#onprint)使用它們的每個頁面的成員函式。 如果您使用相同的檢視物件來執行螢幕顯示和列印，請為每個顯示所需的 GDI 資源使用不同的變數；這可讓您在列印期間更新螢幕。  
  
 您也可以使用此函式，執行因印表機裝置內容屬性而異的初始設定。 例如，列印文件所需的頁數可能會因使用者在 [列印] 對話方塊中指定的設定 (例如頁面長度) 而異。 在這種情況下，您無法指定文件長度，以[OnPreparePrinting](#onprepareprinting)成員函式，其中通常會進行操作，您必須等到印表機裝置內容已建立根據對話方塊設定。 [OnBeginPrinting](#onbeginprinting)是第一個可覆寫函式，可讓您存取[CDC](../../mfc/reference/cdc-class.md)物件，代表印表機裝置內容，所以您可以從此函式設定文件長度。 請注意，如果此時未指定文件長度，預覽列印期間將不會顯示捲軸。  
  
##  <a name="ondragenter"></a>CView::OnDragEnter  
 當滑鼠初次進入置放目標視窗的非捲動區域，由架構呼叫。  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)正在拖曳到檢視的卸除區域。  
  
 `dwKeyState`  
 包含輔助按鍵的狀態。 這是任意數目的下列組合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 目前滑鼠位置相對於用戶端區域的檢視。  
  
### <a name="return-value"></a>傳回值  
 中的值`DROPEFFECT`列舉型別，表示如果使用者已在此位置的物件就會發生的卸除的類型。 卸除類型通常取決於目前所指示的索引鍵狀態`dwKeyState`。 以 keystates 標準對應`DROPEFFECT`值為：  
  
- `DROPEFFECT_NONE`無法卸除的資料物件，此視窗中。  
  
- `DROPEFFECT_LINK`如**MK_CONTROL &#124;MK_SHIFT**建立物件和它的伺服器之間的連結。  
  
- `DROPEFFECT_COPY`如**MK_CONTROL**建立一份已卸除的物件。  
  
- `DROPEFFECT_MOVE`如**MK_ALT**建立一份已卸除的物件，並刪除原始的物件。 這通常是預設的拖放效果，檢視可接受這個資料物件。  
  
 如需詳細資訊，請參閱 MFC 進階概念範例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>備註  
 預設實作會執行任何動作，並傳回`DROPEFFECT_NONE`。  
  
 若要準備的未來呼叫此函式會覆寫[OnDragOver](#ondragover)成員函式。 應該擷取從資料物件所需的任何資料供稍後使用中，此時`OnDragOver`成員函式。 此時若要讓使用者視覺化回應時，應該也更新檢視。 如需詳細資訊，請參閱文章[將拖放： 實作置放目標](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="ondragleave"></a>CView::OnDragLeave  
 超出有效的置放區針對該視窗移動滑鼠時呼叫由架構在拖曳作業期間。  
  
```  
virtual void OnDragLeave();
```  
  
### <a name="remarks"></a>備註  
 如果目前的檢視必須清除期間採取任何動作，請覆寫此函數[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)呼叫，例如當物件已拖曳和卸除時移除任何視覺化使用者意見反應.  
  
##  <a name="ondragover"></a>CView::OnDragOver  
 當滑鼠移動經過置放目標視窗呼叫由架構在拖曳作業期間。  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)拖曳到橢圓形上置放目標。  
  
 `dwKeyState`  
 包含輔助按鍵的狀態。 這是任意數目的下列組合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 目前的滑鼠位置相對於檢視用戶端區域。  
  
### <a name="return-value"></a>傳回值  
 中的值`DROPEFFECT`列舉型別，表示如果使用者已在此位置的物件就會發生的卸除的類型。 卸除類型通常取決於目前的索引鍵狀態所示`dwKeyState`。 以 keystates 標準對應`DROPEFFECT`值為：  
  
- `DROPEFFECT_NONE`無法卸除的資料物件，此視窗中。  
  
- `DROPEFFECT_LINK`如**MK_CONTROL &#124;MK_SHIFT**建立物件和它的伺服器之間的連結。  
  
- `DROPEFFECT_COPY`如**MK_CONTROL**建立一份已卸除的物件。  
  
- `DROPEFFECT_MOVE`如**MK_ALT**建立一份已卸除的物件，並刪除原始的物件。 這通常是預設的拖放效果，檢視可接受的資料物件。  
  
 如需詳細資訊，請參閱 MFC 進階概念範例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>備註  
 預設實作會執行任何動作，並傳回`DROPEFFECT_NONE`。  
  
 此函式可讓使用者視覺化回應拖曳作業期間會覆寫。 因為連續呼叫此函式，其中包含的任何程式碼應該最佳化盡量。 如需詳細資訊，請參閱文章[將拖放： 實作置放目標](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="ondragscroll"></a>CView::OnDragScroll  
 由架構呼叫之前呼叫[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)判斷點是否在捲軸的區域。  
  
```  
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `dwKeyState`  
 包含輔助按鍵的狀態。 這是任意數目的下列組合： **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 包含資料指標，以像素與相對螢幕的位置。  
  
### <a name="return-value"></a>傳回值  
 中的值`DROPEFFECT`列舉型別，表示如果使用者已在此位置的物件就會發生的卸除的類型。 卸除類型通常取決於目前所指示的索引鍵狀態`dwKeyState`。 以 keystates 標準對應`DROPEFFECT`值為：  
  
- `DROPEFFECT_NONE`無法卸除的資料物件，此視窗中。  
  
- `DROPEFFECT_LINK`如**MK_CONTROL &#124;MK_SHIFT**建立物件和它的伺服器之間的連結。  
  
- `DROPEFFECT_COPY`如**MK_CONTROL**建立一份已卸除的物件。  
  
- `DROPEFFECT_MOVE`如**MK_ALT**建立一份已卸除的物件，並刪除原始的物件。  
  
- `DROPEFFECT_SCROLL`表示即將發生拖曳捲軸作業，或目標檢視中發生的狀況。  
  
 如需詳細資訊，請參閱 MFC 進階概念範例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>備註  
 當您想要提供特殊的行為，這個事件時，覆寫這個函式。 預設實作資料指標拖曳至預設捲軸的區域內的每個視窗框線時，會自動捲動 windows。如需詳細資訊，請參閱文章[將拖放： 實作置放目標](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="ondraw"></a>Cview:: Ondraw  
 由架構呼叫以呈現文件的映像。  
  
```  
virtual void OnDraw(CDC* pDC) = 0;  
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指向要用來呈現文件的映像的裝置內容。  
  
### <a name="remarks"></a>備註  
 架構會呼叫此函式來執行螢幕顯示、 列印和預覽列印，並且會傳遞不同的裝置內容中的每個案例。 沒有預設的實作。  
  
 您必須覆寫這個函式來顯示文件的檢視。 您可以進行使用的圖形裝置介面 (GDI) 呼叫[CDC](../../mfc/reference/cdc-class.md)指向的物件`pDC`參數。 您可以選取放入裝置內容，繪製前的 GDI 資源，例如畫筆或字型，然後再之後取消。 通常您的繪圖程式碼可與裝置無關。也就是說，它不需要的裝置類型會顯示映像相關資訊。  
  
 若要最佳化的繪圖，呼叫[RectVisible](../../mfc/reference/cdc-class.md#rectvisible)裝置內容，以了解是否要繪製指定的矩形的成員函式。 如果您要在區別正常螢幕顯示和列印，請呼叫[IsPrinting](../../mfc/reference/cdc-class.md#isprinting)裝置內容的成員函式。  
  
##  <a name="ondrop"></a>CView::OnDrop  
 當使用者放開的有效置放目標的資料物件時，由架構呼叫。  
  
```  
virtual BOOL OnDrop(
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md) ，放到放置目標。  
  
 `dropEffect`  
 使用者已要求置放效果。  
  
- `DROPEFFECT_COPY`建立要卸除的資料物件的複本。  
  
- `DROPEFFECT_MOVE`將資料物件移至目前的滑鼠位置。  
  
- `DROPEFFECT_LINK`建立資料物件和它的伺服器之間的連結。  
  
 `point`  
 目前的滑鼠位置相對於檢視用戶端區域。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果卸除成功。否則便是 0。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作，並傳回**FALSE**。  
  
 此檢視的工作區中實作的 OLE 拖放效果的函式會覆寫。 資料物件可以透過檢查`pDataObject`剪貼簿資料格式和資料在卸除指定的點。  
  
> [!NOTE]
>  架構不會呼叫此函式，如果沒有覆寫， [OnDropEx](#ondropex)此檢視類別中。  
  
##  <a name="ondropex"></a>CView::OnDropEx  
 當使用者放開的有效置放目標的資料物件時，由架構呼叫。  
  
```  
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md) ，放到放置目標。  
  
 `dropDefault`  
 使用者選擇根據索引鍵的目前狀態的預設拖放作業的效果。 它可能是`DROPEFFECT_NONE`。 < 備註 > 一節中討論的置放效果。  
  
 `dropList`  
 置放來源支援置放效果的清單。 可以使用的位元 OR 結合置放效果值 ( **&#124;**) 作業。 < 備註 > 一節中討論的置放效果。  
  
 `point`  
 目前的滑鼠位置相對於檢視用戶端區域。  
  
### <a name="return-value"></a>傳回值  
 卸除嘗試在所指定的位置所產生的置放效果`point`。 這必須是其中一個值所指示*dropEffectList*。 < 備註 > 一節中討論的置放效果。  
  
### <a name="remarks"></a>備註  
 預設實作會執行任何動作，並傳回空值 (-1)，表示應該呼叫架構[OnDrop](#ondrop)處理常式。  
  
 若要實作的滑鼠右鍵拖曳和卸除此函式會覆寫。 滑鼠右鍵拖曳和卸除通常顯示選項功能表，當使用者放開滑鼠右按鈕。  
  
 覆寫`OnDropEx`滑鼠右按鈕應該查詢。 您可以呼叫[GetKeyState](http://msdn.microsoft.com/library/windows/desktop/ms646301)或儲存右邊的滑鼠按鈕狀態從您[OnDragEnter](#ondragenter)處理常式。  
  
-   如果滑鼠右按鈕已關閉，您的覆寫應該會顯示快顯功能表提供拖放效果支援置放來源。  
  
    -   檢查`dropList`決定卸除來源所支援的置放效果。 啟用快顯功能表中的這些動作。  
  
    -   使用[SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996)設為基礎的預設動作`dropDefault`。  
  
    -   最後，採取動作以快顯功能表的使用者選取項目。  
  
-   如果未按下滑鼠右按鈕，您的覆寫應處理此做為標準的卸除要求。 使用指定的拖放效果`dropDefault`。 或者，您的覆寫可能會傳回空值 (-1)，表示`OnDrop`即將處理此拖放作業。  
  
 使用`pDataObject`檢查`COleDataObject`剪貼簿資料格式和資料在卸除指定的點。  
  
 拖放效果描述與拖放作業相關聯的動作。 請參閱下列置放效果的清單：  
  
- `DROPEFFECT_NONE`不允許卸除。  
  
- `DROPEFFECT_COPY`執行複製作業。  
  
- `DROPEFFECT_MOVE`會執行移動作業。  
  
- `DROPEFFECT_LINK`會建立已卸除的資料從原始資料的連結。  
  
- `DROPEFFECT_SCROLL`表示即將發生拖曳捲軸作業，或目標中發生的狀況。  
  
 如需有關設定預設的功能表命令的詳細資訊，請參閱[SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996) Windows SDK 中和[CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu)此磁碟區中。  
  
##  <a name="onendprinting"></a>CView::OnEndPrinting  
 在列印或預覽文件之後，由架構呼叫。  
  
```  
virtual void OnEndPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指向印表機裝置內容。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述目前列印工作的結構。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 覆寫這個函式，以釋出配置在任何 GDI 資源[OnBeginPrinting](#onbeginprinting)成員函式。  
  
##  <a name="onendprintpreview"></a>CView::OnEndPrintPreview  
 當使用者結束預覽列印模式時，由架構呼叫。  
  
```  
virtual void OnEndPrintPreview(
    CDC* pDC,  
    CPrintInfo* pInfo,  
    POINT point,  
    CPreviewView* pView);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指向印表機裝置內容。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述目前列印工作的結構。  
  
 `point`  
 上次在預覽模式中顯示的頁面上指定的點。  
  
 `pView`  
 指向用來預覽的檢視物件。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會呼叫[OnEndPrinting](#onendprinting)成員函式並還原至之前預覽列印狀態的主框架視窗開始。 覆寫此函式以執行特殊處理終止預覽模式時。 例如，如果您想要維護使用者的文件中的位置，從預覽模式切換到一般顯示模式時，您可以捲動到所描述的位置`point`參數和`m_nCurPage`隸屬`CPrintInfo`結構`pInfo`參數所指向。  
  
 請務必呼叫基底類別版本`OnEndPrintPreview`從覆寫中，通常是在函式結尾。  
  
##  <a name="oninitialupdate"></a>Cview:: Oninitialupdate  
 檢視第一次連接到文件，但最初顯示在檢視之前由架構呼叫。  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會呼叫[OnUpdate](#onupdate)成員函式，而不會提示資訊 (也就使用預設值為 0，表示`lHint`參數和**NULL** 的`pHint`參數)。 覆寫這個函式來執行任何一次的初始化需要文件的相關資訊。 例如，如果您的應用程式有固定大小的文件，您可以使用此函式來初始化文件大小為基礎的檢視捲動限制。 如果您的應用程式支援可變動大小的文件，使用[OnUpdate](#onupdate)更新捲動會限制每次文件的變更。  
  
##  <a name="onpreparedc"></a>CView::OnPrepareDC  
 之前由架構呼叫[OnDraw](#ondraw)螢幕顯示和之前，都會呼叫成員函式[OnPrint](#onprint)為每一頁列印或預覽列印期間呼叫成員函式。  
  
```  
virtual void OnPrepareDC(
    CDC* pDC,  
    CPrintInfo* pInfo = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指向要用來呈現文件的映像的裝置內容。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構描述目前列印工作如果`OnPrepareDC`列印或預覽列印; 正在呼叫`m_nCurPage`成員指定即將列印頁面。 這個參數是**NULL**如果`OnPrepareDC`螢幕上的呼叫。  
  
### <a name="remarks"></a>備註  
 如果在螢幕上顯示呼叫函式，此函式的預設實作會沒有任何作用。 不過，此函式會覆寫在衍生類別中，例如[CScrollView](../../mfc/reference/cscrollview-class.md)、 調整屬性的裝置內容中; 因此，您應該一律呼叫基底類別實作您的覆寫的開頭。  
  
 如果列印呼叫此函式時，預設實作會檢查儲存的頁面資訊`pInfo`參數。 如果未指定文件長度，`OnPrepareDC`假設要很長的一頁的文件，並列印一頁之後，停止列印迴圈。 此函式會藉由設定停止列印迴圈`m_bContinuePrinting`結構的成員**FALSE**。  
  
 覆寫`OnPrepareDC`基於下列原因：  
  
-   視需要針對指定的頁面調整裝置內容的屬性。 例如，如果您需要設定對應模式] 或 [裝置內容的其他特性，這樣在這個函式。  
  
-   若要執行列印時分頁。 通常您指定長度的文件列印開始時，使用[OnPreparePrinting](#onprepareprinting)成員函式。 不過，如果您不知道事先多久文件時，（比方說，從資料庫中列印不明的記錄數目），請覆寫`OnPrepareDC`來測試而在列印文件結尾。 當有沒有其他要列印的文件，來設定`m_bContinuePrinting`隸屬`CPrintInfo`結構以**FALSE**。  
  
-   若要將逸出程式碼傳送到印表機頁面的頁面為基礎。 若要傳送逸出程式碼從`OnPrepareDC`，呼叫**逸出**成員函式`pDC`參數。  
  
 呼叫的基底類別版本`OnPrepareDC`覆寫的開頭。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]  
  
##  <a name="onprepareprinting"></a>CView::OnPreparePrinting  
 列印或預覽文件之前，由架構呼叫。  
  
```  
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)描述目前列印工作的結構。  
  
### <a name="return-value"></a>傳回值  
 若要開始列印，則為非零0，表示已取消列印工作。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。  
  
 您必須覆寫此函式可啟用列印和預覽列印。 呼叫[DoPreparePrinting](#doprepareprinting)成員函式，將其傳遞`pInfo`參數，然後傳回其傳回的值;`DoPreparePrinting`會顯示 [列印] 對話方塊並建立印表機裝置內容。 如果您想要初始化列印 對話方塊，使用預設值以外的值，指定的成員值`pInfo`。 例如，如果您知道文件長度，將值傳遞至[SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage)成員函式`pInfo`之前先呼叫`DoPreparePrinting`。 這個值會顯示在 [收件者:] 方塊中的 [列印] 對話方塊的範圍部分。  
  
 `DoPreparePrinting`不會顯示預覽工作 [列印] 對話方塊。 如果您想略過列印工作的 [列印] 對話方塊，請檢查**m_bPreview**隸屬`pInfo`是**FALSE**然後將它設定為**TRUE**再傳遞給`DoPreparePrinting`; 重設它**FALSE**之後。  
  
 如果您需要執行初始化需要存取`CDC`物件，代表印表機裝置內容 （例如，如果您需要知道的頁面大小指定文件長度之前），覆寫`OnBeginPrinting`成員函式。  
  
 如果您想要設定的值**m_nNumPreviewPages**或**m_strPageDesc**成員`pInfo`參數，這樣做之後呼叫`DoPreparePrinting`。 `DoPreparePrinting`成員函式會將**m_nNumPreviewPages**應用程式中找到的值。INI 檔案，並設定**m_strPageDesc**為其預設值。  
  
### <a name="example"></a>範例  
  覆寫`OnPreparePrinting`呼叫`DoPreparePrinting`從覆寫，讓架構會顯示 [列印] 對話方塊，並為您建立的印表機 DC。  
  
 [!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]  
  
 如果您知道文件包含的頁數，請在中設定最大頁面`OnPreparePrinting`之前先呼叫`DoPreparePrinting`。 架構會顯示在 [列印] 對話方塊的"to"方塊的最大頁面數目。  
  
 [!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]  
  
##  <a name="onprint"></a>CView::OnPrint  
 由架構呼叫以列印或預覽文件的頁面。  
  
```  
virtual void OnPrint(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指向印表機裝置內容。  
  
 `pInfo`  
 指向`CPrintInfo`描述目前列印工作的結構。  
  
### <a name="remarks"></a>備註  
 針對每個列印頁面上，架構會呼叫此函式後立即呼叫[OnPrepareDC](#onpreparedc)成員函式。 指定要列印的頁面`m_nCurPage`隸屬[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構`pInfo`指向。 預設實作會呼叫[OnDraw](#ondraw)成員函式，並將它印表機裝置內容。  
  
 基於下列原因，覆寫這個函式：  
  
-   若要允許列印多頁文件。 轉譯只有對應至目前列印頁面的文件的部分。 如果您使用`OnDraw`用以執行呈現，您可以調整檢視區原點，讓列印文件的適當部分。  
  
-   若要列印的影像看起來與不同的螢幕影像 （也就是如果您的應用程式不是 WYSIWYG）。 而不是傳遞印表機裝置內容，以便`OnDraw`，用來呈現使用屬性不會顯示在螢幕上影像的裝置內容。  
  
     如果您需要不用於螢幕顯示的列印的 GDI 資源，將其選取至繪製前的裝置內容，之後將它們取消選取。 在中，應該配置這些 GDI 資源[OnBeginPrinting](#onbeginprinting)和發行的[OnEndPrinting](#onendprinting)。  
  
-   若要實作的頁首或頁尾。 您仍然可以使用`OnDraw`藉由限制可列印的區域進行轉譯。  
  
 請注意， **m_rectDraw**隸屬`pInfo`參數描述以邏輯單位表示頁面的可列印區域。  
  
 請勿呼叫`OnPrepareDC`的覆寫中`OnPrint`; 架構會呼叫`OnPrepareDC`自動之前先呼叫`OnPrint`。  
  
### <a name="example"></a>範例  
 以下是透過覆寫基本架構`OnPrint`函式：  
  
 [!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]  
  
 如需其他範例，請參閱[CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect)。  
  
##  <a name="onscroll"></a>CView::OnScroll  
 可能是由架構呼叫以判斷是否捲動。  
  
```  
virtual BOOL OnScroll(
    UINT nScrollCode,  
    UINT nPos,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nScrollCode`  
 捲軸程式碼，表示使用者的捲動要求。 這個參數由兩個部分組成： 低序位位元組，這會決定捲動發生水平的型別，以及高序位位元組，這會決定捲動發生垂直的類型：  
  
- **SB_BOTTOM**往下捲動。  
  
- **SB_LINEDOWN**向下捲動一行。  
  
- **SB_LINEUP**向上捲動一行。  
  
- **SB_PAGEDOWN**向下捲動一頁。  
  
- **SB_PAGEUP**向上捲動一頁。  
  
- **SB_THUMBTRACK**拖曳捲動方塊到指定的位置。 在指定目前位置`nPos`。  
  
- **SB_TOP**捲動至頂端。  
  
 `nPos`  
 如果捲軸的程式碼，包含目前捲動方塊位置**SB_THUMBTRACK**; 否則會無法使用。 根據初始的捲軸範圍，`nPos`可以是負數，而且應該轉換成`int`如有必要。  
  
 `bDoScroll`  
 決定是否應實際捲動指定的動作。 如果**為 TRUE，**則捲動應該發生; 如果**FALSE**，然後捲動應該不會發生。  
  
### <a name="return-value"></a>傳回值  
 如果`bDoScroll`是**TRUE**實際上捲動檢視，然後傳回非零，否則為 0。 如果`bDoScroll`是**FALSE**，然後您會有傳回值傳回`bDoScroll`已**TRUE**，即使實際上沒有進行捲動。  
  
### <a name="remarks"></a>備註  
 Framework 以及在其中一個案例呼叫此函式`bDoScroll`設**TRUE**檢視當收到的捲軸的訊息。 在此情況下，您應該實際捲動檢視。 在其他情況下呼叫這個函式與`bDoScroll`設**FALSE**當 OLE 項目一開始拖曳到置放目標的自動捲動區域捲動實際發生之前。 在此情況下，您不應該實際捲動檢視。  
  
##  <a name="onscrollby"></a>CView::OnScrollBy  
 當使用者檢視之外存在檢視文件，將 OLE 項目，對檢視的目前框線拖曳，或藉由操作垂直或水平捲軸的區域，由架構呼叫。  
  
```  
virtual BOOL OnScrollBy(
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `sizeScroll`  
 水平及垂直，捲動瀏覽的像素數目。  
  
 `bDoScroll`  
 判斷是否捲動檢視。 如果**為 TRUE，**捲動才會發生; 然後**FALSE**，然後捲動不會發生。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果檢視能夠捲動;否則便是 0。  
  
### <a name="remarks"></a>備註  
 在衍生類別中這個方法會檢查以查看是否可在使用者要求，然後更新新的區域，如有必要的方向捲動檢視。 此函式會自動呼叫[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)執行實際的捲動要求。  
  
 這個方法的預設實作不會變更檢視，但如果不呼叫時，檢視不會捲動中`CScrollView`-衍生的類別。  
  
 如果文件寬度或高度超過 32767 的像素為單位，超過 32767 捲動會失敗，因為`OnScrollBy`稱為無效`sizeScroll`引數。  
  
##  <a name="onupdate"></a>CView::OnUpdate  
 修改檢視的文件; 之後，由架構呼叫會呼叫此函式[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)並允許更新以反映這些修改顯示的檢視。  
  
```  
virtual void OnUpdate(
    CView* pSender,  
    LPARAM lHint,  
    CObject* pHint);
```  
  
### <a name="parameters"></a>參數  
 `pSender`  
 指向修改文件中，檢視或**NULL**如果所有檢視更新。  
  
 `lHint`  
 包含有關所做的修改資訊。  
  
 `pHint`  
 指向以儲存修改的相關資訊的物件。  
  
### <a name="remarks"></a>備註  
 它也會呼叫的預設實作[OnInitialUpdate](#oninitialupdate)。 預設實作會使整個工作區中，將其標示為繪製時的下一步`WM_PAINT`接收訊息。 如果您想要更新對應至文件已修改的部分這些區域，請覆寫這個函式。 若要這樣做，您必須傳遞使用的提示參數所做的修改的相關資訊。  
  
 若要使用`lHint`、 定義特殊提示值、 通常位元遮罩或列舉型別，以及傳遞這些值的其中一個文件。 若要使用`pHint`，衍生提示類別從[CObject](../../mfc/reference/cobject-class.md)和文件的覆寫時，將指標傳遞到提示的物件; `OnUpdate`，使用[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof)成員函式判斷提示物件的執行階段類型。  
  
 通常您不應該執行任何繪製直接從`OnUpdate`。 相反地，判斷裝置座標中，描述需要更新; 區域的矩形傳遞到這個矩形[CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect)。 這會導致發生在下一次繪製[WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213)接收訊息。  
  
 如果`lHint`為 0 和`pHint`是**NULL**，文件已傳送一般更新通知。 如果檢視收到一般的更新通知，或無法解碼的提示，它應該會使其整個工作區。  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例 MDIDOCVW](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)   
 [CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument 類別](../../mfc/reference/cdocument-class.md)
