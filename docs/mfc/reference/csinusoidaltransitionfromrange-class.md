---
title: "CSinusoidalTransitionFromRange 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMaximumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMinimumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_period
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_slope
dev_langs:
- C++
helpviewer_keywords:
- CSinusoidalTransitionFromRange class
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
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
ms.openlocfilehash: f9dd0e236207c0b4139de42f4c616aaad9dcad28
ms.lasthandoff: 02/24/2017

---
# <a name="csinusoidaltransitionfromrange-class"></a>CSinusoidalTransitionFromRange 類別
封裝已指定振動範圍的正弦曲線範圍轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CSinusoidalTransitionFromRange : public CBaseTransition;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange](#csinusoidaltransitionfromrange)|建構轉換物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::m_dblMaximumValue](#m_dblmaximumvalue)|在尖峰時段振動波的動畫變數的值。|  
|[CSinusoidalTransitionFromRange::m_dblMinimumValue](#m_dblminimumvalue)|在透過振動波的動畫變數的值。|  
|[CSinusoidalTransitionFromRange::m_duration](#m_duration)|轉換的持續時間。|  
|[CSinusoidalTransitionFromRange::m_period](#m_period)|以秒為單位的正弦曲線 wave 振盪期間。|  
|[CSinusoidalTransitionFromRange::m_slope](#m_slope)|在開始轉換的斜率。|  
  
## <a name="remarks"></a>備註  
 動畫變數的值半數的正弦曲線範圍轉換整個持續期間指定的最小和最大值。 斜率參數用來釐清兩個可能與其他參數所指定的正弦波。 因為所有的轉換會自動清除，建議配置它們使用新的運算子。 封裝 IUIAnimationTransition 建立 COM 物件是由 CAnimationController::AnimateGroup，直到則為 NULL。 之後建立的 COM 物件沒有任何作用，請變更成員變數。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="create"></a>CSinusoidalTransitionFromRange::Create  
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
  
##  <a name="csinusoidaltransitionfromrange"></a>CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange  
 建構轉換物件。  
  
```  
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE dblMinimumValue,  
    DOUBLE dblMaximumValue,  
    UI_ANIMATION_SECONDS period,  
    UI_ANIMATION_SLOPE slope);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
 `dblMinimumValue`  
 在透過振動波的動畫變數的值。  
  
 `dblMaximumValue`  
 在尖峰時段振動波的動畫變數的值。  
  
 `period`  
 以秒為單位的正弦曲線 wave 振盪期間。  
  
 `slope`  
 在開始轉換的斜率。  
  
##  <a name="m_dblmaximumvalue"></a>CSinusoidalTransitionFromRange::m_dblMaximumValue  
 在尖峰時段振動波的動畫變數的值。  
  
```  
DOUBLE m_dblMaximumValue;  
```  
  
##  <a name="m_dblminimumvalue"></a>CSinusoidalTransitionFromRange::m_dblMinimumValue  
 在透過振動波的動畫變數的值。  
  
```  
DOUBLE m_dblMinimumValue;  
```  
  
##  <a name="m_duration"></a>CSinusoidalTransitionFromRange::m_duration  
 轉換的持續時間。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_period"></a>CSinusoidalTransitionFromRange::m_period  
 以秒為單位的正弦曲線 wave 振盪期間。  
  
```  
UI_ANIMATION_SECONDS m_period;  
```  
  
##  <a name="m_slope"></a>CSinusoidalTransitionFromRange::m_slope  
 在開始轉換的斜率。  
  
```  
UI_ANIMATION_SLOPE m_slope;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

