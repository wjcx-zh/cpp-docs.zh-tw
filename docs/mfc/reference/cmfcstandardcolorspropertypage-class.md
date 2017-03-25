---
title: "CMFCStandardColorsPropertyPage 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
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
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: fade2cc91d9681604fbd664419c693dde1527b84
ms.lasthandoff: 03/17/2017

---
# <a name="cmfcstandardcolorspropertypage-class"></a>CMFCStandardColorsPropertyPage 類別
表示屬性頁使用者用來在色彩對話方塊中選取標準色彩。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCStandardColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|預設建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|說明|  
|`CMFCStandardColorsPropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCStandardColorsPropertyPage::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
  
### <a name="remarks"></a>備註  
 `CMFCColorDialog`類別會使用這個類別來顯示標準的色彩屬性頁。 如需詳細資訊`CMFCColorDialog`，請參閱[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxstandardcolorspropertypage.h  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCCustomColorsPropertyPage 類別](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

