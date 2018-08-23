---
title: CMFCRibbonMiniToolBar 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 789a8165a12977d11220d299e2c99549121dba64
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539203"
---
# <a name="cmfcribbonminitoolbar-class"></a>CMFCRibbonMiniToolBar 類別
實作內容快顯工具列。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|預設建構函式。|  
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCRibbonMiniToolBar::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
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
 **標頭：** afxRibbonMiniToolBar.h  
  
##  <a name="setcommands"></a>  CMFCRibbonMiniToolBar::SetCommands  
 設定要顯示在工具列上的命令清單。  
  
```  
void SetCommands(
    CMFCRibbonBar* pRibbonBar,  
    const CList<UINT,UINT>& lstCommands);
```  
  
### <a name="parameters"></a>參數  
 [in]*pRibbonBar*  
 要顯示的按鈕搜尋迷你工具列功能區列。  
  
 [in]*lstCommands*  
 若要顯示在迷你工具列上的命令清單。 所有的功能區分類會搜尋以尋找相關聯的按鈕。  
  
### <a name="remarks"></a>備註  
 此函式可用於設定要顯示在迷你工具列中的命令清單。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`SetCommands`方法的`CMFCRibbonMiniToolBar`類別。 此程式碼片段是一部分[MS Office 2007 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]  
  
##  <a name="show"></a>  CMFCRibbonMiniToolBar::Show  
 顯示位於指定的螢幕座標的迷你工具列。  
  
```  
BOOL Show(
    int x,  
    int y);
```  
  
### <a name="parameters"></a>參數  
 [in]*x*  
 螢幕座標中指定迷你工具列的水平的位置。  
  
 [in]*y*  
 螢幕座標中指定迷你工具列的垂直的位置。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 顯示迷你工具列，則為 TRUE。否則為 FALSE。  
  
##  <a name="showwithcontextmenu"></a>  CMFCRibbonMiniToolBar::ShowWithContextMenu  
 顯示迷你工具列以及操作功能表。  
  
```  
BOOL ShowWithContextMenu(
    int x,  
    int y,  
    UINT uiMenuResID,  
    CWnd* pWndOwner);
```  
  
### <a name="parameters"></a>參數  
 [in]*x*  
 螢幕座標中指定的內容功能表的水平位置。  
  
 [in]*y*  
 螢幕座標中指定的內容功能表的垂直位置。  
  
 [in]*uiMenuResID*  
 指定要顯示內容功能表中的資源 ID。  
  
 [in]*pWndOwner*  
 識別從內容功能表中接收訊息的視窗。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 顯示內容功能表，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式，顯示具有操作功能表的迷你工具列。 操作功能表是迷你工具列下方的定位 15 像素。  
  
##  <a name="iscontextmenumode"></a>  CMFCRibbonMiniToolBar::IsContextMenuMode  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
BOOL IsContextMenuMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isribbonminitoolbar"></a>  CMFCRibbonMiniToolBar::IsRibbonMiniToolBar  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
virtual BOOL IsRibbonMiniToolBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
