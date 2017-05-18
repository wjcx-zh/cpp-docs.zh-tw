---
title: "CAccelerateDecelerateTransition Class1 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
dev_langs:
- C++
helpviewer_keywords:
- CAccelerateDecelerateTransition class
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
caps.latest.revision: 16
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f11dc96b48695b998fb17c33735e8f56bce517b7
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition 類別
實作加速減速轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CAccelerateDecelerateTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|建構轉換物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|所花費的時間，加快持續時間的比率。|  
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|減速期間所花費的時間比例。|  
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|轉換的持續時間。|  
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|在轉換結束動畫變數的值。|  
  
## <a name="remarks"></a>備註  
 加速期間-減速轉換、 加速動畫變數，且再變慢的轉換，並且在指定的值持續期間。 您可以控制變數速度加速與減速獨立作業，藉由指定不同的加速與減速的比例。 初始速度為零，加速比率時，變數會花加速; 持續時間的比例同樣地與減速的比例。 如果初始速度為非零，則達到零，而轉換速度之間的時間部份。 加速比率和減速比例應該等於最大值為 1.0。 因為所有的轉換會自動清除，建議配置它們使用新的運算子。 封裝 IUIAnimationTransition 建立 COM 物件是由 CAnimationController::AnimateGroup，直到則為 NULL。 之後建立的 COM 物件沒有任何作用，請變更成員變數。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CAccelerateDecelerateTransition`   
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="cacceleratedeceleratetransition"></a>CAccelerateDecelerateTransition::CAccelerateDecelerateTransition  
 建構轉換物件。  
  
```  
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue,  
    DOUBLE accelerationRatio = 0.3,  
    DOUBLE decelerationRatio = 0.3);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
 `finalValue`  
 在轉換結束動畫變數的值。  
  
 `accelerationRatio`  
 所花費的時間，加快持續時間的比率。  
  
 `decelerationRatio`  
 減速期間所花費的時間比例。  
  
##  <a name="create"></a>CAccelerateDecelerateTransition::Create  
 呼叫轉換程式庫來建立封裝的轉換 COM 物件。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* *\not used*\);
```  
  
### <a name="parameters"></a>參數  
`pLibrary`  
 指標[IUIAnimationTransitionLibrary 介面](https://msdn.microsoft.com/library/windows/desktop/dd371897)，以定義的標準轉換的程式庫。  
  
### <a name="return-value"></a>傳回值  
 如果轉換成功; 建立，則為 TRUE。否則為 FALSE。  
  
##  <a name="m_accelerationratio"></a>CAccelerateDecelerateTransition::m_accelerationRatio  
 所花費的時間，加快持續時間的比率。  
  
```  
DOUBLE m_accelerationRatio;  
```  
  
##  <a name="m_decelerationratio"></a>CAccelerateDecelerateTransition::m_decelerationRatio  
 減速期間所花費的時間比例。  
  
```  
DOUBLE m_decelerationRatio;  
```  
  
##  <a name="m_duration"></a>CAccelerateDecelerateTransition::m_duration  
 轉換的持續時間。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_finalvalue"></a>CAccelerateDecelerateTransition::m_finalValue  
 在轉換結束動畫變數的值。  
  
```  
DOUBLE m_finalValue;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

