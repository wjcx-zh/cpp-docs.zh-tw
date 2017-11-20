---
title: "CMFCPopupMenuBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CMFCPopupMenuBar [MFC], AdjustSizeImmediate
- CMFCPopupMenuBar [MFC], BuildOrigItems
- CMFCPopupMenuBar [MFC], CloseDelayedSubMenu
- CMFCPopupMenuBar [MFC], ExportToMenu
- CMFCPopupMenuBar [MFC], FindDestintationToolBar
- CMFCPopupMenuBar [MFC], GetCurrentMenuImageSize
- CMFCPopupMenuBar [MFC], GetDefaultMenuId
- CMFCPopupMenuBar [MFC], GetLastCommandIndex
- CMFCPopupMenuBar [MFC], GetOffset
- CMFCPopupMenuBar [MFC], ImportFromMenu
- CMFCPopupMenuBar [MFC], IsDropDownListMode
- CMFCPopupMenuBar [MFC], IsPaletteMode
- CMFCPopupMenuBar [MFC], IsRibbonPanel
- CMFCPopupMenuBar [MFC], IsRibbonPanelInRegularMode
- CMFCPopupMenuBar [MFC], LoadFromHash
- CMFCPopupMenuBar [MFC], RestoreDelayedSubMenu
- CMFCPopupMenuBar [MFC], SetButtonStyle
- CMFCPopupMenuBar [MFC], SetOffset
- CMFCPopupMenuBar [MFC], StartPopupMenuTimer
- CMFCPopupMenuBar [MFC], m_bDisableSideBarInXPMode
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6be3c3b6028bab04ae3d8ec32f9063d26012778e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|立即重新計算顯示窗格的配置。 (覆寫[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)。)|  
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|從指定的功能表資源載入快顯功能表項目。|  
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|延遲的快顯功能表按鈕會關閉。|  
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|建置的快顯功能表按鈕的功能表。|  
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|尋找工具列指定的點的所在位置。|  
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|表示功能表按鈕影像的大小。|  
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|傳回預設的功能表項目的識別項。|  
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|取得最近叫用的功能表命令的索引。|  
|[CMFCPopupMenuBar::GetOffset](#getoffset)|取得快顯功能表列的資料列位移。|  
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|匯入快顯功能表按鈕，從指定的功能表。|  
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|指出快顯功能表列是否為下拉式選單模式。|  
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|指出快顯功能表列是否為調色盤模式。|  
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|指出這是否為功能區面板 (`FALSE`依預設)。|  
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|指出這是否以一般模式的功能區面板 (`FALSE`依預設)。|  
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|載入保存的功能表。|  
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|還原延遲的功能表按鈕關閉快顯功能表列。|  
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|設定指定索引處的工具列按鈕的樣式。 (覆寫[CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle)。)|  
|[CMFCPopupMenuBar::SetOffset](#setoffset)|設定快顯功能表列的資料列位移。|  
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|啟動指定的延遲快顯功能表按鈕的計時器。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|指定應用程式有 Windows XP 外觀時，是否會顯示灰色提要欄位。|  
  
## <a name="remarks"></a>備註  
 `CMFCPopupMenuBar`建立在相同的時間，做為[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)和內嵌在它之內。 `CMFCPopupMenuBar`涵蓋整個工作區`CMFCPopupMenu`物件。 它支援鍵盤和滑鼠輸入。 它也會進行通訊的輸入要`CMFCPopupMenu`和最上層框架視窗。  
  
## <a name="example"></a>範例  
 下列範例示範如何初始化`CMFCPopupMenuBar`物件從`CMFCPopupMenu`物件。 這段程式碼片段是 [Draw 用戶端範例](../../visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]  
  
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
 **標頭：** afxpopupmenubar.h  
  
##  <a name="adjustsizeimmediate"></a>CMFCPopupMenuBar::AdjustSizeImmediate  
 立即重新計算快顯功能表列 窗格的配置。 (覆寫[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)。  
  
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
 指定要載入功能表資源的功能表識別碼。  
  
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
 建置的快顯功能表按鈕的功能表。  
  
```  
virtual HMENU ExportToMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回新功能表的控制代碼。  
  
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
 將控制代碼傳回至工具列點所在的位置，如果 therei 的話，或`NULL`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcurrentmenuimagesize"></a>CMFCPopupMenuBar::GetCurrentMenuImageSize  
 表示功能表按鈕影像的大小。  
  
```  
virtual CSize GetCurrentMenuImageSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回在工具列中的功能表按鈕影像的大小。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getdefaultmenuid"></a>CMFCPopupMenuBar::GetDefaultMenuId  
 傳回預設的功能表項目的識別項。  
  
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
 傳回快顯功能表列的資料列位移。  
  
### <a name="remarks"></a>備註  
 這個值會設定使用[CMFCPopupMenuBar::SetOffset](#setoffset)。  
  
##  <a name="importfrommenu"></a>CMFCPopupMenuBar::ImportFromMenu  
 匯入快顯功能表按鈕，從指定的功能表。  
  
```  
virtual BOOL ImportFromMenu(
    HMENU hMenu,  
    BOOL bShowAllCommands = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `hMenu`  
 要從中匯入的快顯功能表按鈕功能表。  
  
 [in] `bShowAllCommands`  
 `TRUE`如果功能表上的所有命令匯入，或`FALSE`如果很少使用的項目可能會隱藏起來。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`功能表按鈕已順利匯入從功能表中，如果或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isdropdownlistmode"></a>CMFCPopupMenuBar::IsDropDownListMode  
 指出快顯功能表列是否為下拉式選單模式。  
  
```  
BOOL IsDropDownListMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`快顯功能表列在下拉式清單清單模式中，如果或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ispalettemode"></a>CMFCPopupMenuBar::IsPaletteMode  
 指出快顯功能表列是否為調色盤模式。  
  
```  
BOOL IsPaletteMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果調色盤模式已啟用，或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
 當功能表列設定為調色盤模式時，功能表項目出現在多個資料行以及有限的數目的資料列。  
  
##  <a name="isribbonpanel"></a>CMFCPopupMenuBar::IsRibbonPanel  
 指出這是否為功能區面板 (`FALSE`依預設)。  
  
```  
virtual BOOL IsRibbonPanel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`FALSE`根據預設值，指出這不在功能區面板。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isribbonpanelinregularmode"></a>CMFCPopupMenuBar::IsRibbonPanelInRegularMode  
 指出這是否以一般模式的功能區面板 (`FALSE`依預設)。  
  
```  
virtual BOOL IsRibbonPanelInRegularMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`FALSE`根據預設，表示這不在功能區面板一般模式。  
  
### <a name="remarks"></a>備註  
  
##  <a name="loadfromhash"></a>CMFCPopupMenuBar::LoadFromHash  
 載入保存的功能表。  
  
```  
BOOL LoadFromHash(HMENU hMenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `hMenu`  
 載入 [封存] 功能表的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果成功，載入功能表或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_bdisablesidebarinxpmode"></a>CMFCPopupMenuBar::m_bDisableSideBarInXPMode  
 表示包含 Windows XP 外觀時，您的應用程式是否有灰色提要欄位的布林參數。  
  
```  
BOOL m_bDisableSideBarInXPMode;  
```  
  
### <a name="remarks"></a>備註  
 如果此成員變數會設為`FALSE`您的應用程式和 Windows XP 外觀，架構應用程式中繪製灰色提要欄位。  
  
 預設值是 `FALSE`。  
  
##  <a name="restoredelayedsubmenu"></a>CMFCPopupMenuBar::RestoreDelayedSubMenu  
 還原延遲的功能表按鈕關閉快顯功能表列。  
  
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
 工具列按鈕的樣式是要設定的以零為起始的索引。  
  
 [in] `nStyle`  
 按鈕的樣式。 請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)可用工具列按鈕樣式的清單。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setoffset"></a>CMFCPopupMenuBar::SetOffset  
 設定快顯功能表列的資料列位移。  
  
```  
void SetOffset(int iOffset);
```  
  
### <a name="parameters"></a>參數  
 [in] `iOffset`  
 快顯功能表列應進行位移的資料列數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="startpopupmenutimer"></a>CMFCPopupMenuBar::StartPopupMenuTimer  
 啟動指定的延遲快顯功能表按鈕的計時器。  
  
```  
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,  
    int nDelayFactor = 1);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuButton`  
 要設定延遲計時器的功能表按鈕的指標。  
  
 [in] `nDelayFactor`  
 延遲因素，等於至少一個，乘以標準功能表的延遲時間 （通常之間半秒和 5 秒）。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)
