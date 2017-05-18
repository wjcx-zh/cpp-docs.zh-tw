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
- CMFCRibbonCustomizeDialog class
- CMFCRibbonCustomizeDialog class, destructor
- ~CMFCRibbonCustomizeDialog destructor
- GetThisClass method
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: d27247f89901adad1778313cdde6fe206a569f0d
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog 類別
顯示功能區**自訂**頁面。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|建構 `CMFCRibbonCustomizeDialog` 物件。|  
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCRibbonCustomizeDialog::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
  
## <a name="remarks"></a>備註  
 MFC 會自動產生這個類別，如果您不會處理 AFX_WM_ON_RIBBON_CUSTOMIZE 訊息，或如果您的訊息處理常式傳回 0。  
  
 如果您想要顯示功能區應用程式中使用這個類別**自訂**對話方塊方塊中，只要它執行個體化，並呼叫`DoModal`方法。  
  
 因為這個類別衍生自[CMFCPropertySheet 類別](../../mfc/reference/cmfcpropertysheet-class.md)，您可以藉由加入自訂頁面`CMFCPropertySheet`API。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
 [CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxribboncustomizedialog.h  
  
##  <a name="cmfcribboncustomizedialog"></a>CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog  
 建構 `CMFCRibbonCustomizeDialog` 物件。  
  
```  
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,  
    CMFCRibbonBar* pRibbon);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
 父視窗 （通常是主框架） 的指標。  
  
 [in] `pRibbon`  
 指標`CMFCRibbonBar`要加以自訂。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構`CMFCRibbonCustomizeDialog`物件。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&18;](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]  
  
### <a name="remarks"></a>備註  
 建構函式具現化[CMFCRibbonCustomizePropertyPage 類別](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)物件，並將它加入至屬性工作表頁的集合。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

