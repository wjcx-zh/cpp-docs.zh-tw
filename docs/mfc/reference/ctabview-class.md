---
title: "CTabView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTabView
dev_langs:
- C++
helpviewer_keywords:
- CTabView class
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
caps.latest.revision: 32
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
ms.openlocfilehash: 20f5745c3784e771d6ec95f7d4dc363142c687f8
ms.lasthandoff: 02/24/2017

---
# <a name="ctabview-class"></a>CTabView 類別
`CTabView`類別簡化了使用索引標籤控制項類別 ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) 在使用 MFC 的文件/檢視架構的應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
class CTabbedView : public CView  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CTabView::AddView](#addview)|將新的檢視加入至索引標籤控制項。|  
|[CTabView::FindTab](#findtab)|傳回指定之檢視的索引 索引標籤控制項中。|  
|[CTabView::GetActiveView](#getactiveview)|將指標傳回至目前使用的檢視|  
|[CTabView::GetTabControl](#gettabcontrol)|傳回與檢視相關聯的索引標籤控制項的參考。|  
|[CTabView::RemoveView](#removeview)|從索引標籤控制項移除檢視。|  
|[CTabView::SetActiveView](#setactiveview)|讓檢視成為使用中。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CTabView::IsScrollBar](#isscrollbar)|在建立索引標籤檢視來判斷索引標籤檢視是否有共用水平捲軸時，由架構呼叫。|  
|[CTabView::OnActivateView](#onactivateview)|索引標籤檢視進行作用中或非作用中時，由架構呼叫。|  
  
## <a name="remarks"></a>備註  
 此類別可讓您輕鬆地將索引標籤式的檢視放入文件/檢視應用程式。 `CTabView`是`CView`-衍生的類別，其中包含內嵌`CMFCTabCtrl`物件。 `CTabView`處理支援所需的所有訊息`CMFCTabCtrl`物件。 直接衍生自`CTabView`並插入您的應用程式，然後新增`CView`-藉由衍生類別`AddView`方法。 這些檢視就會顯示索引標籤控制項 索引標籤。  
  
 例如，您可能可以用不同的方式表示的文件︰ 試算表、 圖表、 可編輯的表單等等。 您可以建立繪圖資料所需的個別檢視、 插入到您`CTabView`-衍生物件，並讓它們不含任何額外的程式碼索引標籤。  
  
 [TabbedView 範例︰ MFC 索引標籤式檢視應用程式](../../visual-cpp-samples.md)說明使用方式的`CTabView`。  
  
## <a name="example"></a>範例  
 下列範例將示範如何`CTabView`TabbedView 範例中使用。  
  
 [!code-cpp[NVC_MFC_TabbedView #&1;](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxTabView.h  
  
##  <a name="a-nameaddviewa--ctabviewaddview"></a><a name="addview"></a>CTabView::AddView  
 將檢視加入至索引標籤控制項。  
  
```  
int AddView(
    CRuntimeClass* pViewClass,  
    const CString& strViewLabel,  
    int iIndex=-1,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pViewClass`  
 [插入] 檢視的執行階段類別的指標。  
  
 [in] `strViewLabel`  
 指定在索引標籤的文字。  
  
 [in] `iIndex`  
 指定要插入的檢視以零為起始的位置。 如果這個位置是新的索引標籤插入尾端的-1。  
  
 [in] `pContext`  
 指標`CCreateContext`的檢視。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為檢視索引。 反之則為-1。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可加入內嵌於框架 索引標籤控制項的檢視。  
  
##  <a name="a-namefindtaba--ctabviewfindtab"></a><a name="findtab"></a>CTabView::FindTab  
 傳回指定之檢視的索引 索引標籤控制項中。  
  
```  
int FindTab(HWND hWndView) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `hWndView`  
 檢視的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果找到，檢視的索引反之則為-1。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可擷取具有指定控制代碼的檢視索引。  
  
##  <a name="a-namegetactiveviewa--ctabviewgetactiveview"></a><a name="getactiveview"></a>CTabView::GetActiveView  
 傳回目前使用中檢視的指標。  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 有效的指標使用中的檢視，或`NULL`如果沒有使用中的檢視。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettabcontrola--ctabviewgettabcontrol"></a><a name="gettabcontrol"></a>CTabView::GetTabControl  
 傳回與檢視相關聯的索引標籤控制項的參考。  
  
```  
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```  
  
### <a name="return-value"></a>傳回值  
 與檢視相關聯的索引標籤控制項參考。  
  
##  <a name="a-nameisscrollbara--ctabviewisscrollbar"></a><a name="isscrollbar"></a>CTabView::IsScrollBar  
 在建立索引標籤檢視來判斷索引標籤檢視是否有共用水平捲軸時，由架構呼叫。  
  
```  
virtual BOOL IsScrollBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果應該建立索引標籤檢視，以及共用的捲軸。 否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法時`CTabView`建立物件。  
  
 覆寫`IsScrollBar`方法中的`CTabView`-衍生類別，並傳回`TRUE`如果您想要建立具有共用水平捲軸檢視。  
  
##  <a name="a-nameonactivateviewa--ctabviewonactivateview"></a><a name="onactivateview"></a>CTabView::OnActivateView  
 索引標籤檢視進行作用中或非作用中時，由架構呼叫。  
  
```  
virtual void OnActivateView(CView* view);
```  
  
### <a name="parameters"></a>參數  
 [in] `view`  
 檢視指標。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。 覆寫這個方法在`CTabView`-衍生的類別來處理此通知。  
  
##  <a name="a-nameremoveviewa--ctabviewremoveview"></a><a name="removeview"></a>CTabView::RemoveView  
 從索引標籤控制項移除檢視。  
  
```  
BOOL RemoveView(int iTabNum);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTabNum`  
 要移除之檢視的索引。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功移除檢視的索引。 否則為-1。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetactiveviewa--ctabviewsetactiveview"></a><a name="setactiveview"></a>CTabView::SetActiveView  
 讓檢視成為使用中。  
  
```  
BOOL SetActiveView(int iTabNum);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTabNum`  
 索引標籤檢視以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果指定的檢視已啟用，`FALSE`如果檢視的索引無效。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)   
 [CView 類別](../../mfc/reference/cview-class.md)

