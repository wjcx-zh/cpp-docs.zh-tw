---
title: CMFCRibbonStatusBar 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3123206c90bd5dd901e25ff3fe26e48ba8809452
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710504"
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
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|將功能區的 [狀態] 列中的動態項目。|  
|[CMFCRibbonStatusBar::AddElement](#addelement)|將新的功能區項目加入至功能區狀態列中。|  
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|將功能區項目加入至功能區狀態列擴充區域中。|  
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|將功能區的 [狀態] 列中的分隔符號。|  
|[CMFCRibbonStatusBar::Create](#create)|建立功能區狀態列。|  
|[CMFCRibbonStatusBar::CreateEx](#createex)|建立功能區狀態列擴充的樣式。|  
|[CMFCRibbonStatusBar::FindByID](#findbyid)||  
|[CMFCRibbonStatusBar::FindElement](#findelement)|讓指標回到具有指定之命令識別碼的項目|  
|[CMFCRibbonStatusBar::GetCount](#getcount)|傳回位於功能區狀態列的主要區域中的項目數。|  
|[CMFCRibbonStatusBar::GetElement](#getelement)|讓指標回到指定的索引處的項目。|  
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|傳回位於功能區狀態列擴充區域中的項目數。|  
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|傳回指標，該指標指向功能區狀態列擴充區域中，位於指定索引上的元素。|  
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||  
|[CMFCRibbonStatusBar::GetSpace](#getspace)||  
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||  
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||  
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|判斷是否啟用功能區狀態列的資訊模式。|  
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(覆寫[CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout)。)|  
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|移除功能區的 [狀態] 列中的所有項目。|  
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|移除具有指定的命令 ID，從功能區狀態列的項目。|  
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|啟用或停用功能區狀態列的資訊模式。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|在功能區狀態列的資訊模式啟用時，會顯示所顯示的資訊字串。|  
  
## <a name="remarks"></a>備註  
 使用者可以變更所使用的內建的內容功能表功能區狀態列的功能區項目在功能區狀態列上的可見性。 您可以動態加入或移除項目。  
  
 功能區狀態列上包含兩個區域： 主要區域和擴充的區域。 擴充的區域會顯示功能區的 [狀態] 列右邊，而且比主要區域，會出現在不同的色彩。  
  
 一般而言，[狀態] 列的主要區域會顯示狀態的通知，並擴充的區域會顯示檢視控制項。 擴充的區域保持可見狀態時間愈長愈當使用者調整功能區狀態列。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用中的各種方法`CMFCRibbonStatusBar`類別。 此範例示範如何將新的功能區項目加入至功能區狀態列、 功能區狀態列擴充區域中加入功能區項目新增為分隔符號，並啟用功能區狀態列的一般模式。  
  
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
  
##  <a name="adddynamicelement"></a>  CMFCRibbonStatusBar::AddDynamicElement  
 將功能區的 [狀態] 列中的動態項目。  
  
```  
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>參數  
*pElement*<br/>
[in]動態項目的指標。  
  
### <a name="remarks"></a>備註  
 不同規則的項目，於動態元素，而且非屬可自訂狀態列的 [自訂] 功能表不會顯示它們。  
  
##  <a name="addelement"></a>  CMFCRibbonStatusBar::AddElement  
 將新的功能區項目加入至功能區狀態列中。  
  
```  
void AddElement(
    CMFCRibbonBaseElement* pElement,  
    LPCTSTR lpszLabel,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>參數  
*pElement*<br/>
[in]若要加入的項目指標。  
  
*lpszLabel*<br/>
[in]項目的文字標籤。  
  
*bIsVisible*<br/>
[in]如果您想要新增的項目為可見，FALSE 如果您想要新增項目為隱藏，則為 TRUE。  
  
##  <a name="addextendedelement"></a>  CMFCRibbonStatusBar::AddExtendedElement  
 將功能區項目加入至功能區狀態列擴充區域中。  
  
```  
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,  
    LPCTSTR lpszLabel,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>參數  
*pElement*<br/>
[in]若要加入的項目指標。  
  
*lpszLabel*<br/>
[in]項目的文字標籤。  
  
*bIsVisible*<br/>
[in]如果您想要新增的項目為可見，FALSE 如果您想要新增項目為隱藏，則為 TRUE。  
  
### <a name="remarks"></a>備註  
 擴充區域位於狀態列控制項右邊。  
  
##  <a name="addseparator"></a>  CMFCRibbonStatusBar::AddSeparator  
 將功能區的 [狀態] 列中的分隔符號。  
  
```  
void AddSeparator();
```  
  
### <a name="remarks"></a>備註  
 此架構方法之後新增分隔符號[CMFCRibbonStatusBar::AddElement](#addelement)。 將插入的最後一個元素。  
  
##  <a name="create"></a>  CMFCRibbonStatusBar::Create  
 建立功能區狀態列。  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,  
    UINT nID=AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>參數  
*pParentWnd*<br/>
[in]父視窗的指標。  
  
*cheaderctrl:: Create*<br/>
[in]邏輯 OR 運算子組合的控制項的樣式。  
  
*nID*<br/>
[in]狀態列控制項識別碼。  
  
### <a name="return-value"></a>傳回值  
 [狀態] 列已成功建立，FALSE 否則，其值為 TRUE。  
  
##  <a name="createex"></a>  CMFCRibbonStatusBar::CreateEx  
 建立功能區狀態列擴充的樣式。  
  
```  
BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle=0,  
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,  
    UINT nID=AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>參數  
 *pParentWnd*  
 父視窗的指標。  
  
 *dwCtrlStyle*  
 邏輯 OR 運算子組合的建立狀態 列物件的其他樣式。  
  
 *cheaderctrl:: Create*  
 狀態列控制項樣式。  
  
 *nID*  
 狀態列控制項識別碼。  
  
### <a name="return-value"></a>傳回值  
 [狀態] 列已成功建立，FALSE 否則，其值為 TRUE。  
  
##  <a name="findbyid"></a>  CMFCRibbonStatusBar::FindByID  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```  
  
### <a name="parameters"></a>參數  
*uiCmdID*<br/>
[in][in]*BOOL*  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="findelement"></a>  CMFCRibbonStatusBar::FindElement  
 讓指標回到具有指定之命令識別碼的項目  
  
```  
CMFCRibbonBaseElement* FindElement(UINT uiID);
```  
  
### <a name="parameters"></a>參數  
*uiID*<br/>
[in]項目的識別碼。  
  
### <a name="return-value"></a>傳回值  
 具有指定之命令識別碼的項目指標 如果沒有這類項目，則為 NULL。  
  
##  <a name="getcount"></a>  CMFCRibbonStatusBar::GetCount  
 傳回位於功能區狀態列的主要區域中的項目數。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位於功能區狀態列的主要區域中的元素數目。  
  
##  <a name="getelement"></a>  CMFCRibbonStatusBar::GetElement  
 讓指標回到指定的索引處的項目。  
  
```  
CMFCRibbonBaseElement* GetElement(int nIndex);
```  
  
### <a name="parameters"></a>參數  
*nIndex*<br/>
[in]指定以零為起始的索引，位於狀態列控制項的主要區域中的項目。  
  
### <a name="return-value"></a>傳回值  
 位於指定索引處的項目指標。 如果索引是負值或超過在狀態列中的項目數，則為 NULL。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getexcount"></a>  CMFCRibbonStatusBar::GetExCount  
 傳回位於功能區狀態列擴充區域中的項目數。  
  
```  
int GetExCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位於功能區狀態列擴充區域中的元素數目。  
  
##  <a name="getexelement"></a>  CMFCRibbonStatusBar::GetExElement  
 傳回指標，該指標指向功能區狀態列擴充區域中，位於指定索引上的元素。 擴充區域位於狀態列控制項右邊。  
  
```  
CMFCRibbonBaseElement* GetExElement(int nIndex);
```  
  
### <a name="parameters"></a>參數  
*nIndex*<br/>
[in]指定位於狀態列控制項擴充區域中的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 此指標指向功能區狀態列擴充區域中，位於指定索引上的元素。 如果*nIndex*是負數，或超過功能區狀態列擴充區域中的項目數。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getextendedarea"></a>  CMFCRibbonStatusBar::GetExtendedArea  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
virtual BOOL GetExtendedArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*rect*  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getspace"></a>  CMFCRibbonStatusBar::GetSpace  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
int GetSpace() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isbottomframe"></a>  CMFCRibbonStatusBar::IsBottomFrame  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
BOOL IsBottomFrame() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isextendedelement"></a>  CMFCRibbonStatusBar::IsExtendedElement  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*pElement*  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="isinformationmode"></a>  CMFCRibbonStatusBar::IsInformationMode  
 判斷是否啟用功能區狀態列的資訊模式。  
  
```  
BOOL IsInformationMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果 狀態 列可以在 資訊模式; 中工作，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 在資訊模式中，[狀態] 列會隱藏所有規則的窗格，並顯示訊息字串。  
  
##  <a name="ondrawinformation"></a>  CMFCRibbonStatusBar::OnDrawInformation  
 在功能區狀態列的資訊模式啟用時，會顯示顯示的字串。  
  
```  
virtual void OnDrawInformation(
    CDC* pDC,  
    CString& strInfo,  
    CRect rectInfo);
```  
  
### <a name="parameters"></a>參數  
*pDC*<br/>
[in]裝置內容指標。  
  
*strInfo*<br/>
[in]資訊的字串。  
  
*rectInfo*<br/>
[in]週框的矩形。  
  
### <a name="remarks"></a>備註  
 如果您想要自訂狀態列上的資訊字串的外觀，請覆寫這個方法在衍生類別中。 使用[CMFCRibbonStatusBar::SetInformation](#setinformation)方法，將 [狀態] 列中的資訊模式。 在此模式中，[狀態] 列會隱藏所有窗格，並顯示所指定的資訊字串*strInfo*。  
  
##  <a name="recalclayout"></a>  CMFCRibbonStatusBar::RecalcLayout  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="removeall"></a>  CMFCRibbonStatusBar::RemoveAll  
 移除功能區的 [狀態] 列中的所有項目。  
  
```  
void RemoveAll();
```  
  
##  <a name="removeelement"></a>  CMFCRibbonStatusBar::RemoveElement  
 移除具有指定的命令 ID，從功能區狀態列的項目。  
  
```  
BOOL RemoveElement(UINT uiID);
```  
  
### <a name="parameters"></a>參數  
*uiID*<br/>
[in]從 [狀態] 列中移除之項目的識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果具有指定的項目，則為 TRUE *uiID*已移除。 FALSE 否則。  
  
##  <a name="setinformation"></a>  CMFCRibbonStatusBar::SetInformation  
 啟用或停用功能區狀態列的資訊模式。  
  
```  
void SetInformation(LPCTSTR lpszInfo);
```  
  
### <a name="parameters"></a>參數  
*lpszInfo*<br/>
[in]資訊的字串。  
  
### <a name="remarks"></a>備註  
 使用這個方法，將 [狀態] 列中的資訊模式。 在此模式中，[狀態] 列會隱藏所有窗格，並顯示所指定的資訊字串*lpszInfo*。  
  
 NULL lpszInfo 時，狀態列會還原為一般模式。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)   
 [CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
