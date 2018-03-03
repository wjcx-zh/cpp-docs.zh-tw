---
title: "CMFCRibbonStatusBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 596d39f5d6338f7a16e7a6090fbc47f5ca799d6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar 類別
`CMFCRibbonStatusBar`類別會實作狀態列控制項可以顯示功能區項目。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonStatusBar : public CMFCRibbonBar  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|將動態項目加入至功能區狀態列。|  
|[CMFCRibbonStatusBar::AddElement](#addelement)|將新的功能區項目加入至功能區狀態列。|  
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|將功能區項目加入至功能區狀態列擴充區域中。|  
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|將功能區狀態列的分隔字元。|  
|[CMFCRibbonStatusBar::Create](#create)|建立功能區狀態列。|  
|[CMFCRibbonStatusBar::CreateEx](#createex)|建立功能區狀態列擴充的樣式。|  
|[CMFCRibbonStatusBar::FindByID](#findbyid)||  
|[CMFCRibbonStatusBar::FindElement](#findelement)|讓指標回到具有指定之命令識別碼的項目|  
|[CMFCRibbonStatusBar::GetCount](#getcount)|傳回位於功能區狀態列的主要區域中的項目數目。|  
|[CMFCRibbonStatusBar::GetElement](#getelement)|讓指標回到指定的索引處的項目。|  
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|傳回位於功能區狀態列擴充區域中的項目數目。|  
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|傳回指標，該指標指向功能區狀態列擴充區域中，位於指定索引上的元素。|  
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||  
|[CMFCRibbonStatusBar::GetSpace](#getspace)||  
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||  
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||  
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|判斷是否啟用功能區狀態列的資訊模式。|  
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(覆寫[CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout)。)|  
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|從功能區狀態列中移除所有項目。|  
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|移除具有指定的命令識別碼，從功能區狀態列的元素。|  
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|啟用或停用功能區狀態列的資訊模式。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|在功能區狀態列的資訊模式啟用時顯示資訊的字串，會出現。|  
  
## <a name="remarks"></a>備註  
 使用者可以透過內建的快顯功能表功能區狀態列的變更在功能區狀態列的功能區項目的可見性。 您可以動態加入或移除項目。  
  
 功能區狀態列上包含兩個區域： 主要區域和擴充的區域。 擴充的區域會顯示在功能區狀態列的右邊，而且比主要區域，會出現在不同的色彩。  
  
 一般而言，[狀態] 列的主要區域會顯示狀態通知，並擴充的區域顯示檢視控制項。 擴充的區域保持可見狀態盡可能長期當使用者調整功能區狀態列的大小。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCRibbonStatusBar`類別。 此範例顯示如何將新的功能區項目加入至功能區狀態列，功能區狀態列擴充區域中加入功能區項目新增為分隔符號，並啟用功能區狀態列的一般模式。  
  
 [!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]  
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)  
  
 [CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxribbonstatusbar.h  
  
##  <a name="adddynamicelement"></a>CMFCRibbonStatusBar::AddDynamicElement  
 將動態項目加入至功能區狀態列。  
  
```  
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pElement`  
 動態項目之指標。  
  
### <a name="remarks"></a>備註  
 不同於規則的項目動態項目不是可自訂並自訂 功能表的 狀態 列不會顯示它們。  
  
##  <a name="addelement"></a>CMFCRibbonStatusBar::AddElement  
 將新的功能區項目加入至功能區狀態列。  
  
```  
void AddElement(
    CMFCRibbonBaseElement* pElement,  
    LPCTSTR lpszLabel,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pElement`  
 加入項目的指標。  
  
 [輸入] `lpszLabel`  
 項目的文字標籤。  
  
 [輸入] `bIsVisible`  
 `TRUE`如果您想要將項目新增為可見，`FALSE`如果您想要新增項目，做為隱藏。  
  
##  <a name="addextendedelement"></a>CMFCRibbonStatusBar::AddExtendedElement  
 將功能區項目加入至功能區狀態列擴充區域中。  
  
```  
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,  
    LPCTSTR lpszLabel,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pElement`  
 加入項目的指標。  
  
 [輸入] `lpszLabel`  
 項目的文字標籤。  
  
 [輸入] `bIsVisible`  
 `TRUE`如果您想要將項目新增為可見，`FALSE`如果您想要新增項目，做為隱藏。  
  
### <a name="remarks"></a>備註  
 擴充區域位於狀態列控制項右邊。  
  
##  <a name="addseparator"></a>CMFCRibbonStatusBar::AddSeparator  
 將功能區狀態列的分隔字元。  
  
```  
void AddSeparator();
```  
  
### <a name="remarks"></a>備註  
 架構方法之後加入分隔符號[CMFCRibbonStatusBar::AddElement](#addelement)。 將插入的最後一個元素。  
  
##  <a name="create"></a>CMFCRibbonStatusBar::Create  
 建立功能區狀態列。  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,  
    UINT nID=AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pParentWnd`  
 父視窗的指標。  
  
 [輸入] `dwStyle`  
 邏輯 OR 組合的控制項樣式。  
  
 [輸入] `nID`  
 狀態列控制項 ID。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功，建立狀態列`FALSE`否則。  
  
##  <a name="createex"></a>CMFCRibbonStatusBar::CreateEx  
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
 `TRUE`如果成功，建立狀態列`FALSE`否則。  
  
##  <a name="findbyid"></a>CMFCRibbonStatusBar::FindByID  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiCmdID`  
 [輸入] `BOOL`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="findelement"></a>CMFCRibbonStatusBar::FindElement  
 讓指標回到具有指定之命令識別碼的項目  
  
```  
CMFCRibbonBaseElement* FindElement(UINT uiID);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiID`  
 項目的識別碼。  
  
### <a name="return-value"></a>傳回值  
 指標的項目具有指定的命令識別碼。 `NULL`如果沒有這類項目。  
  
##  <a name="getcount"></a>CMFCRibbonStatusBar::GetCount  
 傳回位於功能區狀態列的主要區域中的項目數目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位於功能區狀態列的主要區域中的元素數目。  
  
##  <a name="getelement"></a>CMFCRibbonStatusBar::GetElement  
 讓指標回到指定的索引處的項目。  
  
```  
CMFCRibbonBaseElement* GetElement(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nIndex`  
 指定位於狀態列控制項的主要區域中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 位於指定索引處的項目之指標。 `NULL`如果索引是負值或超過在狀態列中的項目數。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getexcount"></a>CMFCRibbonStatusBar::GetExCount  
 傳回位於功能區狀態列擴充區域中的項目數目。  
  
```  
int GetExCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位於功能區狀態列擴充區域中的元素數目。  
  
##  <a name="getexelement"></a>CMFCRibbonStatusBar::GetExElement  
 傳回指標，該指標指向功能區狀態列擴充區域中，位於指定索引上的元素。 擴充區域位於狀態列控制項右邊。  
  
```  
CMFCRibbonBaseElement* GetExElement(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nIndex`  
 指定位於狀態列控制項擴充區域中之元素的以零起始索引。  
  
### <a name="return-value"></a>傳回值  
 此指標指向功能區狀態列擴充區域中，位於指定索引上的元素。 如果 `NULL` 為負數，或超過功能區狀態列擴充區域中的元素數目，則為 `nIndex`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getextendedarea"></a>CMFCRibbonStatusBar::GetExtendedArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL GetExtendedArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `rect`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getspace"></a>CMFCRibbonStatusBar::GetSpace  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetSpace() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isbottomframe"></a>CMFCRibbonStatusBar::IsBottomFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsBottomFrame() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isextendedelement"></a>CMFCRibbonStatusBar::IsExtendedElement  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pElement`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isinformationmode"></a>CMFCRibbonStatusBar::IsInformationMode  
 判斷是否啟用功能區狀態列的資訊模式。  
  
```  
BOOL IsInformationMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 [狀態] 列可以使用以資訊模式;否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 在資訊模式中，[狀態] 列會隱藏所有規則的窗格，並顯示訊息字串。  
  
##  <a name="ondrawinformation"></a>CMFCRibbonStatusBar::OnDrawInformation  
 顯示字串，會出現在功能區狀態列的資訊模式啟用時。  
  
```  
virtual void OnDrawInformation(
    CDC* pDC,  
    CString& strInfo,  
    CRect rectInfo);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標。  
  
 [輸入] `strInfo`  
 資訊的字串。  
  
 [輸入] `rectInfo`  
 週框。  
  
### <a name="remarks"></a>備註  
 如果您想要自訂 [狀態] 列上的資訊字串的外觀，請覆寫這個方法在衍生類別中。 使用[CMFCRibbonStatusBar::SetInformation](#setinformation)方法，將 [狀態] 列置於資訊模式。 在此模式中，[狀態] 列會隱藏所有窗格，顯示所指定的資訊字串`strInfo`。  
  
##  <a name="recalclayout"></a>CMFCRibbonStatusBar::RecalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="removeall"></a>CMFCRibbonStatusBar::RemoveAll  
 從功能區狀態列中移除所有項目。  
  
```  
void RemoveAll();
```  
  
##  <a name="removeelement"></a>CMFCRibbonStatusBar::RemoveElement  
 移除具有指定的命令識別碼，從功能區狀態列的元素。  
  
```  
BOOL RemoveElement(UINT uiID);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiID`  
 從 [狀態] 列中移除項目的 ID。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果具有指定的項目`uiID`已移除。 否則為 `FALSE`。  
  
##  <a name="setinformation"></a>CMFCRibbonStatusBar::SetInformation  
 啟用或停用功能區狀態列的資訊模式。  
  
```  
void SetInformation(LPCTSTR lpszInfo);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszInfo`  
 資訊的字串。  
  
### <a name="remarks"></a>備註  
 使用這個方法，將 [狀態] 列中的資訊模式。 在此模式中，[狀態] 列會隱藏所有窗格，顯示所指定的資訊字串`lpszInfo`。  
  
 LpszInfo 時`NULL`，狀態列會還原為一般模式。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)   
 [CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
