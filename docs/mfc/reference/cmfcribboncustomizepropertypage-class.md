---
title: CMFCRibbonCustomizePropertyPage 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b6c5501159cfdb46107b4fef34637195d52f465
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368003"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage 類別
實作自訂頁面**自訂**在功能區應用程式中的對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|建構 `CMFCRibbonCustomizePropertyPage` 物件。|  
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|新增自訂類別以**命令**下拉式方塊。|  
|`CMFCRibbonCustomizePropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|由系統呼叫，當使用者按一下**確定**上**自訂** 對話方塊。|  
  
## <a name="remarks"></a>備註  
 如果您想要新增自訂命令至**自訂**對話方塊中，您必須處理 AFX_WM_ON_RIBBON_CUSTOMIZE 訊息。 在訊息處理常式中，具現化`CMFCRibbonCustomizePropertyPage`堆疊上的物件。 建立自訂命令的清單，然後呼叫`AddCustomCategory`要加入新的頁面，即可**自訂** 對話方塊。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構`CMFCRibbonCustomizePropertyPage`物件，並將自訂類別。  
  
 [!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
 [CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxribboncustomizedialog.h  
  
##  <a name="addcustomcategory"></a>  CMFCRibbonCustomizePropertyPage::AddCustomCategory  
 新增自訂類別以**命令**下拉式方塊。  
  
```  
void AddCustomCategory(
    LPCTSTR lpszName,  
    const CList<UINT, UINT>& lstIDS);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[輸入] `lpszName`|指定自訂的類別名稱。|  
|[輸入] `lstIDS`|包含要在自訂的類別目錄中顯示功能區命令識別碼。|  
  
### <a name="remarks"></a>備註  
 這個方法會加入名為 category`lpszName`至**命令**下拉式方塊。 當使用者選取類別目錄時，在指定的命令`lstIDS`命令清單中出現。  
  
##  <a name="cmfcribboncustomizepropertypage"></a>  CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage  
 建構 `CMFCRibbonCustomizePropertyPage` 物件。  
  
```  
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pRibbonBar`  
 在功能區控制項的指標以自訂的選項。  
  
##  <a name="onok"></a>  CMFCRibbonCustomizePropertyPage::OnOK  
 由系統中，當使用者按一下 Calleld**確定**上**自訂** 對話方塊。  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>備註  
 預設實作適用於中選取的選項**自訂**快速存取工具列 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
