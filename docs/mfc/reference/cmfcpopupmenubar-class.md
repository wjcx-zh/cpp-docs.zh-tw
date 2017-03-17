---
title: "CMFCPopupMenuBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::AdjustSizeImmediate
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::BuildOrigItems
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::CloseDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ExportToMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::FindDestintationToolBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetCurrentMenuImageSize
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetDefaultMenuId
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetLastCommandIndex
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ImportFromMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsDropDownListMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsPaletteMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanel
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanelInRegularMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::LoadFromHash
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::RestoreDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetButtonStyle
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::StartPopupMenuTimer
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::m_bDisableSideBarInXPMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCPopupMenuBar class
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
caps.latest.revision: 32
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 46f86035fecc16c45e01a1c70cdde610093d377b
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar 類別
內嵌於快顯功能表的功能表列。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCPopupMenuBar : public CMFCToolBar  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|立刻重新計算 窗格的版面配置。 (覆寫[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)。)|  
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|從指定的功能表資源載入快顯功能表項目。|  
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|關閉延遲的快顯功能表按鈕。|  
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|建置功能表上，從快顯功能表按鈕。|  
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|尋找工具列指定的點的所在位置。|  
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|表示功能表按鈕影像的大小。|  
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|傳回預設的功能表項目識別碼。|  
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|取得最近叫用的功能表命令的索引。|  
|[CMFCPopupMenuBar::GetOffset](#getoffset)|取得快顯功能表列的資料列位移。|  
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|從指定的功能表會匯入快顯功能表按鈕。|  
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|指出是否在卸除 模式下快顯功能表列。|  
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|指出快顯功能表列處於調色盤模式。|  
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|指出是否在功能區面板 (`FALSE`預設情況下)。|  
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|指出這是否以一般模式在功能區面板 (`FALSE`預設情況下)。|  
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|載入保存的功能表。|  
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|還原延遲的功能表按鈕來關閉快顯功能表列。|  
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|設定指定索引處的工具列按鈕的樣式。 (覆寫[CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle)。)|  
|[CMFCPopupMenuBar::SetOffset](#setoffset)|設定快顯功能表列的資料列的位移。|  
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|啟動計時器指定延遲的快顯功能表按鈕。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|指定應用程式有 Windows XP 外觀時，是否會顯示灰色提要欄位。|  
  
## <a name="remarks"></a>備註  
 `CMFCPopupMenuBar`建立做為同時[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)和內嵌。 `CMFCPopupMenuBar`涵蓋整個工作區的`CMFCPopupMenu`物件。 它支援鍵盤和滑鼠輸入。 它也會進行通訊的輸入要`CMFCPopupMenu`和最上層框架視窗。  
  
## <a name="example"></a>範例  
 下列範例示範如何初始化`CMFCPopupMenuBar`物件從`CMFCPopupMenu`物件。 此程式碼片段是一部分[繪製的用戶端範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient #&7;](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxpopupmenubar.h  
  
##  <a name="adjustsizeimmediate"></a>CMFCPopupMenuBar::AdjustSizeImmediate  
 立刻重新計算快顯功能表列 窗格的版面配置。 (覆寫[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)。  
  
```  
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```  
  
### <a name="parameters"></a>參數  
 [in] `bRecalcLayout`  
 `TRUE`若要自動重新計算配置的快顯功能表列 窗格中。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="buildorigitems"></a>CMFCPopupMenuBar::BuildOrigItems  
 從指定的功能表資源載入快顯功能表項目。  
  
```  
BOOL BuildOrigItems(UINT uiMenuResID);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiMenuResID`  
 指定要載入功能表資源功能表的識別碼。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果成功或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="closedelayedsubmenu"></a>CMFCPopupMenuBar::CloseDelayedSubMenu  
 關閉已延遲的快顯功能表按鈕。  
  
```  
virtual void CloseDelayedSubMenu();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="exporttomenu"></a>CMFCPopupMenuBar::ExportToMenu  
 建置功能表上，從快顯功能表按鈕。  
  
```  
virtual HMENU ExportToMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回新的功能表上的控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="finddestintationtoolbar"></a>CMFCPopupMenuBar::FindDestintationToolBar  
 尋找工具列指定的點的所在位置。  
  
```  
CMFCToolBar* FindDestintationToolBar(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 在螢幕上的點。  
  
### <a name="return-value"></a>傳回值  
 將控制代碼傳回至工具列點所在的位置，如果 therei 的話或`NULL`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcurrentmenuimagesize"></a>CMFCPopupMenuBar::GetCurrentMenuImageSize  
 表示功能表按鈕影像的大小。  
  
```  
virtual CSize GetCurrentMenuImageSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回在工具列上的功能表按鈕影像的大小。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getdefaultmenuid"></a>CMFCPopupMenuBar::GetDefaultMenuId  
 傳回預設的功能表項目識別碼。  
  
```  
UINT GetDefaultMenuId() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回快顯功能表列中的預設功能表項目的識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getlastcommandindex"></a>CMFCPopupMenuBar::GetLastCommandIndex  
 取得最近叫用的功能表命令的索引。  
  
```  
static int __stdcall GetLastCommandIndex();
```  
  
### <a name="return-value"></a>傳回值  
 傳回最後一個功能表命令已叫用的索引。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getoffset"></a>CMFCPopupMenuBar::GetOffset  
 取得快顯功能表列的資料列位移。  
  
```  
int GetOffset() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回快顯功能表列的資料列的位移。  
  
### <a name="remarks"></a>備註  
 這個值會設定使用[CMFCPopupMenuBar::SetOffset](#setoffset)。  
  
##  <a name="importfrommenu"></a>CMFCPopupMenuBar::ImportFromMenu  
 從指定的功能表會匯入快顯功能表按鈕。  
  
```  
virtual BOOL ImportFromMenu(
    HMENU hMenu,  
    BOOL bShowAllCommands = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `hMenu`  
 要從中匯入的快顯功能表按鈕功能表。  
  
 [in] `bShowAllCommands`  
 `TRUE`如果功能表上的所有命令匯入，或`FALSE`如果很少使用的項目可能會隱藏。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`功能表按鈕已順利匯入從功能表中，如果或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isdropdownlistmode"></a>CMFCPopupMenuBar::IsDropDownListMode  
 指出是否在卸除 模式下快顯功能表列。  
  
```  
BOOL IsDropDownListMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`快顯功能表列是在卸除 模式中，如果或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ispalettemode"></a>CMFCPopupMenuBar::IsPaletteMode  
 指出快顯功能表列處於調色盤模式。  
  
```  
BOOL IsPaletteMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果調色盤模式已啟用，或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
 功能表列設定為調色盤模式時，功能表項目會在多個資料行和資料列數量有限。  
  
##  <a name="isribbonpanel"></a>CMFCPopupMenuBar::IsRibbonPanel  
 指出是否在功能區面板 (`FALSE`預設情況下)。  
  
```  
virtual BOOL IsRibbonPanel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`FALSE`根據預設值，指出這不在功能區面板。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isribbonpanelinregularmode"></a>CMFCPopupMenuBar::IsRibbonPanelInRegularMode  
 指出這是否以一般模式在功能區面板 (`FALSE`預設情況下)。  
  
```  
virtual BOOL IsRibbonPanelInRegularMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`FALSE`根據預設值，指出這不在功能區面板以一般模式。  
  
### <a name="remarks"></a>備註  
  
##  <a name="loadfromhash"></a>CMFCPopupMenuBar::LoadFromHash  
 載入保存的功能表。  
  
```  
BOOL LoadFromHash(HMENU hMenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `hMenu`  
 要載入的封存功能表控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果成功，載入功能表或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_bdisablesidebarinxpmode"></a>CMFCPopupMenuBar::m_bDisableSideBarInXPMode  
 布林值的參數，指出包含 Windows XP 外觀時，您的應用程式是否有灰色提要欄位。  
  
```  
BOOL m_bDisableSideBarInXPMode;  
```  
  
### <a name="remarks"></a>備註  
 如果這個成員變數設定為`FALSE`，而且您的應用程式具有 Windows XP 外觀，架構應用程式會以灰色提要欄位。  
  
 預設值是 `FALSE`。  
  
##  <a name="restoredelayedsubmenu"></a>CMFCPopupMenuBar::RestoreDelayedSubMenu  
 還原延遲的功能表按鈕來關閉快顯功能表列。  
  
```  
virtual void RestoreDelayedSubMenu();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="setbuttonstyle"></a>CMFCPopupMenuBar::SetButtonStyle  
 設定指定索引處的工具列按鈕的樣式。 (覆寫[CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle)。)  
  
```  
virtual void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 設定為其樣式的工具列按鈕的以零為起始的索引。  
  
 [in] `nStyle`  
 按鈕的樣式。 請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)可用工具列按鈕樣式清單。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setoffset"></a>CMFCPopupMenuBar::SetOffset  
 設定快顯功能表列的資料列的位移。  
  
```  
void SetOffset(int iOffset);
```  
  
### <a name="parameters"></a>參數  
 [in] `iOffset`  
 快顯功能表列應進行位移的資料列數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="startpopupmenutimer"></a>CMFCPopupMenuBar::StartPopupMenuTimer  
 啟動計時器指定延遲的快顯功能表按鈕。  
  
```  
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,  
    int nDelayFactor = 1);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuButton`  
 指標，這是要設定延遲計時器的功能表按鈕。  
  
 [in] `nDelayFactor`  
 延遲因素，等於至少一個要乘以的標準功能表延遲時間 （通常以半秒，且五秒）。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)

