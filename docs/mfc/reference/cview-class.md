---
title: CView 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e76dc8ca4a61839b893b4328bdb9d606424def91
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062225"
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
|[CView::DoPreparePrinting](#doprepareprinting)|顯示 [列印] 對話方塊中，並建立印表機裝置內容;當覆寫時，呼叫`OnPreparePrinting`成員函式。|
|[CView::GetDocument](#getdocument)|傳回與檢視相關聯的文件。|
|[CView::IsSelected](#isselected)|測試是否已選取文件項目。 OLE 支援的必要項。|
|[CView::OnDragEnter](#ondragenter)|當項目第一次拖曳到檢視的拖放區域時呼叫。|
|[CView::OnDragLeave](#ondragleave)|拖曳的項目離開檢視的拖放區域時呼叫。|
|[CView::OnDragOver](#ondragover)|當項目拖曳至檢視的拖放區域上方時呼叫。|
|[CView::OnDragScroll](#ondragscroll)|呼叫以判斷是否要將資料指標拖曳至視窗的捲軸的區域。|
|[CView::OnDrop](#ondrop)|已經卸除檢視時，預設處理常式的拖放區域到的項目時呼叫。|
|[CView::OnDropEx](#ondropex)|已經卸除到檢視中，主要的處理常式的拖放區域的項目時呼叫。|
|[Cview:: Oninitialupdate](#oninitialupdate)|檢視第一次附加至文件之後呼叫。|
|[CView::OnPrepareDC](#onpreparedc)|之前呼叫`OnDraw`螢幕上的呼叫成員函式或`OnPrint`成員函式稱為列印或預覽列印。|
|[CView::OnScroll](#onscroll)|當 OLE 項目拖曳超出檢視的邊界時呼叫。|
|[CView::OnScrollBy](#onscrollby)|捲動檢視，其中包含作用中的就地 OLE 項目時呼叫。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CView::OnActivateFrame](#onactivateframe)|包含檢視的框架視窗啟用或停用時呼叫。|
|[CView::OnActivateView](#onactivateview)|檢視啟動時呼叫。|
|[CView::OnBeginPrinting](#onbeginprinting)|列印工作開始; 時呼叫覆寫，以配置圖形裝置介面 (GDI) 資源。|
|[Cview:: Ondraw](#ondraw)|呼叫以呈現螢幕顯示、 列印或預覽列印文件中的影像。 所需的實作。|
|[CView::OnEndPrinting](#onendprinting)|當列印工作結束; 時呼叫若要解除配置 GDI 資源覆寫。|
|[CView::OnEndPrintPreview](#onendprintpreview)|結束 [預覽] 模式時呼叫。|
|[CView::OnPreparePrinting](#onprepareprinting)|在列印或預覽; 文件之前呼叫覆寫以初始化 [列印] 對話方塊。|
|[CView::OnPrint](#onprint)|呼叫以列印或預覽文件的頁面。|
|[CView::OnUpdate](#onupdate)|呼叫以通知檢視其文件已修改。|

## <a name="remarks"></a>備註

檢視附加至文件，並做為文件與使用者之間的媒介： 檢視呈現螢幕或印表機上的文件的映像，並將使用者輸入解譯為文件作業。

檢視是框架視窗的子系。 多個檢視可以共用框架視窗中，分隔器視窗的情況。 檢視類別、 框架視窗類別，與文件類別之間的關聯性藉由`CDocTemplate`物件。 當使用者開啟新視窗，或將分割的現有架構，其中建構新的檢視，並將它附加至文件。

檢視可以附加到只有一個文件，但文件可以有多個同時連接的檢視 — 比方說，如果文件會顯示在分隔器視窗，或多個文件介面 (MDI) 應用程式中的多個子視窗中。 您的應用程式可支援不同類型的檢視，給定文件類型;例如，文書處理程式可能會提供文件的完整文字檢視和顯示區段標題的大綱檢視。 這些不同類型的檢視可以放在個別的框架視窗中，或在個別的單一框架視窗的窗格如果您使用分隔器視窗。

檢視可能會負責處理許多不同類型的輸入，例如鍵盤、 滑鼠輸入或透過拖放，以及命令的功能表、 工具列或捲軸的輸入。 檢視接收轉送的及其框架視窗的命令。 如果檢視不會處理指定的命令，它會轉送至其相關聯的文件的命令。 所有的命令目標，例如檢視會處理透過訊息對應的訊息。

檢視是負責顯示和修改文件的資料，但不是用來儲存它。 文件提供有關其資料與必要的詳細資料檢視。 您可以讓文件的資料成員直接，或者您可以提供成員函式呼叫的檢視類別的文件類別中的檢視存取權。

當文件的資料變更時，檢視負責所做的變更通常會呼叫[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)文件，就會通知所有其他的檢視，藉由呼叫的函式`OnUpdate`成員函式每個。 預設實作`OnUpdate`失效檢視的整個工作區。 您可以覆寫它要使其失效的只有這些區域的工作區對應至文件已修改的部分。

若要使用`CView`，從它衍生的類別並實作`OnDraw`成員函式來執行螢幕顯示。 您也可以使用`OnDraw`執行列印和預覽列印。 架構會處理列印和文件預覽的列印迴圈。

檢視會處理具有捲軸訊息[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)並[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成員函式。 您可以實作捲軸訊息處理的這些函式，或者您可以使用`CView`衍生類別[CScrollView](../../mfc/reference/cscrollview-class.md)來處理您捲動功能。

除了`CScrollView`，Microsoft Foundation 類別庫提供九個衍生自其他類別`CView`:

- [CCtrlView](../../mfc/reference/cctrlview-class.md)，允許使用的文件-檢視架構與樹狀目錄、 清單和 rich edit 控制項的檢視。

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)，對話方塊在控制項中顯示資料庫記錄的檢視。

- [CEditView](../../mfc/reference/ceditview-class.md)，提供一個簡單的多行文字編輯器的檢視。 您可以使用`CEditView`物件做為控制項在對話方塊中，以及文件的檢視。

- [CFormView](../../mfc/reference/cformview-class.md)，其中包含對話方塊控制項，且會以對話方塊範本資源為基礎的可捲動檢視。

- [CListView](../../mfc/reference/clistview-class.md)，允許使用的文件-檢視架構與清單控制項的檢視。

- [CRecordView](../../mfc/reference/crecordview-class.md)，對話方塊在控制項中顯示資料庫記錄的檢視。

- [CRichEditView](../../mfc/reference/cricheditview-class.md)，允許使用的文件-檢視架構與 rich edit 控制項的檢視。

- [CScrollView](../../mfc/reference/cscrollview-class.md)，會自動提供捲動支援的檢視。

- [CTreeView](../../mfc/reference/ctreeview-class.md)，允許使用的文件-檢視架構與樹狀目錄控制項的檢視。

`CView`類別也有一個名為的衍生的實作類別`CPreviewView`，這由架構進行預覽列印。 這個類別會提供支援特有的功能 [預覽列印] 視窗中，例如工具列、 單一或雙精度浮點數頁面預覽和縮放的，加大預覽映像。 您不需要呼叫或覆寫任何`CPreviewView`的成員函式，除非您想要實作您自己的介面，預覽列印 （例如，如果您想要支援在預覽列印模式中編輯）。 如需有關使用`CView`，請參閱 <<c2> [ 文件/檢視架構](../../mfc/document-view-architecture.md)並[列印](../../mfc/printing.md)。 此外，請參閱 <<c0> [ 技術的附註 30](../../mfc/tn030-customizing-printing-and-print-preview.md)如需有關自訂列印預覽。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cview"></a>  CView::CView

建構 `CView` 物件。

```
CView();
```

### <a name="remarks"></a>備註

建立新的框架視窗或分隔視窗時，架構會呼叫建構函式。 覆寫[OnInitialUpdate](#oninitialupdate)成員函式來初始化之後附加文件的檢視。

##  <a name="doprepareprinting"></a>  CView::DoPreparePrinting

呼叫此函式的覆寫從[OnPreparePrinting](#onprepareprinting)來叫用 [列印] 對話方塊中，並建立印表機裝置內容。

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pInfo*<br/>
指向描述目前列印工作的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 結構。

### <a name="return-value"></a>傳回值

列印或預覽列印就可以開始; 如果為非零0，表示作業已取消。

### <a name="remarks"></a>備註

此函式的行為取決於是否呼叫它的列印或預覽列印 (所指定`m_bPreview`隸屬*pInfo*參數)。 如果列印檔案時，此函式會叫用列印對話方塊中，使用中的值[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構*pInfo*指向; 使用者已關閉對話方塊之後，會建立函式印表機裝置內容 對話方塊中指定的使用者為基礎的設定，並傳回這個裝置內容，透過*pInfo*參數。 這個裝置內容用來列印文件。

如果正開放預覽檔案，此函式，將會建立使用目前的印表機設定; 印表機裝置內容在預覽期間模擬印表機用於這個裝置內容。

##  <a name="getdocument"></a>  CView::GetDocument

呼叫此函式可取得檢視的文件的指標。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>傳回值

指標[CDocument](../../mfc/reference/cdocument-class.md)與檢視相關聯的物件。 如果檢視未附加至文件，則為 NULL。

### <a name="remarks"></a>備註

這可讓您呼叫文件的成員函式。

##  <a name="isselected"></a>  CView::IsSelected

由架構呼叫以檢查是否已選取指定的文件項目。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>參數

*pDocItem*<br/>
正在測試的文件項目點。

### <a name="return-value"></a>傳回值

選取指定的文件項目; 如果為非零否則為 0。

### <a name="remarks"></a>備註

此函式的預設實作會傳回 FALSE。 如果您要實作選取項目使用覆寫此函數[CDocItem](../../mfc/reference/cdocitem-class.md)物件。 如果您的檢視包含 OLE 項目，您必須覆寫這個函式。

##  <a name="onactivateframe"></a>  CView::OnActivateFrame

包含檢視的框架視窗啟用或停用時由架構呼叫。

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>參數

*nState*<br/>
指定是否要在框架視窗啟用或停用。 它可以是下列值之一：

- 正在停用 WA_INACTIVE 框架視窗。

- 框架視窗正在啟用透過滑鼠以外的某種方法 WA_ACTIVE 按一下 （例如，藉由使用的鍵盤介面，以選取的視窗）。

- 正在啟用按一下滑鼠 WA_CLICKACTIVE 框架視窗

*pFrameWnd*<br/>
要啟動的框架視窗的指標。

### <a name="remarks"></a>備註

如果您想要執行特殊處理與檢視相關聯的框架視窗啟用或停用時，請覆寫此成員函式。 例如， [CFormView](../../mfc/reference/cformview-class.md)執行此覆寫時，它會將儲存並還原具有焦點的控制項。

##  <a name="onactivateview"></a>  CView::OnActivateView

啟用或停用檢視時，由架構呼叫。

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>參數

*bActivate*<br/>
表示正在檢視是否啟用或停用。

*pActivateView*<br/>
正在啟動的檢視物件的點。

*pDeactiveView*<br/>
正在停用的檢視物件的點。

### <a name="remarks"></a>備註

此函式的預設實作會將焦點設定到 [啟動] 檢視。 如果您想要執行特殊處理，啟用或停用檢視時，請覆寫這個函式。 例如，如果您想要提供特殊的視覺提示以區別現用檢視從非作用中的檢視，您會檢查*bActivate*參數並據此更新檢視的外觀。

*PActivateView*並*pDeactiveView*參數指向相同的檢視如果應用程式的主框架視窗已啟動且不會變更使用中的檢視 — 比方說，如果正在焦點在 MDI 子視窗之間切換時，傳送到這台，另一個應用程式，而不是一個檢視，以另一個應用程式內或。 如有需要這可讓重新了解其選擇區中，檢視。

這些參數與不同時[CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview)什麼不同的檢視稱為[CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview)會傳回。 發生這種情況最常使用的分隔視窗。

##  <a name="onbeginprinting"></a>  CView::OnBeginPrinting

在呼叫 `OnPreparePrinting` 之後，由架構在列印或預覽列印工作開始時呼叫。

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向印表機裝置內容。

*pInfo*<br/>
指向描述目前列印工作的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 結構。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 覆寫此函式以配置列印特別需要的任何 GDI 資源，例如畫筆或字型。 為使用 GDI 物件的每個頁面，將 GDI 物件選取至 [OnPrint](#onprint) 成員函式的裝置內容中。 如果您使用相同的檢視物件來執行螢幕顯示和列印，請為每個顯示所需的 GDI 資源使用不同的變數；這可讓您在列印期間更新螢幕。

您也可以使用此函式，執行因印表機裝置內容屬性而異的初始設定。 例如，列印文件所需的頁數可能會因使用者在 [列印] 對話方塊中指定的設定 (例如頁面長度) 而異。 在這種情況下，您無法在通常使用的 [OnPreparePrinting](#onprepareprinting) 成員函式中指定文件長度，而必須等到印表機裝置內容已根據對話方塊設定建立完成。 [OnBeginPrinting](#onbeginprinting) 是第一個可讓您存取代表印表機裝置內容之 [CDC](../../mfc/reference/cdc-class.md) 物件的可覆寫函式，因此您可以從此函式設定文件長度。 請注意，如果此時未指定文件長度，預覽列印期間將不會顯示捲軸。

##  <a name="ondragenter"></a>  CView::OnDragEnter

當滑鼠初次進入置放目標視窗的非捲動區域，由架構呼叫。

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
指向[COleDataObject](../../mfc/reference/coledataobject-class.md)被拖曳到檢視的卸除區域。

*dwKeyState*<br/>
包含的輔助按鍵的狀態。 這是任意數目的下列組合： MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*點*<br/>
目前滑鼠位置相對於用戶端區域的檢視。

### <a name="return-value"></a>傳回值

DROPEFFECT 值的列舉型別，這表示如果使用者在這個位置卸除該物件就會發生的卸除的型別。 卸除類型通常取決於目前所指示的索引鍵狀態*dwKeyState*。 Keystates DROPEFFECT 值的標準對應是：

- 無法卸除 DROPEFFECT_NONE 資料物件，此視窗中。

- 針對 MK_CONTROL DROPEFFECT_LINK &#124; MK_SHIFT 建立物件和它的伺服器之間的連結。

- 如 MK_CONTROL DROPEFFECT_COPY 會建立一份已卸除的物件。

- 如 MK_ALT DROPEFFECT_MOVE 會建立一份已卸除的物件和刪除原始的物件。 這通常是預設的拖放效果，檢視可接受這個資料物件。

如需詳細資訊，請參閱 MFC 進階概念範例[OCLIENT](../../visual-cpp-samples.md)。

### <a name="remarks"></a>備註

預設實作是不執行任何動作，並傳回 DROPEFFECT_NONE。

覆寫這個函式來準備進行後續的呼叫來[OnDragOver](#ondragover)成員函式。 從其中擷取從資料物件所需的任何資料，在此階段供稍後用於`OnDragOver`成員函式。 檢視也應該更新目前使用者的視覺化回饋提供。 如需詳細資訊，請參閱文章[拖放： 實作置放目標](../../mfc/drag-and-drop-implementing-a-drop-target.md)。

##  <a name="ondragleave"></a>  CView::OnDragLeave

由架構中，呼叫時有效的置放區超出該視窗移動滑鼠拖曳作業期間中。

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>備註

如果目前的檢視必須清除期間採取任何動作，請覆寫這個函式[OnDragEnter](#ondragenter)或是[OnDragOver](#ondragover)呼叫，例如拖曳和卸除物件時，移除任何視覺化使用者意見反應.

##  <a name="ondragover"></a>  CView::OnDragOver

當滑鼠移動經過置放目標視窗呼叫由架構在拖曳作業期間。

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
指向[COleDataObject](../../mfc/reference/coledataobject-class.md)被拖曳到置放目標。

*dwKeyState*<br/>
包含的輔助按鍵的狀態。 這是任意數目的下列組合： MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*點*<br/>
目前的滑鼠位置相對於檢視用戶端區域。

### <a name="return-value"></a>傳回值

DROPEFFECT 值的列舉型別，這表示如果使用者在這個位置卸除該物件就會發生的卸除的型別。 卸除類型通常取決於目前的索引鍵狀態所示*dwKeyState*。 Keystates DROPEFFECT 值的標準對應是：

- 無法卸除 DROPEFFECT_NONE 資料物件，此視窗中。

- 針對 MK_CONTROL DROPEFFECT_LINK &#124; MK_SHIFT 建立物件和它的伺服器之間的連結。

- 如 MK_CONTROL DROPEFFECT_COPY 會建立一份已卸除的物件。

- 如 MK_ALT DROPEFFECT_MOVE 會建立一份已卸除的物件和刪除原始的物件。 這通常是預設的拖放效果，檢視可接受的資料物件。

如需詳細資訊，請參閱 MFC 進階概念範例[OCLIENT](../../visual-cpp-samples.md)。

### <a name="remarks"></a>備註

預設實作是不執行任何動作，並傳回 DROPEFFECT_NONE。

此函式以使用者的視覺化回饋提供拖曳作業期間會覆寫。 因為連續呼叫此函式，其內所含的任何程式碼應該最佳化盡量。 如需詳細資訊，請參閱文章[拖放： 實作置放目標](../../mfc/drag-and-drop-implementing-a-drop-target.md)。

##  <a name="ondragscroll"></a>  CView::OnDragScroll

由架構呼叫之前，先呼叫[OnDragEnter](#ondragenter)或是[OnDragOver](#ondragover)來判斷點是否在捲軸的區域中。

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*dwKeyState*<br/>
包含的輔助按鍵的狀態。 這是任意數目的下列組合： MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。

*點*<br/>
包含的資料指標，像素為單位，相對於畫面的位置。

### <a name="return-value"></a>傳回值

DROPEFFECT 值的列舉型別，這表示如果使用者在這個位置卸除該物件就會發生的卸除的型別。 卸除類型通常取決於目前所指示的索引鍵狀態*dwKeyState*。 Keystates DROPEFFECT 值的標準對應是：

- 無法卸除 DROPEFFECT_NONE 資料物件，此視窗中。

- 針對 MK_CONTROL DROPEFFECT_LINK &#124; MK_SHIFT 建立物件和它的伺服器之間的連結。

- 如 MK_CONTROL DROPEFFECT_COPY 會建立一份已卸除的物件。

- 如 MK_ALT DROPEFFECT_MOVE 會建立一份已卸除的物件和刪除原始的物件。

- DROPEFFECT_SCROLL 表示拖曳捲軸作業會發生，或作業在目標檢視。

如需詳細資訊，請參閱 MFC 進階概念範例[OCLIENT](../../visual-cpp-samples.md)。

### <a name="remarks"></a>備註

當您想要提供特殊的行為，這個事件時，請覆寫這個函式。 預設實作會自動捲動 windows 游標拖曳到 預設的捲動區域內的每個視窗的框線時。如需詳細資訊，請參閱文章[拖放： 實作置放目標](../../mfc/drag-and-drop-implementing-a-drop-target.md)。

##  <a name="ondraw"></a>  Cview:: Ondraw

由架構呼叫以呈現文件的影像。

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向裝置內容，以用來呈現文件的映像。

### <a name="remarks"></a>備註

架構會呼叫此函式來執行螢幕顯示、 列印和預覽列印，並且會傳遞不同的裝置內容中每個案例。 沒有預設的實作。

您必須覆寫這個函式，以顯示您的文件的檢視。 您可以使用的圖形裝置介面 (GDI) 呼叫[CDC](../../mfc/reference/cdc-class.md)指向的物件*pDC*參數。 您可以選取 GDI 資源，例如畫筆或字型繪製前的裝置內容，然後之後取消選取它們。 您的繪圖程式碼通常可以與裝置無關;也就是說，它不需要哪種裝置類型會顯示映像的相關資訊。

若要最佳化的繪圖，呼叫[RectVisible](../../mfc/reference/cdc-class.md#rectvisible)成員函式的裝置內容，以查明是否會繪製指定的矩形。 如果您需要區別正常螢幕顯示和列印，呼叫[IsPrinting](../../mfc/reference/cdc-class.md#isprinting)裝置內容的成員函式。

##  <a name="ondrop"></a>  CView::OnDrop

在使用者釋放資料物件的有效置放目標時，由架構呼叫。

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>參數

' pDataObject * 指向[COleDataObject](../../mfc/reference/coledataobject-class.md) ，控制項置放到置放目標。

*dropEffect*<br/>
使用者已要求下拉式效果。

- DROPEFFECT_COPY 會建立一份要卸除的資料物件。

- DROPEFFECT_MOVE 資料將物件移至目前的滑鼠位置。

- DROPEFFECT_LINK 建立資料物件與其伺服器之間的連結。

*點*<br/>
目前的滑鼠位置相對於檢視用戶端區域。

### <a name="return-value"></a>傳回值

非零值，如果卸除成功;否則為 0。

### <a name="remarks"></a>備註

預設實作不做任何動作，且會傳回 FALSE。

覆寫這個函式來實作的 OLE 拖放效果到檢視的工作區。 資料物件可以透過檢查*pDataObject*剪貼簿資料格式和資料在卸除指定的點。

> [!NOTE]
>  架構不會呼叫此函式，如果沒有要覆寫[OnDropEx](#ondropex)這個檢視類別中。

##  <a name="ondropex"></a>  CView::OnDropEx

在使用者釋放資料物件的有效置放目標時，由架構呼叫。

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
指向[COleDataObject](../../mfc/reference/coledataobject-class.md) ，控制項置放到置放目標。

*dropDefault*<br/>
使用者選擇針對根據目前的索引鍵狀態預設拖放作業效果。 它可能是 DROPEFFECT_NONE。 置放效果是 < 備註 > 一節所述。

*下拉清單*<br/>
拖曳來源所支援的拖放效果的清單。 可以使用的位元 OR 組合置放效果值 ( **&#124;**) 作業。 置放效果是 < 備註 > 一節所述。

*點*<br/>
目前的滑鼠位置相對於檢視用戶端區域。

### <a name="return-value"></a>傳回值

卸除嘗試在所指定的位置產生的置放效果*點*。 這必須是其中一個值所指示*dropEffectList*。 置放效果是 < 備註 > 一節所述。

### <a name="remarks"></a>備註

預設實作是不執行任何動作，並傳回空值 (-1)，表示應該呼叫 framework [OnDrop](#ondrop)處理常式。

覆寫這個函式，以實作正確的滑鼠按鈕拖曳和卸除的效果。 滑鼠右鍵拖曳和置放通常顯示選項的功能表，當使用者放開滑鼠右按鈕。

覆寫`OnDropEx`應該查詢適當的滑鼠按鈕。 您可以呼叫[GetKeyState](https://msdn.microsoft.com/library/windows/desktop/ms646301)或從右滑鼠按鈕狀態儲存您[OnDragEnter](#ondragenter)處理常式。

- 如果滑鼠右按鈕已關閉，您的覆寫應該會顯示快顯功能表來提供拖曳來源所支援的置放效果。

   - 檢查*下拉清單*以判斷拖曳來源所支援的置放效果。 啟用快顯功能表中的這些動作。

   - 使用[SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem)設定為基礎的預設動作*dropDefault*。

   - 最後，採取動作以從快顯功能表的使用者選取項目。

- 如果未按下滑鼠右按鈕，覆寫應該處理此做為標準的卸除要求。 使用指定的拖放效果*dropDefault*。 或者，您的覆寫可以傳回空值 (-1) 表示`OnDrop`會處理這項拖放作業。

使用*pDataObject*檢查`COleDataObject`剪貼簿資料格式和資料在卸除指定的點。

置放效果描述與拖放作業相關聯的動作。 請參閱下列清單中的拖放效果：

- DROPEFFECT_NONE 不會允許卸除。

- DROPEFFECT_COPY 執行複製作業。

- DROPEFFECT_MOVE 會執行移動作業。

- 會建立已卸除的資料從原始資料的 DROPEFFECT_LINK 的連結。

- DROPEFFECT_SCROLL 表示拖曳捲軸作業會發生，或在目標中進行。

如需有關如何設定預設的功能表命令的詳細資訊，請參閱 < [SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem) Windows SDK 中並[CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu)此磁碟區中。

##  <a name="onendprinting"></a>  CView::OnEndPrinting

列印或預覽文件之後，由架構呼叫。

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向印表機裝置內容。

*pInfo*<br/>
指向描述目前列印工作的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 結構。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 覆寫這個函式來釋放配置在任何 GDI 資源[OnBeginPrinting](#onbeginprinting)成員函式。

##  <a name="onendprintpreview"></a>  CView::OnEndPrintPreview

當使用者結束預覽列印模式時，由架構呼叫。

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向印表機裝置內容。

*pInfo*<br/>
指向描述目前列印工作的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 結構。

*點*<br/>
上次在預覽模式中顯示的頁面上指定的點。

*pView*<br/>
指向用來預覽的檢視物件。

### <a name="remarks"></a>備註

此函式的預設實作會呼叫[OnEndPrinting](#onendprinting)成員函式並還原到之前預覽列印狀態的主框架視窗開始。 覆寫這個函式來執行特殊處理序終止 [預覽] 模式時。 例如，如果您想要維護文件中的使用者的位置，從 [預覽] 模式切換到一般顯示模式時，您可以捲動到所描述的位置*點*參數和`m_nCurPage`的成員`CPrintInfo`結構*pInfo*參數所指向。

請務必呼叫基底類別版本`OnEndPrintPreview`從您的覆寫通常是在函式結尾。

##  <a name="oninitialupdate"></a>  Cview:: Oninitialupdate

檢視第一次附加至文件之後，但一開始顯示檢視之前，由架構呼叫。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>備註

此函式的預設實作會呼叫[OnUpdate](#onupdate)成員函式，而不提示的資訊 (也就使用預設值為 0，表示*lHint*參數，則為 NULL *pHint*參數)。 覆寫這個函式來執行任何需要的文件的相關資訊的單次初始化。 比方說，如果您的應用程式有固定大小的文件，您可以使用此函式來初始化檢視的捲動文件大小為基礎的限制。 如果您的應用程式支援可變大小的文件，請使用[OnUpdate](#onupdate)更新捲動會限制每次文件變更。

##  <a name="onpreparedc"></a>  CView::OnPrepareDC

由架構之前呼叫[OnDraw](#ondraw)進行螢幕顯示和之前，呼叫成員函式[OnPrint](#onprint)成員函式列印或預覽列印期間，會呼叫每個頁面。

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向裝置內容，以用來呈現文件的映像。

*pInfo*<br/>
指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構，描述目前列印工作，如果`OnPrepareDC`呼叫的列印或預覽列印;`m_nCurPage`成員指定即將列印的頁面。 這個參數是 NULL，如果`OnPrepareDC`呼叫進行螢幕顯示。

### <a name="remarks"></a>備註

如果函式針對螢幕上顯示呼叫此函式的預設實作沒有任何作用。 不過，此函式會覆寫在衍生類別中，這類[CScrollView](../../mfc/reference/cscrollview-class.md)調整裝置內容; 的屬性中，因此，務必呼叫基底類別實作覆寫的開頭。

如果列印呼叫函式，則預設實作會檢查中儲存的頁面資訊*pInfo*參數。 如果未指定文件長度，`OnPrepareDC`假設要很長的一頁的文件，並列印一頁之後，停止列印迴圈。 此函式來設定停止列印迴圈`m_bContinuePrinting`為 FALSE 結構的成員。

覆寫`OnPrepareDC`任何原因如下：

- 若要視需要針對指定的頁面，請調整裝置內容的屬性。 例如，如果您需要設定對應模式] 或 [裝置內容的其他特性，這麼做在此函式。

- 若要執行列印時分頁。 通常您指定長度的文件列印開始時，使用[OnPreparePrinting](#onprepareprinting)成員函式。 不過，如果您不知道事先多久文件 （例如，當列印不確定的數目的記錄從資料庫），覆寫`OnPrepareDC`時它正在列印的文件結尾的測試。 當有沒有其他要列印的文件，來設定`m_bContinuePrinting`隸屬`CPrintInfo`結構為 FALSE。

- 若要將逸出程式碼傳送到印表機的頁面為基礎。 要傳送的逸出代碼`OnPrepareDC`，呼叫`Escape`成員函式*pDC*參數。

呼叫的基底類別版本`OnPrepareDC`覆寫的開頭。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>  CView::OnPreparePrinting

列印或預覽文件之前，由架構呼叫。

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pInfo*<br/>
指向描述目前列印工作的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 結構。

### <a name="return-value"></a>傳回值

若要開始列印; Nonzero0，表示列印工作已取消。

### <a name="remarks"></a>備註

預設實作不做任何動作。

您必須覆寫這個函式，可讓列印和預覽列印。 呼叫[DoPreparePrinting](#doprepareprinting)成員函式，將它傳遞*pInfo*參數，然後傳回它的傳回值;`DoPreparePrinting`會顯示 [列印] 對話方塊中，並建立印表機裝置內容。 如果您想要初始化 [列印] 對話方塊中，使用預設值以外的值，則將值指派給成員*pInfo*。 例如，如果您知道文件長度，將值傳遞至[SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage)成員函式*pInfo*再呼叫`DoPreparePrinting`。 這個值會顯示在 [收件者:] 方塊中的 [列印] 對話方塊中的範圍部分。

`DoPreparePrinting` 不會顯示預覽工作 [列印] 對話方塊。 如果您想要略過的列印工作的 [列印] 對話方塊，請確認`m_bPreview`隸屬*pInfo*為 FALSE，然後將它設定為 TRUE，再傳遞給`DoPreparePrinting`; 之後重設為 FALSE。

如果您需要執行初始化，需要存取`CDC`物件，代表印表機裝置內容 （例如，如果您需要之前要知道的頁面大小指定文件的長度），覆寫`OnBeginPrinting`成員函式。

如果您想要設定的值`m_nNumPreviewPages`或是`m_strPageDesc`的成員*pInfo*參數，這樣做之後呼叫`DoPreparePrinting`。 `DoPreparePrinting`成員函式會將`m_nNumPreviewPages`應用程式中找到的值。INI 檔案，並設定`m_strPageDesc`為其預設值。

### <a name="example"></a>範例

  覆寫`OnPreparePrinting`並呼叫`DoPreparePrinting`從覆寫，讓架構會顯示 [列印] 對話方塊，並為您建立是印表機 DC。

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

如果您知道文件中包含的頁數，請在中設定最大頁面`OnPreparePrinting`再呼叫`DoPreparePrinting`。 架構會顯示在 [列印] 對話方塊中的 [到] 方塊中的最大頁面數目。

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>  CView::OnPrint

由架構呼叫以列印或預覽文件的頁面。

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向印表機裝置內容。

*pInfo*<br/>
指向`CPrintInfo`結構，描述目前列印工作。

### <a name="remarks"></a>備註

針對每個列印頁面，架構會呼叫此函式後立即呼叫[OnPrepareDC](#onpreparedc)成員函式。 正在列印的頁面由`m_nCurPage`隸屬[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構*pInfo*指向。 預設實作會呼叫[OnDraw](#ondraw)成員函式，並將它傳遞印表機裝置內容。

覆寫此函數，任何原因如下：

- 若要允許列印多頁文件。 呈現只對應於目前列印的頁面的文件的一部分。 如果您使用`OnDraw`用以執行呈現，您可以調整檢視區原點，因此會列印文件的適當部分。

- 若要列印的影像 （也就是如果您的應用程式不是 WYSIWYG） 不同畫面影像。 而不是傳遞印表機裝置內容`OnDraw`，使用裝置內容來呈現使用屬性不會顯示在螢幕上的影像。

   如果您需要不用於螢幕顯示的列印的 GDI 資源，將其選取至裝置內容的繪圖之前和之後將它們取消選取。 中應該配置這些 GDI 資源[OnBeginPrinting](#onbeginprinting)並在發行[OnEndPrinting](#onendprinting)。

- 若要實作的頁首或頁尾。 您仍然可以使用`OnDraw`藉由限制它就可以列印的區域中進行轉譯。

請注意，`m_rectDraw`隸屬*pInfo*參數描述中的邏輯單元的頁面可列印區域。

請勿呼叫`OnPrepareDC`中的覆寫`OnPrint`; 架構會呼叫`OnPrepareDC`自動再呼叫`OnPrint`。

### <a name="example"></a>範例

以下是覆寫基本架構`OnPrint`函式：

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

如需其他範例，請參閱[CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect)。

##  <a name="onscroll"></a>  CView::OnScroll

由架構呼叫以判斷是否捲動是可行的。

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*nScrollCode*<br/>
捲軸的程式碼，指出使用者的捲動要求。 這個參數由兩個部分組成： 低序位位元組，這會決定捲動發生水平的型別，以及高序位位元組，這會決定捲動發生垂直的類型：

- SB_BOTTOM 捲動至底部。

- SB_LINEDOWN 捲動下一行。

- SB_LINEUP 捲動上一行。

- 向下 SB_PAGEDOWN 捲動一頁。

- 向上 SB_PAGEUP 捲動一頁。

- SB_THUMBTRACK 拖曳捲動方塊以指定的位置。 在指定目前位置*nPos*。

- SB_TOP 捲動至頂端。

*nPos*<br/>
如果捲軸的程式碼 SB_THUMBTRACK;，包含目前的捲動方塊位置否則它不會使用。 初始的捲軸範圍，根據*nPos*可以是負數，並且應該轉換成**int**如有必要。

*bDoScroll*<br/>
決定是否實際上就應該指定捲動的動作。 如果為 TRUE，然後捲動應該進行;如果為 FALSE，然後捲動應該不會發生。

### <a name="return-value"></a>傳回值

如果*bDoScroll*為 TRUE，而且實際上捲動檢視，然後傳回非零值; 否則為 0。 如果*bDoScroll*為 FALSE，則傳回值，如果會傳回您*bDoScroll*是 TRUE，即使您沒有實際進行捲動。

### <a name="remarks"></a>備註

使用架構在其中一個案例呼叫此函式*bDoScroll*設為 TRUE，當檢視收到的捲軸的訊息。 在此情況下，您應該實際捲動檢視。 在其他情況下呼叫此函式與*bDoScroll*捲動實際發生之前一開始 OLE 項目拖曳到置放目標的自動捲動區域時，設定為 FALSE。 在此情況下，您不應該實際捲動檢視。

##  <a name="onscrollby"></a>  CView::OnScrollBy

當使用者檢視之外存在檢視文件，將 OLE 項目，針對檢視的目前框線拖曳，或藉由操作的垂直或水平捲軸的區域時由架構呼叫。

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*sizeScroll*<br/>
水平和垂直，捲動到像素數目。

*bDoScroll*<br/>
決定是否捲動檢視的發生。 如果為 TRUE，然後捲動會發生;如果為 FALSE，不會再捲動。

### <a name="return-value"></a>傳回值

如果能夠捲動; 檢視，非零值。否則為 0。

### <a name="remarks"></a>備註

在衍生類別中這個方法會檢查檢視是否可捲動的方向，使用者要求，並如有必要，然後更新新的區域。 此函式會自動呼叫[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)並[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)執行實際的捲動要求。

這個方法的預設實作不會變更檢視，但如果不呼叫它時，檢視將無法捲動中`CScrollView`-衍生的類別。

如果文件寬度或高度超過 32767 的像素為單位，超過 32767 捲動會失敗，因為`OnScrollBy`呼叫無效*sizeScroll*引數。

##  <a name="onupdate"></a>  CView::OnUpdate

修改檢視的文件; 之後，由架構呼叫此函式會呼叫[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) ，並可讓更新以反映這些修改其顯示的檢視。

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>參數

*pSender*<br/>
指向修改文件中，檢視或更新所有的檢視是否為 NULL。

*lHint*<br/>
包含資訊所做的修改。

*pHint*<br/>
指向儲存修改的相關資訊的物件。

### <a name="remarks"></a>備註

它也會呼叫的預設實作[OnInitialUpdate](#oninitialupdate)。 預設實作會使整個工作區中，將其標示為繪製，收到下一步 WM_PAINT 訊息時的失效。 如果您想要更新只有在對應至文件的部分修改過的區域，請覆寫這個函式。 若要這樣做，您必須傳遞所做的修改使用提示參數的相關資訊。

若要使用*lHint*、 定義特殊的提示值、 通常位元遮罩或列舉的類型，並傳遞其中一個值的文件。 若要使用*pHint*，衍生的提示類別[CObject](../../mfc/reference/cobject-class.md)文件的覆寫時，將指標傳遞到提示的物件; 還有`OnUpdate`，使用[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof)若要判斷提示物件的執行階段類型的成員函式。

通常您不應該執行任何繪製直接從`OnUpdate`。 相反地，判斷裝置的座標，描述需要更新; 區域的矩形傳遞到這個矩形[CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect)。 這會導致發生在下一次繪製[WM_PAINT](/windows/desktop/gdi/wm-paint)接收訊息。

如果*lHint*為 0 並*pHint*是 NULL，文件已傳送的一般更新通知。 如果檢視收到的一般更新通知，或如果無法解碼的提示，其應該使其整個工作區失效。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDIDOCVW](../../visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)
