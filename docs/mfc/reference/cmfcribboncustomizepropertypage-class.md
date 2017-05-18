---
title: "CMFCRibbonCustomizePropertyPage 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- ~CMFCRibbonCustomizePropertyPage destructor
- CMFCRibbonCustomizePropertyPage class, destructor
- GetThisClass method
- CreateObject method
- CMFCRibbonCustomizePropertyPage class
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
caps.latest.revision: 26
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
ms.openlocfilehash: 83323142441de13140383152a32122bf1644003f
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage 類別
實作自訂頁面**自訂**在功能區應用程式中的對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|建構 `CMFCRibbonCustomizePropertyPage` 物件。|  
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|新增自訂的類別，以**命令**下拉式方塊。|  
|`CMFCRibbonCustomizePropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|由系統呼叫，當使用者按一下**確定**上**自訂**對話方塊。|  
  
## <a name="remarks"></a>備註  
 如果您想要新增自訂命令**自訂**對話方塊中，您必須處理 AFX_WM_ON_RIBBON_CUSTOMIZE 訊息。 訊息處理常式中，在具現化`CMFCRibbonCustomizePropertyPage`堆疊上的物件。 建立自訂命令的清單，然後呼叫`AddCustomCategory`來加入新的頁面，以便**自訂**對話方塊。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構`CMFCRibbonCustomizePropertyPage`物件，並將自訂類別。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&22;](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
 [CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxribboncustomizedialog.h  
  
##  <a name="addcustomcategory"></a>CMFCRibbonCustomizePropertyPage::AddCustomCategory  
 新增自訂的類別，以**命令**下拉式方塊。  
  
```  
void AddCustomCategory(
    LPCTSTR lpszName,  
    const CList<UINT, UINT>& lstIDS);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `lpszName`|指定自訂的類別名稱。|  
|[in] `lstIDS`|包含要顯示在 [自訂] 類別的功能區命令 Id。|  
  
### <a name="remarks"></a>備註  
 這個方法會加入名為類別目錄`lpszName`至**命令**下拉式方塊。 當使用者選取類別目錄時，命令中指定`lstIDS`出現在 [命令] 清單中。  
  
##  <a name="cmfcribboncustomizepropertypage"></a>CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage  
 建構 `CMFCRibbonCustomizePropertyPage` 物件。  
  
```  
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pRibbonBar`  
 在功能區控制項的指標選項來自訂。  
  
##  <a name="onok"></a>CMFCRibbonCustomizePropertyPage::OnOK  
 當使用者按一下系統 Calleld**確定**上**自訂**對話方塊。  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>備註  
 預設實作會套用在選取的選項**自訂**對話方塊，即可快速存取工具列。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

