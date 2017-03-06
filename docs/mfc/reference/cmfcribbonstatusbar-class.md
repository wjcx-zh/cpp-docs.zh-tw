---
title: "CMFCRibbonStatusBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonStatusBar class
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
caps.latest.revision: 37
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
ms.openlocfilehash: 8fc2ec14c3f6320f45128bf36824ce7f9b8de9c5
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar 類別
`CMFCRibbonStatusBar`類別會實作可以顯示功能區項目的狀態列控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonStatusBar : public CMFCRibbonBar  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|將動態項目加入至功能區狀態列。|  
|[CMFCRibbonStatusBar::AddElement](#addelement)|將新的功能區項目加入至功能區狀態列。|  
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|將功能區項目加入至功能區狀態列擴充區域中。|  
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|將功能區狀態列的分隔符號。|  
|[CMFCRibbonStatusBar::Create](#create)|建立功能區狀態列。|  
|[CMFCRibbonStatusBar::CreateEx](#createex)|建立功能區狀態列擴充的樣式。|  
|[CMFCRibbonStatusBar::FindByID](#findbyid)||  
|[CMFCRibbonStatusBar::FindElement](#findelement)|具有指定的命令 ID 的項目中傳回的指標|  
|[CMFCRibbonStatusBar::GetCount](#getcount)|傳回位於功能區狀態列的主要區域中的項目數目。|  
|[CMFCRibbonStatusBar::GetElement](#getelement)|傳回位於指定索引處的元素的指標。|  
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|傳回位於功能區狀態列擴充區域中的項目數目。|  
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|傳回指標，該指標指向功能區狀態列擴充區域中，位於指定索引上的元素。|  
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||  
|[CMFCRibbonStatusBar::GetSpace](#getspace)||  
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||  
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||  
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|判斷是否啟用功能區狀態列的資訊模式。|  
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(覆寫[CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout)。)|  
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|從功能區狀態列中移除所有項目。|  
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|移除具有指定的命令識別碼，從功能區狀態列的項目。|  
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|啟用或停用功能區狀態列的資訊模式。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|功能區狀態列的啟用資訊模式時，會顯示資訊的字串，會出現。|  
  
## <a name="remarks"></a>備註  
 使用者可以利用內建的快顯功能表功能區狀態列的變更在功能區狀態列的功能區項目的可見性。 您可以動態加入或移除項目。  
  
 功能區狀態列上包含兩個區域︰ 主要區域和擴充的區域。 擴充的區域會顯示在功能區狀態列的右側，並出現在不同的色彩比主要區域。  
  
 一般而言，[狀態] 列的主要區域會顯示狀態通知，並擴充的區域顯示檢視控制項。 當使用者調整功能區狀態列，保持盡可能可見擴充的區域。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCRibbonStatusBar`類別。 此範例示範如何將新的功能區項目加入至功能區狀態列、 功能區項目加入至功能區狀態列擴充區域新增為分隔符號，並啟用功能區狀態列的一般模式。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&15;](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]  
[!code-cpp[NVC_MFC_RibbonApp #&16;](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)  
  
 [CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxribbonstatusbar.h  
  
##  <a name="a-nameadddynamicelementa--cmfcribbonstatusbaradddynamicelement"></a><a name="adddynamicelement"></a>CMFCRibbonStatusBar::AddDynamicElement  
 將動態項目加入至功能區狀態列。  
  
```  
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>參數  
 [in] `pElement`  
 動態項目之指標。  
  
### <a name="remarks"></a>備註  
 不同於規則的項目動態項目不是可自訂和狀態列的 [自訂] 功能表不會顯示它們。  
  
##  <a name="a-nameaddelementa--cmfcribbonstatusbaraddelement"></a><a name="addelement"></a>CMFCRibbonStatusBar::AddElement  
 將新的功能區項目加入至功能區狀態列。  
  
```  
void AddElement(
    CMFCRibbonBaseElement* pElement,  
    LPCTSTR lpszLabel,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pElement`  
 加入項目的指標。  
  
 [in] `lpszLabel`  
 項目的文字標籤。  
  
 [in] `bIsVisible`  
 `TRUE`如果您想要將項目新增為可見，`FALSE`如果您想要新增項目做為隱藏。  
  
##  <a name="a-nameaddextendedelementa--cmfcribbonstatusbaraddextendedelement"></a><a name="addextendedelement"></a>CMFCRibbonStatusBar::AddExtendedElement  
 將功能區項目加入至功能區狀態列擴充區域中。  
  
```  
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,  
    LPCTSTR lpszLabel,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pElement`  
 加入項目的指標。  
  
 [in] `lpszLabel`  
 項目的文字標籤。  
  
 [in] `bIsVisible`  
 `TRUE`如果您想要將項目新增為可見，`FALSE`如果您想要新增項目做為隱藏。  
  
### <a name="remarks"></a>備註  
 擴充區域位於狀態列控制項右邊。  
  
##  <a name="a-nameaddseparatora--cmfcribbonstatusbaraddseparator"></a><a name="addseparator"></a>CMFCRibbonStatusBar::AddSeparator  
 將功能區狀態列的分隔符號。  
  
```  
void AddSeparator();
```  
  
### <a name="remarks"></a>備註  
 架構的方法後面加入分隔符號[CMFCRibbonStatusBar::AddElement](#addelement)。 將最後一個項目。  
  
##  <a name="a-namecreatea--cmfcribbonstatusbarcreate"></a><a name="create"></a>CMFCRibbonStatusBar::Create  
 建立功能區狀態列。  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,  
    UINT nID=AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParentWnd`  
 父視窗的指標。  
  
 [in] `dwStyle`  
 邏輯 OR 運算子組合控制項樣式。  
  
 [in] `nID`  
 狀態列控制項 ID。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果建立成功，狀態列`FALSE`否則。  
  
##  <a name="a-namecreateexa--cmfcribbonstatusbarcreateex"></a><a name="createex"></a>CMFCRibbonStatusBar::CreateEx  
 建立功能區狀態列擴充的樣式。  
  
```  
BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle=0,  
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,  
    UINT nID=AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>參數  
 `pParentWnd`  
 父視窗的指標。  
  
 `dwCtrlStyle`  
 建立狀態列物件的其他樣式的邏輯 OR 組合。  
  
 `dwStyle`  
 狀態列控制項樣式。  
  
 `nID`  
 狀態列控制項 ID。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果建立成功，狀態列`FALSE`否則。  
  
##  <a name="a-namefindbyida--cmfcribbonstatusbarfindbyid"></a><a name="findbyid"></a>CMFCRibbonStatusBar::FindByID  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdID`  
 [in] `BOOL`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namefindelementa--cmfcribbonstatusbarfindelement"></a><a name="findelement"></a>CMFCRibbonStatusBar::FindElement  
 具有指定的命令 ID 的項目中傳回的指標  
  
```  
CMFCRibbonBaseElement* FindElement(UINT uiID);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiID`  
 項目的識別碼。  
  
### <a name="return-value"></a>傳回值  
 指向項目具有指定之的命令 id。 `NULL`如果沒有這類項目。  
  
##  <a name="a-namegetcounta--cmfcribbonstatusbargetcount"></a><a name="getcount"></a>CMFCRibbonStatusBar::GetCount  
 傳回位於功能區狀態列的主要區域中的項目數目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位於功能區狀態列的主要區域中的項目數目。  
  
##  <a name="a-namegetelementa--cmfcribbonstatusbargetelement"></a><a name="getelement"></a>CMFCRibbonStatusBar::GetElement  
 傳回位於指定索引處的元素的指標。  
  
```  
CMFCRibbonBaseElement* GetElement(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定位於狀態列控制項的主要區域中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 位於指定索引處的項目指標。 `NULL`如果索引是負值，或超過在狀態列中的項目數。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetexcounta--cmfcribbonstatusbargetexcount"></a><a name="getexcount"></a>CMFCRibbonStatusBar::GetExCount  
 傳回位於功能區狀態列擴充區域中的項目數目。  
  
```  
int GetExCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位於功能區狀態列擴充區域中的項目數目。  
  
##  <a name="a-namegetexelementa--cmfcribbonstatusbargetexelement"></a><a name="getexelement"></a>CMFCRibbonStatusBar::GetExElement  
 傳回指標，該指標指向功能區狀態列擴充區域中，位於指定索引上的元素。 擴充區域位於狀態列控制項右邊。  
  
```  
CMFCRibbonBaseElement* GetExElement(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定位於狀態列控制項擴充區域中之元素的以零起始索引。  
  
### <a name="return-value"></a>傳回值  
 此指標指向功能區狀態列擴充區域中，位於指定索引上的元素。 如果 `NULL` 為負數，或超過功能區狀態列擴充區域中的元素數目，則為 `nIndex`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetextendedareaa--cmfcribbonstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCRibbonStatusBar::GetExtendedArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL GetExtendedArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `rect`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetspacea--cmfcribbonstatusbargetspace"></a><a name="getspace"></a>CMFCRibbonStatusBar::GetSpace  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetSpace() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisbottomframea--cmfcribbonstatusbarisbottomframe"></a><a name="isbottomframe"></a>CMFCRibbonStatusBar::IsBottomFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsBottomFrame() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisextendedelementa--cmfcribbonstatusbarisextendedelement"></a><a name="isextendedelement"></a>CMFCRibbonStatusBar::IsExtendedElement  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pElement`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisinformationmodea--cmfcribbonstatusbarisinformationmode"></a><a name="isinformationmode"></a>CMFCRibbonStatusBar::IsInformationMode  
 判斷是否啟用功能區狀態列的資訊模式。  
  
```  
BOOL IsInformationMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 [狀態] 列可以使用資訊模式;否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 在資訊模式中，[狀態] 列會隱藏所有規則的窗格，並顯示訊息字串。  
  
##  <a name="a-nameondrawinformationa--cmfcribbonstatusbarondrawinformation"></a><a name="ondrawinformation"></a>CMFCRibbonStatusBar::OnDrawInformation  
 在功能區狀態列上啟用資訊模式時，會顯示字串，會出現。  
  
```  
virtual void OnDrawInformation(
    CDC* pDC,  
    CString& strInfo,  
    CRect rectInfo);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `strInfo`  
 資訊的字串。  
  
 [in] `rectInfo`  
 週框。  
  
### <a name="remarks"></a>備註  
 如果您想要自訂狀態列上的資訊字串的外觀，請覆寫這個方法在衍生類別中。 使用[CMFCRibbonStatusBar::SetInformation](#setinformation)方法，以將狀態列放置在資訊模式。 在此模式中，狀態列會隱藏所有窗格，並會顯示所指定的資訊字串`strInfo`。  
  
##  <a name="a-namerecalclayouta--cmfcribbonstatusbarrecalclayout"></a><a name="recalclayout"></a>CMFCRibbonStatusBar::RecalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameremovealla--cmfcribbonstatusbarremoveall"></a><a name="removeall"></a>CMFCRibbonStatusBar::RemoveAll  
 從功能區狀態列中移除所有項目。  
  
```  
void RemoveAll();
```  
  
##  <a name="a-nameremoveelementa--cmfcribbonstatusbarremoveelement"></a><a name="removeelement"></a>CMFCRibbonStatusBar::RemoveElement  
 移除具有指定的命令識別碼，從功能區狀態列的項目。  
  
```  
BOOL RemoveElement(UINT uiID);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiID`  
 從 [狀態] 列中移除之項目的識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果具有指定的項目`uiID`已移除。 否則為 `FALSE`。  
  
##  <a name="a-namesetinformationa--cmfcribbonstatusbarsetinformation"></a><a name="setinformation"></a>CMFCRibbonStatusBar::SetInformation  
 啟用或停用功能區狀態列的資訊模式。  
  
```  
void SetInformation(LPCTSTR lpszInfo);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszInfo`  
 資訊的字串。  
  
### <a name="remarks"></a>備註  
 使用這個方法，將 [狀態] 列中的資訊模式。 在此模式中，狀態列會隱藏所有窗格，並會顯示所指定的資訊字串`lpszInfo`。  
  
 LpszInfo 時`NULL`，狀態列會還原為一般模式。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)   
 [CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)

