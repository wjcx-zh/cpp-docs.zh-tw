---
title: CToolBar 類別
ms.date: 11/04/2016
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
ms.openlocfilehash: cbb2d1bb797737a14e9728d339305bf9c371b543
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752202"
---
# <a name="ctoolbar-class"></a>CToolBar 類別

有一列點陣圖按鈕和選擇性分隔線的控制列。

## <a name="syntax"></a>語法

```
class CToolBar : public CControlBar
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CToolBar:CToolBar](#ctoolbar)|建構 `CToolBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CToolbar::命令索引](#commandtoindex)|返回具有給定命令 ID 的按鈕的索引。|
|[CToolBar:建立](#create)|創建 Windows 工具列並將其`CToolBar`附加到 物件。|
|[CToolBar::建立Ex](#createex)|為`CToolBar`嵌`CToolBarCtrl`入 物件創建具有其他樣式的物件。|
|[CToolBar:取得按鈕資訊](#getbuttoninfo)|檢索按鈕的 ID、樣式和圖像編號。|
|[CToolBar:取得按鈕樣式](#getbuttonstyle)|檢索按鈕的樣式。|
|[CToolBar:取得按鈕文字](#getbuttontext)|檢索將顯示在按鈕上的文本。|
|[CToolBar:取得項目ID](#getitemid)|在給定索引處返回按鈕或分隔符的命令 ID。|
|[CToolBar:取得項目重新完成](#getitemrect)|檢索給定索引處項的顯示矩形。|
|[CToolBar::取得工具列](#gettoolbarctrl)|允許直接訪問基礎公共控件。|
|[CToolBar::載入點陣圖](#loadbitmap)|載入包含點陣圖按鈕圖像的點陣圖。|
|[CToolBar::載入工具列](#loadtoolbar)|載入資源編輯器建立的工具列資源。|
|[CToolBar::設定點陣圖](#setbitmap)|設置位映射圖像。|
|[CToolBar::設定按鈕資訊](#setbuttoninfo)|設置按鈕的 ID、樣式和圖像編號。|
|[CToolBar:設定按鈕](#setbuttons)|設置點陣圖中的按鈕樣式和按鈕圖像索引。|
|[CToolBar:設定按鈕樣式](#setbuttonstyle)|設置按鈕的樣式。|
|[CToolBar::設定按鈕文字](#setbuttontext)|設定將顯示在按鈕上的文本。|
|[CToolBar::設定高度](#setheight)|設置工具列的高度。|
|[CToolBar::設定大小](#setsizes)|設置按鈕的大小及其位圖。|

## <a name="remarks"></a>備註

按鈕可以像按鈕、複選框按鈕或單選按鈕一樣。 `CToolBar`物件通常是派生自類[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)的幀視窗物件的嵌入成員。

[CToolBar:GetToolBarCtrl](#gettoolbarctrl)是 MFC 4.0 中新成員函數,允許您利用 Windows 通用控件對工具列自定義和其他功能的支援。 `CToolBar`成員函數為您提供 Windows 公共控件的大部分功能;但是,當您調用`GetToolBarCtrl`時,您可以為您的工具列提供更多 Windows 95/98 工具列的特徵。 調用`GetToolBarCtrl`時,它將返回`CToolBarCtrl`對 物件的引用。 有關使用 Windows 常見控制程式設計工具列的詳細資訊,請參閱[CToolBarCtrl。](../../mfc/reference/ctoolbarctrl-class.md) 有關常見控制項的更多一般資訊,請參閱 Windows SDK[中的常見控制項](/windows/win32/Controls/common-controls-intro)。

視覺化C++為您提供了建立工具列的兩種方法。 要使用資源編輯器建立工具列資源,請按照以下步驟操作:

1. 創建工具列資源。

1. 建構 `CToolBar` 物件。

1. 呼叫["建立](#create)"(或[CreateEx](#createex)) 函數以創建 Windows`CToolBar`工具列並將其附加到 物件。

1. 調用[LoadToolBar](#loadtoolbar)以載入工具列資源。

否則，請遵循下列步驟進行︰

1. 建構 `CToolBar` 物件。

1. 呼叫["建立](#create)"(或[CreateEx](#createex)) 函數以創建 Windows`CToolBar`工具列並將其附加到 物件。

1. 調用[LoadBitmap](#loadbitmap)以載入包含工具列按鈕圖像的點陣圖。

1. 調用[SetButtons](#setbuttons)以設定按鈕樣式,並將每個按鈕與位圖中的圖像相關聯。

工具列中的所有按鈕圖像都取自一個位圖,該位圖必須為每個按鈕包含一個圖像。 所有圖像的大小必須相同;默認值為 16 像素寬,高 15 圖元。 圖像必須並排在位圖中。

函數`SetButtons`獲取指向控制項指示陣列的指標和指定陣列中元素數的整數。 該函數將每個按鈕的 ID 設定到陣列的相應元素的值,並為每個按鈕分配一個圖像索引,該索引指定按鈕圖像在位圖中的位置。 如果陣列元素的值ID_SEPARATOR,則不分配圖像索引。

點陣圖中影像的順序通常是在螢幕上繪製影像的順序,但您可以使用[SetButtonInfo](#setbuttoninfo)函數來更改影像順序和繪圖順序之間的關係。

工具列中的所有按鈕大小都相同。 預設值為 24 x 22 像素,根據*Windows 介面軟體設計指南*。 圖像和按鈕尺寸之間的任何附加空間都用於在圖像周圍形成邊框。

每個按鈕都有一個圖像。 各種按鈕狀態和樣式(按下、向上、向下、禁用、向下禁用和不確定)從該圖像生成。 儘管點陣圖可以是任何顏色,但您可以使用黑色和灰色陰影的圖像獲得最佳效果。

> [!WARNING]
> `CToolBar`支援最多 16 種顏色的位圖。 將圖像載入到工具列編輯器中時,Visual Studio 會自動將影像轉換為 16 色位圖(如有必要),如果影像已轉換,則顯示警告消息。 如果使用具有 16 種顏色以上的圖像(使用外部編輯器編輯圖像),則應用程式可能會出乎意料地運行。

默認情況下,工具列按鈕會模仿按鈕。 但是,工具列按鈕也可以模仿複選框按鈕或單選按鈕。 複選框按鈕有三種狀態:已選中、清除和不確定。 單選按鈕只有兩種狀態:已選中並清除。

若要在不指向數位的情況下設定單個按鈕或分隔符樣式,請呼叫[GetButtonStyle](#getbuttonstyle)來檢索該樣式,然後呼叫[SetButtonStyle](#setbuttonstyle)而不是`SetButtons`。 `SetButtonStyle`當您想在運行時更改按鈕的樣式時,最有用。

要將文字指定在按鈕上顯示,請致電[GetButtonText](#getbuttontext)以檢索顯示在按鈕上的文本,然後調用[SetButtonText](#setbuttontext)來設定文本。

要創建複選框按鈕,請為其分配樣式TBBS_CHECKBOX或在ON_UPDATE_COMMAND_UI處理程式中使用`CCmdUI``SetCheck`對象的成員函數。 呼叫`SetCheck`將按鈕轉換為複選框按鈕。 將`SetCheck`參數 0 表示未選中,1 表示選中,2 表示不確定。

要建立單選按鈕,請從ON_UPDATE_COMMAND_UI處理程式呼叫[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的[SetRadio](../../mfc/reference/ccmdui-class.md#setradio)成員函數。 為`SetRadio`未選中或未選中傳遞參數 0 或非零。 為了提供無線電組的互斥行為,您必須為組中的所有按鈕ON_UPDATE_COMMAND_UI處理程式。

有關使用`CToolBar`的詳細資訊,請參閱文章[MFC 工具列實現](../../mfc/mfc-toolbar-implementation.md)[與技術說明 31:控制列](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[C控制列](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="ctoolbarcommandtoindex"></a><a name="commandtoindex"></a>CToolbar::命令索引

此成員函數返回第一個工具列按鈕的索引,從命令 ID`nIDFind`匹配的位置 0 開始。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>參數

*nIDFind*<br/>
工具列按鈕的命令 ID。

### <a name="return-value"></a>傳回值

按鈕的索引,如果沒有按鈕具有給定的命令 ID,則為 -1。

## <a name="ctoolbarcreate"></a><a name="create"></a>CToolBar:建立

此成員函數創建 Windows 工具列(子視窗),並將`CToolBar`其與 物件關聯。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向工具列的父視窗。

*dwStyle*<br/>
工具欄樣式。 支援的其他工具列樣式包括:

- CBRS_TOP控制欄位於框架視窗的頂部。

- CBRS_BOTTOM控制欄位於框架視窗的底部。

- CBRS_NOALIGN調整父控件欄的大小時,不會重新置放。

- CBRS_TOOLTIPS控制列顯示工具提示。

- CBRS_SIZE_DYNAMIC控制欄是動態的。

- CBRS_SIZE_FIXED控制欄已固定。

- CBRS_FLOATING控制欄是浮動的。

- CBRS_FLYBY 狀態列顯示有關按鈕的資訊。

- CBRS_HIDE_INPLACE控件欄不向用戶顯示。

*nID*<br/>
工具列的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

它還將工具列高度設置為預設值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

## <a name="ctoolbarcreateex"></a><a name="createex"></a>CToolBar::建立Ex

呼叫此函數以創建 Windows 工具列(子視窗),並將`CToolBar`其與 物件關聯。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,
    CRect rcBorders = CRect(
    0,
    0,
    0,
    0),
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向工具列的父視窗。

*dwCtrl風格*<br/>
用於創建嵌入式[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)物件的其他樣式。 默認情況下,此值設置為TBSTYLE_FLAT。 有關工具列樣式的完整清單,請參閱*dwStyle*。

*dwStyle*<br/>
工具欄樣式。 有關適當樣式的清單,請參閱 Windows SDK 中的[工具列控制項與按鈕樣式](/windows/win32/Controls/toolbar-control-and-button-styles)。

*rcBorders*<br/>
定義工具列視窗邊框寬度的[CRect](../../atl-mfc-shared/reference/crect-class.md)物件。 默認情況下,這些邊框設置為 0,0,0,0,從而生成沒有邊框的工具列視窗。

*nID*<br/>
工具列的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

它還將工具列高度設置為預設值。

在`CreateEx`創建嵌入工具列控制項期間需要存在某些樣式時,請使用而不是[Create。](#create) 例如,將*dwCtrlStyle*設置為TBSTYLE_FLAT&#124;TBSTYLE_TRANSPARENT創建類似於 Internet Explorer 4 工具列的工具列。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

## <a name="ctoolbarctoolbar"></a><a name="ctoolbar"></a>CToolBar:CToolBar

此成員函數建構物件`CToolBar`並設置預設大小。

```
CToolBar();
```

### <a name="remarks"></a>備註

呼叫[「創建](#create)成員」函數以創建工具列視窗。

## <a name="ctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a>CToolBar:取得按鈕資訊

此成員函數檢索 nIndex 指定位置工具列按鈕或分隔符的控制 ID、樣式和圖像*索引。*

```cpp
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要檢索其資訊的工具列按鈕或分隔符的索引。

*nID*<br/>
對設置為按鈕的命令 ID 的 UINT 的引用。

*nStyle*<br/>
引用設定為按鈕樣式的 UINT。

*i 影像*<br/>
引用設置為位圖中按鈕圖像索引的整數。

### <a name="remarks"></a>備註

這些值分配給*nID、nStyle**nID*和*iImage*引用的變數。 圖像索引是圖像在位圖中的位置,該位圖包含所有工具列按鈕的圖像。 第一個圖像位於位置 0。

如果*nIndex*指定分隔符,則*iImage*設置為分隔符寬度(以像素為單位)。

## <a name="ctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a>CToolBar:取得按鈕樣式

呼叫此成員函數以檢索工具列上的按鈕或分隔符的樣式。

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要檢索的工具列按鈕或分隔符樣式的索引。

### <a name="return-value"></a>傳回值

*nIndex*指定的按鈕或分隔符的樣式。

### <a name="remarks"></a>備註

按鈕的樣式確定按鈕的顯示方式以及按鈕如何回應使用者輸入。 有關按鈕樣式的示例,請參閱[設置ButtonStyle。](#setbuttonstyle)

## <a name="ctoolbargetbuttontext"></a><a name="getbuttontext"></a>CToolBar:取得按鈕文字

呼叫此成員函數以檢索顯示在按鈕上的文本。

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要檢索的文本的索引。

*rString*<br/>
對包含要檢索的文本的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的引用。

### <a name="return-value"></a>傳回值

包含`CString`按鈕文字的物件。

### <a name="remarks"></a>備註

此成員函數的第二種形式使用字串文本填充`CString`物件。

## <a name="ctoolbargetitemid"></a><a name="getitemid"></a>CToolBar:取得項目ID

此成員函數返回*nIndex*指定的按鈕或分隔符的命令 ID。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要檢索其ID的項的索引。

### <a name="return-value"></a>傳回值

*nIndex*指定的按鈕或分隔符的命令 ID。

### <a name="remarks"></a>備註

分離器返回ID_SEPARATOR。

## <a name="ctoolbargetitemrect"></a><a name="getitemrect"></a>CToolBar:取得項目重新完成

此成員函數使用`RECT`*nIndex*指定的按鈕或分隔符的座標填充其位址包含在*lpRect*中的結構。

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要檢索其矩形座標的項的索引(按鈕或分隔符)。

*lpRect*<br/>
將包含項座標的[RECT](/windows/win32/api/windef/ns-windef-rect)結構的位址。

### <a name="remarks"></a>備註

座標相對於工具列的左上角以像素為單位。

用於`GetItemRect`獲取要替換為組合框或其他控制項的分隔符的座標。

### <a name="example"></a>範例

  請參考[CToolBar 的範例:設定大小](#setsizes)。

## <a name="ctoolbargettoolbarctrl"></a><a name="gettoolbarctrl"></a>CToolBar::取得工具列

此成員函數允許直接訪問基礎公共控件。

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>傳回值

`CToolBarCtrl` 物件的參考。

### <a name="remarks"></a>備註

用於`GetToolBarCtrl`利用 Windows 工具列通用控制件的功能,並利用[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)提供的工具列自訂支援。

有關使用常見控制項的詳細資訊,請參閱 Windows SDK 中的「[控制件](../../mfc/controls-mfc.md)」和[「常見控制件](/windows/win32/Controls/common-controls-intro)」一文。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

## <a name="ctoolbarloadbitmap"></a><a name="loadbitmap"></a>CToolBar::載入點陣圖

調用此成員函數以載入`lpszResourceName``nIDResource`或指定的點陣圖。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>參數

*lpsz 資源名稱*<br/>
指向要載入的位圖的資源名稱的指標。

*nID資源*<br/>
要載入的點陣圖的資源 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

位圖應包含每個工具列按鈕的一個圖像。 如果圖像不是標準大小(16 像素寬,15 像素高),請調用[SetSizes](#setsizes)來設置按鈕大小及其圖像。

> [!WARNING]
> `CToolBar`支援最多 16 種顏色的位圖。 將圖像載入到工具列編輯器中時,Visual Studio 會自動將影像轉換為 16 色位圖(如有必要),如果影像已轉換,則顯示警告消息。 如果使用具有 16 種顏色以上的圖像(使用外部編輯器編輯圖像),則應用程式可能會出乎意料地運行。

## <a name="ctoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CToolBar::載入工具列

呼叫此成員函數以載入*lpszResourceName*或*nIDResource*指定的工具列。

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>參數

*lpsz 資源名稱*<br/>
指向要載入的工具列的資源名稱的指標。

*nID資源*<br/>
要載入的工具列的資源 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

有關建立工具列資源的詳細資訊,請參閱 中的[工具列編輯器](../../windows/toolbar-editor.md)。

### <a name="example"></a>範例

  請參考[CToolBar 的範例:建立Ex](#createex)。

## <a name="ctoolbarsetbitmap"></a><a name="setbitmap"></a>CToolBar::設定點陣圖

調用此成員函數以設置工具列的位圖圖像。

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>參數

*hbmImageWell*<br/>
與工具列關聯的位圖圖像的句柄。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

例如,在使用者`SetBitmap`對更改按鈕操作的文檔執行操作後,調用更改位映射圖像。

## <a name="ctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a>CToolBar::設定按鈕資訊

呼叫此成員函數以設置按鈕的命令 ID、樣式和圖像編號。

```cpp
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要為其設置資訊的按鈕或分隔符的零基索引。

*nID*<br/>
按鈕的命令 ID 設定為的值。

*nStyle*<br/>
新的按鈕樣式。 支援以下按鈕樣式:

- TBBS_BUTTON標準按鈕 (預設)

- TBBS_SEPARATOR分離器

- TBBS_CHECKBOX 自動複選框按鈕

- TBBS_GROUP 標籤一組按鈕的開始

- TBBS_CHECKGROUP 標籤一組選擇框按鈕的開始

- TBBS_DROPDOWN 創建下拉清單按鈕。

- TBBS_AUTOSIZE 按鈕的寬度將根據按鈕的文本而不是圖像的大小進行計算。

- TBBS_NOPREFIX 按鈕文本將沒有與其關聯的快速鍵前綴。

*i 影像*<br/>
點陣圖中按鈕圖像的新索引。

### <a name="remarks"></a>備註

對於具有樣式TBBS_SEPARATOR的分隔符,此函數將分隔符的寬度(以像素為單位)設置為存儲在*iImage*中的值。

> [!NOTE]
> 您還可以使用*nStyle*參數設置按鈕狀態;但是,由於按鈕狀態由[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)處理程式控制,因此在下次空閒處理`SetButtonInfo`期間, 您設置使用的任何狀態都將丟失。 有關詳細資訊[,請參閱如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)和[TN031:控制列](../../mfc/tn031-control-bars.md)。

有關點陣圖影像和按鈕的資訊,請參閱[CToolBar](../../mfc/reference/ctoolbar-class.md)概述和[CToolBar::LoadBitmap](#loadbitmap)。

## <a name="ctoolbarsetbuttons"></a><a name="setbuttons"></a>CToolBar:設定按鈕

此成員函數將每個工具列按鈕的命令 ID 設置到陣列*lpIDArray*的相應元素指定的值。

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>參數

*lpIDArray*<br/>
指向命令 ID 的陣列的指標。 分配空按鈕可以為 NULL。

*nID( N) Count*<br/>
*lpIDArray*指向的陣列中的元素數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

如果陣列的元素具有值ID_SEPARATOR,則在工具列的相應位置創建分隔符。 此函數還將每個按鈕的樣式設置為TBBS_BUTTON,每個分隔符的樣式TBBS_SEPARATOR,並將圖像索引分配給每個按鈕。 圖像索引指定按鈕圖像在位圖中的位置。

不需要考慮點陣圖中的分隔符,因為此函數不為分隔符分配圖像索引。 如果工具列在位置 0、1 和 3 處具有按鈕,在位置 2 處有分隔符,則位圖中位置 0、1 和 2 處的圖像將分別分配給位置 0、1 和 3 處的按鈕。

如果*lpIDArray*為 NULL,則此函數為*nIDCount*指定的項數分配空間。 使用[SetButtonInfo](#setbuttoninfo)設置每個項目的屬性。

## <a name="ctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CToolBar:設定按鈕樣式

呼叫此成員函數以設置按鈕或分隔符的樣式,或對按鈕進行分組。

```cpp
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要設置其資訊的按鈕或分隔符的索引。

*nStyle*<br/>
按鈕樣式。 支援以下按鈕樣式:

- TBBS_BUTTON標準按鈕 (預設)

- TBBS_SEPARATOR分離器

- TBBS_CHECKBOX 自動複選框按鈕

- TBBS_GROUP 標籤一組按鈕的開始

- TBBS_CHECKGROUP 標籤一組選擇框按鈕的開始

- TBBS_DROPDOWN 建立下拉清單按鈕

- TBBS_AUTOSIZE按鈕的寬度將根據按鈕的文字(而不是影像的大小)計算

- TBBS_NOPREFIX 按鍵文字將沒有與其關聯的捷徑前置字串

### <a name="remarks"></a>備註

按鈕的樣式確定按鈕的顯示方式以及按鈕如何回應使用者輸入。

在調用`SetButtonStyle`之前,調用[GetButtonStyle](#getbuttonstyle)成員函數來檢索按鈕或分隔符樣式。

> [!NOTE]
> 您還可以使用*nStyle*參數設置按鈕狀態;但是,由於按鈕狀態由[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)處理程式控制,因此在下次空閒處理`SetButtonStyle`期間, 您設置使用的任何狀態都將丟失。 有關詳細資訊[,請參閱如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)和[TN031:控制列](../../mfc/tn031-control-bars.md)。

## <a name="ctoolbarsetbuttontext"></a><a name="setbuttontext"></a>CToolBar::設定按鈕文字

呼叫此函數以設定按鈕上的文本。

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要設置其文本的按鈕的索引。

*lpszText*<br/>
指向要在按鈕上設置的文本。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參閱[CToolBar 的範例:獲取工具列。](#gettoolbarctrl)

## <a name="ctoolbarsetheight"></a><a name="setheight"></a>CToolBar::設定高度

此成員函數將工具列的高度設置為*在 cyHeight*中指定的值(以像素為單位)。

```cpp
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>參數

*賽高地*<br/>
工具列的高度(以像素為單位)。

### <a name="remarks"></a>備註

調用[SetSizes](#setsizes)後,使用此成員函數覆蓋標準工具列高度。 如果高度太小,按鈕將在底部被剪切。

如果未調用此功能,框架將使用按鈕的大小來確定工具列的高度。

## <a name="ctoolbarsetsizes"></a><a name="setsizes"></a>CToolBar::設定大小

呼叫此成員函數將工具列的按鈕設置為大小按鈕指定的*大小*(以像素為單位)。

```cpp
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>參數

*大小按鈕*<br/>
每個按鈕的大小(以像素為單位)。

*大小影像*<br/>
每個圖像的大小(以像素為單位)。

### <a name="remarks"></a>備註

*sizeImage*參數必須包含工具列位圖中圖像的大小(以像素為單位)。 *尺寸按鈕*的尺寸必須足以容納圖像加上 7 像素的額外寬度和 6 像素的額外高度。 此功能還設置工具列高度以適合按鈕。

僅對未遵循*Windows 介面指南的軟體設計*建議按鈕和圖像大小的工具列調用此成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品對接](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 類別](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)
