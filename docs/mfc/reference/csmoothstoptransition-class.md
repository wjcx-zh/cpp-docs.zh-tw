---
title: "CSmoothStopTransition 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSmoothStopTransition
- afxanimationcontroller/CSmoothStopTransition
dev_langs:
- C++
helpviewer_keywords:
- CSmoothStopTransition class
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
caps.latest.revision: 18
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 60cdc3528d10270187dccd42a634f7483c58821f
ms.lasthandoff: 02/24/2017

---
# <a name="csmoothstoptransition-class"></a>CSmoothStopTransition 類別
封裝平滑停止轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CSmoothStopTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSmoothStopTransition::CSmoothStopTransition](#csmoothstoptransition)|建構平滑停止轉換，並初始化其持續時間上限和最後一個值。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSmoothStopTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CSmoothStopTransition::m_dblFinalValue](#m_dblfinalvalue)|在轉換結束動畫變數的值。|  
|[CSmoothStopTransition::m_maximumDuration](#m_maximumduration)|轉換的時間上限。|  
  
## <a name="remarks"></a>備註  
 平滑停止轉換會減慢接近特定的最後一個值，並包含零的速度。 轉換的持續時間取決於初始速度，也就是初始和最終的值與指定的最大持續時間之間的差異。 如果沒有組成單一的拋物弧形的解決方法，這個方法會建立立方轉換。 因為所有的轉換會自動清除，建議配置它們使用新的運算子。 封裝 IUIAnimationTransition 建立 COM 物件是由 CAnimationController::AnimateGroup，直到則為 NULL。 之後建立的 COM 物件沒有任何作用，請變更成員變數。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSmoothStopTransition](../../mfc/reference/csmoothstoptransition-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="a-namecreatea--csmoothstoptransitioncreate"></a><a name="create"></a>CSmoothStopTransition::Create  
 呼叫轉換程式庫來建立封裝的轉換 COM 物件。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>參數  
 `pLibrary`  
 這是負責建立的標準轉換轉換程式庫指標。  
  
### <a name="return-value"></a>傳回值  
 如果轉換成功; 建立，則為 TRUE。否則為 FALSE。  
  
##  <a name="a-namecsmoothstoptransitiona--csmoothstoptransitioncsmoothstoptransition"></a><a name="csmoothstoptransition"></a>CSmoothStopTransition::CSmoothStopTransition  
 建構平滑停止轉換，並初始化其持續時間上限和最後一個值。  
  
```  
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>參數  
 `maximumDuration`  
 轉換的時間上限。  
  
 `dblFinalValue`  
 在轉換結束動畫變數的值。  
  
##  <a name="a-namemdblfinalvaluea--csmoothstoptransitionmdblfinalvalue"></a><a name="m_dblfinalvalue"></a>CSmoothStopTransition::m_dblFinalValue  
 在轉換結束動畫變數的值。  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="a-namemmaximumdurationa--csmoothstoptransitionmmaximumduration"></a><a name="m_maximumduration"></a>CSmoothStopTransition::m_maximumDuration  
 轉換的時間上限。  
  
```  
UI_ANIMATION_SECONDS m_maximumDuration;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

