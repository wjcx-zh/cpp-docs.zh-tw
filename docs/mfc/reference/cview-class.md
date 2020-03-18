---
title: CView 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: f6be846e80209ce94c84222d61c37a7964baad03
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421566"
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
|[CView：： CView](#cview)|建構 `CView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CView：:D oPreparePrinting](#doprepareprinting)|顯示 [列印] 對話方塊並建立印表機裝置內容;覆寫 `OnPreparePrinting` 成員函式時呼叫。|
|[CView：： GetDocument](#getdocument)|傳回與此視圖相關聯的檔。|
|[CView：： IsSelected](#isselected)|測試是否已選取檔專案。 OLE 支援所需。|
|[CView：： System.windows.uielement.ondragenter](#ondragenter)|當專案第一次拖曳至視圖的拖放區域時呼叫。|
|[CView：： System.windows.uielement.ondragleave](#ondragleave)|當拖曳的專案離開視圖的拖放區域時呼叫。|
|[CView：： System.windows.uielement.ondragover](#ondragover)|當專案拖曳至視圖的拖放區域時呼叫。|
|[CView：： OnDragScroll](#ondragscroll)|呼叫以決定是否將游標拖曳至視窗的捲軸區域。|
|[CView：： System.windows.uielement.ondrop](#ondrop)|當專案已放入視圖的拖放區域中時呼叫（預設處理常式）。|
|[CView：： OnDropEx](#ondropex)|當專案已放入視圖的拖放區域、主要處理常式時呼叫。|
|[CView：： OnInitialUpdate](#oninitialupdate)|在第一次將視圖附加至檔後呼叫。|
|[CView：： OnPrepareDC](#onpreparedc)|在呼叫 `OnDraw` 成員函式以進行螢幕顯示之前呼叫，或呼叫 `OnPrint` 成員函式以進行列印或預覽列印。|
|[CView：： OnScroll](#onscroll)|當 OLE 專案拖曳至超過視圖的框線時呼叫。|
|[CView：： OnScrollBy](#onscrollby)|當包含作用中就地 OLE 專案的視圖滾動時呼叫。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[CView：： OnActivateFrame](#onactivateframe)|當包含此視圖的框架視窗已啟用或停用時呼叫。|
|[CView：： OnActivateView](#onactivateview)|在啟動視圖時呼叫。|
|[CView：： OnBeginPrinting](#onbeginprinting)|當列印工作開始時呼叫;覆寫以配置圖形裝置介面（GDI）資源。|
|[CView：： OnDraw](#ondraw)|呼叫以呈現螢幕顯示、列印或預覽列印檔的影像。 需要執行。|
|[CView：： OnEndPrinting](#onendprinting)|當列印工作結束時呼叫;覆寫以解除配置 GDI 資源。|
|[CView：： OnEndPrintPreview](#onendprintpreview)|當預覽模式結束時呼叫。|
|[CView：： OnPreparePrinting](#onprepareprinting)|在列印或預覽檔之前呼叫;覆寫以初始化 [列印] 對話方塊。|
|[CView：： OnPrint](#onprint)|呼叫以列印或預覽檔的頁面。|
|[CView：： OnUpdate](#onupdate)|呼叫以通知視圖其檔已修改。|

## <a name="remarks"></a>備註

視圖會附加至檔，並做為檔與使用者之間的媒介：此視圖會在螢幕或印表機上轉譯檔的影像，並將使用者輸入轉譯為檔上的作業。

View 是框架視窗的子系。 一個以上的視圖可以共用框架視窗，就像在分隔視窗中的情況一樣。 View 類別、框架視窗類別和檔類別之間的關聯性是由 `CDocTemplate` 物件所建立。 當使用者開啟新視窗或分割現有視窗時，架構會建立新的視圖，並將其附加至檔。

一個視圖只能附加至一個檔，但一個檔可以同時附加多個視圖，例如，如果檔顯示在分隔視窗中，或在多重文件介面（MDI）應用程式的多個子視窗中。 您的應用程式可以針對指定的檔案類型支援不同類型的視圖;例如，文字處理程式可能會同時提供檔的完整文字視圖，以及只顯示區段標題的大綱視圖。 如果您使用分隔視窗，這些不同類型的視圖可以放在不同的框架視窗中，或放置在單一框架視窗的個別窗格中。

視圖可能負責處理數種不同類型的輸入，例如鍵盤輸入、滑鼠輸入或透過拖放的輸入，以及來自功能表、工具列或捲軸的命令。 View 會接收其框架視窗所轉送的命令。 如果此視圖未處理指定的命令，它會將命令轉送至其相關聯的檔。 如同所有的命令目標，視圖會透過訊息對應來處理訊息。

此視圖會負責顯示和修改檔的資料，但不會儲存它。 檔會提供其資料所需的詳細資訊給視圖。 您可以讓此視圖直接存取檔的資料成員，或者您可以在檔類別中提供成員函式，以供 view 類別呼叫。

當檔的資料變更時，負責變更的視圖通常會呼叫檔的[CDocument：： UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)函式，藉由呼叫每個的 `OnUpdate` 成員函式來通知所有其他視圖。 預設的 `OnUpdate` 執行會使視圖的整個工作區失效。 您可以覆寫它，使工作區中對應至已修改檔部分的區域失效。

若要使用 `CView`，請從它衍生類別，並執行 `OnDraw` 成員函式以執行螢幕顯示。 您也可以使用 `OnDraw` 來執行列印和預覽列印。 架構會處理列印迴圈，以列印和預覽您的檔。

View 會使用[cwnd：： OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[Cwnd：： OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成員函式來處理捲軸訊息。 您可以在這些函式中執行捲軸訊息處理，也可以使用 `CView` 衍生的類別[CScrollView](../../mfc/reference/cscrollview-class.md)來處理您的滾動。

除了 `CScrollView`以外，MFC 程式庫還提供了其他九個衍生自 `CView`的類別：

- [CCtrlView](../../mfc/reference/cctrlview-class.md)，這是允許使用具有樹狀結構、清單和豐富編輯控制項之檔視圖架構的視圖。

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)，這是在對話方塊控制項中顯示資料庫記錄的視圖。

- [CEditView](../../mfc/reference/ceditview-class.md)，提供簡單多行文字編輯器的視圖。 您可以使用 `CEditView` 物件做為對話方塊中的控制項，以及檔的視圖。

- [CFormView](../../mfc/reference/cformview-class.md)，這是一個可滾動的視圖，其中包含對話方塊控制項，而且是以對話方塊範本資源為基礎。

- [CListView](../../mfc/reference/clistview-class.md)，這是允許使用檔視圖架構與清單控制項的視圖。

- [CRecordView](../../mfc/reference/crecordview-class.md)，這是在對話方塊控制項中顯示資料庫記錄的視圖。

- [CRichEditView](../../mfc/reference/cricheditview-class.md)，這是允許使用具有豐富編輯控制項之檔視圖架構的視圖。

- [CScrollView](../../mfc/reference/cscrollview-class.md)，這是自動提供滾動支援的視圖。

- [CTreeView](../../mfc/reference/ctreeview-class.md)，這是允許使用具有樹狀目錄控制項之檔查看架構的視圖。

`CView` 類別也有一個名為 `CPreviewView`的衍生實類別，架構會使用此類別來執行預覽列印。 這個類別可支援預覽列印視窗特有的功能，例如工具列、單一或雙頁預覽，以及縮放，也就是放大預覽的影像。 您不需要呼叫或覆寫任何 `CPreviewView`的成員函式，除非您想要執行自己的預覽列印介面（例如，如果您想要支援在預覽列印模式中編輯）。 如需使用 `CView`的詳細資訊，請參閱[檔/視圖架構](../../mfc/document-view-architecture.md)和[列印](../../mfc/printing.md)。 此外，如需自訂預覽列印的詳細資訊，請參閱[技術提示 30](../../mfc/tn030-customizing-printing-and-print-preview.md) 。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cview"></a>CView：： CView

建構 `CView` 物件。

```
CView();
```

### <a name="remarks"></a>備註

當建立新的框架視窗或分割視窗時，架構會呼叫這個函式。 在附加檔之後，覆寫[OnInitialUpdate](#oninitialupdate)成員函式以初始化 view。

##  <a name="doprepareprinting"></a>CView：:D oPreparePrinting

從您的[OnPreparePrinting](#onprepareprinting)覆寫呼叫此函式，以叫用 [列印] 對話方塊並建立印表機裝置內容。

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pInfo*<br/>
指向描述目前列印工作的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 結構。

### <a name="return-value"></a>傳回值

如果列印或預覽列印可以開始，則為非零;如果作業已取消，則為0。

### <a name="remarks"></a>備註

此函式的行為取決於其是否針對列印或預覽列印而呼叫（由*pInfo*參數的 `m_bPreview` 成員指定）。 如果檔案正在列印，此函式會叫用 [列印] 對話方塊，並使用*pInfo*指向的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構中的值。在使用者關閉對話方塊之後，此函式會根據使用者在對話方塊中指定的設定來建立印表機裝置內容，並透過*pInfo*參數傳回此裝置內容。 此裝置內容是用來列印檔案。

如果檔案正在預覽中，此函式會使用目前的印表機設定來建立印表機裝置內容;此裝置內容用於在預覽期間模擬印表機。

##  <a name="getdocument"></a>CView：： GetDocument

呼叫此函式可取得視圖檔的指標。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>傳回值

與視圖相關聯之[CDocument](../../mfc/reference/cdocument-class.md)物件的指標。 如果未將此視圖附加至檔，則為 Null。

### <a name="remarks"></a>備註

這可讓您呼叫檔的成員函式。

##  <a name="isselected"></a>CView：： IsSelected

由架構呼叫，以檢查指定的檔專案是否已選取。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>參數

*pDocItem*<br/>
指向正在測試的檔專案。

### <a name="return-value"></a>傳回值

如果已選取指定的檔專案，則為非零。否則為0。

### <a name="remarks"></a>備註

此函式的預設實作用會傳回 FALSE。 如果您要使用[CDocItem](../../mfc/reference/cdocitem-class.md)物件來執行選取專案，請覆寫此函式。 如果您的視圖包含 OLE 專案，您必須覆寫這個函式。

##  <a name="onactivateframe"></a>CView：： OnActivateFrame

當包含此視圖的框架視窗已啟用或停用時，由架構呼叫。

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>參數

*nState*<br/>
指定是否要啟用或停用框架視窗。 它可能是下列其中一個值：

- WA_INACTIVE 框架視窗已停用。

- WA_ACTIVE 框架視窗是透過滑鼠點擊以外的某個方法來啟動（例如，藉由使用鍵盤介面來選取視窗）。

- WA_CLICKACTIVE 按滑鼠按一下來啟動框架視窗

*pFrameWnd*<br/>
要啟動之框架視窗的指標。

### <a name="remarks"></a>備註

如果您想要在與視圖相關聯的框架視窗啟動或停用時執行特殊處理，請覆寫這個成員函式。 例如，當[CFormView](../../mfc/reference/cformview-class.md)儲存並還原具有焦點的控制項時，會執行此覆寫。

##  <a name="onactivateview"></a>CView：： OnActivateView

當 view 已啟動或停用時，由架構呼叫。

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>參數

*bActivate*<br/>
指出是否正在啟動或停用此視圖。

*pActivateView*<br/>
指向正在啟用的 view 物件。

*pDeactiveView*<br/>
指向要停用的 view 物件。

### <a name="remarks"></a>備註

此函式的預設實作用會將焦點設定為正在啟動的視圖。 如果您想要在啟用或停用視圖時執行特殊處理，請覆寫此函數。 例如，如果您想要提供特別的視覺提示來區分現用視圖與非使用中的視圖，您會檢查*bActivate*參數，並據以更新視圖的外觀。

如果應用程式的主框架視窗在使用中的流覽中沒有任何變更的情況下啟動， *pActivateView*和*pDeactiveView*參數會指向相同的視圖，例如，如果焦點是從另一個應用程式轉移到這個視窗，而不是在應用程式內的某個視圖之間，或是在 MDI 子視窗之間切換時。 這可讓視圖視需要重新實現其調色板。

當以不同于[CFrameWnd：： GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview)會傳回的視圖呼叫[CFrameWnd：： SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview)時，這些參數會有所不同。 這種情況最常發生在分隔視窗中。

##  <a name="onbeginprinting"></a>CView：： OnBeginPrinting

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

##  <a name="ondragenter"></a>CView：： System.windows.uielement.ondragenter

當滑鼠第一次進入 [放置目標] 視窗的非捲動區域時，由架構呼叫。

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
指向要拖曳至視圖放置區的[COleDataObject](../../mfc/reference/coledataobject-class.md) 。

*dwKeyState*<br/>
包含輔助按鍵的狀態。 這是下列任意數目的組合： MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。

*此處*<br/>
相對於視圖工作區的目前滑鼠位置。

### <a name="return-value"></a>傳回值

DROPEFFECT 列舉型別中的值，指出當使用者在這個位置卸載物件時，會發生的卸載型別。 Drop 的類型通常取決於*dwKeyState*所指出的目前索引鍵狀態。 Keystates 與 DROPEFFECT 值的標準對應為：

- DROPEFFECT_NONE 無法在此視窗中卸載資料物件。

- MK_CONTROL &#124; MK_SHIFT 的 DROPEFFECT_LINK 會在物件與其伺服器之間建立連結。

- MK_CONTROL 的 DROPEFFECT_COPY 會建立已卸載之物件的複本。

- MK_ALT 的 DROPEFFECT_MOVE 會建立已捨棄物件的複本，並刪除原始物件。 當 view 可以接受這個資料物件時，這通常是預設的捨棄效果。

如需詳細資訊，請參閱 MFC Advanced 概念範例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>備註

預設的實作為不執行任何動作，並傳回 DROPEFFECT_NONE。

覆寫此函式，以準備未來呼叫[system.windows.uielement.ondragover](#ondragover)成員函式。 此時應該會抓取資料物件所需的任何資料，以供稍後在 `OnDragOver` 成員函式中使用。 此時應該也會更新此視圖，以提供使用者視覺效果的意見反應。 如需詳細資訊，請參閱[OLE 拖放：執行放置目標一](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)文。

##  <a name="ondragleave"></a>CView：： System.windows.uielement.ondragleave

在拖曳作業期間，當滑鼠移出該視窗的有效下拉區域時，由架構呼叫。

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>備註

如果目前的視圖需要清除在[system.windows.uielement.ondragenter](#ondragenter)或[system.windows.uielement.ondragover](#ondragover)呼叫期間所採取的任何動作（例如，在拖放物件時移除任何視覺使用者意見反應），請覆寫此函式。

##  <a name="ondragover"></a>CView：： System.windows.uielement.ondragover

當滑鼠移到放置目標視窗上時，由架構在拖曳作業期間呼叫。

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
指向拖放目標上的[COleDataObject](../../mfc/reference/coledataobject-class.md) 。

*dwKeyState*<br/>
包含輔助按鍵的狀態。 這是下列任意數目的組合： MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。

*此處*<br/>
相對於 view 工作區的目前滑鼠位置。

### <a name="return-value"></a>傳回值

DROPEFFECT 列舉型別中的值，指出當使用者在這個位置卸載物件時，會發生的卸載型別。 卸載的類型通常取決於目前的索引鍵狀態，如*dwKeyState*所示。 Keystates 與 DROPEFFECT 值的標準對應為：

- DROPEFFECT_NONE 無法在此視窗中卸載資料物件。

- MK_CONTROL &#124; MK_SHIFT 的 DROPEFFECT_LINK 會在物件與其伺服器之間建立連結。

- MK_CONTROL 的 DROPEFFECT_COPY 會建立已卸載之物件的複本。

- MK_ALT 的 DROPEFFECT_MOVE 會建立已捨棄物件的複本，並刪除原始物件。 當 view 可以接受資料物件時，這通常是預設的捨棄效果。

如需詳細資訊，請參閱 MFC Advanced 概念範例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>備註

預設的實作為不執行任何動作，且會傳回 DROPEFFECT_NONE。

覆寫此函式，以在拖曳作業期間提供使用者視覺效果的意見反應。 因為此函式會持續呼叫，所以包含在其中的任何程式碼都應該盡可能優化。 如需詳細資訊，請參閱[OLE 拖放：執行放置目標一](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)文。

##  <a name="ondragscroll"></a>CView：： OnDragScroll

在呼叫[system.windows.uielement.ondragenter](#ondragenter)或[system.windows.uielement.ondragover](#ondragover)來判中斷點是否在捲動區域中之前，由架構呼叫。

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*dwKeyState*<br/>
包含輔助按鍵的狀態。 這是下列任意數目的組合： MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON 和 MK_RBUTTON。

*此處*<br/>
包含游標相對於螢幕的位置（以圖元為單位）。

### <a name="return-value"></a>傳回值

DROPEFFECT 列舉型別中的值，指出當使用者在這個位置卸載物件時，會發生的卸載型別。 Drop 的類型通常取決於*dwKeyState*所指出的目前索引鍵狀態。 Keystates 與 DROPEFFECT 值的標準對應為：

- DROPEFFECT_NONE 無法在此視窗中卸載資料物件。

- MK_CONTROL &#124; MK_SHIFT 的 DROPEFFECT_LINK 會在物件與其伺服器之間建立連結。

- MK_CONTROL 的 DROPEFFECT_COPY 會建立已卸載之物件的複本。

- MK_ALT 的 DROPEFFECT_MOVE 會建立已捨棄物件的複本，並刪除原始物件。

- DROPEFFECT_SCROLL 表示拖曳捲軸操作即將發生或發生在目標視圖中。

如需詳細資訊，請參閱 MFC Advanced 概念範例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>備註

當您想要為此事件提供特殊行為時，請覆寫此函式。 當游標拖曳到每個視窗的框線內的預設捲動區域時，預設的執行會自動滾動視窗。 如需詳細資訊，請參閱[OLE 拖放：執行放置目標一](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)文。

##  <a name="ondraw"></a>CView：： OnDraw

由架構呼叫以呈現檔的影像。

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向用來呈現檔影像的裝置內容。

### <a name="remarks"></a>備註

此架構會呼叫此函式來執行螢幕顯示、列印和預覽列印，並在每個案例中傳遞不同的裝置內容。 沒有預設的實作。

您必須覆寫這個函式，以顯示檔的視圖。 您可以使用*pDC*參數所指向的[CDC](../../mfc/reference/cdc-class.md)物件，進行圖形裝置介面（GDI）呼叫。 您可以選取 GDI 資源（例如畫筆或字型）到裝置內容中，然後再進行繪製，然後在之後取消選取。 您的繪圖程式碼通常可以與裝置無關;也就是，它不需要顯示影像的裝置類型的相關資訊。

若要優化繪圖，請呼叫裝置內容的[RectVisible](../../mfc/reference/cdc-class.md#rectvisible)成員函式，以瞭解是否將繪製指定的矩形。 如果您需要區別一般螢幕顯示和列印，請呼叫裝置內容的[IsPrinting](../../mfc/reference/cdc-class.md#isprinting)成員函式。

##  <a name="ondrop"></a>CView：： System.windows.uielement.ondrop

當使用者透過有效的放置目標釋放資料物件時，由架構呼叫。

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>參數

' pDataObject * 指向拖放到放置目標的[COleDataObject](../../mfc/reference/coledataobject-class.md) 。

*dropEffect*<br/>
使用者所要求的捨棄效果。

- DROPEFFECT_COPY 會建立要卸載之資料物件的複本。

- DROPEFFECT_MOVE 將資料物件移至目前的滑鼠位置。

- DROPEFFECT_LINK 會在資料物件與其伺服器之間建立連結。

*此處*<br/>
相對於 view 工作區的目前滑鼠位置。

### <a name="return-value"></a>傳回值

如果卸載成功，則為非零;否則為0。

### <a name="remarks"></a>備註

預設的執行不會執行任何操作，而且會傳回 FALSE。

覆寫此函式，以實作用於將 OLE 拖放到 view 的工作區。 您可以透過*pDataObject*檢查資料物件，以取得剪貼簿資料格式，並在指定的點上捨棄資料。

> [!NOTE]
>  如果此 view 類別中有[OnDropEx](#ondropex)的覆寫，則架構不會呼叫這個函式。

##  <a name="ondropex"></a>CView：： OnDropEx

當使用者透過有效的放置目標釋放資料物件時，由架構呼叫。

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
指向放入放置目標的[COleDataObject](../../mfc/reference/coledataobject-class.md) 。

*dropDefault*<br/>
根據目前的索引鍵狀態，使用者為預設的卸載作業所選擇的效果。 可能是 DROPEFFECT_NONE。 「備註」一節會討論捨棄效果。

*dropList*<br/>
捨棄來源所支援的卸載效果清單。 捨棄效果值可以使用位 OR （ **&#124;** ）運算來結合。 「備註」一節會討論捨棄效果。

*此處*<br/>
相對於 view 工作區的目前滑鼠位置。

### <a name="return-value"></a>傳回值

從*point*指定之位置的 drop 嘗試產生的捨棄效果。 這必須是*dropEffectList*所指示的其中一個值。 「備註」一節會討論捨棄效果。

### <a name="remarks"></a>備註

預設的實作為不執行任何動作，且會傳回虛擬值（-1），表示架構應該呼叫[system.windows.uielement.ondrop](#ondrop)處理常式。

覆寫此函式以實作用滑鼠按鍵拖放功能。 滑鼠右鍵拖放通常會在放開滑鼠右鍵時，顯示選項的功能表。

您的 `OnDropEx` 覆寫應該查詢滑鼠右鍵。 您可以從[system.windows.uielement.ondragenter](#ondragenter)處理常式呼叫[GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate)或儲存滑鼠右鍵的狀態。

- 如果滑鼠右鍵已關閉，您的覆寫應該會顯示快顯功能表，提供卸載來源所支援的捨棄效果。

   - 檢查*dropList* ，以判斷卸載來源所支援的捨棄效果。 只在快顯功能表上啟用這些動作。

   - 根據*dropDefault*，使用[SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)來設定預設動作。

   - 最後，從快顯功能表中，採取使用者選擇所指示的動作。

- 如果滑鼠右鍵未關閉，您的覆寫應該將此處理為標準 drop 要求。 使用*dropDefault*中指定的捨棄效果。 或者，您的覆寫可能會傳回虛擬值（-1），以指出 `OnDrop` 將會處理此 drop 作業。

使用*pDataObject*來檢查剪貼簿資料格式的 `COleDataObject`，以及在指定的點上卸載的資料。

捨棄效果描述與 drop 作業相關聯的動作。 請參閱下列捨棄效果清單：

- DROPEFFECT_NONE 不允許使用 drop。

- DROPEFFECT_COPY 會執行複製作業。

- DROPEFFECT_MOVE 會執行移動作業。

- DROPEFFECT_LINK 會建立從已卸載資料到原始資料的連結。

- DROPEFFECT_SCROLL 表示拖曳捲軸操作即將發生或發生在目標中。

如需設定預設功能表命令的詳細資訊，請參閱在此磁片區中的 Windows SDK 和[CMenu：： GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu)中的[SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) 。

##  <a name="onendprinting"></a>CView：： OnEndPrinting

在列印或預覽檔之後，由架構呼叫。

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

此函式的預設實作不做任何動作。 覆寫此函式以釋放您在[OnBeginPrinting](#onbeginprinting)成員函式中配置的任何 GDI 資源。

##  <a name="onendprintpreview"></a>CView：： OnEndPrintPreview

當使用者離開預覽列印模式時，由架構呼叫。

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

*此處*<br/>
指定頁面上上次以預覽模式顯示的時間點。

*pView*<br/>
指向用於預覽的 view 物件。

### <a name="remarks"></a>備註

此函式的預設實作用會呼叫[OnEndPrinting](#onendprinting)成員函式，並將主框架視窗還原至預覽列印開始之前的狀態。 當預覽模式終止時，覆寫此函式以執行特殊處理。 例如，如果您想要在從 [預覽] 模式切換至 [一般顯示模式] 時，維護使用者在檔中的位置，您可以滾動到*point*參數所描述的位置，以及*pInfo*參數所指向之 `CPrintInfo` 結構的 `m_nCurPage` 成員。

一律從您的覆寫呼叫 `OnEndPrintPreview` 的基類版本，通常是在函式的結尾。

##  <a name="oninitialupdate"></a>CView：： OnInitialUpdate

在第一次將視圖附加至檔，但在一開始顯示視圖之前，由架構呼叫。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>備註

此函式的預設執行會呼叫[OnUpdate](#onupdate)成員函式，但不含任何提示資訊（也就是針對*lHint*參數使用0的預設值，而*pHint*參數為 Null）。 覆寫這個函式，以執行需要檔相關資訊的任何一次性初始化。 例如，如果您的應用程式具有固定大小的檔，您可以使用此函式，根據檔案大小來初始化視圖的滾動限制。 如果您的應用程式支援可變大小的檔，請使用[OnUpdate](#onupdate)來更新每次檔變更時的滾動限制。

##  <a name="onpreparedc"></a>CView：： OnPrepareDC

在將[OnDraw](#ondraw)成員函式用於螢幕顯示之前，以及在列印或預覽列印期間針對每個頁面呼叫[OnPrint](#onprint)成員函式之前，由架構呼叫。

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向用來呈現檔影像的裝置內容。

*pInfo*<br/>
指向描述目前列印工作的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構（如果已針對列印或預覽列印呼叫 `OnPrepareDC`）;`m_nCurPage` 成員指定要列印的頁面。 如果針對螢幕顯示呼叫 `OnPrepareDC`，則此參數為 Null。

### <a name="remarks"></a>備註

如果針對螢幕顯示呼叫函式，此函式的預設執行不會執行任何操作。 不過，此函式會在衍生類別（例如[CScrollView](../../mfc/reference/cscrollview-class.md)）中覆寫，以調整裝置內容的屬性;因此，您應該一律在覆寫的開頭呼叫基類實。

如果呼叫函式來進行列印，則預設的執行會檢查儲存在*pInfo*參數中的頁面資訊。 如果尚未指定檔的長度，`OnPrepareDC` 會假設檔為一頁長，並在列印一頁之後停止列印迴圈。 函式會將結構的 `m_bContinuePrinting` 成員設定為 FALSE，藉以停止列印迴圈。

基於下列任何原因覆寫 `OnPrepareDC`：

- 視需要針對指定的頁面調整裝置內容的屬性。 例如，如果您需要設定對應模式或裝置內容的其他特性，請在此函式中執行此動作。

- 執行列印時間分頁。 一般來說，您可以使用[OnPreparePrinting](#onprepareprinting)成員函式，在列印開始時指定檔的長度。 不過，如果您事先不知道檔的長度（例如，從資料庫列印不確定的記錄數目），請覆寫 `OnPrepareDC`，以在列印檔案時測試其結尾。 當不再需要列印檔案時，請將 `CPrintInfo` 結構的 `m_bContinuePrinting` 成員設定為 FALSE。

- 以逐頁的方式將 escape 程式碼傳送至印表機。 若要從 `OnPrepareDC`傳送 escape 碼，請呼叫*pDC*參數的 `Escape` 成員函式。

在覆寫的開頭呼叫 `OnPrepareDC` 的基類版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>CView：： OnPreparePrinting

在列印或預覽檔之前，由架構呼叫。

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pInfo*<br/>
指向描述目前列印工作的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 結構。

### <a name="return-value"></a>傳回值

要開始列印的非零值;如果列印工作已取消，則為0。

### <a name="remarks"></a>備註

預設實作不做任何動作。

您必須覆寫此函式，才能啟用列印和預覽列印。 呼叫[DoPreparePrinting](#doprepareprinting)成員函式，將*pInfo*參數傳遞給它，然後傳回其傳回值。`DoPreparePrinting` 會顯示 [列印] 對話方塊，並建立印表機裝置內容。 如果您想要使用非預設值來初始化 [列印] 對話方塊，請將值指派給*pInfo*的成員。 例如，如果您知道檔的長度，請先將值傳遞給*pInfo*的[SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage)成員函式，再呼叫 `DoPreparePrinting`。 這個值會顯示在 [列印] 對話方塊範圍部分的 [到：] 方塊中。

`DoPreparePrinting` 不會顯示預覽工作的 [列印] 對話方塊。 如果您想要略過列印工作的 [列印] 對話方塊，請檢查*pInfo*的 `m_bPreview` 成員是否為 FALSE，然後將它設定為 TRUE，再將它傳遞給 `DoPreparePrinting`;之後將它重設為 FALSE。

如果您需要執行需要存取代表印表機裝置內容之 `CDC` 物件的初始化（例如，如果您需要在指定檔長度之前知道頁面大小），請覆寫 `OnBeginPrinting` 成員函式。

如果您想要設定*pInfo*參數的 `m_nNumPreviewPages` 或 `m_strPageDesc` 成員的值，請在呼叫 `DoPreparePrinting`之後執行此動作。 `DoPreparePrinting` 成員函式會將 `m_nNumPreviewPages` 設定為在應用程式的中找到的值。INI 檔，並將 `m_strPageDesc` 設為其預設值。

### <a name="example"></a>範例

  覆寫 `OnPreparePrinting` 並從覆寫呼叫 `DoPreparePrinting`，讓架構會顯示 [列印] 對話方塊，並為您建立印表機 DC。

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

如果您知道檔包含多少頁數，在呼叫 `DoPreparePrinting`之前，請先在 `OnPreparePrinting` 中設定 [最大值] 頁面。 此架構會顯示 [列印] 對話方塊的 [到] 方塊中的最大頁數。

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>CView：： OnPrint

由架構呼叫，以列印或預覽檔的頁面。

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向印表機裝置內容。

*pInfo*<br/>
指向描述目前列印工作的 `CPrintInfo` 結構。

### <a name="remarks"></a>備註

針對每個列印的頁面，架構會在呼叫[OnPrepareDC](#onpreparedc)成員函式之後立即呼叫此函式。 要列印的頁面是由*pInfo*指向之[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構的 `m_nCurPage` 成員所指定。 預設的實值會呼叫[OnDraw](#ondraw)成員函式，並將它傳遞至印表機裝置內容。

基於下列任何原因，覆寫此函式：

- 允許列印多頁檔。 只轉譯檔中與目前列印的頁面對應的部分。 如果您使用 `OnDraw` 來執行轉譯，您可以調整 [視口] 原點，只列印檔案的適當部分。

- 讓列印的影像看起來與螢幕影像不同（也就是，如果您的應用程式不是 WYSIWYG）。 不會將印表機裝置內容傳遞至 `OnDraw`，而是使用裝置內容來轉譯影像，使用畫面上未顯示的屬性。

   如果您需要用來列印的 GDI 資源，而不是用於螢幕顯示，請先將其選取到裝置內容中，然後再進行繪製和取消選取。 這些 GDI 資源應配置於[OnBeginPrinting](#onbeginprinting)中，並在[OnEndPrinting](#onendprinting)中發行。

- 以執行標頭或頁尾。 您仍然可以藉由限制可列印的區域，使用 `OnDraw` 來進行轉譯。

請注意， *pInfo*參數的 `m_rectDraw` 成員會以邏輯單元描述頁面的可列印範圍。

請勿在 `OnPrint`的覆寫中呼叫 `OnPrepareDC`;架構會在呼叫 `OnPrint`之前自動呼叫 `OnPrepareDC`。

### <a name="example"></a>範例

以下是覆寫 `OnPrint` 函式的基本架構：

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

如需其他範例，請參閱[CRichEditView：:P rintinsiderect](../../mfc/reference/cricheditview-class.md#printinsiderect)。

##  <a name="onscroll"></a>CView：： OnScroll

由架構呼叫以判斷是否可能進行滾動。

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*nScrollCode*<br/>
表示使用者的滾動要求的捲軸程式碼。 這個參數是由兩個部分組成：低序位位元組，可決定水準發生的滾動類型，而高序位位元組則會決定垂直發生的滾動類型：

- SB_BOTTOM 向下滾動。

- SB_LINEDOWN 向下滾動一行。

- SB_LINEUP 向上滾動一行。

- SB_PAGEDOWN 向下滾動一頁。

- SB_PAGEUP 向上滾動一頁。

- SB_THUMBTRACK 將捲動方塊拖曳至指定的位置。 目前的位置是在*nPos*中指定。

- SB_TOP 滾動到頁首。

*nPos*<br/>
包含捲軸程式碼 SB_THUMBTRACK 時的目前捲動方塊位置。否則不會使用它。 視初始捲軸範圍而定， *nPos*可能是負值，而且應該在必要時轉換成**int** 。

*bDoScroll*<br/>
決定您是否應該實際執行指定的滾動動作。 若為 TRUE，則應該進行滾動;如果為 FALSE，則不應該進行滾動。

### <a name="return-value"></a>傳回值

如果*bDoScroll*為 TRUE 且此視圖實際為滾動，則傳回非零值;否則為0。 如果*bDoScroll*為 FALSE，則會傳回您在*bDoScroll*為 TRUE 時所傳回的值，即使您不會實際進行滾動也一樣。

### <a name="remarks"></a>備註

在其中一種情況下，此函式是由架構呼叫，而當*bDoScroll*設定為 TRUE 時，則是在視圖收到捲軸訊息時。 在此情況下，您應該實際地滾動視圖。 在另一種情況下，當 OLE 專案一開始拖曳至放置目標的自動捲動區域，並實際進行滾動之前，會呼叫此函式，並將*bDoScroll*設為 FALSE。 在這種情況下，您實際上不應流覽此視圖。

##  <a name="onscrollby"></a>CView：： OnScrollBy

當使用者透過將 OLE 專案拖曳至視圖的目前框線，或藉由操作垂直或水準捲軸，來流覽檔目前視圖以外的區域時，由架構呼叫。

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*sizeScroll*<br/>
水準和垂直捲動的圖元數目。

*bDoScroll*<br/>
決定是否要進行視圖的滾動。 若為 TRUE，則會進行滾動;如果為 FALSE，則不會進行滾動。

### <a name="return-value"></a>傳回值

如果可以滾動視圖，則為非零。否則為0。

### <a name="remarks"></a>備註

在衍生類別中，這個方法會查看使用者要求的方向是否可以滾動此視圖，然後視需要更新新的區域。 [Cwnd：： OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[Cwnd：： OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)會自動呼叫此函式，以執行實際的滾動要求。

這個方法的預設執行不會變更視圖，但如果沒有呼叫，則此視圖不會在 `CScrollView`衍生的類別中進行滾動。

如果檔寬度或高度超過32767圖元，則滾動到32767將會失敗，因為使用不正確*sizeScroll*引數呼叫 `OnScrollBy`。

##  <a name="onupdate"></a>CView：： OnUpdate

在修改視圖的檔之後，由架構呼叫;此函式是由[CDocument：： UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)所呼叫，可讓此視圖更新其顯示以反映這些修改。

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>參數

*pSender*<br/>
指向修改檔的視圖，如果要更新所有的視圖，則為 Null。

*lHint*<br/>
包含修改的相關資訊。

*pHint*<br/>
指向儲存修改相關資訊的物件。

### <a name="remarks"></a>備註

[OnInitialUpdate](#oninitialupdate)的預設執行也會呼叫它。 預設的執行會使整個工作區失效，並在收到下一個 WM_PAINT 訊息時，將它標示為繪製。 如果您只想要更新對應至檔之修改部分的區域，請覆寫此函式。 若要這麼做，您必須使用提示參數傳遞有關修改的資訊。

若要使用*lHint*，請定義特殊提示值（通常是位元遮罩或列舉類型），並讓檔傳遞其中一個值。 若要使用*pHint*，請從[CObject](../../mfc/reference/cobject-class.md)衍生一個提示類別，並讓檔將指標傳遞給提示物件;覆寫 `OnUpdate`時，請使用[CObject：： IsKindOf](../../mfc/reference/cobject-class.md#iskindof)成員函式來判斷提示物件的執行時間類型。

一般來說，您不應該直接從 `OnUpdate`執行任何繪製。 相反地，請決定在裝置座標中描述需要更新之區域的矩形;將此矩形傳遞給[CWnd：： InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect)。 這會導致在下一次收到[WM_PAINT](/windows/win32/gdi/wm-paint)訊息時進行繪製。

如果*lHint*為0，而*pHint*為 Null，則檔已傳送一般更新通知。 如果視圖收到一般更新通知，或如果無法解碼提示，則會使其整個工作區失效。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)
