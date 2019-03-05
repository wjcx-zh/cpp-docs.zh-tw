---
title: CHeaderCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
helpviewer_keywords:
- CHeaderCtrl [MFC], CHeaderCtrl
- CHeaderCtrl [MFC], ClearAllFilters
- CHeaderCtrl [MFC], ClearFilter
- CHeaderCtrl [MFC], Create
- CHeaderCtrl [MFC], CreateDragImage
- CHeaderCtrl [MFC], CreateEx
- CHeaderCtrl [MFC], DeleteItem
- CHeaderCtrl [MFC], DrawItem
- CHeaderCtrl [MFC], EditFilter
- CHeaderCtrl [MFC], GetBitmapMargin
- CHeaderCtrl [MFC], GetFocusedItem
- CHeaderCtrl [MFC], GetImageList
- CHeaderCtrl [MFC], GetItem
- CHeaderCtrl [MFC], GetItemCount
- CHeaderCtrl [MFC], GetItemDropDownRect
- CHeaderCtrl [MFC], GetItemRect
- CHeaderCtrl [MFC], GetOrderArray
- CHeaderCtrl [MFC], GetOverflowRect
- CHeaderCtrl [MFC], HitTest
- CHeaderCtrl [MFC], InsertItem
- CHeaderCtrl [MFC], Layout
- CHeaderCtrl [MFC], OrderToIndex
- CHeaderCtrl [MFC], SetBitmapMargin
- CHeaderCtrl [MFC], SetFilterChangeTimeout
- CHeaderCtrl [MFC], SetFocusedItem
- CHeaderCtrl [MFC], SetHotDivider
- CHeaderCtrl [MFC], SetImageList
- CHeaderCtrl [MFC], SetItem
- CHeaderCtrl [MFC], SetOrderArray
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
ms.openlocfilehash: a683c877b67f4eae1a7411f5916987c9789b6817
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261345"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl 類別

提供 Windows 通用標頭控制項的功能。

## <a name="syntax"></a>語法

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|建構 `CHeaderCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|清除所有篩選器標題控制項。|
|[CHeaderCtrl::ClearFilter](#clearfilter)|清除標頭控制項的篩選。|
|[CHeaderCtrl::Create](#create)|會建立標題控制項，並將它附加至`CHeaderCtrl`物件。|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|建立標題控制項內的項目影像的透明的版本。|
|[CHeaderCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式中建立標題控制項，並將它附加至`CListCtrl`物件。|
|[CHeaderCtrl::DeleteItem](#deleteitem)|刪除的項目從標頭中的控制項。|
|[CHeaderCtrl::DrawItem](#drawitem)|繪製標題控制項的指定項目。|
|[CHeaderCtrl::EditFilter](#editfilter)|開始編輯指定的篩選條件，標題控制項。|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|擷取控制項中的點陣圖邊界的寬度。|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|取得目前具有焦點的標題控制項中的項目的識別碼。|
|[CHeaderCtrl::GetImageList](#getimagelist)|擷取映像清單控制項中繪製的標頭項目使用的控制代碼。|
|[CHeaderCtrl::GetItem](#getitem)|擷取控制項中項目的資訊。|
|[CHeaderCtrl::GetItemCount](#getitemcount)|擷取控制項中的項目計數。|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|取得指定的下拉式按鈕的週框矩形資訊標頭控制項中。|
|[CHeaderCtrl::GetItemRect](#getitemrect)|擷取指定的項目控制項中指定的週框。|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|擷取由左到右的順序標頭控制項中的項目。|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|取得目前的標頭控制溢位按鈕的週框矩形。|
|[CHeaderCtrl::HitTest](#hittest)|判斷哪一個標頭項目，如果有的話，位於指定的點。|
|[CHeaderCtrl::InsertItem](#insertitem)|將新的項目插入至標題控制項中。|
|[CHeaderCtrl::Layout](#layout)|擷取給定矩形內的標頭控制項的位置與大小。|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|擷取的項目，其標題控制項中的順序為基礎的索引值。|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|設定控制項中的點陣圖的邊界的寬度。|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|設定篩選屬性中的變更生效的時間和張貼之間的逾時間隔`HDN_FILTERCHANGE`通知。|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|將焦點設定至目前的標題控制項中指定的標頭項目。|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|變更標頭項目，以表示手動之間的分隔線拖曳和置放標頭項目。|
|[CHeaderCtrl::SetImageList](#setimagelist)|指派至標題控制項的影像清單。|
|[CHeaderCtrl::SetItem](#setitem)|設定控制項中的指定項目的屬性。|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|設定控制項中的項目的左到右的順序。|

## <a name="remarks"></a>備註

標頭控制項是通常是位於一組文字或數字的資料行上方的視窗。 它包含每個資料行的標題，它可以分割成組件。 使用者可以拖曳分隔線分隔的組件來設定每個資料行的寬度。 如需標題控制項的說明，請參閱 <<c0> [ 標頭控制項](/windows/desktop/Controls/header-controls)。

這個控制項 (並因此`CHeaderCtrl`類別) 僅適用於 Windows 95/98 和 Windows NT 版本 3.51 下執行的程式和更新版本。

Windows 95/Internet Explorer 4.0 通用控制項的新增功能包括下列各項：

- 標頭項目自訂排序。

- 標頭項目拖放，重新排序的標頭項目。 當您建立使用 HDS_DRAGDROP 樣式`CHeaderCtrl`物件。

- 標頭資料行文字資料行調整大小期間持續可檢視。 當您建立使用 HDS_FULLDRAG 樣式`CHeaderCtrl`物件。

- 標頭熱追蹤，這會反白顯示的標題項目，當滑鼠指標停留它。 當您建立使用 HDS_HOTTRACK 樣式`CHeaderCtrl`物件。

- 映像清單支援。 標頭項目可以包含在儲存映像`CImageList`物件或文字。

如需使用詳細資訊`CHeaderCtrl`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)並[使用 CHeaderCtrl](../../mfc/using-cheaderctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="cheaderctrl"></a>  CHeaderCtrl::CHeaderCtrl

建構 `CHeaderCtrl` 物件。

```
CHeaderCtrl();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

##  <a name="clearallfilters"></a>  CHeaderCtrl::ClearAllFilters

清除所有篩選器標題控制項。

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會實作 Win32 訊息的行為[HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter)資料行值為-1，在 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter

清除標頭控制項的篩選。

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>參數

*nColumn*<br/>
資料行值，指出其清除篩選。

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會實作 Win32 訊息的行為[HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

##  <a name="create"></a>  CHeaderCtrl::Create

會建立標題控制項，並將它附加至`CHeaderCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定標題控制項的樣式。 如需標頭控制項樣式的描述，請參閱 <<c0> [ 標頭控制項樣式](/windows/desktop/Controls/header-control-styles)Windows SDK 中。

*rect*<br/>
指定標題控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構。

*pParentWnd*<br/>
指定標題控制項的父視窗，通常`CDialog`。 它必須不是 NULL。

*nID*<br/>
指定標題控制項的識別碼。

### <a name="return-value"></a>傳回值

非零值，如果初始化成功;否則為零。

### <a name="remarks"></a>備註

您建構`CHeaderCtrl`兩個步驟中的物件。 首先，呼叫建構函式，然後呼叫`Create`，這會建立標題控制項，並將它附加至`CHeaderCtrl`物件。

除了標頭控制項樣式中，您可以使用下列常見的控制項樣式，以決定此標題控制項的位置與調整其大小 (請參閱[常見的控制項樣式](/windows/desktop/Controls/common-control-styles)如需詳細資訊):

- CCS_BOTTOM 使控制項本身放置在父視窗工作區底部，並設定要與父系相同寬度視窗的寬度。

- CCS_NODIVIDER 可防止兩個像素從反白顯示所繪製控制項的頂端。

- CCS_NOMOVEY 會導致控制項調整大小並移動本身以水平的方式，但未以垂直方式，以回應 WM_SIZE 訊息。 如果使用 CCS_NORESIZE 樣式，則不適用此樣式。 根據預設，標題控制項具有此樣式。

- CCS_NOPARENTALIGN，防止控制項被自動移至頂端或父視窗的底部。 相反地，控制項會保留它的位置，即使變更父視窗內的父視窗大小。 如果也用於 CCS_TOP 或 CCS_BOTTOM 樣式，高度會調整為預設值，但寬度與位置維持不變。

- CCS_NORESIZE，防止控制項被它的初始大小或新的大小設定時使用的預設寬度和高度。 相反地，控制會使用針對建立或調整大小要求中指定的高度與寬度。

- CCS_TOP 使控制項本身放置在父視窗工作區頂端，並設定要與父系相同寬度視窗的寬度。

您也可以套用下列的視窗樣式至標題控制項 (請參閱[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)如需詳細資訊):

- WS_CHILD 建立子視窗。 無法搭配 WS_POPUP 樣式。

- WS_VISIBLE 會建立一開始即可見的視窗。

- WS_DISABLED 會建立一開始會停用的視窗。

- WS_GROUP 指定的控制項所在使用者可以前往從一個控制項下一步 箭號索引鍵群組的第一個控制項。 之後的第一個控制項屬於相同的群組，以 WS_GROUP 樣式定義的所有控制項。 WS_GROUP 樣式的下一個控制項結束 樣式 群組，並開始下一步 群組 （也就是一個群組結束下一步 開始的位置）。

- WS_TABSTOP 指定任意數目的其中一個控制項，讓使用者可以使用 TAB 鍵移動。 TAB 鍵會將使用者移至下一個 WS_TABSTOP 樣式所指定的控制項。

如果您想要使用擴充的 windows 樣式和控制項，呼叫[CreateEx](#createex)而不是`Create`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>  CHeaderCtrl::CreateEx

建立控制項 （子視窗） 和其關聯`CHeaderCtrl`物件。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
指定正在建立之控制項的延伸的樣式。 如需延伸的 Windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*dwStyle*<br/>
標題控制項的樣式。 如需標頭控制項樣式的描述，請參閱 <<c0> [ 標頭控制項樣式](/windows/desktop/Controls/header-control-styles)Windows SDK 中。 請參閱[建立](#create)如需其他樣式的清單。

*rect*<br/>
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置，在中建立工作區座標中的視窗*pParentWnd*。

*pParentWnd*<br/>
是控制項的父視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而非`Create`套用延伸的 Windows 樣式，由 Windows 延伸的樣式前置詞**WS_EX_**。

##  <a name="createdragimage"></a>  CHeaderCtrl::CreateDragImage

建立標題控制項內的項目影像的透明的版本。

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
標題控制項中的項目以零為起始的索引。 映像指派給這個項目是透明的映像的基礎。

### <a name="return-value"></a>傳回值

指標[CImageList](../../mfc/reference/cimagelist-class.md)如果成功，否則為 NULL 的物件。 傳回的清單會包含只有一個映像。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[HDM_CREATEDRAGIMAGE](/windows/desktop/Controls/hdm-createdragimage)、 Windows SDK 中所述。 它可支援標頭項目拖曳和卸除。

`CImageList`的傳回的指標指向是暫存物件，刪除在下一步 的閒置時間處理的物件。

##  <a name="deleteitem"></a>  CHeaderCtrl::DeleteItem

刪除的項目從標頭中的控制項。

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定要刪除之項目的以零為起始的索引。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

##  <a name="drawitem"></a>  CHeaderCtrl::DrawItem

由架構的視覺外觀的主控描繪標題控制項變更時呼叫。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
指標[DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct)結構，描述要繪製的項目。

### <a name="remarks"></a>備註

`itemAction`隸屬`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。

根據預設，此成員函式沒有任何作用。 覆寫此成員函式，來實作活動，抽獎獲得主控描繪`CHeaderCtrl`物件。

應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件*lpDrawItemStruct*之前此成員函式會結束。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

##  <a name="editfilter"></a>  CHeaderCtrl::EditFilter

開始編輯指定的篩選條件，標題控制項。

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>參數

*nColumn*<br/>
若要編輯資料行。

*bDiscardChanges*<br/>
值，指定如何處理使用者的編輯變更，如果使用者正在編輯篩選時[HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter)傳送訊息。

指定 TRUE，即可捨棄對使用者] 或 [假接受使用者所做的變更的變更。

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會實作 Win32 訊息的行為[HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>  CHeaderCtrl::GetBitmapMargin

擷取控制項中的點陣圖邊界的寬度。

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>傳回值

邊界的寬度點陣圖像素為單位。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[HDM_GETBITMAPMARGIN](/windows/desktop/Controls/hdm-getbitmapmargin)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

##  <a name="getfocuseditem"></a>  CHeaderCtrl::GetFocusedItem

取得在目前的標頭控制項具有焦點之項目的索引。

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>傳回值

具有焦點的標題項目以零為起始的索引。

### <a name="remarks"></a>備註

這個方法會傳送[HDM_GETFOCUSEDITEM](/windows/desktop/Controls/hdm-getfocuseditem)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_headerCtrl`，也就是用來存取目前的標頭控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範`SetFocusedItem`和`GetFocusedItem`方法。 在先前章節中的程式碼，我們會建立標題控制項具有五個資料行。 不過，您可以拖曳資料行分隔符號，以便看不到 資料行。 下列範例會設定，然後確認 最後一個資料行標頭，為焦點的項目。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>  CHeaderCtrl::GetImageList

擷取映像清單控制項中繪製的標頭項目使用的控制代碼。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

指標[CImageList](../../mfc/reference/cimagelist-class.md)物件。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[HDM_GETIMAGELIST](/windows/desktop/Controls/hdm-getimagelist)、 Windows SDK 中所述。 `CImageList`的傳回的指標指向是暫存物件，刪除在下一步 的閒置時間處理的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

##  <a name="getitem"></a>  CHeaderCtrl::GetItem

擷取標頭的控制項項目的相關資訊。

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定要擷取之項目的以零為起始的索引。

*pHeaderItem*<br/>
指標[HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema)結構會接收新的項目。 此結構會搭配`InsertItem`和`SetItem`成員函式。 在設定任何旗標`mask`項目可讓您確保傳回時正確地填入對應的項目中的值。 如果`mask`元素設定為零，其他的結構項目中的值為沒有意義。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

##  <a name="getitemcount"></a>  CHeaderCtrl::GetItemCount

擷取控制項中的項目計數。

```
int GetItemCount() const;
```

### <a name="return-value"></a>傳回值

標頭控制項項目成功; 如果數目否則為-1。

### <a name="example"></a>範例

  範例，請參閱[CHeaderCtrl::DeleteItem](#deleteitem)。

##  <a name="getitemdropdownrect"></a>  CHeaderCtrl::GetItemDropDownRect

取得標頭中的項目目前的標頭控制項下拉式按鈕的週框矩形。

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iItem*|[in]其樣式為 HDF_SPLITBUTTON 標頭項目的以零為起始的索引。 如需詳細資訊，請參閱 <<c0> `fmt` 隸屬[HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema)結構。|
|*lpRect*|[out]指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)接收的週框矩形資訊的結構。|

### <a name="return-value"></a>傳回值

如果成功，此函式，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[HDM_GETITEMDROPDOWNRECT](/windows/desktop/Controls/hdm-getitemdropdownrect)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_headerCtrl`，也就是用來存取目前的標頭控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範`GetItemDropDownRect`方法。 在先前章節中的程式碼，我們會建立標題控制項具有五個資料行。 保留標頭下拉式按鈕的第一個資料行上，下列程式碼範例會繪製 3D 矩形周圍的位置。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>  CHeaderCtrl::GetItemRect

擷取指定的項目控制項中指定的週框。

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
標題控制項項目以零為起始的索引。

*lpRect*<br/>
位址指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)接收到的週框矩形資訊的結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

這個方法會實作 Win32 訊息的行為[HDM_GETITEMRECT](/windows/desktop/Controls/hdm-getitemrect)、 Windows SDK 中所述。

##  <a name="getorderarray"></a>  CHeaderCtrl::GetOrderArray

擷取由左到右的順序標頭控制項中的項目。

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>參數

*piArray*<br/>
在控制項標頭中，依照從左到右的順序接收項目的索引值的緩衝區的位址指標。

*iCount*<br/>
標頭控制項項目數目。 必須為非負數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[HDM_GETORDERARRAY](/windows/desktop/Controls/hdm-getorderarray)、 Windows SDK 中所述。 它被提供來支援標頭項目順序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>  CHeaderCtrl::GetOverflowRect

取得目前的標頭控制項的溢位按鈕的週框矩形。

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpRect*|[out]指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)接收到的週框矩形資訊的結構。|

### <a name="return-value"></a>傳回值

如果成功，此函式，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

標題控制項包含可同時顯示更多的項目，如果控制項可以顯示溢位按鈕捲動至不可見的項目。 標題控制項必須有 HDS_OVERFLOW 和 HDF_SPLITBUTTON 樣式來顯示溢位按鈕。 週框矩形包圍的溢位按鈕，而且有顯示溢位 按鈕時，才。 如需詳細資訊，請參閱 <<c0> [ 標頭控制項樣式](/windows/desktop/Controls/header-control-styles)。

這個方法會傳送[HDM_GETOVERFLOWRECT](/windows/desktop/Controls/hdm-getoverflowrect)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_headerCtrl`，也就是用來存取目前的標頭控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範`GetOverflowRect`方法。 在先前章節中的程式碼，我們會建立標題控制項具有五個資料行。 不過，您可以拖曳資料行分隔符號，以便看不到 資料行。 如果看不到某些資料行，此標題控制項繪製溢位按鈕。 下列程式碼範例會繪製 3D 矩形周圍溢位按鈕的位置。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>  CHeaderCtrl::HitTest

判斷哪一個標頭項目，如果有的話，位於指定的點。

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*phdhti*|[in、 out]指標[HDHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-_hd_hittestinfo)結構，指定要測試的點，並且會收到測試的結果。|

### <a name="return-value"></a>傳回值

標頭項目，如果有的話，在指定的位置; 為起始的索引否則為-1。

### <a name="remarks"></a>備註

這個方法會傳送[HDM_HITTEST](/windows/desktop/Controls/hdm-hittest)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_headerCtrl`，也就是用來存取目前的標頭控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範`HitTest`方法。 在先前章節中的 這個程式碼範例，我們會建立標題控制項具有五個資料行。 不過，您可以拖曳資料行分隔符號，以便看不到 資料行。 這個範例會報告資料行的索引，如果是可見和-1，如果看不到 資料行。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

##  <a name="insertitem"></a>  CHeaderCtrl::InsertItem

新的項目插入位於指定索引處的標頭控制項。

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>參數

*nPos*<br/>
要插入之項目之以零起始的索引。 如果值為零，此標題控制項的開頭插入項目。 如果值大於最大值，此標題控制項的結尾插入項目。

*phdi*<br/>
指標[HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema)結構，其中包含要插入項目的相關資訊。

### <a name="return-value"></a>傳回值

如果成功，新項目的索引否則為-1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>  CHeaderCtrl::Layout

擷取給定矩形內的標頭控制項的位置與大小。

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>參數

*pHeaderLayout*<br/>
指標[HDLAYOUT](/windows/desktop/api/commctrl/ns-commctrl-_hd_layout)結構，其中包含用來設定的大小和位置標頭控制項的資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此函式用來決定適當的大小會佔用指定的矩形的新標頭控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex

擷取的項目，其標題控制項中的順序為基礎的索引值。

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>參數

*nOrder*<br/>
從左到右的項目會出現在標題控制項，並在控制項中以零為起始的順序。

### <a name="return-value"></a>傳回值

項目，其標題控制項中的順序為基礎的索引。 索引計數從左到右，從 0 開始。

### <a name="remarks"></a>備註

此成員函式實作 Win32 巨集的行為[HDM_ORDERTOINDEX](https://msdn.microsoft.com/library/windows/desktop/bb775355)、 Windows SDK 中所述。 它被提供來支援標頭項目順序。

##  <a name="setbitmapmargin"></a>  CHeaderCtrl::SetBitmapMargin

設定控制項中的點陣圖的邊界的寬度。

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
寬度，以像素為單位，括住的點陣圖內現有的標頭控制項的邊界中所指定。

### <a name="return-value"></a>傳回值

邊界的寬度點陣圖像素為單位。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[HDM_SETBITMAPMARGIN](/windows/desktop/Controls/hdm-setbitmapmargin)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>  CHeaderCtrl::SetFilterChangeTimeout

設定逾時之間的間隔中篩選條件屬性的變更生效的時間和張貼[HDN_FILTERCHANGE](/windows/desktop/Controls/hdn-filterchange)通知。

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>參數

*dwTimeOut*<br/>
逾時值，以毫秒為單位。

### <a name="return-value"></a>傳回值

要修改的篩選器控制項的索引。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[HDM_SETFILTERCHANGETIMEOUT](/windows/desktop/Controls/hdm-setfilterchangetimeout)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>  CHeaderCtrl::SetFocusedItem

將焦點設定至目前的標題控制項中指定的標頭項目。

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iItem*|[in]標頭項目的以零為起始的索引。|

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[HDM_SETFOCUSEDITEM](/windows/desktop/Controls/hdm-setfocuseditem)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_headerCtrl`，也就是用來存取目前的標頭控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範`SetFocusedItem`和`GetFocusedItem`方法。 在先前章節中的程式碼，我們會建立標題控制項具有五個資料行。 不過，您可以拖曳資料行分隔符號，以便看不到 資料行。 下列範例會設定，然後確認 最後一個資料行標頭，為焦點的項目。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>  CHeaderCtrl::SetHotDivider

變更標頭項目，以表示手動之間的分隔線拖曳和置放標頭項目。

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>參數

*pt*<br/>
指標的位置。 標題控制項反白顯示適當的分割線，根據指標的位置。

*nIndex*<br/>
反白顯示分割線的索引。

### <a name="return-value"></a>傳回值

反白顯示分割線的索引。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[HDM_SETHOTDIVIDER](/windows/desktop/Controls/hdm-sethotdivider)、 Windows SDK 中所述。 它可支援標頭項目拖曳和卸除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>  CHeaderCtrl::SetImageList

指派至標題控制項的影像清單。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
指標`CImageList`物件，其中包含要指派至標題控制項之影像清單。

### <a name="return-value"></a>傳回值

指標[CImageList](../../mfc/reference/cimagelist-class.md)先前指派給此標題控制項的物件。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[HDM_SETIMAGELIST](/windows/desktop/Controls/hdm-setimagelist)、 Windows SDK 中所述。 `CImageList`的傳回的指標指向是暫存物件，刪除在下一步 的閒置時間處理的物件。

### <a name="example"></a>範例

  範例，請參閱[CHeaderCtrl::GetImageList](#getimagelist)。

##  <a name="setitem"></a>  CHeaderCtrl::SetItem

設定控制項中的指定項目的屬性。

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>參數

*nPos*<br/>
可操作的項目以零為起始的索引。

*pHeaderItem*<br/>
指標[HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema)結構，包含新的項目相關的資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  範例，請參閱[cheaderctrl:: Getitem](#getitem)。

##  <a name="setorderarray"></a>  CHeaderCtrl::SetOrderArray

設定控制項中的項目的左到右的順序。

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>參數

*iCount*<br/>
標頭控制項項目數目。

*piArray*<br/>
在控制項標頭中，依照從左到右的順序接收項目的索引值的緩衝區的位址指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作 Win32 巨集的行為[HDM_SETORDERARRAY](/windows/desktop/Controls/hdm-setorderarray)、 Windows SDK 中所述。 它被提供來支援標頭項目順序。

### <a name="example"></a>範例

  範例，請參閱[cheaderctrl:: Getorderarray](#getorderarray)。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl 類別](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList 類別](../../mfc/reference/cimagelist-class.md)
