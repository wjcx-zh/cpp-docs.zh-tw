---
title: "CMFCColorPopupMenu 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorPopupMenu
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorPopupMenu class
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
caps.latest.revision: 19
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
ms.openlocfilehash: 14076d78eaf86ef01e68656685dd2fd102d96311
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu 類別
表示使用者選取色彩的文件或應用程式中使用的快顯功能表。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCColorPopupMenu : public CMFCPopupMenu  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|建構 `CMFCColorPopupMenu` 物件。|  
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|建立可停駐撕色軸。 (覆寫[CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar)。)|  
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|傳回[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) ，內嵌於快顯功能表。 (覆寫[CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar)。)|  
|`CMFCColorPopupMenu::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCColorPopupMenu::SetPropList](#setproplist)|設定的屬性方格控制項物件嵌入的`CMFCColorBar`物件。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|名稱|說明|  
|`m_bEnabledInCustomizeMode`|布林值，決定是否要顯示色軸。|  
|`m_wndColorBar`|`CMFCColorBar`提供色彩選取的物件。|  
  
### <a name="remarks"></a>備註  
 這個類別繼承的快顯功能表功能`CMFCPopupMenu`類別，並管理`CMFCColorBar`提供色彩選取的物件。 當工具列架構是在自訂模式和`m_bEnabledInCustomizeMode`成員設定為`FALSE`，色軸物件不會顯示。 如需自訂模式的詳細資訊，請參閱[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)  
  
 如需詳細資訊`CMFCColorBar`，請參閱[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxcolorpopupmenu.h  
  
##  <a name="a-namecmfccolorpopupmenua--cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a>CMFCColorPopupMenu::CMFCColorPopupMenu  
 建構 `CMFCColorPopupMenu` 物件。  
  
```  
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    int nHorzDockRows,  
    int nVertDockColumns,  
    COLORREF colorAutomatic,  
    UINT uiCommandID,  
    BOOL bStdColorDlg = FALSE);

 
CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic);

 
CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 [in] `colors`  
 架構會顯示快顯功能表的色彩的陣列。  
  
 [in] `color`  
 選取的預設色彩。  
  
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
  
 [in] `nHorzDockRows`  
 色軸水平的停駐時的資料列數目。  
  
 [in] `nVertDockColumns`  
 色軸垂直的停駐時的資料行數目。  
  
 [in] `colorAutomatic`  
 當您按一下 [自動] 按鈕時，此架構套用的預設色彩。  
  
 [in] `uiCommandID`  
 色彩控制命令識別碼。  
  
 [in] `bStdColorDlg`  
 布林值，指出是否要顯示標準系統色彩 對話方塊或[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)對話方塊。  
  
 [in] `pParentBtn`  
 父代按鈕指標。  
  
 [in] `nID`  
 命令 ID。  
  
### <a name="remarks"></a>備註  
 每個多載建構函式集`m_bEnabledInCustomizeMode`成員`FALSE`。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構`CMFCColorPopupMenu`物件。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&34;](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]  
  
##  <a name="a-namecreatetearoffbara--cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a>CMFCColorPopupMenu::CreateTearOffBar  
 建立可停駐撕色軸。  
  
```  
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,  
    UINT uiID,  
    LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pWndMain`|撕下列的父視窗的指標。|  
|[in] `uiID`|撕下列的命令 ID。|  
|[in] `lpszName`|撕下列的視窗文字。|  
  
### <a name="return-value"></a>傳回值  
 新的撕控制列物件的指標。  
  
### <a name="remarks"></a>備註  
 這個方法會建立[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)物件，並將它轉換成[CPane 類別](../../mfc/reference/cpane-class.md)指標。 您可以將此值轉換回[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)指標所使用的其中一個所述的轉換巨集[型別轉型的 MFC 類別物件](../../mfc/reference/type-casting-of-mfc-class-objects.md)。  
  
##  <a name="a-namegetmenubara--cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a>CMFCColorPopupMenu::GetMenuBar  
 傳回[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) ，內嵌於快顯功能表。  
  
```  
virtual CMFCPopupMenuBar* GetMenuBar();
```  
  
### <a name="return-value"></a>傳回值  
 內嵌的指標`CMFCPopupMenuBar`。  
  
### <a name="remarks"></a>備註  
 色彩快顯功能表有內嵌[CMFCPopupMenuBar 類別](../../mfc/reference/cmfcpopupmenubar-class.md)物件。 如果您的應用程式使用不同的內嵌的類型，請覆寫這個方法在衍生類別中。  
  
##  <a name="a-namesetproplista--cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a>CMFCColorPopupMenu::SetPropList  
 設定的屬性方格控制項物件嵌入的`CMFCColorBar`物件。  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndList`  
 屬性方格控制項物件的指標。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

