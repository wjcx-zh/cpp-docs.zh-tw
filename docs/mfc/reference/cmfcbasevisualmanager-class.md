---
title: "CMFCBaseVisualManager 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCBaseVisualManager
- CMFCBaseVisualManager.~CMFCBaseVisualManager
- ~CMFCBaseVisualManager
- CMFCBaseVisualManager::~CMFCBaseVisualManager
dev_langs:
- C++
helpviewer_keywords:
- ~CMFCBaseVisualManager destructor
- CMFCBaseVisualManager class, destructor
- CMFCBaseVisualManager class
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
caps.latest.revision: 24
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 7c726fe71b7dcf26353fe0ce3a6b383eb5b578b9
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager 類別
在衍生的視覺管理員與 Windows 佈景主題 API 層。  
  
 `CMFCBaseVisualManager`如果有的話，載入 UxTheme.dll，並管理 Windows 佈景主題的 API 方法的存取。  
  
 這個類別是僅供內部使用。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCBaseVisualManager: public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|建構並初始化 `CMFCBaseVisualManager` 物件。|  
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|繪製使用目前的 Windows 佈景主題的核取方塊控制項。|  
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|繪製使用目前的 Windows 佈景主題的下拉式方塊框線。|  
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|繪製使用目前的 Windows 佈景主題的下拉式方塊下拉式按鈕。|  
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|繪製使用目前的 Windows 佈景主題的按鈕。|  
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|使用目前的 Windows 佈景主題繪製選項按鈕控制項。|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|狀態列控制項上繪製一個進度列 ( [CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md)) 使用目前的 Windows 佈景主題。|  
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|使用目前的 Windows 佈景主題，填滿 rebar 控制項的背景。|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|取得目前的 Windows 佈景主題。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|呼叫`CloseThemeData`中取得的所有控制代碼`UpdateSystemColors`。|  
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|呼叫`OpenThemeData`來取得繪製各種控制項的控制代碼︰ windows、 工具列、 按鈕等等。|  
  
## <a name="remarks"></a>備註  
 沒有直接執行個體化這個類別的物件。  
  
 因為它是所有的視覺管理員的基底類別，您可以直接呼叫[CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance)取得的指標給目前視覺管理員，並存取的方法`CMFCBaseVisualManager`使用該指標。 不過，如果您有使用目前的 Windows 佈景主題來顯示控制項，最好是使用`CMFCVisualManagerWindows`介面。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxvisualmanager.h  
  
##  <a name="a-namecleanupthemesa--cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a>CMFCBaseVisualManager::CleanUpThemes  
 呼叫`CloseThemeData`中取得的所有控制代碼`UpdateSystemColors`。  
  
```  
void CleanUpThemes();
```  
  
### <a name="remarks"></a>備註  
 僅供內部使用。  
  
##  <a name="a-namecmfcbasevisualmanagera--cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a>CMFCBaseVisualManager::CMFCBaseVisualManager  
 建構並初始化 `CMFCBaseVisualManager` 物件。  
  
```  
CMFCBaseVisualManager();
```  
  
##  <a name="a-namedrawcheckboxa--cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a>CMFCBaseVisualManager::DrawCheckBox  
 繪製使用目前的 Windows 佈景主題的核取方塊控制項。  
  
```  
virtual BOOL DrawCheckBox(
    CDC* pDC,   
    CRect rect,   
    BOOL bHighlighted,   
    int nState,   
    BOOL bEnabled,   
    BOOL bPressed);

);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標  
  
 [in] `rect`  
 核取方塊，這個周框。  
  
 [in] `bHighlighted`  
 指定核取方塊會反白顯示。  
  
 [in] `nState`  
 0 已檢查的標準，如未選取，1  
  
 適用於混合的標準&2;。  
  
 [in] `bEnabled`  
 指定是否要啟用此核取方塊。  
  
 [in] `bPressed`  
 指定是否要按下核取方塊。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用佈景主題的 API。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 值`nState`對應至下列的核取方塊樣式。  
  
|nState|核取方塊樣式|  
|------------|---------------------|  
|0|CBS_UNCHECKEDNORMAL|  
|1|CBS_CHECKEDNORMAL|  
|2|CBS_MIXEDNORMAL|  
  
##  <a name="a-namedrawcombobordera--cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a>CMFCBaseVisualManager::DrawComboBorder  
 繪製使用目前的 Windows 佈景主題的下拉式方塊框線。  
  
```  
virtual BOOL DrawComboBorder(
    CDC* pDC,   
    CRect rect,   
    BOOL bDisabled,   
    BOOL bIsDropped,   
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 下拉式方塊框的週框。  
  
 [in] `bDisabled`  
 指定是否要停用下拉式方塊框線。  
  
 [in] `bIsDropped`  
 指定是否要卸除的下拉式方塊的框線。  
  
 [in] `bIsHighlighted`  
 指定下拉式方塊框線會反白顯示。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用佈景主題的 API。否則`FALSE`。  
  
##  <a name="a-namedrawcombodropbuttona--cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a>CMFCBaseVisualManager::DrawComboDropButton  
 繪製使用目前的 Windows 佈景主題的下拉式方塊下拉式按鈕。  
  
```  
virtual BOOL DrawComboDropButton(
    CDC* pDC,   
    CRect rect,   
    BOOL bDisabled,   
    BOOL bIsDropped,   
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pDC`|裝置內容的指標。|  
|[in] `rect`|下拉式方塊下拉式按鈕，這個周框。|  
|[in] `bDisabled`|指定是否要停用下拉式方塊下拉式按鈕。|  
|[in] `bIsDropped`|指定是否要卸除下拉式方塊下拉式按鈕。|  
|[in] `bIsHighlighted`|指定下拉式方塊下拉式按鈕會反白顯示。|  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用佈景主題的 API。否則`FALSE`。  
  
##  <a name="a-namedrawpushbuttona--cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a>CMFCBaseVisualManager::DrawPushButton  
 繪製使用目前的 Windows 佈景主題的按鈕。  
  
```  
virtual BOOL DrawPushButton(
    CDC* pDC,   
    CRect rect,   
    CMFCButton* pButton,   
    UINT uiState);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 [推送] 按鈕，這個周框。  
  
 [in] `pButton`  
 指標[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)物件來繪製。  
  
 [in] `uiState`  
 忽略。 狀態取自`pButton`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用佈景主題的 API。否則`FALSE`。  
  
##  <a name="a-namedrawradiobuttona--cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a>CMFCBaseVisualManager::DrawRadioButton  
 使用目前的 Windows 佈景主題繪製選項按鈕控制項。  
  
```  
virtual BOOL DrawRadioButton(
    CDC* pDC,   
    CRect rect,   
    BOOL bHighlighted,   
    BOOL bChecked,   
    BOOL bEnabled,   
    BOOL bPressed);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 選項按鈕，這個周框。  
  
 [in] `bHighlighted`  
 指定的選項按鈕會反白顯示。  
  
 [in] `bChecked`  
 指定是否要檢查的選項按鈕。  
  
 [in] `bEnabled`  
 指定是否要啟用的選項按鈕。  
  
 [in] `bPressed`  
 指定是否要按下的選項按鈕。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用佈景主題的 API。否則`FALSE`。  
  
##  <a name="a-namedrawstatusbarprogressa--cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a>CMFCBaseVisualManager::DrawStatusBarProgress  
 狀態列控制項上繪製進度列 ( [CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md)) 使用目前的 Windows 佈景主題。  
  
```  
virtual BOOL DrawStatusBarProgress(
    CDC* pDC,   
    CMFCStatusBar* pStatusBar,   
    CRect rectProgress,   
    int nProgressTotal,   
    int nProgressCurr,  
    COLORREF clrBar,   
    COLORREF clrProgressBarDest,   
    COLORREF clrProgressText,   
    BOOL bProgressText);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pStatusBar`  
 狀態列指標。 這個值會被忽略。  
  
 [in] `rectProgress`  
 進度列中的周框矩形`pDC`座標。  
  
 [in] `nProgressTotal`  
 整體進度值。  
  
 [in] `nProgressCurr`  
 目前的進度值。  
  
 [in] `clrBar`  
 開始色彩。 `CMFCBaseVisualManager`會忽略這種情況。 在衍生的類別可以使用它的色彩漸層。  
  
 [in] `clrProgressBarDest`  
 結束色彩。 `CMFCBaseVisualManager`會忽略這種情況。 在衍生的類別可以使用它的色彩漸層。  
  
 [in] `clrProgressText`  
 進度的文字色彩。 `CMFCBaseVisualManager`會忽略這種情況。 所定義的文字色彩`afxGlobalData.clrBtnText`。  
  
 [in] `bProgressText`  
 指定是否要顯示進度的文字。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用佈景主題的 API。否則`FALSE`。  
  
##  <a name="a-namefillrebarpanea--cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a>CMFCBaseVisualManager::FillReBarPane  
 使用目前的 Windows 佈景主題，填滿 rebar 控制項的背景。  
  
```  
virtual void FillReBarPane(
    CDC* pDC,   
    CBasePane* pBar,   
    CRect rectClient);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pBar`  
 應該繪製其背景窗格指標。  
  
 [in] `rectClient`  
 要填滿區域的周框矩形。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用佈景主題的 API。否則`FALSE`。  
  
##  <a name="a-namegetstandardwindowsthemea--cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a>CMFCBaseVisualManager::GetStandardWindowsTheme  
 取得目前的 Windows 佈景主題。  
  
```  
virtual WinXpTheme GetStandardWindowsTheme();
```  
  
### <a name="return-value"></a>傳回值  
 目前選取的 Windows 佈景主題色彩。 可以是下列的列舉值之一︰  
  
- `WinXpTheme_None`-沒有啟用無佈景主題。  
  
- `WinXpTheme_NonStandard`-選取非標準的佈景主題 （亦即已選取的佈景主題，但無從以下清單）。  
  
- `WinXpTheme_Blue`-藍色佈景主題 (Luna)。  
  
- `WinXpTheme_Olive`-黃褐色佈景主題。  
  
- `WinXpTheme_Silver`-銀色佈景主題。  
  
##  <a name="a-nameupdatesystemcolorsa--cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a>CMFCBaseVisualManager::UpdateSystemColors  
 呼叫`OpenThemeData`來取得繪製各種控制項的控制代碼︰ windows、 工具列、 按鈕等等。  
  
```  
void UpdateSystemColors();
```  
  
### <a name="remarks"></a>備註  
 僅供內部使用。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

