---
title: CTabView 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
dev_langs:
- C++
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d64d503c4bad0d452be174064e2932ed100d7de
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121753"
---
# <a name="ctabview-class"></a>CTabView 類別
`CTabView`類別簡化索引標籤控制項類別的使用 ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) 在使用 MFC 的文件/檢視架構的應用程式。  
  
## <a name="syntax"></a>語法  
  
```  
class CTabbedView : public CView  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTabView::AddView](#addview)|將新的檢視加入至索引標籤控制項。|  
|[CTabView::FindTab](#findtab)|傳回指定檢視的索引 索引標籤控制項中。|  
|[CTabView::GetActiveView](#getactiveview)|讓指標回到目前使用的檢視|  
|[CTabView::GetTabControl](#gettabcontrol)|傳回與檢視相關聯的索引標籤控制項的參考。|  
|[CTabView::RemoveView](#removeview)|移除索引標籤控制項中的檢視。|  
|[CTabView::SetActiveView](#setactiveview)|讓檢視成為使用中。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTabView::IsScrollBar](#isscrollbar)|在建立索引標籤檢視來判斷索引標籤檢視是否有共用水平捲軸時，由架構呼叫。|  
|[CTabView::OnActivateView](#onactivateview)|索引標籤檢視進行作用中或非使用中時，由架構呼叫。|  
  
## <a name="remarks"></a>備註  
 此類別可讓您更容易置於文件/檢視應用程式中的索引標籤式的檢視。 `CTabView` 是`CView`-衍生的類別，其中包含內嵌`CMFCTabCtrl`物件。 `CTabView` 會處理所有訊息才能支援`CMFCTabCtrl`物件。 只是衍生自`CTabView`並插入您的應用程式，然後新增`CView`-衍生類別使用`AddView`方法。 此索引標籤控制項顯示這些檢視表與索引標籤。  
  
 比方說，您可能會有的文件，可以用不同的方式表示： 試算表、 圖表、 可編輯的表單，等等。 您可以建立視繪製資料的個別檢視、 插入到您`CTabView`-衍生物件，並讓他們不含任何額外的程式碼索引標籤。  
  
 [TabbedView 範例： MFC 索引標籤式檢視應用程式](../../visual-cpp-samples.md)說明的使用方式`CTabView`。  
  
## <a name="example"></a>範例  
 下列範例會示範如何`CTabView`TabbedView 範例中使用。  
  
 [!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]  
  
## <a name="requirements"></a>需求  
 **標頭：** afxTabView.h  
  
##  <a name="addview"></a>  CTabView::AddView  
 將檢視加入至索引標籤控制項。  
  
```  
int AddView(
    CRuntimeClass* pViewClass,  
    const CString& strViewLabel,  
    int iIndex=-1,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in]*pViewClass*  
 執行階段類別，插入檢視的指標。  
  
 [in]*strViewLabel*  
 指定在索引標籤的文字。  
  
 [in]*iIndex*  
 指定要插入檢視以零為起始的位置。 如果這個位置是新的索引標籤插入尾端的-1。  
  
 [in]*pContext*  
 指標`CCreateContext`的檢視。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為檢視索引。 否則為-1。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可將檢視加入至索引標籤控制項內嵌在框架中。  
  
##  <a name="findtab"></a>  CTabView::FindTab  
 傳回指定檢視的索引 索引標籤控制項中。  
  
```  
int FindTab(HWND hWndView) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*hWndView*  
 檢視的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果找到; 檢視的索引否則為-1。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可擷取具有指定的控制代碼檢視的索引。  
  
##  <a name="getactiveview"></a>  CTabView::GetActiveView  
 讓指標回到目前使用的檢視。  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 有效指標的使用中的檢視或為 NULL，如果沒有使用中的檢視。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettabcontrol"></a>  CTabView::GetTabControl  
 傳回與檢視相關聯的索引標籤控制項的參考。  
  
```  
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```  
  
### <a name="return-value"></a>傳回值  
 與檢視相關聯的索引標籤控制項的參考。  
  
##  <a name="isscrollbar"></a>  CTabView::IsScrollBar  
 在建立索引標籤檢視來判斷索引標籤檢視是否有共用水平捲軸時，由架構呼叫。  
  
```  
virtual BOOL IsScrollBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果索引標籤檢視應該要建立與共用的捲軸，則為 TRUE。 否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法時*CTabView*建立物件。  
  
 覆寫*IsScrollBar*方法中的*CTabView*-衍生類別，並傳回 TRUE，如果您想要建立的檢視，有共用水平捲軸。  
  
##  <a name="onactivateview"></a>  CTabView::OnActivateView  
 索引標籤檢視進行作用中或非使用中時，由架構呼叫。  
  
```  
virtual void OnActivateView(CView* view);
```  
  
### <a name="parameters"></a>參數  
 [in]*檢視*  
 檢視指標。  
  
### <a name="remarks"></a>備註  
 預設實作不做任何動作。 覆寫這個方法在`CTabView`-衍生的類別處理此通知。  
  
##  <a name="removeview"></a>  CTabView::RemoveView  
 移除索引標籤控制項中的檢視。  
  
```  
BOOL RemoveView(int iTabNum);
```  
  
### <a name="parameters"></a>參數  
 [in]*iTabNum*  
 要移除之檢視的索引。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功移除檢視的索引。 否則為-1。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setactiveview"></a>  CTabView::SetActiveView  
 讓檢視成為使用中。  
  
```  
BOOL SetActiveView(int iTabNum);
```  
  
### <a name="parameters"></a>參數  
 [in]*iTabNum*  
 索引標籤檢視以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果指定的檢視已啟用，FALSE 如果檢視的索引無效，則為 TRUE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)   
 [CView 類別](../../mfc/reference/cview-class.md)
