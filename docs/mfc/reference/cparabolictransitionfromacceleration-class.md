---
title: "CParabolicTransitionFromAcceleration 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CParabolicTransitionFromAcceleration
- CParabolicTransitionFromAcceleration
dev_langs:
- C++
helpviewer_keywords:
- CParabolicTransitionFromAcceleration class
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
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
ms.openlocfilehash: f0d3089a01cd244851be3d4bdf0453101a9c8274
ms.lasthandoff: 02/24/2017

---
# <a name="cparabolictransitionfromacceleration-class"></a>CParabolicTransitionFromAcceleration 類別
封裝拋物線加速轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CParabolicTransitionFromAcceleration : public CBaseTransition;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](#cparabolictransitionfromacceleration)|建構拋物線加速轉換，並使用指定的參數將它初始化。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::m_dblAcceleration](#m_dblacceleration)|在轉換期間加速的動畫變數。|  
|[CParabolicTransitionFromAcceleration::m_dblFinalValue](#m_dblfinalvalue)|在轉換結束動畫變數的值。|  
|[CParabolicTransitionFromAcceleration::m_dblFinalVelocity](#m_dblfinalvelocity)|在轉換結束動畫變數的速度。|  
  
## <a name="remarks"></a>備註  
 拋物線加速轉換，在動畫變數的值變更的起始值的結束時間指定速度的最終值。 您可以控制變數達到最終的值所指定的加速速率的速度。 因為所有的轉換會自動清除，建議配置它們使用新的運算子。 封裝 IUIAnimationTransition 建立 COM 物件是由 CAnimationController::AnimateGroup，直到則為 NULL。 之後建立的 COM 物件沒有任何作用，請變更成員變數。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="a-namecparabolictransitionfromaccelerationa--cparabolictransitionfromaccelerationcparabolictransitionfromacceleration"></a><a name="cparabolictransitionfromacceleration"></a>CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration  
 建構拋物線加速轉換，並使用指定的參數將它初始化。  
  
```  
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,  
    DOUBLE dblFinalVelocity,  
    DOUBLE dblAcceleration);
```  
  
### <a name="parameters"></a>參數  
 `dblFinalValue`  
 在轉換結束動畫變數的值。  
  
 `dblFinalVelocity`  
 在轉換結束動畫變數的速度。  
  
 `dblAcceleration`  
 在轉換期間加速的動畫變數。  
  
##  <a name="a-namecreatea--cparabolictransitionfromaccelerationcreate"></a><a name="create"></a>CParabolicTransitionFromAcceleration::Create  
 呼叫轉換程式庫來建立封裝的轉換 COM 物件。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* /* not used */);
```  
  
### <a name="parameters"></a>參數  
 `pLibrary`  
 這是負責建立的標準轉換轉換程式庫指標。  
  
### <a name="return-value"></a>傳回值  
 如果轉換成功; 建立，則為 TRUE。否則為 FALSE。  
  
##  <a name="a-namemdblaccelerationa--cparabolictransitionfromaccelerationmdblacceleration"></a><a name="m_dblacceleration"></a>CParabolicTransitionFromAcceleration::m_dblAcceleration  
 在轉換期間加速的動畫變數。  
  
```  
DOUBLE m_dblAcceleration;  
```  
  
##  <a name="a-namemdblfinalvaluea--cparabolictransitionfromaccelerationmdblfinalvalue"></a><a name="m_dblfinalvalue"></a>CParabolicTransitionFromAcceleration::m_dblFinalValue  
 在轉換結束動畫變數的值。  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="a-namemdblfinalvelocitya--cparabolictransitionfromaccelerationmdblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CParabolicTransitionFromAcceleration::m_dblFinalVelocity  
 在轉換結束動畫變數的速度。  
  
```  
DOUBLE m_dblFinalVelocity;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

