---
title: "CMFCColorBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorBar class
- CMFCColorBar::m_ColorAutomatic data member
- CMFCColorBar::m_bInternal data member
- CMFCColorBar::m_bIsEnabled data member
- CMFCColorBar::m_nNumColumnsVert data member
- CMFCColorBar::m_nVertMargin data member
- CMFCColorBar::m_strDocColors data member
- CMFCColorBar::m_BoxSize data member
- CMFCColorBar::m_pParentBtn data member
- CMFCColorBar::m_bIsTearOff data member
- CMFCColorBar::m_nHorzOffset data member
- CMFCColorBar::m_pParentRibbonBtn data member
- CMFCColorBar::m_nNumRowsHorz data member
- CMFCColorBar::m_bStdColorDlg data member
- CMFCColorBar::m_strAutoColor data member
- CMFCColorBar::m_ColorNames data member
- CMFCColorBar::m_strOtherColor data member
- CMFCColorBar::m_lstDocColors data member
- CMFCColorBar::m_pWndPropList data member
- CMFCColorBar::m_ColorSelected data member
- CMFCColorBar::m_nCommandID data member
- CMFCColorBar::m_nHorzMargin data member
- CMFCColorBar::m_nRowHeight data member
- CMFCColorBar::m_Palette data member
- CMFCColorBar::m_colors data member
- CMFCColorBar::m_nVertOffset data member
- CMFCColorBar::m_nNumColumns data member
- CMFCColorBar::m_bShowDocColorsWhenDocked data member
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
caps.latest.revision: 35
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
ms.openlocfilehash: bf4d431a3f3237587dc9f86be91f11b9b5016fe2
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccolorbar-class"></a>CMFCColorBar 類別
`CMFCColorBar`類別表示可以在文件或應用程式中選取色彩的停駐控制列。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCColorBar : public CMFCPopupMenuBar  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|建構 `CMFCColorBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCColorBar::ContextToSize](#contexttosize)|計算的垂直和水平邊界，不需要包含色軸控制項上的按鈕，然後再調整這些按鈕的位置。|  
|[CMFCColorBar::CreateControl](#createcontrol)|建立的色軸控制項的視窗，將它附加`CMFCColorBar`物件，然後將控制項調整為包含指定的色彩調色盤。|  
|[CMFCColorBar::Create](#create)|建立的色軸的控制項視窗並將它附加`CMFCColorBar`物件。|  
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|顯示或隱藏 [自動] 按鈕。|  
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|啟用或停用的對話方塊，讓使用者選取更多的色彩顯示。|  
|[CMFCColorBar::GetColor](#getcolor)|擷取目前選取的色彩。|  
|[CMFCColorBar::GetCommandID](#getcommandid)|擷取目前的色軸控制項的命令 ID。|  
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|擷取表示的色彩按鈕具有焦點，色彩亦即，按鈕是*熱*。|  
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|擷取的水平的邊界，也就是左邊或右邊的色彩資料格和用戶端區域的界限之間的間距。|  
|[CMFCColorBar::GetVertMargin](#getvertmargin)|擷取垂直邊界，也就是頂端或底部色彩的儲存格和用戶端區域的界限之間的間距。|  
|[CMFCColorBar::IsTearOff](#istearoff)|指出是否可停駐在目前的色軸。|  
|[CMFCColorBar::SetColor](#setcolor)|設定目前選取的色彩。|  
|[CMFCColorBar::SetColorName](#setcolorname)|設定指定的色彩的新名稱。|  
|[CMFCColorBar::SetCommandID](#setcommandid)|設定色軸控制項的新命令識別碼。|  
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|設定目前文件所使用的色彩清單。|  
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|設定水平的邊界，也就是左邊或右邊的色彩資料格和用戶端區域的界限之間的間距。|  
|[CMFCColorBar::SetVertMargin](#setvertmargin)|設定垂直邊界，也就是頂端或底端色彩資料格，而用戶端區域的界限之間的間距。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCColorBar::AdjustLocations](#adjustlocations)|調整色彩按鈕，在色軸控制項的位置。|  
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|指出是否可以變更的色彩按鈕的文字標籤。|  
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|指出色軸控制項物件是否可以在自訂程序期間出現在工具列清單。|  
|[CMFCColorBar::CalcSize](#calcsize)|配置計算程序的一部分的架構所呼叫。|  
|[CMFCColorBar::CreatePalette](#createpalette)|初始化具有指定的色彩陣列中的色彩調色盤。|  
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|計算的資料列和資料行在方格中，色軸控制項的數目。|  
|[CMFCColorBar::GetExtraHeight](#getextraheight)|計算目前的色軸顯示其他的使用者介面項目，例如所需的其他高度**其他**按鈕、 文件色彩等等。|  
|[CMFCColorBar::InitColors](#initcolors)|初始化具有指定的調色盤中的系統預設調色盤色彩的色彩的陣列。|  
|[CMFCColorBar::OnKey](#onkey)|當使用者按下鍵盤 按鈕時，由架構呼叫。|  
|[CMFCColorBar::OnSendCommand](#onsendcommand)|若要關閉快顯控制項階層架構呼叫。|  
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|啟用或停用的色軸控制項的使用者介面項目，才能在顯示的項目架構呼叫。|  
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|開啟 [色彩] 對話方塊。|  
|[CMFCColorBar::Rebuild](#rebuild)|完全重新繪製色軸的控制項。|  
|[CMFCColorBar::SelectPalette](#selectpalette)|將指定的裝置內容的邏輯調色盤設定為目前的色彩列控制項的父代按鈕的調色盤。|  
|[CMFCColorBar::SetPropList](#setproplist)|設定`m_pWndPropList`受保護的屬性方格控制項的指定指標的資料成員。|  
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|要求框架視窗擁有色軸控制項來更新狀態 列中的訊息列。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|`m_bInternal`|布林值的欄位，指出是否會處理滑鼠事件。 此欄位時，通常處理滑鼠事件`TRUE`和自訂模式是`FALSE`。|  
|`m_bIsEnabled`|布林值，指出控制項是否已啟用。|  
|`m_bIsTearOff`|布林值，指出是否支援停駐色軸的控制項。|  
|`m_BoxSize`|A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，指定在色軸方格資料格的大小。|  
|`m_bShowDocColorsWhenDocked`|布林值，指出是否要顯示的文件色彩停駐在色軸時。 如需詳細資訊，請參閱[CMFCColorBar::SetDocumentColors](#setdocumentcolors)。|  
|`m_bStdColorDlg`|布林值，指出是否要顯示標準系統色彩 對話方塊或[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)對話方塊。 如需詳細資訊，請參閱[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)會儲存目前的自動色彩。 如需詳細資訊，請參閱[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|  
|`m_ColorNames`|[CMap](../../mfc/reference/cmap-class.md)以其名稱的色彩的 RGB 集合產生關聯的物件。|  
|`m_colors`|A [CArray](../../mfc/reference/carray-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)包含色軸控制項中顯示的色彩值。|  
|`m_ColorSelected`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值為目前使用者從色軸的控制項選取的色彩。|  
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md)的[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) ，其中包含目前文件中使用的色彩值。|  
|`m_nCommandID`|不帶正負號的整數的色彩按鈕的命令 ID。|  
|`m_nHorzMargin`|水平的邊界色彩的方格中的色彩按鈕之間的整數。|  
|`m_nHorzOffset`|為中心的 [色彩] 按鈕的水平位移的整數。 這個值是大按鈕會顯示文字或影像色彩以外。|  
|`m_nNumColumns`|色彩的色軸控制項方格中的資料行數目的整數。|  
|`m_nNumColumnsVert`|垂直方向色彩的方格中的資料行數目的整數。|  
|`m_nNumRowsHorz`|水平方向色彩的方格中的資料行數目的整數。|  
|`m_nRowHeight`|為格線中的色彩的色彩按鈕的資料列高度的整數。|  
|`m_nVertMargin`|垂直的邊界色彩的方格中的色彩按鈕之間的整數。|  
|`m_nVertOffset`|為中心的 [色彩] 按鈕的垂直位移的整數。 這個值是大按鈕會顯示文字或影像色彩以外。|  
|`m_Palette`|A [CPalette](../../mfc/reference/cpalette-class.md)色軸控制項中使用的色彩。|  
|`m_pParentBtn`|指標[CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)目前按鈕的父物件。 如果 [色彩] 按鈕的工具列上的控制項階層架構或色彩屬性方格控制項中，這個值是重要的。|  
|`m_pParentRibbonBtn`|指標[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)物件的功能區上且目前按鈕的 [父] 按鈕。 如果 [色彩] 按鈕的工具列上的控制項階層架構或色彩屬性方格控制項中，這個值是重要的。|  
|`m_pWndPropList`|指標[CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)物件。|  
|`m_strAutoColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md)即會顯示在文字**自動** 按鈕。 如需詳細資訊，請參閱[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)。|  
|`m_strDocColors`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md)也就是顯示在文件的 [色彩] 按鈕的文字。 如需詳細資訊，請參閱[CMFCColorBar::SetDocumentColors](#setdocumentcolors)。|  
|`m_strOtherColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md)即會顯示在文字*其他* 按鈕。 如需詳細資訊，請參閱[CMFCColorBar::EnableOtherButton](#enableotherbutton)。|  
  
## <a name="remarks"></a>備註  
 通常，您不會建立`CMFCColorBar`直接物件。 相反地， [CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md)（用於功能表和工具列） 或[CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)建立`CMFCColorBar`物件。  
  
 `CMFCColorBar`類別會提供下列功能︰  
  
-   自動調整文件色彩的清單。  
  
-   儲存並還原其狀態，以及文件的狀態。  
  
-   管理 「 自動 」 按鈕。  
  
-   使用[CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)控制項選取自訂色彩。  
  
-   支援 「 撕 」 狀態 (如果它由使用[CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md))。  
  
 若要納入`CMFCColorBar`功能納入您的應用程式︰  
  
1.  建立一般功能表按鈕，並將它指派一個識別碼，例如 ID_CHAR_COLOR。  
  
2.  在框架視窗類別中覆寫[CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu)方法，並取代規則功能表按鈕與[CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md)物件 (藉由呼叫[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton))。  
  
3.  設定所有的樣式和啟用或停用的功能`CMFCColorBar`物件期間[CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md)建立。 `CMFCColorMenuButton`會動態建立物件`CMFCColorBar`物件之後，架構會呼叫`CreatePopupMenu`方法。  
  
 當使用者按一下色軸的控制項按鈕時，架構會使用`ON_COMMAND`巨集，以通知色軸控制項的父代。 在巨集、 命令 ID 參數會是您指派給色軸的控制項按鈕，在步驟 1 (在本例中為 ID_CHAR_COLOR) 中的值。 如需詳細資訊，請參閱[CMFCColorMenuButton 類別](../../mfc/reference/cmfccolormenubutton-class.md)， [CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)， [CMFCColorPickerCtrl 類別](../../mfc/reference/cmfccolorpickerctrl-class.md)， [cframewndex 則是類別](../../mfc/reference/cframewndex-class.md)，和[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的設定色軸`CMFCColorBar`類別。 方法將水平和垂直邊界設定、 啟用其他按鈕、 色軸控制項視窗的建立和設定目前選取的色彩。 這個範例是屬於[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&1;](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&2;](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]  
  
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
 **標頭︰** afxcolorbar.h  
  
##  <a name="a-nameadjustlocationsa--cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a>CMFCColorBar::AdjustLocations  
 調整色彩按鈕，在色軸控制項的位置。  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法是在架構`WM_SIZE`訊息處理。  
  
##  <a name="a-nameallowchangetextlabelsa--cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCColorBar::AllowChangeTextLabels  
 指出是否可以變更的色彩按鈕的文字標籤。  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一定是 `FALSE`。  
  
### <a name="remarks"></a>備註  
 根據預設，此方法一律傳回`FALSE`，這表示文字標籤不能修改。 覆寫這個方法讓修改文字標籤。  
  
##  <a name="a-nameallowshowonlista--cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a>CMFCColorBar::AllowShowOnList  
 指出色軸控制項物件是否可以在自訂程序期間出現在工具列清單。  
  
```  
virtual BOOL AllowShowOnList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一定是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 根據預設，此方法一律傳回`TRUE`，這表示架構可以自訂程序期間顯示色軸的控制項。 覆寫這個方法以實作不同的行為。  
  
##  <a name="a-namecalcsizea--cmfccolorbarcalcsize"></a><a name="calcsize"></a>CMFCColorBar::CalcSize  
 配置計算程序的一部分的架構所呼叫。  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>參數  
 [in] `bVertDock`  
 `TRUE`若要指定，色軸控制項停駐垂直;`FALSE`指定色軸控制項停駐水平。  
  
### <a name="return-value"></a>傳回值  
 一維陣列中的色彩列控制項的色彩按鈕的大小。  
  
##  <a name="a-namecmfccolorbara--cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a>CMFCColorBar::CMFCColorBar  
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
 [in] `colors`  
 架構會在色軸控制項顯示的色彩的陣列。  
  
 [in] `color`  
 一開始所選取的色彩。  
  
 [in] `lpszAutoColor`  
 文字標籤*自動*（預設值） 的色彩按鈕，或`NULL`。  
  
 [自動] 按鈕的標準標籤是**自動**。  
  
 [in] `lpszOtherColor`  
 文字標籤*其他* 按鈕，以顯示更多色彩選擇，或`NULL`。  
  
 其他按鈕的標準標籤是**更多色彩...**.  
  
 [in] `lpszDocColors`  
 文件的 [色彩] 按鈕的文字標籤。 文件色彩調色盤會列出所有文件目前使用的色彩。  
  
 [in] `lstDocColors`  
 文件目前使用的色彩清單。  
  
 [in] `nColumns`  
 色彩陣列的資料行數目。  
  
 [in] `nRowsDockHorz`  
 色軸水平的停駐時的資料列數目。  
  
 [in] `nColDockVert`  
 色軸垂直的停駐時的資料行數目。  
  
 [in] `colorAutomatic`  
 當您按一下 [自動] 按鈕時，此架構套用的預設色彩。  
  
 [in] `nCommandID`  
 色彩控制命令識別碼。  
  
 [in] `pParentBtn`  
 父代按鈕指標。  
  
 [in] `src`  
 將現有`CMFCColorBar`物件複製到新`CMFCColorBar`物件。  
  
 [in] `uiCommandID`  
 命令 ID。  
  
##  <a name="a-namecontexttosizea--cmfccolorbarcontexttosize"></a><a name="contexttosize"></a>CMFCColorBar::ContextToSize  
 計算的垂直和水平邊界，才能包含在色軸控制項上的按鈕，調整這些按鈕的位置。  
  
```  
void ContextToSize(
    BOOL bSquareButtons = TRUE,   
    BOOL bCenterButtons = TRUE);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `bSquareButtons`|`TRUE`若要指定色彩控制項上按鈕的形狀是方形;否則， `FALSE`。 預設值是 `TRUE`。|  
|[in] `bCenterButtons`|`TRUE`若要指定，色軸的控制項按鈕表面的內容會置中。否則， `FALSE`。 預設值是 `TRUE`。|  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecreatea--cmfccolorbarcreate"></a><a name="create"></a>CMFCColorBar::Create  
 建立的色軸的控制項視窗並將它附加`CMFCColorBar`物件。  
  
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
 [in] `pParentWnd`  
 父視窗的指標。  
  
 [in] `dwStyle`  
 位元組合 (OR)[視窗樣式](../../mfc/reference/window-styles.md)。  
  
 [in] `nID`  
 命令 ID。  
  
 [in] `pPalette`  
 指標的色彩調色盤。 預設為 `NULL`。  
  
 [in] `nColumns`  
 在色軸控制項中的資料行數目。 預設值為 0。  
  
 [in] `nRowsDockHorz`  
 當停駐水平控制項的色軸中的資料列數目。 預設值為 0。  
  
 [in] `nColDockVert`  
 在垂直停駐的色軸控制項的資料行數目。 預設值為 0。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 若要建構`CMFCColorBar`物件，請呼叫類別建構函式，則這個方法。 `Create`方法會建立 Windows 控制項，並初始化色彩的清單。  
  
##  <a name="a-namecreatecontrola--cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a>CMFCColorBar::CreateControl  
 建立的色軸控制項的視窗，將它附加`CMFCColorBar`物件，並調整大小以包含指定的色彩調色盤的 [控制] 視窗。  
  
```  
virtual BOOL CreateControl(
    CWnd* pParentWnd,  
    const CRect& rect,  
    UINT nID,  
    int nColumns=-1,  
    CPalette* pPalette=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParentWnd`  
 父視窗的指標。 不能是`NULL`。  
  
 [in] `rect`  
 指定位置繪製色軸控制項週框。  
  
 [in] `nID`  
 控制項 id。  
  
 [in] `nColumns`  
 理想的色軸控制項中的資料行數目。 這個方法會修改該數字，符合指定的色彩調色盤。 預設值為-1，表示未指定此參數。  
  
 [in] `pPalette`  
 指標的色彩調色盤或`NULL`。 如果這個參數是`NULL`，這個方法會計算色軸控制項的大小，如同已指定 20 的色彩。 預設為 `NULL`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會使用`rect`， `nColumns`，和`pPalette`參數來計算適當數目或資料列和資料行在色軸的控制項，然後再呼叫[CMFCColorBar::Create](#create)方法。  
  
##  <a name="a-namecreatepalettea--cmfccolorbarcreatepalette"></a><a name="createpalette"></a>CMFCColorBar::CreatePalette  
 初始化具有指定的色彩陣列中的色彩調色盤。  
  
```  
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,   
    CPalette& palette);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `arColors`|色彩的陣列。|  
|[in] `palette`|色的調色盤。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。  
  
##  <a name="a-nameenableautomaticbuttona--cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorBar::EnableAutomaticButton  
 顯示或隱藏 [自動] 按鈕。  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszLabel`  
 文字標籤*自動*（預設值） 的色彩按鈕，或`NULL`。  
  
 [自動] 按鈕的標準標籤是**自動**。  
  
 [in] `colorAutomatic`  
 當您按一下 [自動] 按鈕時，此架構套用的預設色彩。  
  
 [in] `bEnable`  
 `TRUE`若要啟用 [自動] 按鈕。`FALSE`停用 [自動] 按鈕。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 如果文字標籤的 [自動] 按鈕會刪除`lpszLabel`參數是`NULL`或`bEnable`參數是`FALSE`。  
  
##  <a name="a-nameenableotherbuttona--cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorBar::EnableOtherButton  
 啟用或停用的對話方塊，讓使用者選取更多的色彩顯示。  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszLabel`  
 文字標籤*其他* 按鈕，以顯示更多色彩選擇，或`NULL`。  
  
 此按鈕的標準標籤是**更多色彩...**.  
  
 [in] `bAltColorDlg`  
 `TRUE`若要顯示[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)對話方塊。`FALSE`以顯示標準[CColorDialog](../../mfc/reference/ccolordialog-class.md)對話方塊。 預設值是 `TRUE`。  
  
 [in] `bEnable`  
 `TRUE`若要啟用按鈕。`FALSE`來停用按鈕。 預設值是 `TRUE`。  
  
##  <a name="a-namegetcolora--cmfccolorbargetcolor"></a><a name="getcolor"></a>CMFCColorBar::GetColor  
 擷取目前選取的色彩。  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前選取的色彩。  
  
##  <a name="a-namegetcolorgridsizea--cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a>CMFCColorBar::GetColorGridSize  
 計算的資料列和資料行在方格中，色軸控制項的數目。  
  
```  
CSize GetColorGridSize(BOOL bVertDock) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `bVertDock`|`TRUE`執行計算垂直停駐的色彩列控制項。否則，執行計算的水平停駐的控制項。|  
  
### <a name="return-value"></a>傳回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，其`cx`元件包含資料行數目和其`cy`元件包含的資料列數目。  
  
##  <a name="a-namegetcommandida--cmfccolorbargetcommandid"></a><a name="getcommandid"></a>CMFCColorBar::GetCommandID  
 擷取目前的色軸控制項的命令 ID。  
  
```  
UINT GetCommandID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 命令 id。  
  
### <a name="remarks"></a>備註  
 當使用者選取新的色彩時，架構會傳送的命令 ID`WM_COMMAND`訊息，通知的父代`CMFCColorBar`物件。  
  
##  <a name="a-namegetextraheighta--cmfccolorbargetextraheight"></a><a name="getextraheight"></a>CMFCColorBar::GetExtraHeight  
 計算目前的色軸顯示其他的使用者介面項目，例如所需的其他高度**其他**按鈕或文件的色彩。  
  
```  
int GetExtraHeight(int nNumColumns) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `nNumColumns`|如果色軸控制項包含文件色彩，在文件色彩的方格中顯示的資料行數目。 否則，這個值不在使用中。|  
  
### <a name="return-value"></a>傳回值  
 需要計算額外高度。  
  
##  <a name="a-namegethighlightedcolora--cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCColorBar::GetHighlightedColor  
 擷取表示的色彩按鈕具有焦點，色彩亦即，按鈕是*熱*。  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 RGB 值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegethorzmargina--cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a>CMFCColorBar::GetHorzMargin  
 擷取的水平的邊界，也就是左邊或右邊的色彩資料格和用戶端區域的界限之間的間距。  
  
```  
int GetHorzMargin();
```  
  
### <a name="return-value"></a>傳回值  
 水平的邊界。  
  
##  <a name="a-namegetvertmargina--cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a>CMFCColorBar::GetVertMargin  
 擷取垂直邊界，也就是頂端或底部色彩的儲存格和用戶端區域的界限之間的間距。  
  
```  
int GetVertMargin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 垂直的邊界。  
  
##  <a name="a-nameinitcolorsa--cmfccolorbarinitcolors"></a><a name="initcolors"></a>CMFCColorBar::InitColors  
 初始化與色彩在指定的調色盤，或使用系統預設調色盤色彩的陣列。  
  
```  
static int InitColors(
    CPalette* pPalette,   
    CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pPalette`|調色盤物件的指標或`NULL`。 如果這個參數是`NULL`，這個方法會使用預設調色盤的作業系統。|  
|[in] `arColors`|色彩的陣列。|  
  
### <a name="return-value"></a>傳回值  
 色彩的陣列中的元素數目。  
  
##  <a name="a-nameistearoffa--cmfccolorbaristearoff"></a><a name="istearoff"></a>CMFCColorBar::IsTearOff  
 指出是否可停駐在目前的色軸。  
  
```  
BOOL IsTearOff() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果目前的色軸控制項停駐;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果可停駐色軸的控制項，可以關閉控制列損毀和固定在另一個位置。  
  
##  <a name="a-nameonkeya--cmfccolorbaronkey"></a><a name="onkey"></a>CMFCColorBar::OnKey  
 當使用者按下鍵盤 按鈕時，由架構呼叫。  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>參數  
 [in] `nChar`  
 使用者按下按鍵虛擬按鍵碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果這個方法會處理指定的索引鍵。，否則， `FALSE`。  
  
##  <a name="a-nameonsendcommanda--cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a>CMFCColorBar::OnSendCommand  
 若要關閉快顯控制項階層架構呼叫。  
  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pButton`|指標位於工具列的控制項。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。  
  
##  <a name="a-nameonupdatecmduia--cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCColorBar::OnUpdateCmdUI  
 啟用或停用的色軸控制項的使用者介面項目，才能在顯示的項目架構呼叫。  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>參數  
 [in] `pTarget`  
 包含要更新使用者介面項目 視窗的指標。  
  
 [in] `bDisableIfNoHndler`  
 `TRUE`若要停用的使用者介面項目，如果沒有處理常式中定義的訊息對應。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 當應用程式的使用者按一下使用者介面項目時，項目必須知道是否應該顯示為已啟用或停用。 命令訊息的目標是提供這項資訊藉由實作`ON_UPDATE_COMMAND_UI`命令處理常式。 使用這個方法，以協助處理命令。 如需詳細資訊，請參閱[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)。  
  
##  <a name="a-nameopencolordialoga--cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a>CMFCColorBar::OpenColorDialog  
 開啟 [色彩] 對話方塊。  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>參數  
 [in] `colorDefault`  
 [色彩] 對話方塊開啟時預設會選取色彩。  
  
 [輸出] `colorRes`  
 使用者選取色彩。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果使用者選取色彩。，`FALSE`如果使用者已取消 [色彩] 對話方塊。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namerebuilda--cmfccolorbarrebuild"></a><a name="rebuild"></a>CMFCColorBar::Rebuild  
 完全重新繪製色軸的控制項。  
  
```  
virtual void Rebuild();
```  
  
##  <a name="a-nameselectpalettea--cmfccolorbarselectpalette"></a><a name="selectpalette"></a>CMFCColorBar::SelectPalette  
 將指定的裝置內容的邏輯調色盤設定為目前的色彩列控制項的父代按鈕的調色盤。  
  
```  
CPalette* SelectPalette(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pDC`|目前的色彩列控制項的父代按鈕的裝置內容的指標。|  
  
### <a name="return-value"></a>傳回值  
 指標會取代目前的色彩列控制項的父代按鈕的調色盤的調色盤。  
  
##  <a name="a-namesetcolora--cmfccolorbarsetcolor"></a><a name="setcolor"></a>CMFCColorBar::SetColor  
 設定目前選取的色彩。  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 RGB 色彩值。  
  
##  <a name="a-namesetcolornamea--cmfccolorbarsetcolorname"></a><a name="setcolorname"></a>CMFCColorBar::SetColorName  
 設定指定的色彩的新名稱。  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 RGB 色彩的值。  
  
 [in] `strName`  
 指定的色彩新名稱。  
  
### <a name="remarks"></a>備註  
 這個方法會變更在所有指定的色彩名稱`CMFCColorBar`應用程式中的物件。  
  
##  <a name="a-namesetcommandida--cmfccolorbarsetcommandid"></a><a name="setcommandid"></a>CMFCColorBar::SetCommandID  
 設定色軸控制項的新命令識別碼。  
  
```  
void SetCommandID(UINT nCommandID);
```  
  
### <a name="parameters"></a>參數  
 [in] `nCommandID`  
 命令 id。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法修改色軸控制項的命令 ID，並通知識別碼已變更之控制項的父視窗。  
  
##  <a name="a-namesetdocumentcolorsa--cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorBar::SetDocumentColors  
 設定目前文件所使用的色彩清單。  
  
```  
void SetDocumentColors(
    LPCTSTR lpszCaption,  
    CList<COLORREF,COLORREF>& lstDocColors,  
    BOOL bShowWhenDocked=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszCaption`  
 未停駐色軸的控制項時，會顯示標題。  
  
 [in] `lstDocColors`  
 取代目前的文件色彩的色彩清單。  
  
 [in] `bShowWhenDocked`  
 `TRUE`若要顯示色軸控制項停駐; 文件色彩否則， `FALSE`。 預設值是 `FALSE`。  
  
### <a name="remarks"></a>備註  
 *文件色彩*是文件中目前使用的色彩。 架構會自動維護一份文件色彩，但是您可以使用這個方法來修改清單。  
  
##  <a name="a-namesethorzmargina--cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a>CMFCColorBar::SetHorzMargin  
 設定水平的邊界，也就是左邊或右邊的色彩資料格和用戶端區域的界限之間的間距。  
  
```  
void SetHorzMargin(int nHorzMargin);
```  
  
### <a name="parameters"></a>參數  
 [in] `nHorzMargin`  
 水平邊界，以像素為單位。  
  
### <a name="remarks"></a>備註  
 根據預設， [CMFCColorBar::CMFCColorBar](#cmfccolorbar)建構函式會將水平的邊界設定為 4 個像素。  
  
##  <a name="a-namesetproplista--cmfccolorbarsetproplist"></a><a name="setproplist"></a>CMFCColorBar::SetPropList  
 設定`m_pWndPropList`受保護的屬性方格控制項的指定指標的資料成員。  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pWndList`|屬性方格控制項物件的指標。|  
  
##  <a name="a-namesetvertmargina--cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a>CMFCColorBar::SetVertMargin  
 設定垂直邊界，也就是頂端或底端色彩資料格，而用戶端區域的界限之間的間距。  
  
```  
void SetVertMargin(int nVertMargin);
```  
  
### <a name="parameters"></a>參數  
 [in] `nVertMargin`  
 垂直邊界，以像素為單位。  
  
### <a name="remarks"></a>備註  
 根據預設， [CMFCColorBar::CMFCColorBar](#cmfccolorbar)建構函式會將垂直的邊界設定為 4 個像素。  
  
##  <a name="a-nameshowcommandmessagestringa--cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a>CMFCColorBar::ShowCommandMessageString  
 要求框架視窗擁有色軸控制項來更新狀態 列中的訊息列。  
  
```  
virtual void ShowCommandMessageString(UINT uiCmdId);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdId`  
 命令 id。 （這個參數已忽略）。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送`WM_SETMESSAGESTRING`色軸控制項的擁有者的訊息。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

