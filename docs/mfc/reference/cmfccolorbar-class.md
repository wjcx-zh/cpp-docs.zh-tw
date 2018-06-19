---
title: CMFCColorBar 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorBar
- AFXCOLORBAR/CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::ContextToSize
- AFXCOLORBAR/CMFCColorBar::CreateControl
- AFXCOLORBAR/CMFCColorBar::Create
- AFXCOLORBAR/CMFCColorBar::EnableAutomaticButton
- AFXCOLORBAR/CMFCColorBar::EnableOtherButton
- AFXCOLORBAR/CMFCColorBar::GetColor
- AFXCOLORBAR/CMFCColorBar::GetCommandID
- AFXCOLORBAR/CMFCColorBar::GetHighlightedColor
- AFXCOLORBAR/CMFCColorBar::GetHorzMargin
- AFXCOLORBAR/CMFCColorBar::GetVertMargin
- AFXCOLORBAR/CMFCColorBar::IsTearOff
- AFXCOLORBAR/CMFCColorBar::SetColor
- AFXCOLORBAR/CMFCColorBar::SetColorName
- AFXCOLORBAR/CMFCColorBar::SetCommandID
- AFXCOLORBAR/CMFCColorBar::SetDocumentColors
- AFXCOLORBAR/CMFCColorBar::SetHorzMargin
- AFXCOLORBAR/CMFCColorBar::SetVertMargin
- AFXCOLORBAR/CMFCColorBar::AdjustLocations
- AFXCOLORBAR/CMFCColorBar::AllowChangeTextLabels
- AFXCOLORBAR/CMFCColorBar::AllowShowOnList
- AFXCOLORBAR/CMFCColorBar::CalcSize
- AFXCOLORBAR/CMFCColorBar::CreatePalette
- AFXCOLORBAR/CMFCColorBar::GetColorGridSize
- AFXCOLORBAR/CMFCColorBar::GetExtraHeight
- AFXCOLORBAR/CMFCColorBar::InitColors
- AFXCOLORBAR/CMFCColorBar::OnKey
- AFXCOLORBAR/CMFCColorBar::OnSendCommand
- AFXCOLORBAR/CMFCColorBar::OnUpdateCmdUI
- AFXCOLORBAR/CMFCColorBar::OpenColorDialog
- AFXCOLORBAR/CMFCColorBar::Rebuild
- AFXCOLORBAR/CMFCColorBar::SelectPalette
- AFXCOLORBAR/CMFCColorBar::SetPropList
- AFXCOLORBAR/CMFCColorBar::ShowCommandMessageString
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorBar [MFC], CMFCColorBar
- CMFCColorBar [MFC], ContextToSize
- CMFCColorBar [MFC], CreateControl
- CMFCColorBar [MFC], Create
- CMFCColorBar [MFC], EnableAutomaticButton
- CMFCColorBar [MFC], EnableOtherButton
- CMFCColorBar [MFC], GetColor
- CMFCColorBar [MFC], GetCommandID
- CMFCColorBar [MFC], GetHighlightedColor
- CMFCColorBar [MFC], GetHorzMargin
- CMFCColorBar [MFC], GetVertMargin
- CMFCColorBar [MFC], IsTearOff
- CMFCColorBar [MFC], SetColor
- CMFCColorBar [MFC], SetColorName
- CMFCColorBar [MFC], SetCommandID
- CMFCColorBar [MFC], SetDocumentColors
- CMFCColorBar [MFC], SetHorzMargin
- CMFCColorBar [MFC], SetVertMargin
- CMFCColorBar [MFC], AdjustLocations
- CMFCColorBar [MFC], AllowChangeTextLabels
- CMFCColorBar [MFC], AllowShowOnList
- CMFCColorBar [MFC], CalcSize
- CMFCColorBar [MFC], CreatePalette
- CMFCColorBar [MFC], GetColorGridSize
- CMFCColorBar [MFC], GetExtraHeight
- CMFCColorBar [MFC], InitColors
- CMFCColorBar [MFC], OnKey
- CMFCColorBar [MFC], OnSendCommand
- CMFCColorBar [MFC], OnUpdateCmdUI
- CMFCColorBar [MFC], OpenColorDialog
- CMFCColorBar [MFC], Rebuild
- CMFCColorBar [MFC], SelectPalette
- CMFCColorBar [MFC], SetPropList
- CMFCColorBar [MFC], ShowCommandMessageString
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2083c26943768afff4b3b20a2ba95c709648dd50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376134"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar 類別
`CMFCColorBar`類別表示可以在文件或應用程式中選取色彩的停駐控制列。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCColorBar : public CMFCPopupMenuBar  
```  
  
## <a name="members"></a>成員  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|建構 `CMFCColorBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCColorBar::ContextToSize](#contexttosize)|計算的垂直和水平的邊界，不需要包含在色軸的控制項上的按鈕，然後再調整這些按鈕的位置。|  
|[CMFCColorBar::CreateControl](#createcontrol)|建立色軸的控制項視窗中，將它附加至`CMFCColorBar`物件，並調整大小，以包含色彩指定的調色盤控制。|  
|[CMFCColorBar::Create](#create)|建立色軸控制項視窗，並將它附加至`CMFCColorBar`物件。|  
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|顯示或隱藏 [自動] 按鈕。|  
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|啟用或停用的對話方塊，讓使用者選取更多的色彩顯示。|  
|[CMFCColorBar::GetColor](#getcolor)|擷取目前選取的色彩。|  
|[CMFCColorBar::GetCommandID](#getcommandid)|擷取目前的色彩列控制項的命令識別碼。|  
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|擷取表示的色彩按鈕具有焦點，色彩也就是說，按鈕是*熱*。|  
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|擷取的水平的邊界，也就是左邊或右邊的色彩資料格和用戶端區域的界限之間的間距。|  
|[CMFCColorBar::GetVertMargin](#getvertmargin)|擷取垂直邊界，也就是頂端或底部色彩的儲存格和用戶端區域的界限之間的間距。|  
|[CMFCColorBar::IsTearOff](#istearoff)|指出是否可停駐在目前的色軸。|  
|[CMFCColorBar::SetColor](#setcolor)|設定目前選取的色彩。|  
|[CMFCColorBar::SetColorName](#setcolorname)|設定指定的色彩的新名稱。|  
|[CMFCColorBar::SetCommandID](#setcommandid)|設定色軸控制項的新命令識別碼。|  
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|目前的文件中設定所使用的色彩清單。|  
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|設定水平的邊界，也就是左邊或右邊的色彩資料格和用戶端區域的界限之間的間距。|  
|[CMFCColorBar::SetVertMargin](#setvertmargin)|設定垂直邊界，也就是 top 或 bottom 色彩資料格，而用戶端區域的界限之間的間距。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCColorBar::AdjustLocations](#adjustlocations)|調整色彩按鈕，在色軸的控制項上的位置。|  
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|指出是否可以變更色彩按鈕的文字標籤。|  
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|指出是否色軸控制項物件可以出現在工具列清單的自訂程序期間。|  
|[CMFCColorBar::CalcSize](#calcsize)|由架構呼叫配置計算程序的一部分。|  
|[CMFCColorBar::CreatePalette](#createpalette)|初始化具有指定色彩的陣列中的色彩調色盤。|  
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|計算的資料列和資料行在方格中的色彩列控制項的數目。|  
|[CMFCColorBar::GetExtraHeight](#getextraheight)|計算目前色軸顯示其他使用者介面項目，例如所需的其他高度**其他**按鈕、 文件色彩等等。|  
|[CMFCColorBar::InitColors](#initcolors)|初始化與色彩指定的調色盤或系統預設調色盤中的色彩的陣列。|  
|[CMFCColorBar::OnKey](#onkey)|當使用者按下鍵盤 按鈕時由架構呼叫。|  
|[CMFCColorBar::OnSendCommand](#onsendcommand)|若要關閉的快顯控制項階層架構呼叫。|  
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|由架構呼叫以啟用或停用的色彩列控制項的使用者介面項目，顯示項目之前。|  
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|開啟 [色彩] 對話方塊。|  
|[CMFCColorBar::Rebuild](#rebuild)|完全重新繪製色軸控制項。|  
|[CMFCColorBar::SelectPalette](#selectpalette)|指定的裝置內容的邏輯色板設為目前的色彩列控制項的父代按鈕的調色盤。|  
|[CMFCColorBar::SetPropList](#setproplist)|設定`m_pWndPropList`受保護的屬性方格控制項的指定指標的資料成員。|  
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|要求框架視窗擁有色軸控制項來更新 [狀態] 列中的訊息列。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|`m_bInternal`|布林值欄位會決定是否處理滑鼠事件。 這個欄位時，通常處理滑鼠事件`TRUE`和自訂模式是`FALSE`。|  
|`m_bIsEnabled`|布林值，指出控制項是否已啟用。|  
|`m_bIsTearOff`|布林值，指出是否在色彩列控制項支援停駐。|  
|`m_BoxSize`|A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，指定在色軸方格資料格的大小。|  
|`m_bShowDocColorsWhenDocked`|布林值，指出是否要在色軸停駐時顯示文件色彩。 如需詳細資訊，請參閱[CMFCColorBar::SetDocumentColors](#setdocumentcolors)。|  
|`m_bStdColorDlg`|布林值，指出是否要顯示標準系統色彩 對話方塊或[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  對話方塊。 如需詳細資訊，請參閱[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)會儲存目前的自動色彩。 如需詳細資訊，請參閱[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|  
|`m_ColorNames`|[CMap](../../mfc/reference/cmap-class.md)其名稱與色彩的 RGB 集合產生關聯的物件。|  
|`m_colors`|A [CArray](../../mfc/reference/carray-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)包含色軸控制項中顯示的色彩的值。|  
|`m_ColorSelected`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，這是使用者已從色軸控制項中目前選取的色彩。|  
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)包含文件中目前使用的色彩的值。|  
|`m_nCommandID`|不帶正負號的整數的色彩按鈕的命令識別碼。|  
|`m_nHorzMargin`|為格線中的色彩的色彩按鈕之間的水平邊界的整數。|  
|`m_nHorzOffset`|為中心的 [色彩] 按鈕的水平位移的整數。 這個值是大按鈕會顯示文字或影像色彩以外。|  
|`m_nNumColumns`|整數，是色彩的色彩列控制項方格中的資料行的數目。|  
|`m_nNumColumnsVert`|整數，是垂直方向色彩的方格中的資料行的數目。|  
|`m_nNumRowsHorz`|整數，是色彩的水平方向的方格中的資料行的數目。|  
|`m_nRowHeight`|整數，是色彩的方格中的色彩按鈕的資料列的高度。|  
|`m_nVertMargin`|整數，為格線中的色彩的色彩按鈕之間的垂直邊界。|  
|`m_nVertOffset`|為中心的 [色彩] 按鈕的垂直位移的整數。 這個值是大按鈕會顯示文字或影像色彩以外。|  
|`m_Palette`|A [CPalette](../../mfc/reference/cpalette-class.md)色軸控制項中使用的色彩。|  
|`m_pParentBtn`|指標[CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)目前按鈕的父物件。 如果 [色彩] 按鈕的工具列上的控制項階層架構或中色彩屬性方格控制項，此值十分重要。|  
|`m_pParentRibbonBtn`|指標[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)功能區上，且位於目前按鈕的父代按鈕物件。 如果 [色彩] 按鈕的工具列上的控制項階層架構或中色彩屬性方格控制項，此值十分重要。|  
|`m_pWndPropList`|指標[CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)物件。|  
|`m_strAutoColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md)即會顯示在文字**自動** 按鈕。 如需詳細資訊，請參閱[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)。|  
|`m_strDocColors`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md)也就是文件色彩按鈕顯示的文字。 如需詳細資訊，請參閱[CMFCColorBar::SetDocumentColors](#setdocumentcolors)。|  
|`m_strOtherColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md)即會顯示在文字*其他* 按鈕。 如需詳細資訊，請參閱[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|  
  
## <a name="remarks"></a>備註  
 通常，您不會建立`CMFCColorBar`直接物件。 相反地， [CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md)（用於功能表和工具列中） 或[CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)建立`CMFCColorBar`物件。  
  
 `CMFCColorBar`類別會提供下列功能：  
  
-   自動調整文件色彩的清單。  
  
-   儲存並還原其狀態，以及文件狀態。  
  
-   管理 「 自動 」 按鈕。  
  
-   使用[CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)控制項選取自訂色彩。  
  
-   支援 「 分割 」 狀態 (如果它由使用[CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md))。  
  
 若要納入`CMFCColorBar`到您的應用程式的功能：  
  
1.  建立標準功能表按鈕，並將其指派的識別碼，例如 ID_CHAR_COLOR。  
  
2.  在框架視窗類別，覆寫[CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu)方法，並取代一般功能表按鈕與[CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md)物件 (藉由呼叫[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton))。  
  
3.  設定所有的樣式和啟用或停用的功能`CMFCColorBar`物件期間[CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md)建立。 `CMFCColorMenuButton`物件以動態方式建立`CMFCColorBar`之後這個架構會呼叫物件`CreatePopupMenu`方法。  
  
 當使用者按一下色軸的控制項按鈕時，架構會使用`ON_COMMAND`巨集，以通知色軸控制項的父代。 巨集，在命令 ID 參數會是您在步驟 1 (在此範例中 ID_CHAR_COLOR) 色軸控制項按鈕所指定的值。 如需詳細資訊，請參閱[CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md)， [CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)， [CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)， [CFrameWndEx 類別](../../mfc/reference/cframewndex-class.md)，和[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用中的各種方法來設定色軸`CMFCColorBar`類別。 方法可以設定水平和垂直邊界、 啟用 [其他] 按鈕，建立色軸的控制項視窗中，和設定目前選取的色彩。 這個範例是屬於[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)  
  
 [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcolorbar.h  
  
##  <a name="adjustlocations"></a>  CMFCColorBar::AdjustLocations  
 調整色彩按鈕，在色軸的控制項上的位置。  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>備註  
 由架構期間呼叫這個方法`WM_SIZE`訊息處理。  
  
##  <a name="allowchangetextlabels"></a>  CMFCColorBar::AllowChangeTextLabels  
 指出是否可以變更色彩按鈕的文字標籤。  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一定是 `FALSE`。  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法一律會傳回`FALSE`，無法修改這表示文字標籤。 覆寫這個方法，以啟用修改文字標籤。  
  
##  <a name="allowshowonlist"></a>  CMFCColorBar::AllowShowOnList  
 指出是否色軸控制項物件可以出現在工具列清單的自訂程序期間。  
  
```  
virtual BOOL AllowShowOnList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一定是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法一律會傳回`TRUE`，這表示架構的自訂程序期間顯示色軸的控制項。 覆寫這個方法以實作不同的行為。  
  
##  <a name="calcsize"></a>  CMFCColorBar::CalcSize  
 由架構呼叫配置計算程序的一部分。  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bVertDock`  
 `TRUE` 若要指定色彩列控制項停駐垂直;`FALSE`指定色彩列控制項停駐水平。  
  
### <a name="return-value"></a>傳回值  
 一維陣列中的色彩列控制項的色彩按鈕的大小。  
  
##  <a name="cmfccolorbar"></a>  CMFCColorBar::CMFCColorBar  
 建構 `CMFCColorBar` 物件。  
  
```  
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors,  
    CList<COLORREF,COLORREF>& lstDocColors,  
    int nColumns,  
    int nRowsDockHorz,  
    int nColDockVert,  
    COLORREF colorAutomatic,  
    UINT nCommandID,  
    CMFCColorButton* pParentBtn);

 
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors,  
    CList<COLORREF,COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic,  
    UINT nCommandID,  
    CMFCRibbonColorButton* pParentRibbonBtn);

 
CMFCColorBar(
    CMFCColorBar& src,  
    UINT uiCommandID);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `colors`  
 架構會在色軸的控制項顯示的色彩的陣列。  
  
 [輸入] `color`  
 一開始選取之色彩。  
  
 [輸入] `lpszAutoColor`  
 文字標籤*自動*（預設值） 的色彩按鈕，或`NULL`。  
  
 自動按鈕的標準標籤是**自動**。  
  
 [輸入] `lpszOtherColor`  
 文字標籤*其他*按鈕則顯示更多色彩選擇，或`NULL`。  
  
 其他按鈕的標準標籤是**更多色彩...**.  
  
 [輸入] `lpszDocColors`  
 文件色彩按鈕文字標籤。 文件色彩調色盤會列出所有文件目前使用的色彩。  
  
 [輸入] `lstDocColors`  
 文件目前使用的色彩清單。  
  
 [輸入] `nColumns`  
 具有色彩陣列的資料行數目。  
  
 [輸入] `nRowsDockHorz`  
 色軸具有水平停駐時的資料列數目。  
  
 [輸入] `nColDockVert`  
 色軸具有為垂直的停駐時的資料行數目。  
  
 [輸入] `colorAutomatic`  
 當您按一下 [自動] 按鈕時，適用於架構的預設色彩。  
  
 [輸入] `nCommandID`  
 色軸控制項命令識別碼。  
  
 [輸入] `pParentBtn`  
 父代按鈕指標。  
  
 [輸入] `src`  
 現有`CMFCColorBar`物件複製到新`CMFCColorBar`物件。  
  
 [輸入] `uiCommandID`  
 命令 ID。  
  
##  <a name="contexttosize"></a>  CMFCColorBar::ContextToSize  
 計算的垂直和水平的邊界，才能包含在色軸控制項上的按鈕和調整這些按鈕的位置。  
  
```  
void ContextToSize(
    BOOL bSquareButtons = TRUE,   
    BOOL bCenterButtons = TRUE);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `bSquareButtons`|`TRUE` 指定在色軸的控制項上按鈕的形狀是正方形。否則， `FALSE`。 預設值是 `TRUE`。|  
|[輸入] `bCenterButtons`|`TRUE` 若要指定，色軸的控制項按鈕表面的內容會置中。否則， `FALSE`。 預設值是 `TRUE`。|  
  
### <a name="remarks"></a>備註  
  
##  <a name="create"></a>  CMFCColorBar::Create  
 建立色軸控制項視窗，並將它附加至`CMFCColorBar`物件。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle,  
    UINT nID,  
    CPalette* pPalette=NULL,  
    int nColumns=0,  
    int nRowsDockHorz=0,  
    int nColDockVert=0);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pParentWnd`  
 父視窗的指標。  
  
 [輸入] `dwStyle`  
 位元組合 (OR)[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。  
  
 [輸入] `nID`  
 命令 ID。  
  
 [輸入] `pPalette`  
 指標的色彩調色盤。 預設值為 `NULL`。  
  
 [輸入] `nColumns`  
 色軸控制項中的資料行數目。 預設值為 0。  
  
 [輸入] `nRowsDockHorz`  
 當水平停駐色軸控制項中的資料列數目。 預設值為 0。  
  
 [輸入] `nColDockVert`  
 為垂直的停駐時在色軸控制項中的資料行數目。 預設值為 0。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 若要建構`CMFCColorBar`物件，呼叫類別建構函式，則這個方法。 `Create`方法會建立 Windows 控制項，並初始化色彩的清單。  
  
##  <a name="createcontrol"></a>  CMFCColorBar::CreateControl  
 建立色軸的控制項視窗中，將它附加至`CMFCColorBar`物件，並調整大小，以包含色彩指定的調色盤控制 視窗。  
  
```  
virtual BOOL CreateControl(
    CWnd* pParentWnd,  
    const CRect& rect,  
    UINT nID,  
    int nColumns=-1,  
    CPalette* pPalette=NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pParentWnd`  
 父視窗的指標。 不能`NULL`。  
  
 [輸入] `rect`  
 指定要繪製色軸的控制項位置的周框。  
  
 [輸入] `nID`  
 控制項 id。  
  
 [輸入] `nColumns`  
 理想的色軸控制項中的資料行數目。 這個方法會修改該數字，符合指定的色彩調色盤。 預設值為-1，表示未指定這個參數。  
  
 [輸入] `pPalette`  
 指標的色彩調色盤或`NULL`。 如果這個參數是`NULL`，如同指定 20 的色彩，此方法會計算色軸控制項的大小。 預設值為 `NULL`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會使用`rect`， `nColumns`，和`pPalette`參數來計算適當數目或資料列和資料行在色軸控制項，然後呼叫[CMFCColorBar::Create](#create)方法。  
  
##  <a name="createpalette"></a>  CMFCColorBar::CreatePalette  
 初始化具有指定色彩的陣列中的色彩調色盤。  
  
```  
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,   
    CPalette& palette);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `arColors`|色彩的陣列。|  
|[輸入] `palette`|色的調色盤。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。  
  
##  <a name="enableautomaticbutton"></a>  CMFCColorBar::EnableAutomaticButton  
 顯示或隱藏 [自動] 按鈕。  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszLabel`  
 文字標籤*自動*（預設值） 的色彩按鈕，或`NULL`。  
  
 自動按鈕的標準標籤是**自動**。  
  
 [輸入] `colorAutomatic`  
 當您按一下 [自動] 按鈕時，適用於架構的預設色彩。  
  
 [輸入] `bEnable`  
 `TRUE` 若要啟用 [自動] 按鈕。`FALSE`停用 [自動] 按鈕。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 如果刪除自動按鈕的文字標籤`lpszLabel`參數是`NULL`或`bEnable`參數是`FALSE`。  
  
##  <a name="enableotherbutton"></a>  CMFCColorBar::EnableOtherButton  
 啟用或停用的對話方塊，讓使用者選取更多的色彩顯示。  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszLabel`  
 文字標籤*其他*按鈕則顯示更多色彩選擇，或`NULL`。  
  
 此按鈕的標準標籤是**更多色彩...**.  
  
 [輸入] `bAltColorDlg`  
 `TRUE` 若要顯示[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  對話方塊。`FALSE`以顯示標準[CColorDialog](../../mfc/reference/ccolordialog-class.md)  對話方塊。 預設值是 `TRUE`。  
  
 [輸入] `bEnable`  
 `TRUE` 若要啟用按鈕。`FALSE`來停用按鈕。 預設值是 `TRUE`。  
  
##  <a name="getcolor"></a>  CMFCColorBar::GetColor  
 擷取目前選取的色彩。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前選取的色彩。  
  
##  <a name="getcolorgridsize"></a>  CMFCColorBar::GetColorGridSize  
 計算的資料列和資料行在方格中的色彩列控制項的數目。  
  
```  
CSize GetColorGridSize(BOOL bVertDock) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `bVertDock`|`TRUE` 執行計算，以垂直方式停駐的色彩列控制項。否則，執行計算的水平停駐控制項。|  
  
### <a name="return-value"></a>傳回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，其`cx`元件包含的資料行，其數目`cy`元件包含的資料列數目。  
  
##  <a name="getcommandid"></a>  CMFCColorBar::GetCommandID  
 擷取目前的色彩列控制項的命令識別碼。  
  
```  
UINT GetCommandID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 命令 id。  
  
### <a name="remarks"></a>備註  
 當使用者選取新的色彩時，架構會以傳送的命令 ID`WM_COMMAND`訊息，通知的父代`CMFCColorBar`物件。  
  
##  <a name="getextraheight"></a>  CMFCColorBar::GetExtraHeight  
 計算目前色軸顯示其他使用者介面項目，例如所需的其他高度**其他**按鈕或文件的色彩。  
  
```  
int GetExtraHeight(int nNumColumns) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `nNumColumns`|如果色軸控制項包含文件色彩，在文件色彩的方格中顯示的資料行數目。 否則，這個值不在使用中。|  
  
### <a name="return-value"></a>傳回值  
 所需之計算額外高度。  
  
##  <a name="gethighlightedcolor"></a>  CMFCColorBar::GetHighlightedColor  
 擷取表示的色彩按鈕具有焦點，色彩也就是說，按鈕是*熱*。  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 RGB 值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gethorzmargin"></a>  CMFCColorBar::GetHorzMargin  
 擷取的水平的邊界，也就是左邊或右邊的色彩資料格和用戶端區域的界限之間的間距。  
  
```  
int GetHorzMargin();
```  
  
### <a name="return-value"></a>傳回值  
 水平的邊界。  
  
##  <a name="getvertmargin"></a>  CMFCColorBar::GetVertMargin  
 擷取垂直邊界，也就是頂端或底部色彩的儲存格和用戶端區域的界限之間的間距。  
  
```  
int GetVertMargin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 垂直的邊界。  
  
##  <a name="initcolors"></a>  CMFCColorBar::InitColors  
 初始化與色彩指定調色盤，或使用系統預設調色盤色彩的陣列。  
  
```  
static int InitColors(
    CPalette* pPalette,   
    CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `pPalette`|調色盤物件的指標或`NULL`。 如果這個參數是`NULL`，這個方法會使用預設調色盤的作業系統。|  
|[輸入] `arColors`|色彩的陣列。|  
  
### <a name="return-value"></a>傳回值  
 色彩的陣列中的元素數目。  
  
##  <a name="istearoff"></a>  CMFCColorBar::IsTearOff  
 指出是否可停駐在目前的色軸。  
  
```  
BOOL IsTearOff() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果目前的色彩列控制項是可停駐;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果可停駐色軸控制項，它可以損毀的控制列關閉並停駐在另一個位置。  
  
##  <a name="onkey"></a>  CMFCColorBar::OnKey  
 當使用者按下鍵盤 按鈕時由架構呼叫。  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nChar`  
 使用者按下按鍵虛擬按鍵碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果這個方法會處理指定的索引鍵。，否則， `FALSE`。  
  
##  <a name="onsendcommand"></a>  CMFCColorBar::OnSendCommand  
 若要關閉的快顯控制項階層架構呼叫。  
  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `pButton`|位於工具列的控制項的指標。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。  
  
##  <a name="onupdatecmdui"></a>  CMFCColorBar::OnUpdateCmdUI  
 由架構呼叫以啟用或停用的色彩列控制項的使用者介面項目，顯示項目之前。  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pTarget`  
 包含使用者介面項目，以更新的視窗指標。  
  
 [輸入] `bDisableIfNoHndler`  
 `TRUE` 若要停用的使用者介面項目，如果沒有處理常式中定義的訊息對應。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 當應用程式的使用者按一下使用者介面項目時，項目必須知道是否它應該顯示為已啟用或停用。 命令訊息的目標是提供這項資訊藉由實作`ON_UPDATE_COMMAND_UI`命令處理常式。 使用這個方法，以協助處理命令。 如需詳細資訊，請參閱[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)。  
  
##  <a name="opencolordialog"></a>  CMFCColorBar::OpenColorDialog  
 開啟 [色彩] 對話方塊。  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `colorDefault`  
 [色彩] 對話方塊開啟時，依預設會選取色彩。  
  
 [輸出] `colorRes`  
 使用者選取色彩。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果使用者選取色彩。，`FALSE`如果使用者已取消的色彩 對話方塊。  
  
### <a name="remarks"></a>備註  
  
##  <a name="rebuild"></a>  CMFCColorBar::Rebuild  
 完全重新繪製色軸控制項。  
  
```  
virtual void Rebuild();
```  
  
##  <a name="selectpalette"></a>  CMFCColorBar::SelectPalette  
 指定的裝置內容的邏輯色板設為目前的色彩列控制項的父代按鈕的調色盤。  
  
```  
CPalette* SelectPalette(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `pDC`|目前的色彩列控制項的父代按鈕的裝置內容的指標。|  
  
### <a name="return-value"></a>傳回值  
 取代為目前的色彩列控制項的父代按鈕的調色盤的調色盤的指標。  
  
##  <a name="setcolor"></a>  CMFCColorBar::SetColor  
 設定目前選取的色彩。  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `color`  
 RGB 色彩值。  
  
##  <a name="setcolorname"></a>  CMFCColorBar::SetColorName  
 設定指定的色彩的新名稱。  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `color`  
 色彩的 RGB 值。  
  
 [輸入] `strName`  
 指定的色彩的的新名稱。  
  
### <a name="remarks"></a>備註  
 這個方法會變更在所有指定的色彩名稱`CMFCColorBar`應用程式中的物件。  
  
##  <a name="setcommandid"></a>  CMFCColorBar::SetCommandID  
 設定色軸控制項的新命令識別碼。  
  
```  
void SetCommandID(UINT nCommandID);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nCommandID`  
 命令 id。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，若要修改的色彩列控制項的命令識別碼，並通知識別碼已變更之控制項的父視窗。  
  
##  <a name="setdocumentcolors"></a>  CMFCColorBar::SetDocumentColors  
 目前的文件中設定所使用的色彩清單。  
  
```  
void SetDocumentColors(
    LPCTSTR lpszCaption,  
    CList<COLORREF,COLORREF>& lstDocColors,  
    BOOL bShowWhenDocked=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszCaption`  
 未停駐色軸控制項時所顯示的標題。  
  
 [輸入] `lstDocColors`  
 取代目前的文件色彩的色彩清單。  
  
 [輸入] `bShowWhenDocked`  
 `TRUE` 若要顯示色軸控制項停駐; 文件色彩否則， `FALSE`。 預設值是 `FALSE`。  
  
### <a name="remarks"></a>備註  
 *文件色彩*是文件中目前使用的色彩。 架構會自動維護一份文件色彩，但是您可以使用這個方法來修改清單。  
  
##  <a name="sethorzmargin"></a>  CMFCColorBar::SetHorzMargin  
 設定水平的邊界，也就是左邊或右邊的色彩資料格和工作區的界限之間的間距。  
  
```  
void SetHorzMargin(int nHorzMargin);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nHorzMargin`  
 水平邊界，以像素為單位。  
  
### <a name="remarks"></a>備註  
 根據預設， [CMFCColorBar::CMFCColorBar](#cmfccolorbar)建構函式會將水平的邊界設定為 4 個像素。  
  
##  <a name="setproplist"></a>  CMFCColorBar::SetPropList  
 設定`m_pWndPropList`受保護的屬性方格控制項的指定指標的資料成員。  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[輸入] `pWndList`|屬性方格控制項物件的指標。|  
  
##  <a name="setvertmargin"></a>  CMFCColorBar::SetVertMargin  
 設定垂直邊界，也就是 top 或 bottom 色彩資料格，而用戶端區域的界限之間的間距。  
  
```  
void SetVertMargin(int nVertMargin);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nVertMargin`  
 垂直邊界，以像素為單位。  
  
### <a name="remarks"></a>備註  
 根據預設， [CMFCColorBar::CMFCColorBar](#cmfccolorbar)建構函式會將垂直的邊界設定為 4 個像素。  
  
##  <a name="showcommandmessagestring"></a>  CMFCColorBar::ShowCommandMessageString  
 要求框架視窗擁有色軸控制項來更新 [狀態] 列中的訊息列。  
  
```  
virtual void ShowCommandMessageString(UINT uiCmdId);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiCmdId`  
 命令 id。 （這個參數已忽略）。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送`WM_SETMESSAGESTRING`色軸控制項的擁有者的訊息。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
