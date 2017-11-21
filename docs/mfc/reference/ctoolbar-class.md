---
title: "CToolBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2e0e4b0699f17e4bf00106b3d4a22938569a2254
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ctoolbar-class"></a>CToolBar 類別
有一列點陣圖按鈕和選擇性分隔線的控制列。  
  
## <a name="syntax"></a>語法  
  
```  
class CToolBar : public CControlBar  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CToolBar::CToolBar](#ctoolbar)|建構 `CToolBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CToolBar::CommandToIndex](#commandtoindex)|傳回與指定的命令識別碼的按鈕索引|  
|[CToolBar::Create](#create)|建立 Windows 工具列，並將它附加至`CToolBar`物件。|  
|[CToolBar::CreateEx](#createex)|建立`CToolBar`具有其他樣式為內嵌物件`CToolBarCtrl`物件。|  
|[CToolBar::GetButtonInfo](#getbuttoninfo)|擷取識別碼、 樣式和按鈕的影像數目。|  
|[CToolBar::GetButtonStyle](#getbuttonstyle)|擷取按鈕的樣式。|  
|[CToolBar::GetButtonText](#getbuttontext)|擷取會出現在按鈕的文字。|  
|[CToolBar::GetItemID](#getitemid)|傳回按鈕或分隔符號的指定索引處的命令識別碼。|  
|[CToolBar::GetItemRect](#getitemrect)|擷取指定索引處的項目顯示週框。|  
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|允許直接存取基礎的通用控制項。|  
|[CToolBar::LoadBitmap](#loadbitmap)|載入包含點陣圖按鈕影像的點陣圖。|  
|[CToolBar::LoadToolBar](#loadtoolbar)|載入使用資源編輯器建立工具列資源。|  
|[CToolBar::SetBitmap](#setbitmap)|設定點陣圖的影像。|  
|[CToolBar::SetButtonInfo](#setbuttoninfo)|設定識別碼、 樣式和按鈕的影像數目。|  
|[CToolBar::SetButtons](#setbuttons)|設定按鈕樣式和按鈕影像點陣圖內的索引。|  
|[CToolBar::SetButtonStyle](#setbuttonstyle)|設定按鈕的樣式。|  
|[CToolBar::SetButtonText](#setbuttontext)|在按鈕上設定的顯示文字。|  
|[CToolBar::SetHeight](#setheight)|設定工具列的高度。|  
|[CToolBar::SetSizes](#setsizes)|設定按鈕和其點陣圖的大小。|  
  
## <a name="remarks"></a>備註  
 按鈕可以像是按鈕、 核取方塊按鈕、 或選項按鈕。 `CToolBar`物件是衍生自類別的框架視窗物件通常是內嵌的成員[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)。  
  
 [CToolBar::GetToolBarCtrl](#gettoolbarctrl)，成員函式新增到 MFC 4.0 可讓您利用 Windows 通用控制項的工具列和其他功能的支援。 `CToolBar`成員函式可讓您大部分的 Windows 通用控制項; 功能不過，當您呼叫`GetToolBarCtrl`，您就能給予您工具列更多 Windows 95/98 工具列的特性。 當您呼叫`GetToolBarCtrl`，它會傳回參考`CToolBarCtrl`物件。 請參閱[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)如需有關設計 Windows 通用控制項的工具列。 關於通用控制項的一般資訊，請參閱[通用控制項](http://msdn.microsoft.com/library/windows/desktop/bb775493)Windows SDK 中。  
  
 Visual c + + 為您提供兩種方法可以建立工具列。 若要建立工具列資源使用資源編輯器，請遵循下列步驟：  
  
1.  建立工具列資源。  
  
2.  建構 `CToolBar` 物件。  
  
3.  呼叫[建立](#create)(或[CreateEx](#createex)) 函式來建立 Windows 工具列，並將其附加至`CToolBar`物件。  
  
4.  呼叫[LoadToolBar](#loadtoolbar)載入工具列資源。  
  
 否則，請遵循下列步驟：  
  
1.  建構 `CToolBar` 物件。  
  
2.  呼叫[建立](#create)(或[CreateEx](#createex)) 函式來建立 Windows 工具列，並將其附加至`CToolBar`物件。  
  
3.  呼叫[LoadBitmap](#loadbitmap)載入包含的工具列按鈕影像的點陣圖。  
  
4.  呼叫[SetButtons](#setbuttons)將按鈕樣式設定，並讓每個按鈕產生關聯的點陣圖中的映像。  
  
 在工具列中的所有按鈕影像是都取自一個點陣圖，它必須包含一個影像，為每個按鈕。 所有映像必須是相同的大小。預設為 16 個像素寬和高 15 像素。 映像必須在點陣圖中的並排顯示。  
  
 `SetButtons`函式會採用控制項 Id 的陣列中指定的項目數的整數陣列的指標。 函式設定每個按鈕 ID 的值陣列的對應項目，並指派每個按鈕影像索引，指定點陣圖中按鈕的映像的位置。 如果陣列元素值**ID_SEPARATOR**，指派任何映像索引。  
  
 在點陣圖中的映像的順序通常是的順序中，它們會繪製在畫面上，但您可以使用[SetButtonInfo](#setbuttoninfo)函式變更影像的順序和繪圖順序之間的關聯性。  
  
 在工具列中的所有按鈕都都將相同的大小。 預設值為 24 x 22 像素為單位，按照所使用*軟體設計的 Windows 介面指導方針*。 影像和按鈕維度之間任何額外的空間用來形成在影像周圍的框線。  
  
 每個按鈕具有一個映像。 各種按鈕狀態，並從該一個映像會產生樣式 （已按下向上、 向下，已停用、 下、 停用和不定）。 雖然點陣圖可以是任何色彩，您就可以達到最佳的結果中黑白灰階映像。  
  
> [!WARNING]
> `CToolBar`支援最多 16 個色彩的點陣圖。 當您將映像載入工具列編輯器時，Visual Studio 會自動將影像轉換為 16 色點陣圖，如有必要，並顯示一則警告訊息，如果映像已轉換。 如果您使用的影像超過 16 個色彩 （使用外部編輯器編輯映像） 時，應用程式可能會如預期般運作。  
  
 工具列按鈕會模擬預設按鈕。 不過，工具列按鈕也可以模擬核取方塊按鈕或選項按鈕。 核取方塊按鈕狀態有三種： 核取、 已清除，及不定。 選項按鈕有兩個狀態： 選取和清除。  
  
 若要設定個別的按鈕或分隔符號的樣式不指向陣列，呼叫[GetButtonStyle](#getbuttonstyle) ，擷取樣式，然後再呼叫[SetButtonStyle](#setbuttonstyle)而不是`SetButtons`。 `SetButtonStyle`當您想要在執行階段變更按鈕的樣式，則是最有用。  
  
 若要指派要顯示在按鈕上的文字，請呼叫[GetButtonText](#getbuttontext)來擷取文字，會出現在 [] 按鈕，然後再呼叫[SetButtonText](#setbuttontext)設定文字。  
  
 若要建立核取方塊按鈕，將它指派樣式**TBBS_CHECKBOX**或使用`CCmdUI`物件的`SetCheck`成員函式中的`ON_UPDATE_COMMAND_UI`處理常式。 呼叫`SetCheck`按鈕將變為核取方塊按鈕。 傳遞`SetCheck`引數 0 已核取，或 2 的未選取，1 為不定。  
  
 若要建立選項按鈕，請呼叫[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的[SetRadio](../../mfc/reference/ccmdui-class.md#setradio)成員函式，從`ON_UPDATE_COMMAND_UI`處理常式。 傳遞`SetRadio`未核取或為非零，檢查的引數 0。 為了提供選項群組互斥的行為，您必須擁有`ON_UPDATE_COMMAND_UI`所有的按鈕群組中的處理常式。  
  
 如需有關使用`CToolBar`，請參閱文章[MFC 工具列實作](../../mfc/mfc-toolbar-implementation.md)和[技術提示 31： 控制列](../../mfc/tn031-control-bars.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CToolBar`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxext.h  
  
##  <a name="commandtoindex"></a>CToolBar::CommandToIndex  
 此成員函式傳回的第一個工具列按鈕，開始位置 0，其命令 ID 符合索引`nIDFind`。  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIDFind`  
 工具列按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 的索引按鈕，則為-1 沒有按鈕具有所指定的命令識別碼。  
  
##  <a name="create"></a>CToolBar::Create  
 此成員函式會建立 Windows 工具列 （子視窗），並將它與`CToolBar`物件。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,  
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>參數  
 `pParentWnd`  
 工具列的父視窗的指標。  
  
 `dwStyle`  
 工具列的樣式。 支援的其他工具列樣式如下：  
  
- `CBRS_TOP`控制列是在框架視窗的頂端。  
  
- `CBRS_BOTTOM`控制列是在框架視窗的底部。  
  
- `CBRS_NOALIGN`父代重新調整大小時未重新置放控制列。  
  
- `CBRS_TOOLTIPS`控制列會顯示工具提示。  
  
- **CBRS_SIZE_DYNAMIC**控制列是動態的。  
  
- **CBRS_SIZE_FIXED**固定的控制列。  
  
- **CBRS_FLOATING**浮動控制列。  
  
- `CBRS_FLYBY`狀態列會顯示按鈕的相關資訊。  
  
- **CBRS_HIDE_INPLACE**控制列不會顯示給使用者。  
  
 `nID`  
 工具列的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 它也可以設定工具列高度設為預設值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]  
  
##  <a name="createex"></a>CToolBar::CreateEx  
 呼叫此函式可建立 Windows 工具列 （子視窗） 並與`CToolBar`物件。  
  
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
 `pParentWnd`  
 工具列的父視窗的指標。  
  
 `dwCtrlStyle`  
 建立內嵌的其他樣式[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)物件。 根據預設，這個值設為**TBSTYLE_FLAT**。 Toolbar 樣式的完整清單，請參閱`dwStyle`。  
  
 `dwStyle`  
 工具列的樣式。 請參閱[工具列控制項和按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb760439)Windows SDK 中針對適當的樣式清單。  
  
 *rcBorders*  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md)工具列視窗框線的寬度定義的物件。 預設值，進而導致無邊界工具列視窗會將這些框線設 0,0,0,0。  
  
 `nID`  
 工具列的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 它也可以設定工具列高度設為預設值。  
  
 使用`CreateEx`，而不是[建立](#create)，當特定樣式必須要建立內嵌的工具列控制項時出現。 例如，設定`dwCtrlStyle`至**TBSTYLE_FLAT &#124;TBSTYLE_TRANSPARENT**來建立類似 Internet Explorer 4 工具列的工具列。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]  
  
##  <a name="ctoolbar"></a>CToolBar::CToolBar  
 此成員函式會建構`CToolBar`物件，並設定預設大小。  
  
```  
CToolBar();
```  
  
### <a name="remarks"></a>備註  
 呼叫[建立](#create)成員函式來建立 [工具列] 視窗。  
  
##  <a name="getbuttoninfo"></a>CToolBar::GetButtonInfo  
 此成員函式會擷取控制項 ID、 樣式和工具列按鈕或分隔符號所指定的位置的映像索引*nIndex。*  
  
```  
void GetButtonInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& iImage) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 工具列按鈕或分隔符號是擷取其資訊的索引。  
  
 `nID`  
 若要參考**UINT**設定按鈕的命令 id。  
  
 `nStyle`  
 若要參考**UINT**設按鈕的樣式。  
  
 `iImage`  
 按鈕的影像點陣圖內索引設為整數的參考。  
  
### <a name="remarks"></a>備註  
 這些值會指派給所參考的變數`nID`， `nStyle`，和`iImage`。 映像索引是包含所有工具列按鈕的影像點陣圖內影像的位置。 第一個影像都是在位置 0。  
  
 如果`nIndex`指定分隔符號，`iImage`設分隔符號寬度的像素。  
  
##  <a name="getbuttonstyle"></a>CToolBar::GetButtonStyle  
 呼叫此成員函式可擷取按鈕或工具列上的分隔符號的樣式。  
  
```  
UINT GetButtonStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取的工具列按鈕或分隔符號的樣式索引。  
  
### <a name="return-value"></a>傳回值  
 按鈕或所指定的分隔符號的樣式`nIndex`。  
  
### <a name="remarks"></a>備註  
 按鈕的樣式會判斷按鈕的顯示方式，以及它如何回應使用者輸入。 請參閱[SetButtonStyle](#setbuttonstyle)按鈕樣式的範例。  
  
##  <a name="getbuttontext"></a>CToolBar::GetButtonText  
 呼叫此成員函式可擷取按鈕顯示的文字。  
  
```  
CString GetButtonText(int nIndex) const;  
  
void GetButtonText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取之文字的索引。  
  
 `rString`  
 若要參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)會包含要擷取文字的物件。  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含按鈕的文字。  
  
### <a name="remarks"></a>備註  
 這個成員的第二個表單函式的填滿`CString`具有字串文字物件。  
  
##  <a name="getitemid"></a>CToolBar::GetItemID  
 此成員函式傳回的命令識別碼會以按鈕或所指定的分隔符號`nIndex`。  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 ID 是要擷取之項目的索引。  
  
### <a name="return-value"></a>傳回值  
 命令 ID 的按鈕或所指定的分隔符號`nIndex`。  
  
### <a name="remarks"></a>備註  
 分隔符號傳回**ID_SEPARATOR**。  
  
##  <a name="getitemrect"></a>CToolBar::GetItemRect  
 此成員函式會填滿`RECT`其位址包含在結構`lpRect`按鈕或分隔符號所指定的座標`nIndex`。  
  
```  
virtual void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取的項目的索引 （按鈕或分隔符號） 的矩形座標。  
  
 `lpRect`  
 位址[RECT](../../mfc/reference/rect-structure1.md)結構將會包含項目的座標。  
  
### <a name="remarks"></a>備註  
 座標是相對於工具列的左上角像素為單位。  
  
 使用`GetItemRect`若要取得的分隔符號，您想要取代下拉式方塊或其他控制項的座標。  
  
### <a name="example"></a>範例  
  請參閱範例的[CToolBar::SetSizes](#setsizes)。  
  
##  <a name="gettoolbarctrl"></a>CToolBar::GetToolBarCtrl  
 此成員函式可讓您直接存取基礎的通用控制項。  
  
```  
CToolBarCtrl& GetToolBarCtrl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 對 `CToolBarCtrl` 物件的參考。  
  
### <a name="remarks"></a>備註  
 使用`GetToolBarCtrl`充分利用功能的 Windows 工具列通用控制項，並利用支援[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)提供工具列自訂。  
  
 如需使用通用控制項的詳細資訊，請參閱文章[控制項](../../mfc/controls-mfc.md)和[通用控制項](http://msdn.microsoft.com/library/windows/desktop/bb775493)Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]  
  
##  <a name="loadbitmap"></a>CToolBar::LoadBitmap  
 呼叫此成員函式，以載入所指定的點陣圖`lpszResourceName`或`nIDResource`。  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>參數  
 `lpszResourceName`  
 要載入點陣圖的資源名稱的指標。  
  
 `nIDResource`  
 點陣圖的資源識別碼載入。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 點陣圖應包含一個影像的每個工具列按鈕。 如果映像不標準大小 （16 個像素寬和高 15 像素） 的呼叫[SetSizes](#setsizes)設定按鈕大小和其映像。  
  
> [!WARNING]
> `CToolBar`支援最多 16 個色彩的點陣圖。 當您將映像載入工具列編輯器時，Visual Studio 會自動將影像轉換為 16 色點陣圖，如有必要，並顯示一則警告訊息，如果映像已轉換。 如果您使用的影像超過 16 個色彩 （使用外部編輯器編輯映像） 時，應用程式可能會如預期般運作。  
  
##  <a name="loadtoolbar"></a>CToolBar::LoadToolBar  
 呼叫此成員函式，以載入所指定的工具列`lpszResourceName`或`nIDResource`。  
  
```  
BOOL LoadToolBar(LPCTSTR lpszResourceName);  
BOOL LoadToolBar(UINT nIDResource);
```  
  
### <a name="parameters"></a>參數  
 `lpszResourceName`  
 要載入的工具列資源名稱的指標。  
  
 `nIDResource`  
 工具列的資源識別碼載入。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 請參閱[工具列編輯器](../../windows/toolbar-editor.md)中如需有關建立工具列資源。  
  
### <a name="example"></a>範例  
  請參閱範例的[CToolBar::CreateEx](#createex)。  
  
##  <a name="setbitmap"></a>CToolBar::SetBitmap  
 呼叫此成員函式，可以設定工具列的點陣圖影像。  
  
```  
BOOL SetBitmap(HBITMAP hbmImageWell);
```  
  
### <a name="parameters"></a>參數  
 *hbmImageWell*  
 與工具列相關聯的點陣圖影像的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 例如，呼叫`SetBitmap`變更點陣圖影像之後使用者採取動作的文件，以變更按鈕的動作。  
  
##  <a name="setbuttoninfo"></a>CToolBar::SetButtonInfo  
 呼叫此成員函式設定按鈕的命令 ID、 樣式和映像數目。  
  
```  
void SetButtonInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int iImage);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 按鈕或設定資訊的分隔符號的以零為起始的索引。  
  
 `nID`  
 設定按鈕的命令 ID 的值。  
  
 `nStyle`  
 將新的按鈕樣式。 支援下列按鈕樣式：  
  
- **TBBS_BUTTON**標準按鈕 （預設值）  
  
- **TBBS_SEPARATOR**分隔符號  
  
- **TBBS_CHECKBOX**自動核取方塊按鈕  
  
- **TBBS_GROUP**標記的按鈕群組的開頭  
  
- **TBBS_CHECKGROUP**標示的核取方塊按鈕群組開始  
  
- **TBBS_DROPDOWN**建立下拉式選單按鈕。  
  
- **TBBS_AUTOSIZE**按鈕的寬度會以按鈕的文字，而非影像的大小計算。  
  
- **TBBS_NOPREFIX**按鈕的文字不會與其相關聯的對應前置詞。  
  
 `iImage`  
 按鈕的影像點陣圖內的新索引。  
  
### <a name="remarks"></a>備註  
 分隔符號，其具有樣式**TBBS_SEPARATOR**，此函式像素為單位的值儲存在設定的分隔符號寬度`iImage`。  
  
> [!NOTE]
>  您也可以設定使用的按鈕狀態`nStyle`參數; 不過，因為按鈕狀態受到[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)任何處理常式中，狀態使用設定`SetButtonInfo`將會遺失在下次閒置處理程序。 請參閱[如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)和[TN031： 控制列](../../mfc/tn031-control-bars.md)如需詳細資訊。  
  
 點陣圖影像和按鈕上的資訊，請參閱[CToolBar](../../mfc/reference/ctoolbar-class.md)概觀和[CToolBar::LoadBitmap](#loadbitmap)。  
  
##  <a name="setbuttons"></a>CToolBar::SetButtons  
 此成員函式會將每個工具列按鈕的命令 ID 設定為陣列的對應項目所指定的值`lpIDArray`。  
  
```  
BOOL SetButtons(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>參數  
 `lpIDArray`  
 命令 Id 的陣列指標。 它可以是**NULL**配置空的按鈕。  
  
 `nIDCount`  
 所指陣列中的項目數`lpIDArray`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果陣列的項目值**ID_SEPARATOR**，分隔符號會在對應工具列的位置中建立。 此函式也會將每個按鈕樣式設定為**TBBS_BUTTON**和每個分隔符號樣式**TBBS_SEPARATOR**，並將映像索引指派給每個按鈕。 映像索引指定按鈕的影像點陣圖內的位置。  
  
 您不需要分隔符號，點陣圖中的帳戶，因為此函式不會指派分隔符號的影像索引。 如果工具列有按鈕在位置 0，1 和 3 和分隔符號，以在位置 2，在點陣圖中的位置 0、 1 和 2 的映像會指派給按鈕位置 0、 1 和 3，分別。  
  
 如果`lpIDArray`是**NULL**，此函式所指定項目數的配置空間`nIDCount`。 使用[SetButtonInfo](#setbuttoninfo)來設定每個項目的屬性。  
  
##  <a name="setbuttonstyle"></a>CToolBar::SetButtonStyle  
 呼叫此成員函式設定樣式的按鈕或分隔符號，或將按鈕分組。  
  
```  
void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 按鈕或分隔符號設定為其資訊的索引。  
  
 `nStyle`  
 將按鈕樣式。 支援下列按鈕樣式：  
  
- **TBBS_BUTTON**標準按鈕 （預設值）  
  
- **TBBS_SEPARATOR**分隔符號  
  
- **TBBS_CHECKBOX**自動核取方塊按鈕  
  
- **TBBS_GROUP**標記的按鈕群組的開頭  
  
- **TBBS_CHECKGROUP**標示的核取方塊按鈕群組開始  
  
- **TBBS_DROPDOWN**建立下拉式按鈕  
  
- **TBBS_AUTOSIZE**按鈕的寬度會以按鈕的文字，而非影像的大小計算  
  
- **TBBS_NOPREFIX**按鈕的文字不會與其相關聯的對應前置詞  
  
### <a name="remarks"></a>備註  
 按鈕的樣式會判斷按鈕的顯示方式，以及它如何回應使用者輸入。  
  
 然後再呼叫`SetButtonStyle`，呼叫[GetButtonStyle](#getbuttonstyle)成員函式來擷取按鈕或分隔符號的樣式。  
  
> [!NOTE]
>  您也可以設定使用的按鈕狀態`nStyle`參數; 不過，因為按鈕狀態受到[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)任何處理常式中，狀態使用設定`SetButtonStyle`將會遺失在下次閒置處理程序。 請參閱[如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)和[TN031： 控制列](../../mfc/tn031-control-bars.md)如需詳細資訊。  
  
##  <a name="setbuttontext"></a>CToolBar::SetButtonText  
 呼叫此函式可設定 5d; 按鈕的文字。  
  
```  
BOOL SetButtonText(
    int nIndex,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 設定為其文字的按鈕索引。  
  
 `lpszText`  
 指向要在設定按鈕的文字。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例的[CToolBar::GetToolBarCtrl](#gettoolbarctrl)。  
  
##  <a name="setheight"></a>CToolBar::SetHeight  
 此成員函式的值，以像素中指定設定工具列的高度`cyHeight`。  
  
```  
void SetHeight(int cyHeight);
```  
  
### <a name="parameters"></a>參數  
 `cyHeight`  
 像素為單位，工具列的高度。  
  
### <a name="remarks"></a>備註  
 在呼叫[SetSizes](#setsizes)，用於此成員函式覆寫 [標準] 工具列的高度。 如果高度太小，則按鈕會裁剪底部。  
  
 如果未呼叫此函式，架構會使用按鈕的大小來判斷工具列的高度。  
  
##  <a name="setsizes"></a>CToolBar::SetSizes  
 呼叫此成員函式設定工具列的按鈕的大小，單位為像素中指定*sizeButton*。  
  
```  
void SetSizes(
    SIZE sizeButton,  
    SIZE sizeImage);
```  
  
### <a name="parameters"></a>參數  
 *sizeButton*  
 單位為像素的每個按鈕的大小。  
  
 `sizeImage`  
 每個映像素為單位的大小。  
  
### <a name="remarks"></a>備註  
 `sizeImage`參數必須包含在工具列的點陣圖影像像素為單位的大小。 中的維度*sizeButton*必須足以儲存映像加上 7 個像素額外的寬度和高度額外 6 個像素。 此函式也會設定成按鈕的工具列高度。  
  
 呼叫此成員函式只會針對未遵循工具列*軟體設計的 Windows 介面指導方針*按鈕和映像大小的建議。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CTRLBARS](../../visual-cpp-samples.md)   
 [MFC 範例 DLGCBR32](../../visual-cpp-samples.md)   
 [MFC 範例 DOCKTOOL](../../visual-cpp-samples.md)   
 [CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl 類別](../../mfc/reference/ctoolbarctrl-class.md)   
 [CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)
