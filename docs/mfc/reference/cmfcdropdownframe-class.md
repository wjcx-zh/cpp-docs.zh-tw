---
title: "CMFCDropDownFrame 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDropDownFrame
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownFrame class
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
caps.latest.revision: 23
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
ms.openlocfilehash: 5f045e4a3b580f12e64758737495c32963bea6db
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame 類別
提供下拉式清單框架視窗功能下拉式工具列和下拉式工具列按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCDropDownFrame : public CMiniFrameWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|說明|  
|`CMFCDropDownFrame::CMFCDropDownFrame`|預設建構函式。|  
|`CMFCDropDownFrame::~CMFCDropDownFrame`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCDropDownFrame::Create](#create)|建立 `CMFCDropDownFrame` 物件。|  
|`CMFCDropDownFrame::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|擷取父功能表的下拉式清單框架。|  
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|擷取父快顯功能表的下拉式清單的框架。|  
|`CMFCDropDownFrame::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|重新調整位置下拉式框架。|  
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|設定是否會自動終結子下拉式工具列視窗。|  
  
### <a name="remarks"></a>備註  
 這個類別不是直接從您的程式碼使用。  
  
 架構會使用這個類別提供以框架行為`CMFCDropDownToolbar`和`CMFCDropDownToolbarButton`類別。 如需有關這些類別的詳細資訊，請參閱[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)和[CMFCDropDownToolbarButton 類別](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何擷取變數的指標，`CMFCDropDownFrame`物件從`CFrameWnd`類別，以及如何設定子下拉式工具列視窗會自動終結。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&36;](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdropdowntoolbar.h  
  
##  <a name="a-namecreatea--cmfcdropdownframecreate"></a><a name="create"></a>CMFCDropDownFrame::Create  
 建立 `CMFCDropDownFrame` 物件。  
  
```  
virtual BOOL Create(
    CWnd* pWndParent,  
    int x,  
    int y,  
    CMFCDropDownToolBar* pWndOriginToolbar);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pWndParent`|父框架的視窗下拉式清單。|  
|[in] `x`|水平的螢幕座標，向下框架的位置。|  
|[in] `y`|位置清單向下框架的垂直螢幕座標。|  
|[in] `pWndOriginToolbar`|會顯示這個方法會填入新的下拉式清單框架物件使用的下拉式按鈕的工具列。|  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功建立下拉式框架。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫基底[CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法來建立下拉式框架視窗與`WS_POPUP`樣式。 在下拉式清單框架視窗會出現在指定的螢幕座標。 如果[CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法會傳回`FALSE`。  
  
 `CMFCDropDownFrame`類別會建立一份提供的`CMFCDropDownToolBar`參數。 這個方法會複製按鈕影像和按鈕狀態從`pWndOriginToolbar`參數`m_pWndOriginToolbar`資料成員。  
  
##  <a name="a-namegetparentmenubara--cmfcdropdownframegetparentmenubar"></a><a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar  
 擷取父功能表的下拉式清單框架。  
  
```  
CMFCMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 下拉式清單畫面格的父功能表列的指標或`NULL`如果框架沒有父代。  
  
### <a name="remarks"></a>備註  
 這個方法會擷取父功能表的 [父] 按鈕。 這個方法會傳回`NULL`如果下拉式清單框架有沒有父代按鈕或 [父] 按鈕有沒有父功能表列。  
  
##  <a name="a-namegetparentpopupmenua--cmfcdropdownframegetparentpopupmenu"></a><a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu  
 擷取父快顯功能表的下拉式清單的框架。  
  
```  
CMFCDropDownFrame* GetParentPopupMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 父下拉式選單中的下拉式清單框架的指標或`NULL`如果框架沒有父代。  
  
### <a name="remarks"></a>備註  
 這個方法會擷取在父功能表的 [父] 按鈕。 這個方法會傳回`NULL`如果下拉式清單框架有沒有父代按鈕或 [父] 按鈕有沒有父功能表。  
  
##  <a name="a-namerecalclayouta--cmfcdropdownframerecalclayout"></a><a name="recalclayout"></a>CMFCDropDownFrame::RecalcLayout  
 重新調整位置下拉式框架。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `bNotify`|未使用。|  
  
### <a name="remarks"></a>備註  
 建立下拉式框架時，或者調整父視窗的大小，架構會呼叫這個方法。 這個方法會計算所使用的位置和大小的父視窗的位置和大小下拉式框架。  
  
##  <a name="a-namesetautodestroya--cmfcdropdownframesetautodestroy"></a><a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy  
 設定是否會自動終結子下拉式工具列視窗。  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bAutoDestroy`  
 `TRUE`自動終結相關聯的下拉式清單工具列的視窗。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果`bAutoDestroy`是`TRUE`，然後在`CMFCDropDownFrame`解構函式會終結相關聯的下拉式清單工具列視窗。 預設值是 `TRUE`。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCDropDownToolbarButton 類別](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

