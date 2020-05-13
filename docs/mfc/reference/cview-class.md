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
ms.openlocfilehash: 763e36b0736ce588e7e2aded25e50347f9e0ca70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373207"
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
|[C查看:CView](#cview)|建構 `CView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CView::D準備列印](#doprepareprinting)|顯示列印對話框並創建印表機設備上下文;重寫`OnPreparePrinting`成員函數時調用。|
|[CView:取得文件](#getdocument)|返回與檢視關聯的文檔。|
|[CView:已選定](#isselected)|測試是否選擇了文檔項。 OLE 支援是必需的。|
|[C查看::OnDragEnter](#ondragenter)|首次將專案拖入檢視的拖放區域時調用。|
|[C查看::OnDragLeave](#ondragleave)|當拖動的項目離開視圖的拖放區域時調用。|
|[C查看::在德拉格弗](#ondragover)|當專案拖動到視圖的拖放區域時調用。|
|[CView::OnDragScroll](#ondragscroll)|呼叫 以確定游標是否拖入視窗的滾動區域。|
|[C查看:上投](#ondrop)|當專案已放入檢視的拖放區域時調用,預設處理程式。|
|[C查看::OnDropEx](#ondropex)|當項已放入檢視的主處理程式的拖放區域時調用。|
|[CView:初始更新](#oninitialupdate)|視圖首次附加到文檔後調用。|
|[C查看::在準備DC](#onpreparedc)|在要求`OnDraw`成員函數進行螢幕顯示之前調用,或者在`OnPrint`列印或列印預覽時調用成員函數。|
|[C查看::開啟](#onscroll)|當 OLE 項拖出視圖邊界時調用。|
|[CView:OnScrollby](#onscrollby)|滾動包含活動就地 OLE 項的視圖時調用。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CView:開啟畫面](#onactivateframe)|當包含檢視的框架視窗啟動或停用時調用。|
|[C查看:開啟啟動檢視](#onactivateview)|激活視圖時調用。|
|[CView::OnBeginPrinting](#onbeginprinting)|列印作業開始時調用;重寫以分配圖形設備介面 (GDI) 資源。|
|[C查看:在畫上](#ondraw)|調用 以呈現文件的圖像以進行屏幕顯示、列印或列印預覽。 需要實施。|
|[C查看::結束列印](#onendprinting)|列印作業結束時調用;重寫以取消分配 GDI 資源。|
|[CView::結束列印預覽](#onendprintpreview)|退出預覽模式時調用。|
|[C查看::準備列印](#onprepareprinting)|在列印或預覽文檔之前調用;覆蓋以初始化列印對話方塊。|
|[C查看::在列印](#onprint)|已調用以列印或預覽文件的頁面。|
|[CView:開啟更新](#onupdate)|已調用以通知檢視其文檔已被修改。|

## <a name="remarks"></a>備註

檢視附加到文件,充當文件和用戶之間的仲介:檢視在螢幕上或印表機上呈現文檔的圖像,並將使用者輸入解釋為對文檔的操作。

視圖是框架視窗的子級。 多個檢視可以共用幀視窗,例如拆分器視窗。 視圖類、框架視窗類和文檔類之間的關係`CDocTemplate`由 物件建立。 當使用者打開新視窗或拆分現有視窗時,框架將建構一個新視圖並將其附加到文檔。

檢視只能附加到一個文件,但文檔可以同時附加多個檢視-例如,如果文件顯示在拆分器視窗中或多個文檔介面 (MDI) 應用程式中的多個子視窗中)。 您的應用程式可以支援給定文件類型的不同類型的檢視;但是,您的應用程式可以支援指定文檔類型的檢視。例如,字處理程式可能同時提供文檔的完整文本視圖和僅顯示節標題的大綱檢視。 如果使用分割器視窗,則可以將這些不同類型的檢視放置在單獨的框架視窗或單個框架視窗的單獨窗格中。

視圖可能負責處理幾種不同類型的輸入,例如鍵盤輸入、滑鼠輸入或通過拖放輸入,以及功能表、工具列或滾動條中的命令。 視圖接收由其框架窗口轉發的命令。 如果檢視不處理給定命令,它將該命令轉發到其關聯的文檔。 與所有命令目標一樣,視圖通過消息映射處理消息。

檢視負責顯示和修改文件的數據,但不負責儲存文件的數據。 本文檔向檢視提供有關其數據的必要詳細資訊。 您可以讓檢視直接存取文件的數據成員,也可以在文檔類中提供要調用的檢視類的成員函數。

當文件的資料發生更改時,負責更改的檢視通常調用文件的[CDocument:updateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)函數,該函數透過為每個檢視調`OnUpdate`用 成員函數來通知所有其他檢視。 預設實現`OnUpdate`使檢視的整個工作區無效。 您可以重寫它,使其僅使映射到文檔修改部分的工作區區域無效。

要使用`CView`,從派生類並`OnDraw`實現 成員函數來執行屏幕顯示。 您還可以使用`OnDraw`執行列印和列印預覽。 框架處理用於列印和預覽文件的列印迴圈。

視圖處理具有[CWnd::onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd::onVScroll](../../mfc/reference/cwnd-class.md#onvscroll)成員函數的滾動條消息。 您可以在這些函數中實現滾動條消息處理,也可以使用`CView`派生類[CScrollView](../../mfc/reference/cscrollview-class.md)為您處理滾動。

此外`CScrollView`,微軟基礎類庫提供`CView`來自 以下九個其他類:

- [CCtrlView](../../mfc/reference/cctrlview-class.md),一個允許使用具有樹、清單和豐富編輯控制項的文檔視圖體系結構的檢視.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md),一個在對話方塊控制項中顯示資料庫記錄的檢視。

- [CEditView](../../mfc/reference/ceditview-class.md),一個提供簡單多行文字編輯器的檢視。 可以將`CEditView`物件用作對話方塊中的控制程式以及文檔上的檢視。

- [CFormView](../../mfc/reference/cformview-class.md),一個可滾動的視圖,其中包含對話框控件,並且基於對話框範本資源。

- [CListView](../../mfc/reference/clistview-class.md),一種允許使用帶有清單控制項的文件檢視體系結構的檢視.

- [CRecordView](../../mfc/reference/crecordview-class.md),一個在對話方塊控制項中顯示資料庫記錄的檢視。

- [CRichEditView](../../mfc/reference/cricheditview-class.md),一個允許使用具有豐富編輯控制項的文件檢視體系結構的視圖.

- [CScrollView](../../mfc/reference/cscrollview-class.md),自動提供滾動支援的檢視。

- [CTreeView](../../mfc/reference/ctreeview-class.md),一個允許使用帶有樹控件的文檔檢視體繫結構的檢視.

該`CView`類還有一個名為`CPreviewView`的 派生實現類,該類由框架用於執行列印預覽。 此類支援列印預覽視窗獨有的要素,例如工具列、單頁或雙頁預覽和縮放,即放大預覽圖像。 除非要實現自己的介面以進行列印預覽(例如`CPreviewView`,如果要支援在列印預覽模式下進行編輯),否則無需調用或重寫任何成員函數。 有關使用`CView`的詳細資訊,請參閱[文件/檢視體系結構](../../mfc/document-view-architecture.md)和[列印](../../mfc/printing.md)。 此外,有關自定義列印預覽的更多詳細資訊[,請參閱技術說明 30。](../../mfc/tn030-customizing-printing-and-print-preview.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cviewcview"></a><a name="cview"></a>C查看:CView

建構 `CView` 物件。

```
CView();
```

### <a name="remarks"></a>備註

創建新幀視窗或拆分視窗時,框架將調用構造函數。 覆蓋[On初始更新](#oninitialupdate)成員函數,在文檔附加後初始化檢視。

## <a name="cviewdoprepareprinting"></a><a name="doprepareprinting"></a>CView::D準備列印

從[OnPreparePrinting](#onprepareprinting)的重寫中呼叫此函數以呼叫「列印」對話框並創建印表機裝置上下文。

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pInfo*<br/>
指向描述目前列印工作的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 結構。

### <a name="return-value"></a>傳回值

如果可以開始列印或列印預覽,則非零;如果操作已取消,則為 0。

### <a name="remarks"></a>備註

此功能的行為取決於是調用它進行列印或列印預覽(由`m_bPreview`*pInfo*參數的成員指定)。 如果正在列印檔,此函數將使用[cPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構中*pInfo*指向的值呼叫「列印」對話框;使用者關閉對話方塊後,該函數根據使用者在對話方塊中指定的設置創建印表機裝置上下文,並透過*pInfo*參數返回此設備上下文。 此設備上下文用於列印文檔。

如果正在預覽檔,此函數將使用當前印表機設置創建印表機設備上下文;如果正在預覽該檔,則使用當前印表機設置創建印表機設備上下文。此設備上下文用於在預覽期間類比印表機。

## <a name="cviewgetdocument"></a><a name="getdocument"></a>CView:取得文件

呼叫此函數以獲取指向檢視文件的指標。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>傳回值

指向與檢視關聯的[CDocument 物件](../../mfc/reference/cdocument-class.md)的指標。 如果檢視未附加到文件,則為 NULL。

### <a name="remarks"></a>備註

這允許您調用文件的成員函數。

## <a name="cviewisselected"></a><a name="isselected"></a>CView:已選定

由框架調用以檢查是否選擇了指定的文檔項。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>參數

*pDocItem*<br/>
指向要測試的文檔項。

### <a name="return-value"></a>傳回值

如果選擇了指定的文檔項,則非零;否則 0。

### <a name="remarks"></a>備註

此函數的預設實現返回 FALSE。 如果要使用[CDocItem](../../mfc/reference/cdocitem-class.md)物件實現選擇,則重寫此函數。 如果檢視包含 OLE 項,則必須重寫此函數。

## <a name="cviewonactivateframe"></a><a name="onactivateframe"></a>CView:開啟畫面

當包含檢視的框架視窗被啟動或停用時,框架調用。

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>參數

*n州*<br/>
指定幀視窗是激活還是停用。 它可能是下列其中一個值：

- WA_INACTIVE框架視窗正在停用。

- WA_ACTIVE框架視窗正在通過按下滑鼠以外的方法啟動(例如,透過使用鍵盤介面選擇視窗)。

- WA_CLICKACTIVE滑鼠按下啟動框架視窗

*pFramewnd*<br/>
指向要啟動的幀視窗的指標。

### <a name="remarks"></a>備註

如果要在與檢視關聯的幀視窗啟動或停用時執行特殊處理,則覆蓋此成員函數。 例如[,CFormView](../../mfc/reference/cformview-class.md)在儲存和恢復具有焦點的控制項時執行此重寫。

## <a name="cviewonactivateview"></a><a name="onactivateview"></a>C查看:開啟啟動檢視

當視圖啟動或停用時,由框架調用。

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>參數

*b 啟動*<br/>
指示視圖是正在啟動還是停用。

*p 啟動檢視*<br/>
指向正在啟動的檢視物件。

*p 主動檢視*<br/>
指向正在停用的視圖物件。

### <a name="remarks"></a>備註

此函數的預設實現將焦點設置為要啟動的檢視。 如果要在啟動或停用檢視時執行特殊處理,則重寫此函數。 例如,如果要提供特殊視覺提示,將活動視圖和非活動檢視區分開來,則檢查*bActivate*參數並相應地更新視圖的外觀。

如果啟動應用程式的主框架視窗且活動檢視沒有變化 *,pActivateView*和*pDeactiveView*參數指向同一視圖,例如,如果焦點從另一個應用程式傳輸到此應用程式,而不是在應用程式中從一個視圖傳輸到另一個視圖或在 MDI 子視窗之間切換時。 這允許檢視根據需要重新實現其調色板。

當[CFrameWnd:setActiveView](../../mfc/reference/cframewnd-class.md#setactiveview)調用檢視時,這些參數會有所不同,該視圖與[CFrameWnd::getActiveView](../../mfc/reference/cframewnd-class.md#getactiveview)返回的視圖不同。 這通常發生在拆分器視窗。

## <a name="cviewonbeginprinting"></a><a name="onbeginprinting"></a>C查看::開始列印

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

## <a name="cviewondragenter"></a><a name="ondragenter"></a>C查看::OnDragEnter

當滑鼠首次進入放置目標視窗的非滾動區域時,由框架調用。

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
指向被拖入檢視的放置區域的[COleDataObject。](../../mfc/reference/coledataobject-class.md)

*德基州*<br/>
包含修改器鍵的狀態。 這是以下任意數量的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*點*<br/>
相對於檢視的工作區的當前滑鼠位置。

### <a name="return-value"></a>傳回值

DROPEFFECT 枚舉類型中的值,指示使用者在此位置放置物件時將發生的放置類型。 丟棄的類型通常取決於*dwKeyState*指示的當前密鑰狀態。 鍵狀態到 DROPEFFECT 值的標準映射是:

- DROPEFFECT_NONE資料物件不能在此視窗中刪除。

- DROPEFFECT_LINKMK_CONTROL&#124;MK_SHIFT在物件及其伺服器之間創建連結。

- DROPEFFECT_COPYMK_CONTROL 創建已刪除物件的複本。

- DROPEFFECT_MOVEMK_ALT 創建已刪除物件的複本並刪除原始物件。 當檢視可以接受此數據物件時,這通常是默認放置效果。

有關詳細資訊,請參閱 MFC 高級概念範例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>備註

默認實現是不執行任何操作並返回DROPEFFECT_NONE。

重寫此函數,以便為將來對[OnDragOver](#ondragover)成員函數的調用做好準備。 此時應檢查資料物件所需的任何資料,以便以後在成員函數中使用`OnDragOver`。 此時還應更新視圖,以便向使用者提供可視反饋。 有關詳細資訊,請參閱文章 OLE[拖曳:實現放置目標](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)。

## <a name="cviewondragleave"></a><a name="ondragleave"></a>C查看::OnDragLeave

當滑鼠移出該視窗的有效放置區域時,框架在拖動操作期間調用。

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>備註

如果當前檢視需要清理[在 OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)調用期間採取的任何操作,例如在拖動和刪除物件時刪除任何可視用戶反饋,請覆蓋此函數。

## <a name="cviewondragover"></a><a name="ondragover"></a>C查看::在德拉格弗

當滑鼠移到放置目標視窗時,框架在拖動操作期間調用。

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
移到拖曳到放置目標的[COleData 物件](../../mfc/reference/coledataobject-class.md)。

*德基州*<br/>
包含修改器鍵的狀態。 這是以下任意數量的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*點*<br/>
相對於檢視工作區的當前滑鼠位置。

### <a name="return-value"></a>傳回值

DROPEFFECT 枚舉類型中的值,指示使用者在此位置放置物件時將發生的放置類型。 丟棄的類型通常取決於*dwKeyState*指示的當前密鑰狀態。 鍵狀態到 DROPEFFECT 值的標準映射是:

- DROPEFFECT_NONE資料物件不能在此視窗中刪除。

- DROPEFFECT_LINKMK_CONTROL&#124;MK_SHIFT在物件及其伺服器之間創建連結。

- DROPEFFECT_COPYMK_CONTROL 創建已刪除物件的複本。

- DROPEFFECT_MOVEMK_ALT 創建已刪除物件的複本並刪除原始物件。 當檢視可以接受數據物件時,這通常是默認放置效果。

有關詳細資訊,請參閱 MFC 高級概念範例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>備註

默認實現是不執行任何操作並返回DROPEFFECT_NONE。

重寫此函數,在拖動操作期間為使用者提供視覺反饋。 由於此函數是連續調用的,因此應盡可能優化其中包含的任何代碼。 有關詳細資訊,請參閱文章 OLE[拖曳:實現放置目標](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)。

## <a name="cviewondragscroll"></a><a name="ondragscroll"></a>CView::OnDragScroll

在調用[OnDragEnter](#ondragenter)或[OnDragOver](#ondragover)之前由框架調用,以確定該點是否位於滾動區域中。

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>參數

*德基州*<br/>
包含修改器鍵的狀態。 這是以下任意數量的組合:MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON和MK_RBUTTON。

*點*<br/>
包含游標相對於螢幕的位置(以像素為單位)。

### <a name="return-value"></a>傳回值

DROPEFFECT 枚舉類型中的值,指示使用者在此位置放置物件時將發生的放置類型。 丟棄的類型通常取決於*dwKeyState*指示的當前密鑰狀態。 鍵狀態到 DROPEFFECT 值的標準映射是:

- DROPEFFECT_NONE資料物件不能在此視窗中刪除。

- DROPEFFECT_LINKMK_CONTROL&#124;MK_SHIFT在物件及其伺服器之間創建連結。

- DROPEFFECT_COPYMK_CONTROL 創建已刪除物件的複本。

- DROPEFFECT_MOVEMK_ALT 創建已刪除物件的複本並刪除原始物件。

- DROPEFFECT_SCROLL指示拖動滾動操作即將發生或發生在目標視圖中。

有關詳細資訊,請參閱 MFC 高級概念範例[OCLIENT](../../overview/visual-cpp-samples.md)。

### <a name="remarks"></a>備註

如果要為此事件提供特殊行為,請重寫此函數。 當游標拖動到每個視窗邊框內的預設滾動區域時,默認實現會自動滾動視窗。 有關詳細資訊,請參閱文章 OLE[拖曳:實現放置目標](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)。

## <a name="cviewondraw"></a><a name="ondraw"></a>C查看:在畫上

由框架調用以呈現文檔的圖像。

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向用於呈現文件圖像的設備上下文。

### <a name="remarks"></a>備註

框架呼叫此函數以執行螢幕顯示、列印和列印預覽,並在每種情況下傳遞不同的設備上下文。 沒有預設的實作。

必須重寫此函數才能顯示文件的檢視。 您可以使用*pDC*參數指向的[CDC](../../mfc/reference/cdc-class.md)物件進行圖形裝置介面 (GDI) 調用。 在繪製之前,您可以在設備上下文中選擇 GDI 資源(如筆或字型),然後在繪製後取消選擇這些資源。 通常,您的繪圖代碼可以獨立於設備;也就是說,它不需要有關顯示映射的設備類型的資訊。

要優化繪圖,請致電設備上下文的[Rect可見](../../mfc/reference/cdc-class.md#rectvisible)成員函數,以找出是否將繪製給定矩形。 如果需要區分正常螢幕顯示和列印,請致電設備上下文的[IsPrinting](../../mfc/reference/cdc-class.md#isprinting)成員功能。

## <a name="cviewondrop"></a><a name="ondrop"></a>C查看:上投

當使用者在有效的放置目標上釋放數據物件時,由框架調用。

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>參數

"pDataObject] 指向丟棄目標中的[COleDataObject。](../../mfc/reference/coledataobject-class.md)

*滴效果*<br/>
使用者請求的放置效果。

- DROPEFFECT_COPY建立要刪除的資料物件的複本。

- DROPEFFECT_MOVE將數據物件移動到當前滑鼠位置。

- DROPEFFECT_LINK 在數據物件及其伺服器之間創建連結。

*點*<br/>
相對於檢視工作區的當前滑鼠位置。

### <a name="return-value"></a>傳回值

如果下降成功,則為非零;否則 0。

### <a name="remarks"></a>備註

默認實現不執行任何操作,並返回 FALSE。

重寫此函數以實現 OLE 丟棄到檢視的工作區的效果。 數據物件可以通過*pDataObject*檢查剪貼簿數據格式和丟棄在指定點的數據。

> [!NOTE]
> 如果此檢視類中存在對[OnDropEx](#ondropex)的重寫,則框架不會調用此函數。

## <a name="cviewondropex"></a><a name="ondropex"></a>C查看::OnDropEx

當使用者在有效的放置目標上釋放數據物件時,由框架調用。

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>參數

*pDataObject*<br/>
指向丟棄目標中的[COleDataObject。](../../mfc/reference/coledataobject-class.md)

*丟棄預設*<br/>
使用者根據當前鍵狀態為預設放置操作選擇的效果。 它可能是DROPEFFECT_NONE。 「註釋」部分將討論放置效果。

*下拉清單*<br/>
放置來源支援的放置效果的清單。 可以使用位或 **(&#124;**) 操作組合放置效果值。 「註釋」部分將討論放置效果。

*點*<br/>
相對於檢視工作區的當前滑鼠位置。

### <a name="return-value"></a>傳回值

從*點指定的位置*的放置嘗試產生的放置效果。 這必須是*dropEffectList*指示的值之一。 「註釋」部分將討論放置效果。

### <a name="remarks"></a>備註

預設實現是不執行任何操作並返回虛擬值 (-1),以指示框架應調用[OnDrop](#ondrop)處理程式。

重寫此函數以實現滑鼠右鍵拖放的效果。 右滑鼠按鈕拖放通常在釋放滑鼠右鍵時顯示選項功能表。

對滑鼠右`OnDropEx`鍵的重寫應查詢。 您可以調用[GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate)或從[OnDragEnter](#ondragenter)處理程式儲存滑鼠右鍵狀態。

- 如果滑鼠右鍵已關閉,則覆蓋應顯示一個彈出功能表,該功能表提供放置源支援的放置效果。

  - 檢查*放置清單*以確定放置源支援的放置效果。 在彈出式功能表上僅啟用這些操作。

  - 使用[SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)設定基於*刪除預設*的預設操作。

  - 最後,從彈出式功能表中執行用戶選擇指示的操作。

- 如果滑鼠右鍵未關閉,則重寫應作為標準放置請求處理。 使用*在下拉預設*中指定的放置效果。 或者,重寫可以返回虛擬值 (-1),以`OnDrop`指示 將處理此放置操作。

使用*pDataObject*檢查`COleDataObject`用於剪貼簿的資料格式和在指定點丟棄的資料。

放置效果描述與放置操作關聯的操作。 請參考以下放置效果清單:

- DROPEFFECT_NONE不允許掉下。

- DROPEFFECT_COPY將執行複製操作。

- DROPEFFECT_MOVE將執行移動操作。

- DROPEFFECT_LINK將建立從刪除數據到原始數據的連結。

- DROPEFFECT_SCROLL指示拖動滾動操作即將發生或發生在目標中。

有關設置預設功能表命令的詳細資訊,請參閱 Windows SDK 中的[SetMenu 預設專案](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem),以及[CMenu:取得此卷中的 SafeHmenu。](../../mfc/reference/cmenu-class.md#getsafehmenu)

## <a name="cviewonendprinting"></a><a name="onendprinting"></a>C查看::結束列印

在列印或預覽文檔後由框架呼叫。

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

此函式的預設實作不做任何動作。 重寫此函數以釋放您在[OnBeginPrinting](#onbeginprinting)成員函數中分配的任何 GDI 資源。

## <a name="cviewonendprintpreview"></a><a name="onendprintpreview"></a>CView::結束列印預覽

當使用者退出列印預覽模式時由框架調用。

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
指定上次在預覽模式下顯示的頁面上的點。

*pView*<br/>
指向用於預覽的視圖物件。

### <a name="remarks"></a>備註

此函數的預設實現調用[OnEndPrinting](#onendprinting)成員函數,並將主框架視窗還原到列印預覽開始之前的狀態。 覆蓋此函數以在預覽模式終止時執行特殊處理。 例如,如果要在從預覽模式切換到正常顯示模式時維護使用者在文檔中的位置,則可以滾動*point*到 點`m_nCurPage`參數和`CPrintInfo`*pInfo*參數指向的結構成員描述的位置。

始終從重寫調用`OnEndPrintPreview`的 基類版本,通常在函數的末尾。

## <a name="cviewoninitialupdate"></a><a name="oninitialupdate"></a>CView:初始更新

視圖首次附加到文檔後由框架調用,但在最初顯示視圖之前。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>備註

此函數的預設實現調用[OnUpdate](#onupdate)成員函數,沒有提示資訊(即,使用*lHint*參數的預設值 0,對於*pHint*參數使用 NULL)。 重寫此函數以執行任何需要有關文件資訊的一次性初始化。 例如,如果應用程式具有固定大小的文件,則可以使用此函數根據文檔大小初始化檢視的滾動限制。 如果應用程式支援可變大小的文件,請使用[OnUpdate](#onupdate)在每次文件更改時更新滾動限制。

## <a name="cviewonpreparedc"></a><a name="onpreparedc"></a>C查看::在準備DC

在要求[OnDraw](#ondraw)成員函數進行螢幕顯示之前,在列印或列印預覽期間為每個頁面調用[OnPrint](#onprint)成員函數之前,由框架調用。

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向用於呈現文件圖像的設備上下文。

*pInfo*<br/>
指向[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構,該結構描述目前的`OnPrepareDC`列印作業 (如果需要列印或列印預覽);成員`m_nCurPage`指定要列印的頁面。 如果`OnPrepareDC`為螢幕顯示呼叫,則此參數為 NULL。

### <a name="remarks"></a>備註

如果為螢幕顯示調用該函數,則此函數的預設實現將不執行任何操作。 但是,在派生類(如[CScrollView)](../../mfc/reference/cscrollview-class.md)中重寫此函數,以調整設備上下文的屬性;因此,應始終在重寫開始時調用基類實現。

如果調用函數進行列印,則預設實現將檢查存儲在*pInfo*參數中的頁面資訊。 如果未指定文檔的長度,`OnPrepareDC`則假定文檔為一頁長,並在列印一頁後停止列印迴圈。 該函數通過將結構`m_bContinuePrinting`的成員設置為 FALSE 來停止列印迴圈。

由於`OnPrepareDC`以下任何原因,重寫:

- 根據需要調整指定頁面的設備上下文的屬性。 例如,如果需要設置映射模式或設備上下文的其他特徵,則在此函數中執行此操作。

- 執行列印時分。 通常,使用[OnPreparePrinting](#onprepareprinting)成員功能指定列印開始時的文件長度。 但是,如果您事先不知道文檔有多長(例如,從資料庫中列印不確定數量的記錄時),則重`OnPrepareDC`寫 以在列印文檔時測試文檔的末尾。 如果沒有要列印的文檔,則`m_bContinuePrinting``CPrintInfo`將結構的成員設置為 FALSE。

- 逐頁向印表機發送轉義代碼。 要從`OnPrepareDC`傳送轉義`Escape`代碼, 請呼叫*pDC*參數的成員函數。

在重寫開始時調用`OnPrepareDC`的基類版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

## <a name="cviewonprepareprinting"></a><a name="onprepareprinting"></a>C查看::準備列印

在列印或預覽文檔之前由框架呼叫。

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pInfo*<br/>
指向描述目前列印工作的 [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 結構。

### <a name="return-value"></a>傳回值

開始列印的非零;如果列印作業已取消,則為 0。

### <a name="remarks"></a>備註

預設實作不做任何動作。

您必須重寫此函數才能啟用列印和列印預覽。 呼叫[DoPreparePrinting](#doprepareprinting)成員函數,傳遞*pInfo*參數,然後返回其返回值;`DoPreparePrinting`顯示「列印」對話框並創建印表機裝置上下文。 如果要使用預設值以外的值初始化"列印"對話框,請將值分配給*pInfo*的成員。 例如,如果您知道文檔的長度,則在調`DoPreparePrinting`用 之前將值傳遞給*pInfo*的[SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage)成員函數。 此值顯示在「列印」對話框的「範圍」部分的「到:「框中。

`DoPreparePrinting`不顯示預覽作業的「列印」對話框。 如果要繞過列印作業的「列印」對話框,請檢查`m_bPreview`*pInfo*的成員是否為 FALSE,然後將其設定為 TRUE,然後`DoPreparePrinting`再將其傳遞給 ;之後將其重置為 FALSE。

如果需要執行需要存取表示印表機裝置`CDC`上下文的物件的初始化(例如,如果需要在指定文檔長度之前知道頁面大小),`OnBeginPrinting`則重寫成員函數。

如果要設定*pInfo*參數`DoPreparePrinting``m_nNumPreviewPages`或`m_strPageDesc`成員的值,請在呼叫 後執行此操作。 成員`DoPreparePrinting`函數將`m_nNumPreviewPages`設置 到應用程式 中找到的值。INI 檔案`m_strPageDesc`並設定為其預設值。

### <a name="example"></a>範例

  從`OnPreparePrinting`覆蓋`DoPreparePrinting`覆蓋和呼叫,以便框架將顯示一個列印對話方塊,並為您創建印表機 DC。

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

如果知道文檔包含多少頁,則在調`OnPreparePrinting``DoPreparePrinting`用 之前在 中設置最大頁。 框架將在「列印」對話框的「to」框中顯示最大頁碼。

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

## <a name="cviewonprint"></a><a name="onprint"></a>C查看::在列印

由框架調用以列印或預覽文件的頁面。

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向印表機裝置內容。

*pInfo*<br/>
指向描述當前`CPrintInfo`列印作業的結構。

### <a name="remarks"></a>備註

對於要列印的每個頁面,框架在調用[OnPrepareDC](#onpreparedc)成員函數後立即調用此函數。 正在列印的頁面由`m_nCurPage`*pInfo*指向的[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)結構的成員指定。 預設實現調用[OnDraw](#ondraw)成員函數並傳遞印表機裝置上下文。

出於以下任何原因,重寫此函數:

- 允許列印多頁文檔。 僅呈現與當前列印的頁面對應的文檔部分。 如果使用`OnDraw`執行渲染,則可以調整視口原點,以便只列印文檔的適當部分。

- 使列印的圖像看起來與螢幕圖像不同(即,如果應用程式不是WYSIWYG)。 而不是將印表機裝置上下文傳遞`OnDraw`給 ,使用設備上下文使用螢幕上未顯示的屬性渲染圖像。

   如果需要不使用的 GDI 資源進行列印,請在繪製之前將其選擇到設備上下文中,然後取消選擇它們。 這些 GDI 資源應在[OnBeginPrinting 中](#onbeginprinting)分配,並在[OnEndPrinting 中](#onendprinting)發表。

- 實現標題或註腳。 您仍可以`OnDraw`通過 限制可以列印的區域來執行渲染。

請注意`m_rectDraw`*,pInfo*參數的成員以邏輯單位描述頁面的可列印區域。

不要呼叫`OnPrepareDC`您的`OnPrint`覆寫 。框架在呼叫`OnPrepareDC`之前會`OnPrint`自動 呼叫 。

### <a name="example"></a>範例

以下是重寫`OnPrint`函數的骨架:

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

有關另一個範例,請參閱[CRichEditView::PintInsiderect](../../mfc/reference/cricheditview-class.md#printinsiderect)。

## <a name="cviewonscroll"></a><a name="onscroll"></a>C查看::開啟

由框架調用以確定是否可能滾動。

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*nScrollCode*<br/>
指示使用者滾動請求的滾動條代碼。 此參數由兩部分組成:一個低階位元組,它確定水準發生的滾動類型;高階位元組,確定垂直發生的滾動類型:

- SB_BOTTOM滾動到底部。

- SB_LINEDOWN向下滾動一行。

- SB_LINEUP向上滾動一行。

- SB_PAGEDOWN向下滾動一頁。

- SB_PAGEUP向上滾動一頁。

- SB_THUMBTRACK將滾動框拖動到指定位置。 當前位置在*nPos*中指定。

- SB_TOP滾動到頂部。

*nPos*<br/>
如果滾動條代碼SB_THUMBTRACK,則包含當前滾動框位置;否則,它不使用。 根據初始滾動範圍 *,nPos*可能是負的,如有必要,應強制轉換為**int。**

*b多卷*<br/>
確定是否實際執行指定的滾動操作。 如果為 TRUE,則應進行滾動;如果 FALSE,則不應進行滾動。

### <a name="return-value"></a>傳回值

如果*bDoScroll*為 TRUE,並且視圖實際上已滾動,則返回非零;否則 0。 如果*bDoScroll*是 FALSE,則傳回如果*bDoScroll*為 TRUE 時返回的值,即使您實際上沒有進行滾動。

### <a name="remarks"></a>備註

在一種情況下,當檢視收到滾動條消息時,框架將此函數調用 *,其中 bDoScroll*設置為 TRUE。 在這種情況下,您實際上應該滾動視圖。 在其他情況下,當 OLE 項最初在實際滾動之前拖入放置目標的自動滾動區域時,使用*bDoScroll*將此函數設置為 FALSE 時調用此函數。 在這種情況下,您實際上不應滾動視圖。

## <a name="cviewonscrollby"></a><a name="onscrollby"></a>CView:OnScrollby

當使用者查看文檔當前檢視以外的區域時,由框架調用,通過根據檢視的當前邊框拖動 OLE 項或操作垂直或水準滾動條。

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>參數

*大小捲動*<br/>
水準和垂直滾動的圖元數。

*b多卷*<br/>
確定是否進行視圖滾動。 如果為 TRUE,則進行滾動;如果為 TRUE,則進行滾動。如果 FALSE,則不會發生滾動。

### <a name="return-value"></a>傳回值

如果視圖能夠滾動,則非零;否則 0。

### <a name="remarks"></a>備註

在派生類中,此方法檢查視圖是否按使用者請求的方向滾動,然後在必要時更新新區域。 [CWnd::onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd:onVScroll](../../mfc/reference/cwnd-class.md#onvscroll)自動調用此功能,以執行實際滾動請求。

此方法的預設實現不會更改檢視,但如果不調用檢視,視圖將不會在`CScrollView`派生類中滾動。

如果文檔寬度或高度超過 32767 像素,則滾動超過 32767 將`OnScrollBy`失敗,因為調用的大小*滾動*參數無效。

## <a name="cviewonupdate"></a><a name="onupdate"></a>CView:開啟更新

修改檢視文檔後由框架調用;此函數由[CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)調用,並允許檢視更新其顯示以反映這些修改。

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>參數

*pSender*<br/>
指向修改文件的檢視,如果要更新所有檢視,則指向 NULL。

*lHint*<br/>
包含有關修改的資訊。

*pHint*<br/>
指向存儲有關修改資訊的物件。

### <a name="remarks"></a>備註

它也稱為[On初始更新](#oninitialupdate)的預設實現。 默認實現使整個工作區無效,在收到下一WM_PAINT消息時將其標記為繪製。 如果只想更新映射到文檔修改部分的區域,請覆蓋此函數。 為此,您必須使用提示參數傳遞有關修改的資訊。

要使用*lHint*,請定義特殊提示值(通常是位掩碼或枚舉類型),並讓文檔傳遞這些值之一。 要使用*pHint*,請從[CObject](../../mfc/reference/cobject-class.md)派生提示類,並讓文件傳遞指向提示物件的指標;例如,請從 CObject 派生提示類。重寫`OnUpdate`時,使用[CObject:isKindOf](../../mfc/reference/cobject-class.md#iskindof)成員函數來確定提示物件的運行時類型。

通常,不應直接從 執行任何繪`OnUpdate`圖 。 相反,確定在設備座標中描述需要更新的區域的矩形;將此矩形傳遞給[CWnd::不合法 。](../../mfc/reference/cwnd-class.md#invalidaterect) 這將導致下次收到[WM_PAINT](/windows/win32/gdi/wm-paint)消息時發生繪製。

如果*lHint*為*0,pHint*為 NULL,則文件已發送通用更新通知。 如果檢視收到泛型更新通知,或者無法解碼提示,則應將其整個工作區無效。

## <a name="see-also"></a>另請參閱

[MFC 樣品 MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)
