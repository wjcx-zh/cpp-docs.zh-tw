---
title: CMFCBaseVisualManager 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawCheckBox
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboBorder
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboDropButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawPushButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawRadioButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawStatusBarProgress
- AFXVISUALMANAGER/CMFCBaseVisualManager::FillReBarPane
- AFXVISUALMANAGER/CMFCBaseVisualManager::GetStandardWindowsTheme
- AFXVISUALMANAGER/CMFCBaseVisualManager::CleanUpThemes
- AFXVISUALMANAGER/CMFCBaseVisualManager::UpdateSystemColors
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseVisualManager [MFC], CMFCBaseVisualManager
- CMFCBaseVisualManager [MFC], DrawCheckBox
- CMFCBaseVisualManager [MFC], DrawComboBorder
- CMFCBaseVisualManager [MFC], DrawComboDropButton
- CMFCBaseVisualManager [MFC], DrawPushButton
- CMFCBaseVisualManager [MFC], DrawRadioButton
- CMFCBaseVisualManager [MFC], DrawStatusBarProgress
- CMFCBaseVisualManager [MFC], FillReBarPane
- CMFCBaseVisualManager [MFC], GetStandardWindowsTheme
- CMFCBaseVisualManager [MFC], CleanUpThemes
- CMFCBaseVisualManager [MFC], UpdateSystemColors
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7b21651bdab6bf2e4603a8fa012480a6201e34b
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336214"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager 類別
在衍生的視覺管理員與 Windows 佈景主題 API 之間的層。  
  
 `CMFCBaseVisualManager` 如果有的話，載入 UxTheme.dll，，和管理 Windows 佈景主題 API 方法的存取權。  
  
 這個類別是僅供內部使用。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCBaseVisualManager: public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|建構並初始化 `CMFCBaseVisualManager` 物件。|  
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|使用目前的 Windows 佈景主題來繪製核取方塊控制項。|  
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|繪製使用目前的 Windows 佈景主題的下拉式方塊框線。|  
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|繪製使用目前的 Windows 佈景主題的下拉式方塊下拉式按鈕。|  
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|繪製按鈕，使用目前的 Windows 佈景主題。|  
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|使用目前的 Windows 佈景主題來繪製選項按鈕控制項。|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|狀態列控制項上繪製一個進度列 ( [CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md)) 使用目前的 Windows 佈景主題。|  
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|使用目前的 Windows 佈景主題，填滿 rebar 控制項的背景。|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|取得目前的 Windows 佈景主題。|  
  
### <a name="protected-methods"></a>保護方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|呼叫`CloseThemeData`中的所有控制代碼取得`UpdateSystemColors`。|  
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|呼叫`OpenThemeData`取得繪製各種控制項的控制代碼： windows、 工具列、 按鈕等等。|  
  
## <a name="remarks"></a>備註  
 您不必直接執行個體化這個類別的物件。  
  
 因為它是所有的視覺管理員的基底類別，您可以直接呼叫[CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance)，取得的指標至目前 Visual Manager，並存取的方法`CMFCBaseVisualManager`使用該指標。 不過，如果您有使用目前的 Windows 佈景主題中顯示控制項，最好是使用`CMFCVisualManagerWindows`介面。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxvisualmanager.h  
  
##  <a name="cleanupthemes"></a>  CMFCBaseVisualManager::CleanUpThemes  
 呼叫`CloseThemeData`中的所有控制代碼取得`UpdateSystemColors`。  
  
```  
void CleanUpThemes();
```  
  
### <a name="remarks"></a>備註  
 僅供內部使用。  
  
##  <a name="cmfcbasevisualmanager"></a>  CMFCBaseVisualManager::CMFCBaseVisualManager  
 建構並初始化 `CMFCBaseVisualManager` 物件。  
  
```  
CMFCBaseVisualManager();
```  
  
##  <a name="drawcheckbox"></a>  CMFCBaseVisualManager::DrawCheckBox  
 使用目前的 Windows 佈景主題來繪製核取方塊控制項。  
  
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
 [in]*pDC*  
 裝置內容的指標  
  
 [in]*rect*  
 核取方塊的週框。  
  
 [in]*bHighlighted*  
 指定核取方塊會反白顯示。  
  
 [in]*nState*  
 0 適用於已檢查的標準，未選取，1  
  
 適用於混合的標準 2。  
  
 [in]*bEnabled*  
 指定是否要啟用此核取方塊。  
  
 [in]*bPressed*  
 指定是否已按下核取方塊。  
  
### <a name="return-value"></a>傳回值  
 如果已啟用佈景主題的 API，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 值*nState*對應至下列的核取方塊樣式。  
  
|nState|核取方塊樣式|  
|------------|---------------------|  
|0|CBS_UNCHECKEDNORMAL|  
|1|CBS_CHECKEDNORMAL|  
|2|CBS_MIXEDNORMAL|  
  
##  <a name="drawcomboborder"></a>  CMFCBaseVisualManager::DrawComboBorder  
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
 [in]*pDC*  
 裝置內容的指標。  
  
 [in]*rect*  
 下拉式方塊框線的週框。  
  
 [in]*bDisabled*  
 指定是否要停用下拉式方塊框線。  
  
 [in]*bIsDropped*  
 指定是否要向下卸除下拉式方塊框線。  
  
 [in]*bIsHighlighted*  
 指定下拉式方塊框線會反白顯示。  
  
### <a name="return-value"></a>傳回值  
 如果已啟用佈景主題的 API，則為 TRUE。否則為 FALSE。  
  
##  <a name="drawcombodropbutton"></a>  CMFCBaseVisualManager::DrawComboDropButton  
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
|[in]*pDC*|裝置內容的指標。|  
|[in]*rect*|下拉式方塊下拉式按鈕的週框。|  
|[in]*bDisabled*|指定是否要停用下拉式方塊下拉式按鈕。|  
|[in]*bIsDropped*|指定是否要向下卸除下拉式方塊下拉式按鈕。|  
|[in]*bIsHighlighted*|指定下拉式方塊下拉式按鈕已反白顯示。|  
  
### <a name="return-value"></a>傳回值  
 如果已啟用佈景主題的 API，則為 TRUE。否則為 FALSE。  
  
##  <a name="drawpushbutton"></a>  CMFCBaseVisualManager::DrawPushButton  
 繪製按鈕，使用目前的 Windows 佈景主題。  
  
```  
virtual BOOL DrawPushButton(
    CDC* pDC,   
    CRect rect,   
    CMFCButton* pButton,   
    UINT uiState);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
 裝置內容的指標。  
  
 [in]*rect*  
 週框的按鈕。  
  
 [in]*pButton*  
 指標[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)来繪製物件。  
  
 [in]*uiState*  
 忽略。 狀態取自*pButton*。  
  
### <a name="return-value"></a>傳回值  
 如果已啟用佈景主題的 API，則為 TRUE。否則為 FALSE。  
  
##  <a name="drawradiobutton"></a>  CMFCBaseVisualManager::DrawRadioButton  
 使用目前的 Windows 佈景主題來繪製選項按鈕控制項。  
  
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
 [in]*pDC*  
 裝置內容的指標。  
  
 [in]*rect*  
 選項按鈕的週框。  
  
 [in]*bHighlighted*  
 指定的選項按鈕已反白顯示。  
  
 [in]*bChecked*  
 指定是否要檢查的選項按鈕。  
  
 [in]*bEnabled*  
 指定是否要啟用的選項按鈕。  
  
 [in]*bPressed*  
 指定是否已按下選項按鈕。  
  
### <a name="return-value"></a>傳回值  
 如果已啟用佈景主題的 API，則為 TRUE。否則為 FALSE。  
  
##  <a name="drawstatusbarprogress"></a>  CMFCBaseVisualManager::DrawStatusBarProgress  
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
 [in]*pDC*  
 裝置內容的指標。  
  
 [in]*pStatusBar*  
 狀態列指標。 這個值會被忽略。  
  
 [in]*rectProgress*  
 進度列中的週框矩形*pDC*座標。  
  
 [in]*nProgressTotal*  
 整體進度值。  
  
 [in]*nProgressCurr*  
 目前的進度值。  
  
 [in]*clrBar*  
 開始色彩。 `CMFCBaseVisualManager` 會忽略這種情況。 在衍生的類別可以使用它的色彩漸層。  
  
 [in]*clrProgressBarDest*  
 結束色彩。 `CMFCBaseVisualManager` 會忽略這種情況。 在衍生的類別可以使用它的色彩漸層。  
  
 [in]*clrProgressText*  
 進度的文字色彩。 `CMFCBaseVisualManager` 會忽略這種情況。 所定義的文字色彩`afxGlobalData.clrBtnText`。  
  
 [in]*bProgressText*  
 指定是否要顯示進度的文字。  
  
### <a name="return-value"></a>傳回值  
 如果已啟用佈景主題的 API，則為 TRUE。否則為 FALSE。  
  
##  <a name="fillrebarpane"></a>  CMFCBaseVisualManager::FillReBarPane  
 使用目前的 Windows 佈景主題，填滿 rebar 控制項的背景。  
  
```  
virtual void FillReBarPane(
    CDC* pDC,   
    CBasePane* pBar,   
    CRect rectClient);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
 裝置內容的指標。  
  
 [in]*pBar*  
 應該繪製其背景窗格指標。  
  
 [in]*rectClient*  
 要填滿區域的周框。  
  
### <a name="return-value"></a>傳回值  
 如果已啟用佈景主題的 API，則為 TRUE。否則為 FALSE。  
  
##  <a name="getstandardwindowstheme"></a>  CMFCBaseVisualManager::GetStandardWindowsTheme  
 取得目前的 Windows 佈景主題。  
  
```  
virtual WinXpTheme GetStandardWindowsTheme();
```  
  
### <a name="return-value"></a>傳回值  
 目前選取的 Windows 佈景主題色彩。 可以是下列的列舉值之一：  
  
- `WinXpTheme_None` -沒有啟用任何佈景主題。  
  
- `WinXpTheme_NonStandard` -非標準的佈景主題選取 （亦即已選取的佈景主題，但無從下方清單）。  
  
- `WinXpTheme_Blue` -藍色佈景主題 (Luna)。  
  
- `WinXpTheme_Olive` -橄欖佈景主題。  
  
- `WinXpTheme_Silver` -銀色佈景主題。  
  
##  <a name="updatesystemcolors"></a>  CMFCBaseVisualManager::UpdateSystemColors  
 呼叫`OpenThemeData`取得繪製各種控制項的控制代碼： windows、 工具列、 按鈕等等。  
  
```  
void UpdateSystemColors();
```  
  
### <a name="remarks"></a>備註  
 僅供內部使用。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
