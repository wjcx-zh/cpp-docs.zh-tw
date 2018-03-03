---
title: "CMFCRibbonCustomizeDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c674cc127f08109ecf40d99d890b088d55e9c906
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog 類別
顯示功能區**自訂**頁面。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|建構 `CMFCRibbonCustomizeDialog` 物件。|  
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCRibbonCustomizeDialog::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
  
## <a name="remarks"></a>備註  
 MFC 會自動產生這個類別，如果您不處理 AFX_WM_ON_RIBBON_CUSTOMIZE 訊息，或如果您從訊息處理常式傳回 0。  
  
 如果您想要在應用程式中使用這個類別，來顯示功能區**自訂**對話方塊方塊中，只要將它執行個體化，並呼叫`DoModal`方法。  
  
 因為這個類別衍生自[CMFCPropertySheet 類別](../../mfc/reference/cmfcpropertysheet-class.md)，您可以藉由加入自訂頁面`CMFCPropertySheet`應用程式開發介面。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
 [CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxribboncustomizedialog.h  
  
##  <a name="cmfcribboncustomizedialog"></a>CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog  
 建構 `CMFCRibbonCustomizeDialog` 物件。  
  
```  
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,  
    CMFCRibbonBar* pRibbon);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pWndParent`  
 父視窗 （通常是主框架） 的指標。  
  
 [輸入] `pRibbon`  
 指標`CMFCRibbonBar`要加以自訂。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構`CMFCRibbonCustomizeDialog`物件。  
  
 [!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]  
  
### <a name="remarks"></a>備註  
 建構函式具現化[CMFCRibbonCustomizePropertyPage 類別](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)物件並將它加入至屬性工作表頁的集合。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
