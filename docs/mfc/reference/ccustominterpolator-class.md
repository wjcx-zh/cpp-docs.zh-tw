---
title: "CCustomInterpolator 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CCustomInterpolator
- CCustomInterpolator
dev_langs:
- C++
helpviewer_keywords:
- CCustomInterpolator class
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
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
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: 4d0b38543092dc68c2527f7e1385712164faf996
ms.lasthandoff: 02/24/2017

---
# <a name="ccustominterpolator-class"></a>CCustomInterpolator 類別
實作基本 Interpolator。  
  
## <a name="syntax"></a>語法  
  
```  
class CCustomInterpolator;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|多載。 建構自訂 interpolator 物件並初始化期間和指定的值的速度。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CCustomInterpolator::GetDependencies](#getdependencies)|取得 interpolator 的相依性。|  
|[CCustomInterpolator::GetDuration](#getduration)|取得 interpolator 的持續時間。|  
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|取得 interpolator 會導致的最後一個值。|  
|[CCustomInterpolator::Init](#init)|初始化期間和最後一個值。|  
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|進行中的指定位移的值。|  
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|指定位移處的速度進行插補|  
|[CCustomInterpolator::SetDuration](#setduration)|設定 interpolator 的持續時間。|  
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Interpolator 的起始值和速度設定。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|插補的值。|  
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|插補的速度。|  
|[CCustomInterpolator::m_duration](#m_duration)|轉換的持續時間。|  
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|最後的變數在轉換結束值。|  
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|在開始轉換的變數的值。|  
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|在開始轉換的變數的速度。|  
  
## <a name="remarks"></a>備註  
 從 CCustomInterpolator 衍生類別並覆寫所有必要的方法，以實作自訂的插補演算法。 這個類別的指標應該做為參數傳遞至 CCustomTransition。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CCustomInterpolator`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="a-nameccustominterpolatora--ccustominterpolatorccustominterpolator"></a><a name="ccustominterpolator"></a>CCustomInterpolator::CCustomInterpolator  
 建構自訂 interpolator 物件，並設定所有預設值為 0 的值。  
  
```  
CCustomInterpolator();

 
CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
 `finalValue`  
  
### <a name="remarks"></a>備註  
 您可以使用 CCustomInterpolator::Init 初始化持續期間和稍後在程式碼中的最後一個值。  
  
##  <a name="a-namegetdependenciesa--ccustominterpolatorgetdependencies"></a><a name="getdependencies"></a>CCustomInterpolator::GetDependencies  
 取得 interpolator 的相依性。  
  
```  
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,  
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,  
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>參數  
 `initialValueDependencies`  
 輸出。 Interpolator 的層面的起始值而定，傳遞至 SetInitialValueAndVelocity。  
  
 `initialVelocityDependencies`  
 輸出。 Interpolator 的初始速度而定的層面傳遞至 SetInitialValueAndVelocity。  
  
 `durationDependencies`  
 輸出。 Interpolator 的持續時間而定的層面傳遞至 SetDuration。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一定會傳回 TRUE。 傳回 FALSE 覆寫實如果您想要失敗事件。  
  
##  <a name="a-namegetdurationa--ccustominterpolatorgetduration"></a><a name="getduration"></a>CCustomInterpolator::GetDuration  
 取得 interpolator 的持續時間。  
  
```  
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 輸出。 轉換，以秒為單位的持續時間。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一定會傳回 TRUE。 傳回 FALSE 覆寫實如果您想要失敗事件。  
  
##  <a name="a-namegetfinalvaluea--ccustominterpolatorgetfinalvalue"></a><a name="getfinalvalue"></a>CCustomInterpolator::GetFinalValue  
 取得 interpolator 會導致的最後一個值。  
  
```  
virtual BOOL GetFinalValue(DOUBLE* value);
```  
  
### <a name="parameters"></a>參數  
 `value`  
 輸出。 最後的變數在轉換結束值。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一定會傳回 TRUE。 傳回 FALSE 覆寫實如果您想要失敗事件。  
  
##  <a name="a-nameinita--ccustominterpolatorinit"></a><a name="init"></a>CCustomInterpolator::Init  
 初始化期間和最後一個值。  
  
```  
void Init(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
 `finalValue`  
 最後的變數在轉換結束值。  
  
##  <a name="a-nameinterpolatevaluea--ccustominterpolatorinterpolatevalue"></a><a name="interpolatevalue"></a>CCustomInterpolator::InterpolateValue  
 進行中的指定位移的值。  
  
```  
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* value);
```  
  
### <a name="parameters"></a>參數  
 `value`  
 輸出。 插補的值。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一定會傳回 TRUE。 傳回 FALSE 覆寫實如果您想要失敗事件。  
  
##  <a name="a-nameinterpolatevelocitya--ccustominterpolatorinterpolatevelocity"></a><a name="interpolatevelocity"></a>CCustomInterpolator::InterpolateVelocity  
 指定位移處的速度進行插補  
  
```  
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* velocity);
```  
  
### <a name="parameters"></a>參數  
 `velocity`  
 輸出。 在位移變數的速度。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一定會傳回 TRUE。 傳回 FALSE 覆寫實如果您想要失敗事件。  
  
##  <a name="a-namemcurrentvaluea--ccustominterpolatormcurrentvalue"></a><a name="m_currentvalue"></a>CCustomInterpolator::m_currentValue  
 插補的值。  
  
```  
DOUBLE m_currentValue;  
```  
  
##  <a name="a-namemcurrentvelocitya--ccustominterpolatormcurrentvelocity"></a><a name="m_currentvelocity"></a>CCustomInterpolator::m_currentVelocity  
 插補的速度。  
  
```  
DOUBLE m_currentVelocity;  
```  
  
##  <a name="a-namemdurationa--ccustominterpolatormduration"></a><a name="m_duration"></a>CCustomInterpolator::m_duration  
 轉換的持續時間。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="a-namemfinalvaluea--ccustominterpolatormfinalvalue"></a><a name="m_finalvalue"></a>CCustomInterpolator::m_finalValue  
 最後的變數在轉換結束值。  
  
```  
DOUBLE m_finalValue;  
```  
  
##  <a name="a-nameminitialvaluea--ccustominterpolatorminitialvalue"></a><a name="m_initialvalue"></a>CCustomInterpolator::m_initialValue  
 在開始轉換的變數的值。  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="a-nameminitialvelocitya--ccustominterpolatorminitialvelocity"></a><a name="m_initialvelocity"></a>CCustomInterpolator::m_initialVelocity  
 在開始轉換的變數的速度。  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="a-namesetdurationa--ccustominterpolatorsetduration"></a><a name="setduration"></a>CCustomInterpolator::SetDuration  
 設定 interpolator 的持續時間。  
  
```  
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一定會傳回 TRUE。 傳回 FALSE 覆寫實如果您想要失敗事件。  
  
##  <a name="a-namesetinitialvalueandvelocitya--ccustominterpolatorsetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CCustomInterpolator::SetInitialValueAndVelocity  
 Interpolator 的起始值和速度設定。  
  
```  
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,  
    DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>參數  
 `initialValue`  
 在開始轉換的變數的值。  
  
 `initialVelocity`  
 在開始轉換的變數的速度。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一定會傳回 TRUE。 傳回 FALSE 覆寫實如果您想要失敗事件。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

