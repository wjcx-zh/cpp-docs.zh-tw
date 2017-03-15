---
title: "CCubicTransition 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCubicTransition
- afxanimationcontroller/CCubicTransition
dev_langs:
- C++
helpviewer_keywords:
- CCubicTransition class
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
caps.latest.revision: 17
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
ms.openlocfilehash: 511dc175d51db7887a462aaf63f4f91290375751
ms.lasthandoff: 02/24/2017

---
# <a name="ccubictransition-class"></a>CCubicTransition 類別
封裝立方轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CCubicTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CCubicTransition::CCubicTransition](#ccubictransition)|建構轉換物件並初始化它的參數。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CCubicTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|在轉換結束動畫變數的值。|  
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|在轉換結束變數的速度。|  
|[CCubicTransition::m_duration](#m_duration)|轉換的持續時間。|  
  
## <a name="remarks"></a>備註  
 立方轉換，在動畫變數的值從變更其初始值為指定的最後一個值的轉換，並且在指定的速度持續期間。 因為所有的轉換會自動清除，建議配置它們使用新的運算子。 封裝 IUIAnimationTransition 建立 COM 物件是由 CAnimationController::AnimateGroup，直到則為 NULL。 之後建立的 COM 物件沒有任何作用，請變更成員變數。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CCubicTransition`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="a-nameccubictransitiona--ccubictransitionccubictransition"></a><a name="ccubictransition"></a>CCubicTransition::CCubicTransition  
 建構轉換物件並初始化它的參數。  
  
```  
CCubicTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue,  
    DOUBLE finalVelocity);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
 `finalValue`  
 在轉換結束動畫變數的值。  
  
 `finalVelocity`  
 在轉換結束變數的速度。  
  
##  <a name="a-namecreatea--ccubictransitioncreate"></a><a name="create"></a>CCubicTransition::Create  
 呼叫轉換程式庫來建立封裝的轉換 COM 物件。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>參數  
`pLibrary`  
 指標[IUIAnimationTransitionLibrary 介面](https://msdn.microsoft.com/library/windows/desktop/dd371897)，以定義的標準轉換的程式庫。  

### <a name="return-value"></a>傳回值  
 如果轉換成功; 建立，則為 TRUE。否則為 FALSE。  
  
##  <a name="a-namemdblfinalvaluea--ccubictransitionmdblfinalvalue"></a><a name="m_dblfinalvalue"></a>CCubicTransition::m_dblFinalValue  
 在轉換結束動畫變數的值。  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="a-namemdblfinalvelocitya--ccubictransitionmdblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CCubicTransition::m_dblFinalVelocity  
 在轉換結束變數的速度。  
  
```  
DOUBLE m_dblFinalVelocity;  
```  
  
##  <a name="a-namemdurationa--ccubictransitionmduration"></a><a name="m_duration"></a>CCubicTransition::m_duration  
 轉換的持續時間。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

