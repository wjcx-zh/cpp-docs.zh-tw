---
title: "CView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CView
dev_langs:
- C++
helpviewer_keywords:
- views [C++], view classes
- multiple views
- CView class
- document/view architecture
- input, and view class
- MDI [C++], view windows
- print preview, view windows
- windows [C++], views
- child windows, views
- frame windows [C++], views
- user input [C++], interpreting through view class
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
caps.latest.revision: 25
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
ms.openlocfilehash: ce5100a9ee4a1c20df04f79f0c8cd645ae3afce7
ms.lasthandoff: 02/24/2017

---
# <a name="cview-class"></a>CView 類別
提供使用者定義的檢視類別的基本功能。  
  
## <a name="syntax"></a>語法  
  
```  
class AFX_NOVTABLE CView : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CView::CView](#cview)|建構 `CView` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CView::DoPreparePrinting](#doprepareprinting)|顯示 [列印] 對話方塊並建立印表機裝置內容。覆寫時，呼叫`OnPreparePrinting`成員函式。|  
|[CView::GetDocument](#getdocument)|傳回與檢視相關聯的文件。|  
|[CView::IsSelected](#isselected)|測試是否已選取文件項目。 所需的 OLE 支援。|  
|[CView::OnDragEnter](#ondragenter)|項目第一次拖曳至檢視的拖放區域時呼叫。|  
|[CView::OnDragLeave](#ondragleave)|拖曳的項目離開檢視拖放區域時呼叫。|  
|[CView::OnDragOver](#ondragover)|項目拖曳至檢視的拖放區域上方時呼叫。|  
|[CView::OnDragScroll](#ondragscroll)|呼叫以判斷是否要將資料指標拖曳至捲動視窗的區域。|  
|[CView::OnDrop](#ondrop)|已經卸除項目至檢視時，預設處理常式的拖放區域時呼叫。|  
|[CView::OnDropEx](#ondropex)|已經卸除項目至檢視時，主要的處理常式的拖放區域時呼叫。|  
|[Cview:: Oninitialupdate](#oninitialupdate)|檢視第一次連接至文件之後呼叫。|  
|[CView::OnPrepareDC](#onpreparedc)|之前呼叫`OnDraw`螢幕上顯示呼叫成員函式或`OnPrint`列印或列印預覽呼叫成員函式。|  
|[CView::OnScroll](#onscroll)|當 OLE 項目拖曳超出檢視的邊界時呼叫。|  
|[CView::OnScrollBy](#onscrollby)|捲動檢視，包含使用中的就地 OLE 項目時呼叫。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CView::OnActivateFrame](#onactivateframe)|包含檢視的框架視窗是啟用或停用時呼叫。|  
|[CView::OnActivateView](#onactivateview)|檢視啟動時呼叫。|  
|[CView::OnBeginPrinting](#onbeginprinting)|呼叫時開始列印工作。覆寫，以配置圖形裝置介面 (GDI) 資源。|  
|[Ongetembeddeditem](#ondraw)|呼叫來轉譯螢幕顯示、 列印或預覽列印的文件的映像。 所需的實作。|  
|[CView::OnEndPrinting](#onendprinting)|呼叫時結束某項列印工作。若要解除配置 GDI 資源覆寫。|  
|[CView::OnEndPrintPreview](#onendprintpreview)|預覽模式結束時呼叫。|  
|[CView::OnPreparePrinting](#onprepareprinting)|列印或預覽; 文件之前呼叫覆寫以初始化 [列印] 對話方塊。|  
|[CView::OnPrint](#onprint)|呼叫以列印或預覽文件的頁面。|  
|[CView::OnUpdate](#onupdate)|呼叫以通知的檢視，其文件已被修改。|  
  
## <a name="remarks"></a>備註  
 檢視附加至文件，並做為文件與使用者之間的媒介︰ 檢視呈現在螢幕或印表機上的文件影像，但將使用者輸入解譯為文件的操作。  
  
 檢視是框架視窗的子系。 多個檢視可以共用框架視窗，如下所示的分隔視窗的大小寫。 框架視窗類別中，檢視類別的文件類別之間的關聯性由建立`CDocTemplate`物件。 當使用者開啟新視窗或分割現有一個架構建構新的檢視，並將其附加至文件。  
  
 檢視可以附加至單一文件，但文件可以有多個同時連接到它的檢視 — 例如，如果文件會顯示在分隔視窗中，或在多個文件介面 (MDI) 應用程式中的多個子視窗。 您的應用程式可支援不同類型的檢視給定文件類型。例如，文書處理程式可能會提供文件的完整文字檢視和顯示區段標頭的大綱檢視。 這些不同類型的檢視可以放在個別的框架視窗中，或在個別的單一框架視窗的窗格如果您使用的分隔視窗。  
  
 檢視可能會負責處理許多不同類型的輸入，例如鍵盤、 滑鼠輸入或輸入透過拖放，以及命令的功能表、 工具列或捲軸。 檢視接收轉送的其框架視窗的命令。 如果檢視不會處理指定的命令，它會轉送至其相關聯的文件的命令。 所有的命令目標，例如檢視會處理透過訊息對應的訊息。  
  
 此檢視會負責顯示和修改文件的資料，但不適用於儲存它。 文件提供有關其資料與必要的詳細資料檢視。 您可以讓文件的資料成員，或者您可以提供成員函式呼叫的檢視類別的文件類別中的檢視存取權。  
  
 當文件的資料變更時，負責變更檢視通常會呼叫[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)文件，就會通知所有其他檢視所呼叫的函式`OnUpdate`每個成員函式。 預設實作`OnUpdate`使檢視的整個用戶端區域。 您可以覆寫它使其失效的只有這些區域的工作區對應至文件已修改的部分。  
  
 若要使用`CView`、 衍生的類別和實作`OnDraw`進行螢幕顯示的成員函式。 您也可以使用`OnDraw`執行列印和預覽列印。 架構會處理列印和文件預覽列印迴圈。  
  
 檢視會處理具有捲軸訊息[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成員函式。 您可以實作捲軸訊息處理的這些函式，或者您可以使用`CView`衍生的類別[CScrollView](../../mfc/reference/cscrollview-class.md)來處理您捲動功能。  
  
 除了`CScrollView`，Mfc 程式庫提供九個衍生自其他類別`CView`:  
  
- [CCtrlView](../../mfc/reference/cctrlview-class.md)，允許文件-架構與樹狀目錄、 清單和 rich edit 控制項的檢視使用的檢視。  
  
- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)，對話方塊在控制項中顯示資料庫記錄的檢視。  
  
- [CEditView](../../mfc/reference/ceditview-class.md)，提供一個簡單的多行文字編輯器的檢視。 您可以使用`CEditView`為控制項的對話方塊，以及文件中的檢視中的物件。  
  
- [CFormView](../../mfc/reference/cformview-class.md)，包含對話方塊控制項和對話方塊範本資源為基礎的可捲動檢視。  
  
- [CListView](../../mfc/reference/clistview-class.md)，允許使用文件-使用清單控制項的檢視架構的檢視。  
  
- [CRecordView](../../mfc/reference/crecordview-class.md)，對話方塊在控制項中顯示資料庫記錄的檢視。  
  
- [CRichEditView](../../mfc/reference/cricheditview-class.md)，允許文件-架構與 rich edit 控制項的檢視使用的檢視。  
  
- [CScrollView](../../mfc/reference/cscrollview-class.md)，會自動提供支援捲動檢視。  
  
- [CTreeView](../../mfc/reference/ctreeview-class.md)，允許使用文件-檢視架構與樹狀目錄控制項的檢視。  
  
 `CView`類別也具有名為衍生的實作類別**CPreviewView**，由架構用來執行 預覽列印時。 這個類別提供預覽列印 視窗中，例如工具列、 單一或雙頁面預覽的獨特功能的支援和縮放的，擴大預覽的影像。 您不需要呼叫或覆寫任何**CPreviewView**的成員函式，除非您想要實作您自己的預覽列印的介面 （例如，如果您想要支援在預覽列印模式中編輯）。 如需有關使用`CView`，請參閱[文件/檢視架構](../../mfc/document-view-architecture.md)和[列印](../../mfc/printing.md)。 此外，請參閱[技術附註 30](../../mfc/tn030-customizing-printing-and-print-preview.md)如需有關自訂列印預覽。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CView`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-namecviewa--cviewcview"></a><a name="cview"></a>CView::CView  
 建構 `CView` 物件。  
  
```  
CView();
```  
  
### <a name="remarks"></a>備註  
 建立新的框架視窗，或分隔視窗時，架構會呼叫建構函式。 覆寫[OnInitialUpdate](#oninitialupdate)文件連結之後初始化檢視的成員函式。  
  
##  <a name="a-namedoprepareprintinga--cviewdoprepareprinting"></a><a name="doprepareprinting"></a>CView::DoPreparePrinting  
 呼叫此函式的覆寫從[OnPreparePrinting](#onprepareprinting)叫用 [列印] 對話方塊中，並建立印表機裝置內容。  
  
```  
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)該結構描述目前的列印工作。  
  
### <a name="return-value"></a>傳回值  
 非零，如果可以開始列印或列印預覽。0，表示作業已取消。  
  
### <a name="remarks"></a>備註  
 此函式的行為取決於是否呼叫它的列印或預覽列印 (所指定**m_bPreview**成員`pInfo`參數)。 如果列印檔案後，此函式會叫用列印對話方塊中，使用中的值[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構`pInfo`指向; 使用者關閉對話方塊之後，此函數便會根據使用者在對話方塊中指定，並傳回透過這個裝置內容設定的印表機裝置內容`pInfo`參數。 這個裝置內容用來列印文件。  
  
 如果預覽檔案時，此函式會建立使用目前的印表機設定，印表機裝置內容這個裝置內容可以用來模擬在預覽期間的印表機。  
  
##  <a name="a-namegetdocumenta--cviewgetdocument"></a><a name="getdocument"></a>CView::GetDocument  
 呼叫此函式可取得檢視的文件的指標。  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CDocument](../../mfc/reference/cdocument-class.md)與檢視相關聯的物件。 **NULL**檢視並未附加至文件。  
  
### <a name="remarks"></a>備註  
 這可讓您呼叫文件的成員函式。  
  
##  <a name="a-nameisselecteda--cviewisselected"></a><a name="isselected"></a>CView::IsSelected  
 若要檢查是否已選取指定的文件項目架構呼叫。  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `pDocItem`  
 指向要測試的文件項目。  
  
### <a name="return-value"></a>傳回值  
 選取指定的文件項目; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會傳回**FALSE**。 覆寫這個函式，如果您正在實作選擇使用[CDocItem](../../mfc/reference/cdocitem-class.md)物件。 如果您檢視包含 OLE 項目，您必須覆寫這個函式。  
  
##  <a name="a-nameonactivateframea--cviewonactivateframe"></a><a name="onactivateframe"></a>CView::OnActivateFrame  
 包含檢視的框架視窗是啟用或停用時，由架構呼叫。  
  
```  
virtual void OnActivateFrame(
    UINT nState,  
    CFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>參數  
 `nState`  
 指定是否要在框架視窗啟用或停用。 它可以是下列值之一︰  
  
- **WA_INACTIVE**框架視窗正在停用。  
  
- **WA_ACTIVE**框架視窗正在啟用透過某些方法以外 （例如，藉由使用的選取視窗的鍵盤介面） 按一下滑鼠。  
  
- **WA_CLICKACTIVE**滑鼠點按啟動框架視窗  
  
 `pFrameWnd`  
 要啟動的框架視窗的指標。  
  
### <a name="remarks"></a>備註  
 如果您想要執行特殊處理與檢視相關聯的框架視窗是啟用或停用時，覆寫此成員函式。 例如， [CFormView](../../mfc/reference/cformview-class.md)執行此覆寫時，它會儲存並還原具有焦點的控制項。  
  
##  <a name="a-nameonactivateviewa--cviewonactivateview"></a><a name="onactivateview"></a>CView::OnActivateView  
 啟用或停用檢視時，由架構呼叫。  
  
```  
virtual void OnActivateView(
    BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView);
```  
  
### <a name="parameters"></a>參數  
 `bActivate`  
 指出檢視是否目前已啟用或停用。  
  
 `pActivateView`  
 正在啟動之 view 物件的指標。  
  
 `pDeactiveView`  
 正在停用的檢視物件的指標。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會將焦點設的檢視，使其無法啟動。 如果您想要執行特殊處理，啟用或停用檢視時，覆寫這個函式。 例如，如果您想要提供特殊視覺提示以區別現用檢視的非作用中的檢視，您會檢查`bActivate`參數並據此更新檢視的外觀。  
  
 `pActivateView`和`pDeactiveView`參數指向同一個檢視如果應用程式的主框架視窗已啟動且不會變更使用中的檢視 — 例如，如果焦點在傳輸到這台，另一個應用程式，而不是一個檢視，以另一個應用程式內或 MDI 子視窗之間切換時。 如有需要這可讓重新了解其調色盤上，檢視。  
  
 這些參數與不同時[CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview)檢視不同的功能稱為[CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview)會傳回。 發生這種情況最常使用分隔視窗。  
  
##  <a name="a-nameonbeginprintinga--cviewonbeginprinting"></a><a name="onbeginprinting"></a>CView::OnBeginPrinting  
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
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)該結構描述目前的列印工作。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 覆寫此函式以配置列印特別需要的任何 GDI 資源，例如畫筆或字型。 選取的 GDI 物件放入裝置內容中，從[OnPrint](#onprint)成員函式會使用這些資源的每一頁。 如果您使用相同的檢視物件來執行螢幕顯示和列印，請為每個顯示所需的 GDI 資源使用不同的變數；這可讓您在列印期間更新螢幕。  
  
 您也可以使用此函式，執行因印表機裝置內容屬性而異的初始設定。 例如，列印文件所需的頁數可能會因使用者在 [列印] 對話方塊中指定的設定 (例如頁面長度) 而異。 在這種情況下，您無法指定文件的長度，以[OnPreparePrinting](#onprepareprinting)成員函式，其中通常會進行操作，您必須等到印表機裝置內容建立根據對話方塊設定。 [OnBeginPrinting](#onbeginprinting)是第一個可覆寫函式，可讓您存取[CDC](../../mfc/reference/cdc-class.md)物件，代表印表機裝置內容，因此您可以從這個函式來設定文件的長度。 請注意，如果此時未指定文件長度，預覽列印期間將不會顯示捲軸。  
  
##  <a name="a-nameondragentera--cviewondragenter"></a><a name="ondragenter"></a>CView::OnDragEnter  
 當滑鼠初次進入置放目標視窗的非捲動區域，由架構呼叫。  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)被拖曳至檢視的放置區。  
  
 `dwKeyState`  
 包含輔助按鍵的狀態。 這是下列任何數目的組合︰ **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 目前滑鼠位置相對於用戶端區域的檢視。  
  
### <a name="return-value"></a>傳回值  
 介於`DROPEFFECT`列舉型別，指出如果使用者在這個位置卸除物件就會發生的卸除的類型。 卸除類型通常取決於目前所指示的索引鍵狀態`dwKeyState`。 以 keystates 標準對應`DROPEFFECT`值為︰  
  
- `DROPEFFECT_NONE`無法卸除的資料物件，此視窗中。  
  
- `DROPEFFECT_LINK`如**MK_CONTROL |MK_SHIFT**建立物件和它的伺服器之間的連結。  
  
- `DROPEFFECT_COPY`如**MK_CONTROL**會建立一份已卸除物件。  
  
- `DROPEFFECT_MOVE`如**MK_ALT**會建立一份已卸除的物件，並刪除原始的物件。 這通常是預設的拖放效果，檢視可接受這個資料物件。  
  
 如需詳細資訊，請參閱 MFC 進階概念範例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>備註  
 預設實作會執行任何動作，並傳回`DROPEFFECT_NONE`。  
  
 若要準備的未來呼叫此函式會覆寫[OnDragOver](#ondragover)成員函式。 應該擷取從資料物件所需的任何資料，供稍後使用，此時`OnDragOver`成員函式。 讓使用者視覺化回應，此時也應該更新檢視。 如需詳細資訊，請參閱文章[將拖放︰ 實作置放目標](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="a-nameondragleavea--cviewondragleave"></a><a name="ondragleave"></a>CView::OnDragLeave  
 有效的置放區超出該視窗移動滑鼠時呼叫架構在拖曳作業期間。  
  
```  
virtual void OnDragLeave();
```  
  
### <a name="remarks"></a>備註  
 如果目前的檢視必須清除期間採取任何動作，請覆寫此函數[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)呼叫，例如當物件被拖曳和卸除時移除任何視覺化使用者意見反應。  
  
##  <a name="a-nameondragovera--cviewondragover"></a><a name="ondragover"></a>CView::OnDragOver  
 當滑鼠移動經過置放目標視窗呼叫由架構在拖曳作業期間。  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)拖曳到置放目標。  
  
 `dwKeyState`  
 包含輔助按鍵的狀態。 這是下列任何數目的組合︰ **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 目前的滑鼠位置相對於檢視用戶端區域。  
  
### <a name="return-value"></a>傳回值  
 介於`DROPEFFECT`列舉型別，指出如果使用者在這個位置卸除物件就會發生的卸除的類型。 卸除類型通常取決於目前的索引鍵狀態所示`dwKeyState`。 以 keystates 標準對應`DROPEFFECT`值為︰  
  
- `DROPEFFECT_NONE`無法卸除的資料物件，此視窗中。  
  
- `DROPEFFECT_LINK`如**MK_CONTROL |MK_SHIFT**建立物件和它的伺服器之間的連結。  
  
- `DROPEFFECT_COPY`如**MK_CONTROL**會建立一份已卸除物件。  
  
- `DROPEFFECT_MOVE`如**MK_ALT**會建立一份已卸除的物件，並刪除原始的物件。 這通常是預設的拖放效果，檢視可接受的資料物件。  
  
 如需詳細資訊，請參閱 MFC 進階概念範例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>備註  
 預設實作會執行任何動作，並傳回`DROPEFFECT_NONE`。  
  
 此函式可讓使用者視覺化回應拖曳作業期間會覆寫。 因為連續呼叫此函式，其內所含的任何程式碼應該最佳化儘可能。 如需詳細資訊，請參閱文章[將拖放︰ 實作置放目標](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="a-nameondragscrolla--cviewondragscroll"></a><a name="ondragscroll"></a>CView::OnDragScroll  
 然後再呼叫架構呼叫[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)判斷點是否捲動區域。  
  
```  
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `dwKeyState`  
 包含輔助按鍵的狀態。 這是下列任何數目的組合︰ **MK_CONTROL**， **MK_SHIFT**， **MK_ALT**， **MK_LBUTTON**， **MK_MBUTTON**，和**MK_RBUTTON**。  
  
 `point`  
 包含的資料指標，相對於螢幕像素為單位的位置。  
  
### <a name="return-value"></a>傳回值  
 介於`DROPEFFECT`列舉型別，指出如果使用者在這個位置卸除物件就會發生的卸除的類型。 卸除類型通常取決於目前所指示的索引鍵狀態`dwKeyState`。 以 keystates 標準對應`DROPEFFECT`值為︰  
  
- `DROPEFFECT_NONE`無法卸除的資料物件，此視窗中。  
  
- `DROPEFFECT_LINK`如**MK_CONTROL |MK_SHIFT**建立物件和它的伺服器之間的連結。  
  
- `DROPEFFECT_COPY`如**MK_CONTROL**會建立一份已卸除物件。  
  
- `DROPEFFECT_MOVE`如**MK_ALT**會建立一份已卸除的物件，並刪除原始的物件。  
  
- `DROPEFFECT_SCROLL`表示拖曳捲軸作業即將發生或發生在 [目標] 檢視。  
  
 如需詳細資訊，請參閱 MFC 進階概念範例[OCLIENT](../../visual-cpp-samples.md)。  
  
### <a name="remarks"></a>備註  
 當您想要針對此事件提供特殊行為時，覆寫這個函式。 預設實作資料指標拖曳至預設的捲動區域內的每個視窗框線時，會自動捲動 windows。如需詳細資訊，請參閱文章[將拖放︰ 實作置放目標](../../mfc/drag-and-drop-implementing-a-drop-target.md)。  
  
##  <a name="a-nameondrawa--cviewondraw"></a><a name="ondraw"></a>Ongetembeddeditem  
 呈現影像的文件的架構所呼叫。  
  
```  
virtual void OnDraw(CDC* pDC) = 0;  
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 裝置內容，以便用來呈現文件的映像的指標。  
  
### <a name="remarks"></a>備註  
 架構會呼叫此函式來執行螢幕顯示、 列印和預覽列印，並且會傳遞不同的裝置內容中的每個案例。 沒有預設的實作。  
  
 您必須覆寫這個函式來顯示文件的檢視。 您可以使用的圖形裝置介面 (GDI) 呼叫[CDC](../../mfc/reference/cdc-class.md)指向的物件`pDC`參數。 您可以選取放入裝置內容中繪製前的 GDI 資源，例如 [畫筆] 或 [字型]，並接著之後取消。 繪圖程式碼通常可以與裝置無關。也就是說，它不需要哪種裝置類型顯示影像的相關資訊。  
  
 若要最佳化的繪圖，呼叫[RectVisible](../../mfc/reference/cdc-class.md#rectvisible)裝置內容，以找出是否要繪製指定的矩形的成員函式。 如果您需要區別正常螢幕顯示和列印，呼叫[IsPrinting](../../mfc/reference/cdc-class.md#isprinting)裝置內容的成員函式。  
  
##  <a name="a-nameondropa--cviewondrop"></a><a name="ondrop"></a>CView::OnDrop  
 在使用者釋放資料物件的有效置放目標時，由架構呼叫。  
  
```  
virtual BOOL OnDrop(
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md) ，放入置放目標。  
  
 `dropEffect`  
 使用者已要求置放效果。  
  
- `DROPEFFECT_COPY`建立要卸除的資料物件的複本。  
  
- `DROPEFFECT_MOVE`將資料物件移至目前的滑鼠位置。  
  
- `DROPEFFECT_LINK`建立資料物件和它的伺服器之間的連結。  
  
 `point`  
 目前的滑鼠位置相對於檢視用戶端區域。  
  
### <a name="return-value"></a>傳回值  
 非零，如果卸除成功。否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作，並傳回**FALSE**。  
  
 覆寫此函式可檢視的工作區中實作的 OLE 拖放效果。 資料物件可以透過檢查`pDataObject`剪貼簿資料格式和資料在卸除指定的點。  
  
> [!NOTE]
>  架構不會呼叫此函式，如果沒有覆寫， [OnDropEx](#ondropex)這個檢視類別中。  
  
##  <a name="a-nameondropexa--cviewondropex"></a><a name="ondropex"></a>CView::OnDropEx  
 在使用者釋放資料物件的有效置放目標時，由架構呼叫。  
  
```  
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md) ，放入置放目標。  
  
 `dropDefault`  
 使用者選擇根據索引鍵的目前狀態的預設拖放作業效果。 可能是`DROPEFFECT_NONE`。 < 備註 > 一節中討論的置放效果。  
  
 `dropList`  
 卸除來源支援拖放效果的清單。 可以使用的位元 OR 合併置放效果值 ( **|**) 作業。 < 備註 > 一節中討論的置放效果。  
  
 `point`  
 目前的滑鼠位置相對於檢視用戶端區域。  
  
### <a name="return-value"></a>傳回值  
 卸除嘗試在所指定的位置所產生的置放效果`point`。 這必須是其中一個值表示*dropEffectList*。 < 備註 > 一節中討論的置放效果。  
  
### <a name="remarks"></a>備註  
 預設實作會執行任何動作，並傳回空值 (-1)，表示應該呼叫架構[OnDrop](#ondrop)處理常式。  
  
 覆寫此函式以實作滑鼠右鍵拖曳和卸除的效果。 滑鼠右鍵拖曳和卸除通常會顯示選項功能表時釋放滑鼠右按鈕。  
  
 覆寫`OnDropEx`應該查詢滑鼠右按鈕。 您可以呼叫[GetKeyState](http://msdn.microsoft.com/library/windows/desktop/ms646301)或從右邊的滑鼠按鈕狀態儲存您[OnDragEnter](#ondragenter)處理常式。  
  
-   如果右邊的滑鼠按鈕已關閉，您的覆寫應該會顯示快顯功能表提供支援置放來源置放效果。  
  
    -   檢查`dropList`以判斷拖曳來源所支援的拖放效果。 啟用快顯功能表中的這些動作。  
  
    -   使用[SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996)設為基礎的預設動作`dropDefault`。  
  
    -   最後，採取動作以快顯功能表的使用者選取項目。  
  
-   如果未按下滑鼠右鍵，覆寫應該處理這個做為標準的卸除要求。 使用指定的拖放效果`dropDefault`。 或者，您的覆寫可能會傳回空值 (-1)，指出`OnDrop`會處理此拖放作業。  
  
 使用`pDataObject`檢查`COleDataObject`剪貼簿資料格式和資料在卸除指定的點。  
  
 置放效果會描述與拖放作業相關聯的動作。 請參閱下列置放效果的清單︰  
  
- `DROPEFFECT_NONE`不會允許置放。  
  
- `DROPEFFECT_COPY`執行複製作業。  
  
- `DROPEFFECT_MOVE`會執行移動作業。  
  
- `DROPEFFECT_LINK`會建立原始資料的連結從卸除的資料。  
  
- `DROPEFFECT_SCROLL`表示拖曳捲軸作業即將發生或發生在目標中。  
  
 如需有關如何設定預設的功能表命令的詳細資訊，請參閱[SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]和[CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu)此磁碟區中。  
  
##  <a name="a-nameonendprintinga--cviewonendprinting"></a><a name="onendprinting"></a>CView::OnEndPrinting  
 列印或預覽的文件之後，由架構呼叫。  
  
```  
virtual void OnEndPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指向印表機裝置內容。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)該結構描述目前的列印工作。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 覆寫這個函式來釋放任何您在中配置的 GDI 資源[OnBeginPrinting](#onbeginprinting)成員函式。  
  
##  <a name="a-nameonendprintpreviewa--cviewonendprintpreview"></a><a name="onendprintpreview"></a>CView::OnEndPrintPreview  
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
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)該結構描述目前的列印工作。  
  
 `point`  
 在上一次顯示在預覽模式 頁面上指定的點。  
  
 `pView`  
 用來預覽的檢視物件的指標。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會呼叫[OnEndPrinting](#onendprinting)成員函式並還原主框架視窗的預覽列印之前的狀態開始。 覆寫這個函式來執行特殊處理終止預覽模式時。 例如，如果您想要維護使用者的文件中的位置，從 [預覽] 模式切換到一般顯示模式時，您可以捲動所描述的位置`point`參數和`m_nCurPage`成員`CPrintInfo`結構`pInfo`參數所指向。  
  
 請務必呼叫基底類別版本`OnEndPrintPreview`從您的覆寫通常是在函式結尾。  
  
##  <a name="a-nameoninitialupdatea--cviewoninitialupdate"></a><a name="oninitialupdate"></a>Cview:: Oninitialupdate  
 檢視第一次連接到文件之後，但一開始會顯示檢視之前，由架構呼叫。  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會呼叫[OnUpdate](#onupdate)成員函式，而沒有提示的資訊 (也就使用預設值為 0，表示`lHint`參數和**NULL**的`pHint`參數)。 覆寫這個函式來執行任何需要文件的相關資訊的單次初始化。 比方說，如果您的應用程式有固定大小的文件，您可以使用此函式來初始化檢視的捲動根據文件大小的限制。 如果您的應用程式支援可變大小的文件，使用[OnUpdate](#onupdate)更新捲動會限制每次文件的變更。  
  
##  <a name="a-nameonpreparedca--cviewonpreparedc"></a><a name="onpreparedc"></a>CView::OnPrepareDC  
 之前的架構所呼叫[OnDraw](#ondraw)螢幕顯示和更早呼叫成員函式[OnPrint](#onprint)成員函式列印或預覽列印期間，會呼叫每個頁面。  
  
```  
virtual void OnPrepareDC(
    CDC* pDC,  
    CPrintInfo* pInfo = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 裝置內容，以便用來呈現文件的映像的指標。  
  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構描述目前的列印工作，如果`OnPrepareDC`呼叫以列印或列印預覽功能;`m_nCurPage`成員指定即將列印的頁面。 這個參數是**NULL**如果`OnPrepareDC`螢幕上的呼叫。  
  
### <a name="remarks"></a>備註  
 如果螢幕顯示被呼叫函式，此函式的預設實作會沒有作用。 不過，此函式會覆寫在衍生類別中，例如[CScrollView](../../mfc/reference/cscrollview-class.md)、 調整屬性的裝置內容中; 因此，務必呼叫基底類別實作您的覆寫的開頭。  
  
 如果列印的呼叫函式，則預設實作會檢查中儲存的頁面資訊`pInfo`參數。 如果未指定文件的長度，`OnPrepareDC`假設只有一頁長文件，並在列印頁之後，停止列印迴圈。 函式藉由設定停止列印迴圈`m_bContinuePrinting`結構的成員**FALSE**。  
  
 覆寫`OnPrepareDC`基於下列原因︰  
  
-   視需要針對指定的頁面調整裝置內容的屬性。 比方說，如果您需要設定的對應模式] 或 [裝置內容的其他特性，這樣在這個函式。  
  
-   若要執行列印時分頁。 通常您指定長度的文件列印開始時，使用[OnPreparePrinting](#onprepareprinting)成員函式。 不過，如果您不知道事先多久文件列印中時 （例如，不確定的數目的記錄從資料庫），覆寫`OnPrepareDC`測試時在列印文件結尾。 當有沒有其他要列印的文件，來設定`m_bContinuePrinting`成員`CPrintInfo`結構以**FALSE**。  
  
-   若要傳送至印表機的頁面為基礎的逸出程式碼。 若要傳送逸出程式碼從`OnPrepareDC`，呼叫**逸出**成員函式`pDC`參數。  
  
 呼叫基底類別版本`OnPrepareDC`覆寫的開頭。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&183;](../../mfc/codesnippet/cpp/cview-class_1.cpp)]  
  
##  <a name="a-nameonprepareprintinga--cviewonprepareprinting"></a><a name="onprepareprinting"></a>CView::OnPreparePrinting  
 由架構呼叫之前列印或預覽文件。  
  
```  
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pInfo`  
 指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)該結構描述目前的列印工作。  
  
### <a name="return-value"></a>傳回值  
 非零開始列印。0，表示已取消列印工作。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。  
  
 您必須覆寫這個函式會啟用列印和預覽列印。 呼叫[DoPreparePrinting](#doprepareprinting)成員函式，將它傳遞`pInfo`參數，然後傳回它的傳回值。`DoPreparePrinting`會顯示 [列印] 對話方塊中，並建立印表機裝置內容。 如果您想要初始化列印對話方塊中，使用預設值以外的值，指定的成員值`pInfo`。 例如，如果您知道文件的長度，將值傳遞到[SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage)成員函式`pInfo`之前，先呼叫`DoPreparePrinting`。 這個值會顯示在 [收件者:] 方塊中的 [列印] 對話方塊中的範圍部分。  
  
 `DoPreparePrinting`不會顯示預覽工作 [列印] 對話方塊。 如果您想要略過的列印工作的 [列印] 對話方塊，請檢查**m_bPreview**成員`pInfo`是**FALSE**然後將它設定為**TRUE**再傳遞給`DoPreparePrinting`; 它重設為**FALSE**之後。  
  
 如果您要執行需要存取的初始化`CDC`物件，代表印表機裝置內容 （例如，如果您需要知道的頁面大小指定文件的長度），覆寫`OnBeginPrinting`成員函式。  
  
 如果您想要設定的值**m_nNumPreviewPages**或**m_strPageDesc**成員`pInfo`參數，執行這項操作之後呼叫`DoPreparePrinting`。 `DoPreparePrinting`成員函式集合**m_nNumPreviewPages**找到的應用程式中的值。INI 檔案，並設定**m_strPageDesc**為其預設值。  
  
### <a name="example"></a>範例  
  覆寫`OnPreparePrinting`呼叫`DoPreparePrinting`覆寫從使得架構將顯示 [列印] 對話方塊，然後為您建立的印表機 DC。  
  
 [!code-cpp[NVC_MFCDocView #&184;](../../mfc/codesnippet/cpp/cview-class_2.cpp)]  
  
 如果您知道文件中包含的頁數，請在中設定最大頁面`OnPreparePrinting`之前，先呼叫`DoPreparePrinting`。 架構會顯示 [列印] 對話方塊中的 「 目標 」 方塊中的最大頁面數目。  
  
 [!code-cpp[NVC_MFCDocView #&185;](../../mfc/codesnippet/cpp/cview-class_3.cpp)]  
  
##  <a name="a-nameonprinta--cviewonprint"></a><a name="onprint"></a>CView::OnPrint  
 若要列印或預覽文件的頁面架構呼叫。  
  
```  
virtual void OnPrint(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指向印表機裝置內容。  
  
 `pInfo`  
 指向`CPrintInfo`該結構描述目前的列印工作。  
  
### <a name="remarks"></a>備註  
 針對每個正在列印的頁面，架構會呼叫此函式後立即呼叫[OnPrepareDC](#onpreparedc)成員函式。 正在列印的頁面由`m_nCurPage`成員[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構`pInfo`指向。 預設實作會呼叫[OnDraw](#ondraw)成員函式，並將它印表機裝置內容。  
  
 基於下列原因，覆寫這個函式︰  
  
-   若要允許列印多頁文件。 轉譯只對應於目前列印的頁面的文件的一部分。 如果您使用`OnDraw`若要執行的轉譯，您可以調整檢視區原點使列印文件的適當部分。  
  
-   若要列印的影像看起來不同於螢幕影像 （也就是說，如果您的應用程式不是 WYSIWYG）。 而不是傳遞印表機裝置內容至`OnDraw`，用來呈現使用屬性不會顯示在螢幕上影像的裝置內容。  
  
     如果您不要使用螢幕上顯示的列印需要 GDI 資源放入裝置內容中繪製前加以選取，之後將它們取消選取。 這些 GDI 資源應該配置在[OnBeginPrinting](#onbeginprinting)及發行在[OnEndPrinting](#onendprinting)。  
  
-   若要實作的頁首或頁尾。 您仍然可以使用`OnDraw`如何呈現藉由限制可列印的區域。  
  
 請注意， **m_rectDraw**成員`pInfo`參數描述中的邏輯單元的頁面可列印區域。  
  
 請勿呼叫`OnPrepareDC`在覆寫`OnPrint`，架構會呼叫`OnPrepareDC`呼叫之前自動`OnPrint`。  
  
### <a name="example"></a>範例  
 以下是透過覆寫基本架構`OnPrint`函式︰  
  
 [!code-cpp[NVC_MFCDocView #&186;](../../mfc/codesnippet/cpp/cview-class_4.cpp)]  
  
 如需其他範例，請參閱[CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect)。  
  
##  <a name="a-nameonscrolla--cviewonscroll"></a><a name="onscroll"></a>CView::OnScroll  
 若要判斷是否捲動架構呼叫可供使用。  
  
```  
virtual BOOL OnScroll(
    UINT nScrollCode,  
    UINT nPos,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nScrollCode`  
 捲軸程式碼，指出使用者的捲動要求。 這個參數由兩個部分組成︰ 低序位位元組，這會決定捲動發生水平的型別，以及高序位位元組，這會決定捲動發生垂直的型別︰  
  
- **SB_BOTTOM**向下捲動。  
  
- **SB_LINEDOWN**向下捲動一行。  
  
- **SB_LINEUP**向上捲動一行。  
  
- **SB_PAGEDOWN**向下捲動一頁。  
  
- **SB_PAGEUP**向上捲動一頁。  
  
- **SB_THUMBTRACK**拖曳捲動方塊以指定的位置。 目前的位置中指定`nPos`。  
  
- **SB_TOP**捲動至最上方。  
  
 `nPos`  
 如果捲軸的程式碼，包含目前的捲動方塊位置**SB_THUMBTRACK**; 否則會無法使用。 根據初始的捲軸範圍，`nPos`可能是負數，並且應該轉換成`int`如有必要。  
  
 `bDoScroll`  
 決定是否應該實際進行指定捲動的動作。 如果**為 TRUE，**再捲動應該發生; 如果**FALSE**，然後捲動應該不會發生。  
  
### <a name="return-value"></a>傳回值  
 如果`bDoScroll`是**TRUE**實際上捲動檢視，然後傳回非零，否則為 0。 如果`bDoScroll`是**FALSE**，則傳回值，如果會傳回您`bDoScroll`已**TRUE**，即使實際上沒有進行捲動。  
  
### <a name="remarks"></a>備註  
 使用架構在某種情況下呼叫這個函式`bDoScroll`設**TRUE**檢視當接收捲軸訊息。 在此情況下，您應該實際捲動檢視。 在其他情況下呼叫這個函式與`bDoScroll`設**FALSE**當 OLE 項目一開始拖曳到置放目標的自動捲動區域捲動實際發生之前。 在此情況下，您不應該實際捲動檢視。  
  
##  <a name="a-nameonscrollbya--cviewonscrollby"></a><a name="onscrollby"></a>CView::OnScrollBy  
 當使用者檢視之外存在的文件，藉由拖曳 OLE 項目對檢視目前的框線或操作的垂直或水平捲軸檢視區域時，由架構呼叫。  
  
```  
virtual BOOL OnScrollBy(
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `sizeScroll`  
 水平及垂直，捲動到 像素數目。  
  
 `bDoScroll`  
 判斷是否捲動檢視。 如果**為 TRUE，**捲動會發生; 然後**FALSE**，然後捲動不會發生。  
  
### <a name="return-value"></a>傳回值  
 檢視已設為 1; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 在衍生類別中這個方法會檢查以查看是否可在使用者要求，然後更新新的區域，如有必要的方向捲動檢視。 此函式會自動呼叫[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)執行實際的捲動要求。  
  
 這個方法的預設實作不會變更檢視，但如果不呼叫時，檢視不會捲動中`CScrollView`-衍生的類別。  
  
 如果文件寬度或高度超過 32767 個像素，超過 32767 捲動會失敗，因為`OnScrollBy`稱為無效`sizeScroll`引數。  
  
##  <a name="a-nameonupdatea--cviewonupdate"></a><a name="onupdate"></a>CView::OnUpdate  
 修改檢視的文件; 之後，由框架呼叫此函式會呼叫[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) ，並可讓更新以反映這些修改顯示的檢視。  
  
```  
virtual void OnUpdate(
    CView* pSender,  
    LPARAM lHint,  
    CObject* pHint);
```  
  
### <a name="parameters"></a>參數  
 `pSender`  
 指向修改文件中，檢視或**NULL**如果所有的檢視更新。  
  
 `lHint`  
 包含資訊所做的修改。  
  
 `pHint`  
 指向以儲存修改的相關資訊的物件。  
  
### <a name="remarks"></a>備註  
 它也可以呼叫的預設實作[OnInitialUpdate](#oninitialupdate)。 預設實作會使整個工作區中，繪製時，將下一個`WM_PAINT`接收訊息。 如果您想要更新只有在對應至文件已修改的部分的區域，請覆寫此函式。 若要這樣做，您必須傳遞修改使用提示參數的相關資訊。  
  
 若要使用`lHint`、 定義特殊的提示值通常位元遮罩或列舉型別，以及文件傳遞其中一個值。 若要使用`pHint`，衍生的提示類別[CObject](../../mfc/reference/cobject-class.md)和文件的覆寫時，將指標傳遞到提示的物件; `OnUpdate`，使用[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof)成員函式來判斷提示物件的執行階段型別。  
  
 通常您不應該執行任何直接從描繪`OnUpdate`。 相反地，判斷裝置座標中描述需要更新; 區域的矩形傳遞到這個矩形[CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect)。 這會導致發生在下一次繪製[WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213)接收訊息。  
  
 如果`lHint`為 0 和`pHint`是**NULL**，文件已傳送的一般更新通知。 如果檢視收到一般的更新通知，或無法解碼的提示，它應該確認其整個工作區。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDIDOCVW](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)   
 [CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument 類別](../../mfc/reference/cdocument-class.md)

