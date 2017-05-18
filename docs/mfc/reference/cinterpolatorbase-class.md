---
title: "CInterpolatorBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
dev_langs:
- C++
helpviewer_keywords:
- CInterpolatorBase class
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
caps.latest.revision: 19
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 44c67eef38b34a2a3cf677b42a40304c01668b42
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase 類別
實作回呼，當動畫 API 必須計算動畫變數的新值時由此 API 呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|建構`CInterpolatorBase`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CInterpolatorBase::CreateInstance](#createinstance)|建立的執行個體`CInterpolatorBase`和儲存自訂 interpolator，將會處理事件的指標。|  
|[CInterpolatorBase::GetDependencies](#getdependencies)|取得 interpolator 的相依性。 (覆寫 `CUIAnimationInterpolatorBase::GetDependencies`。)|  
|[CInterpolatorBase::GetDuration](#getduration)|取得 interpolator 的持續時間。 (覆寫 `CUIAnimationInterpolatorBase::GetDuration`。)|  
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|取得 interpolator 會導致的最後一個值。 (覆寫 `CUIAnimationInterpolatorBase::GetFinalValue`。)|  
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|指定位移處的值進行插補 (覆寫`CUIAnimationInterpolatorBase::InterpolateValue`。)|  
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|指定位移處的速度進行插補 (覆寫`CUIAnimationInterpolatorBase::InterpolateVelocity`。)|  
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|儲存自訂 interpolator，將會處理事件的指標。|  
|[CInterpolatorBase::SetDuration](#setduration)|設定 interpolator 的持續期間 (覆寫`CUIAnimationInterpolatorBase::SetDuration`。)|  
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Interpolator 的起始值和速度設定。 (覆寫 `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`。)|  
  
## <a name="remarks"></a>備註  
 此處理常式會建立並傳遞至`IUIAnimationTransitionFactory::CreateTransition`時`CCustomTransition`動畫初始化處理程序的一部份建立物件 (由啟動`CAnimationController::AnimateGroup`)。 通常您不需要直接使用這個類別，它只是 routs 所有事件`CCustomInterpolator`-衍生的類別，其指標傳遞給建構函式的`CCustomTransition`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationInterpolatorBase`  
  
 `CInterpolatorBase`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase  
 建構 CInterpolatorBase 物件。  
  
```  
CInterpolatorBase();
```  
  
##  <a name="createinstance"></a>CInterpolatorBase::CreateInstance  
 建立 CInterpolatorBase 的執行個體，並將自訂 interpolator，將會處理事件的指標。  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,  
    IUIAnimationInterpolator** ppHandler);
```  
  
### <a name="parameters"></a>參數  
 `pInterpolator`  
 自訂 interpolator 指標。  
  
 `ppHandler`  
 輸出。 函式傳回時，請包含 CInterpolatorBase 的執行個體的指標。  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="getdependencies"></a>CInterpolatorBase::GetDependencies  
 取得 interpolator 的相依性。  
  
```  
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>參數  
 `initialValueDependencies`  
 輸出。 Interpolator 的層面的起始值而定，傳遞至 SetInitialValueAndVelocity。  
  
 `initialVelocityDependencies`  
 輸出。 Interpolator 的初始速度而定的層面傳遞至 SetInitialValueAndVelocity。  
  
 `durationDependencies`  
 輸出。 Interpolator 的持續時間而定的層面傳遞至 SetDuration。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE GetDependencies 方法會傳回 E_FAIL。  
  
##  <a name="getduration"></a>CInterpolatorBase::GetDuration  
 取得 interpolator 的持續時間。  
  
```  
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 輸出。 轉換，以秒為單位的持續時間。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE GetDuration 方法會傳回 E_FAIL。  
  
##  <a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue  
 取得 interpolator 會導致的最後一個值。  
  
```  
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```  
  
### <a name="parameters"></a>參數  
 `value`  
 輸出。 最後的變數在轉換結束值。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE GetFinalValue 方法會傳回 E_FAIL。  
  
##  <a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue  
 指定位移處的值進行插補  
  
```  
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset, 
  __out DOUBLE* value);
```  
  
### <a name="parameters"></a>參數  
 `offset`  
 從轉換的開始位移。 位移永遠是大於或等於&0; 且小於轉換的持續時間。 如果轉換的持續時間為零，不會呼叫這個方法。  
  
 `value`  
 輸出。 插補的值。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE InterpolateValue 方法會傳回 E_FAIL。  
  
##  <a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity  
 指定位移處的速度進行插補  
  
```  
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```  
  
### <a name="parameters"></a>參數  
 `offset`  
 從轉換的開始位移。 位移永遠是大於或等於&0; 且小於或等於轉換的持續時間。 如果轉換的持續時間為零，不會呼叫這個方法。  
  
 `velocity`  
 輸出。 在位移變數的速度。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE InterpolateVelocity 方法會傳回 E_FAIL。  
  
##  <a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator  
 儲存自訂 interpolator，將會處理事件的指標。  
  
```  
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>參數  
 `pInterpolator`  
 自訂 interpolator 指標。  
  
##  <a name="setduration"></a>CInterpolatorBase::SetDuration  
 設定 interpolator 的持續時間  
  
```  
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE SetDuration 方法會傳回 E_FAIL。  
  
##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity  
 Interpolator 的起始值和速度設定。  
  
```  
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue, 
  __in DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>參數  
 `initialValue`  
 在開始轉換的變數的值。  
  
 `initialVelocity`  
 在開始轉換的變數的速度。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE SetInitialValueAndVelocity 方法會傳回 E_FAIL。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

