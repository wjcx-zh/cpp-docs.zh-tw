---
title: "CMFCRibbonMiniToolBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonMiniToolBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonMiniToolBar class
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7c69880578c0aba88a8463112f4d1e05f6032497
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonminitoolbar-class"></a>CMFCRibbonMiniToolBar 類別
實作內容快顯工具列。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|預設建構函式。|  
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCRibbonMiniToolBar::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||  
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(覆寫 `CMFCPopupMenu::IsRibbonMiniToolBar`。)|  
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|設定要顯示在工具列上的命令清單。|  
|[CMFCRibbonMiniToolBar::Show](#show)|顯示位於指定的螢幕座標的迷你工具列。|  
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|顯示迷你工具列以及操作功能表。|  
  
## <a name="remarks"></a>備註  
 使用者在文件中選取物件之後，通常會顯示迷你工具列。 比方說，在使用者於文書處理程式中選取文字區塊之後，應用程式會顯示包含文字格式化命令的迷你工具列。  
  
 當滑鼠指標超出迷你工具列的範圍時，迷你工具列會變成透明。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 `CMFCRibbonPanelMenu`  
  
 [CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxRibbonMiniToolBar.h  
  
##  <a name="a-namesetcommandsa--cmfcribbonminitoolbarsetcommands"></a><a name="setcommands"></a>CMFCRibbonMiniToolBar::SetCommands  
 設定要顯示在工具列上的命令清單。  
  
```  
void SetCommands(
    CMFCRibbonBar* pRibbonBar,  
    const CList<UINT,UINT>& lstCommands);
```  
  
### <a name="parameters"></a>參數  
 [in] `pRibbonBar`  
 要顯示的按鈕搜尋迷你工具列功能區列。  
  
 [in] `lstCommands`  
 要顯示在迷你工具列上的命令清單。 所有的功能區類別目錄會搜尋來尋找相關聯的按鈕。  
  
### <a name="remarks"></a>備註  
 使用此函式來設定要顯示在迷你工具列命令的清單。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`SetCommands`方法`CMFCRibbonMiniToolBar`類別。 此程式碼片段是一部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&9;](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]  
  
##  <a name="a-nameshowa--cmfcribbonminitoolbarshow"></a><a name="show"></a>CMFCRibbonMiniToolBar::Show  
 顯示位於指定的螢幕座標的迷你工具列。  
  
```  
BOOL Show(
    int x,  
    int y);
```  
  
### <a name="parameters"></a>參數  
 [in] `x`  
 螢幕座標中指定迷你工具列的水平的位置。  
  
 [in] `y`  
 螢幕座標中指定迷你工具列的垂直的位置。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果顯示 迷你工具列已順利啟動。否則， `FALSE`。  
  
##  <a name="a-nameshowwithcontextmenua--cmfcribbonminitoolbarshowwithcontextmenu"></a><a name="showwithcontextmenu"></a>CMFCRibbonMiniToolBar::ShowWithContextMenu  
 顯示迷你工具列以及操作功能表。  
  
```  
BOOL ShowWithContextMenu(
    int x,  
    int y,  
    UINT uiMenuResID,  
    CWnd* pWndOwner);
```  
  
### <a name="parameters"></a>參數  
 [in] `x`  
 指定螢幕座標中的內容功能表中的水平位置。  
  
 [in] `y`  
 螢幕座標中指定的內容功能表的垂直位置。  
  
 [in] `uiMenuResID`  
 指定要顯示內容功能表中的資源 ID。  
  
 [in] `pWndOwner`  
 識別會從內容功能表中接收訊息的視窗。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功，顯示內容功能表否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來顯示具有內容功能表的迷你工具列。 內容功能表是迷你工具列下方的定位 15 像素。  
  
##  <a name="a-nameiscontextmenumodea--cmfcribbonminitoolbariscontextmenumode"></a><a name="iscontextmenumode"></a>CMFCRibbonMiniToolBar::IsContextMenuMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsContextMenuMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisribbonminitoolbara--cmfcribbonminitoolbarisribbonminitoolbar"></a><a name="isribbonminitoolbar"></a>CMFCRibbonMiniToolBar::IsRibbonMiniToolBar  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsRibbonMiniToolBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

