---
title: "CMFCRibbonContextCaption 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonContextCaption
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonContextCaption class
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
caps.latest.revision: 24
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
ms.openlocfilehash: 54f71af5ec46a8ddac4459e9ffdbc5b10f3106d4
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncontextcaption-class"></a>CMFCRibbonContextCaption 類別
實作出現在功能區類別或內容類別頂端的彩色標題。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonContextCaption : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCRibbonContextCaption::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCRibbonContextCaption::GetColor](#getcolor)|傳回標題的色彩。|  
|[CMFCRibbonContextCaption::GetRightTabX](#getrighttabx)||  
|`CMFCRibbonContextCaption::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
  
## <a name="remarks"></a>備註  
 此類別無法直接具現化。 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)類別會使用這個類別在內部將色彩加入至功能區分類。  
  
 若要設定功能區分類的色彩，請呼叫[CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor)。 若要設定內容分類的色彩，請呼叫[CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxRibbonBar.h  
  
##  <a name="a-namegetcolora--cmfcribboncontextcaptiongetcolor"></a><a name="getcolor"></a>CMFCRibbonContextCaption::GetColor  
 傳回標題的背景色彩。  
  
```  
AFX_RibbonCategoryColor GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回的值可以是下列的列舉值之一︰  
  
- `AFX_CategoryColor_None`  
  
- `AFX_CategoryColor_Red`  
  
- `AFX_CategoryColor_Orange`  
  
- `AFX_CategoryColor_Yellow`  
  
- `AFX_CategoryColor_Green`  
  
- `AFX_CategoryColor_Blue`  
  
- `AFX_CategoryColor_Indigo`  
  
- `AFX_CategoryColor_Violet`  
  
### <a name="remarks"></a>備註  
 可以藉由呼叫設定標題色彩[CMFCRibbonCategory::SetTabColor](../../mfc/reference/cmfcribboncategory-class.md#settabcolor)或[CMFCRibbonBar::AddContextCategory](../../mfc/reference/cmfcribbonbar-class.md#addcontextcategory)。  
  
##  <a name="a-namegetrighttabxa--cmfcribboncontextcaptiongetrighttabx"></a><a name="getrighttabx"></a>CMFCRibbonContextCaption::GetRightTabX  
 擷取類別的功能區索引標籤的右側邊緣的位置。  
  
```  
int GetRightTabX() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回的封入矩形的右 X 值`CMFCRibbonCategory`物件的功能區索引標籤上或為-1 索引標籤會被截斷的值。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonCategory 類別](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)

