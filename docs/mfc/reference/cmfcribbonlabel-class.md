---
title: CMFCRibbonLabel 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36b2d78bb3f1ffaefa67a062c6498c195d46336f
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042491"
---
# <a name="cmfcribbonlabel-class"></a>CMFCRibbonLabel 類別
實作功能區的不可點選式文字標籤。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonLabel : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|建構並初始化`CMFCRibbonLabel`物件與指定的文字字串。|  
|`CMFCRibbonLabel::~CMFCRibbonLabel`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCRibbonLabel::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCRibbonLabel::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCRibbonLabel::SetACCData](#setaccdata)|判斷目前的功能區 label 元素的協助工具資料。 (覆寫[cmfcribbonbutton:: Setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|  
  
### <a name="remarks"></a>備註  
 建立功能區標籤之後，將它加入至面板藉由呼叫[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。  
  
 您無法加入快速存取工具列的功能區標籤。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxRibbonLabel.h  
  
##  <a name="cmfcribbonlabel"></a>  CMFCRibbonLabel::CMFCRibbonLabel  
 建構並初始化[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)顯示指定的文字字串的物件。  
  
```  
CMFCRibbonLabel(
    LPCTSTR lpszText,  
    BOOL bIsMultiLine = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszText*  
 在標籤中顯示的文字。  
  
 [in]*bIsMultiLine*  
 `TRUE` 若要指定標籤為多行標籤。否則， `FALSE`。  
  
##  <a name="setaccdata"></a>  CMFCRibbonLabel::SetACCData  
 判斷目前的功能區 label 元素的協助工具資料。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>參數  
 [in]*pParent*  
 表示目前的功能區標籤的父視窗。  
  
 [out]*資料*  
 型別的物件`CAccessibilityData`填入目前的功能區標籤的協助工具資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果*資料*參數已成功填入目前的功能區標籤的協助工具資料，否則`FALSE`。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)
