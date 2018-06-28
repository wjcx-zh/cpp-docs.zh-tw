---
title: CInterpolatorBase 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81ad51fe00a0b205000b15a05ede9497850f488e
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041269"
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase 類別
實作回呼，當動畫 API 必須計算動畫變數的新值時由此 API 呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;  
```  
  
## <a name="members"></a>成員  
  
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
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|取得 interpolator 會導致的最終值。 (覆寫 `CUIAnimationInterpolatorBase::GetFinalValue`。)|  
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|插補在指定的位移值 (會覆寫`CUIAnimationInterpolatorBase::InterpolateValue`。)|  
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|插補在指定位移的速度 (會覆寫`CUIAnimationInterpolatorBase::InterpolateVelocity`。)|  
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|儲存自訂 interpolator，將會處理事件的指標。|  
|[CInterpolatorBase::SetDuration](#setduration)|Interpolator 的持續時間設定 (會覆寫`CUIAnimationInterpolatorBase::SetDuration`。)|  
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Interpolator 的起始值和速度設定。 (覆寫 `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`。)|  
  
## <a name="remarks"></a>備註  
 建立並傳遞至這個處理常式`IUIAnimationTransitionFactory::CreateTransition`時`CCustomTransition`動畫初始化處理程序的一部分建立物件 (由啟動`CAnimationController::AnimateGroup`)。 通常您不需要直接使用這個類別，它只 routs 所有事件`CCustomInterpolator`-衍生的類別，其指標傳遞給建構函式的`CCustomTransition`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationInterpolatorBase`  
  
 `CInterpolatorBase`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="cinterpolatorbase"></a>  CInterpolatorBase::CInterpolatorBase  
 建構 CInterpolatorBase 物件。  
  
```  
CInterpolatorBase();
```  
  
##  <a name="createinstance"></a>  CInterpolatorBase::CreateInstance  
 建立 CInterpolatorBase 的執行個體，並將自訂 interpolator，將會處理事件的指標。  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,  
    IUIAnimationInterpolator** ppHandler);
```  
  
### <a name="parameters"></a>參數  
 *pInterpolator*  
 自訂 interpolator 指標。  
  
 *ppHandler*  
 輸出。 此函式傳回時包含 CInterpolatorBase 的執行個體的指標。  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="getdependencies"></a>  CInterpolatorBase::GetDependencies  
 取得 interpolator 的相依性。  
  
```  
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>參數  
 *initialValueDependencies*  
 輸出。 Interpolator 的起始值而定的各個層面傳遞給 SetInitialValueAndVelocity。  
  
 *initialVelocityDependencies*  
 輸出。 Interpolator 的初始速度而定的部分傳遞至 SetInitialValueAndVelocity。  
  
 *durationDependencies*  
 輸出。 Interpolator 的持續時間而定的部分傳遞至 SetDuration。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE 從 GetDependencies 方法，它會傳回 E_FAIL。  
  
##  <a name="getduration"></a>  CInterpolatorBase::GetDuration  
 取得 interpolator 的持續時間。  
  
```  
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>參數  
 *持續時間*  
 輸出。 轉換，以秒為單位的持續時間。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE 從 GetDuration 方法，它會傳回 E_FAIL。  
  
##  <a name="getfinalvalue"></a>  CInterpolatorBase::GetFinalValue  
 取得 interpolator 會導致的最終值。  
  
```  
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```  
  
### <a name="parameters"></a>參數  
 *值*  
 輸出。 變數在轉換結束最後的值。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE 從 GetFinalValue 方法，它會傳回 E_FAIL。  
  
##  <a name="interpolatevalue"></a>  CInterpolatorBase::InterpolateValue  
 插補在指定位移的值  
  
```  
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset, 
  __out DOUBLE* value);
```  
  
### <a name="parameters"></a>參數  
 *offset*  
 從轉換的起始位移。 此位移一律為大於或等於零且小於轉換的持續時間。 如果轉換的持續時間為零，不會呼叫這個方法。  
  
 *值*  
 輸出。 插補的值。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE 從 InterpolateValue 方法，它會傳回 E_FAIL。  
  
##  <a name="interpolatevelocity"></a>  CInterpolatorBase::InterpolateVelocity  
 插補在指定位移的速度  
  
```  
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```  
  
### <a name="parameters"></a>參數  
 *offset*  
 從轉換的起始位移。 位移永遠是大於或等於零且小於或等於轉換的持續時間。 如果轉換的持續時間為零，不會呼叫這個方法。  
  
 *速度*  
 輸出。 在位移變數的速度。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE 從 InterpolateVelocity 方法，它會傳回 E_FAIL。  
  
##  <a name="setcustominterpolator"></a>  CInterpolatorBase::SetCustomInterpolator  
 儲存自訂 interpolator，將會處理事件的指標。  
  
```  
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>參數  
 *pInterpolator*  
 自訂 interpolator 指標。  
  
##  <a name="setduration"></a>  CInterpolatorBase::SetDuration  
 Interpolator 的持續時間設定  
  
```  
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>參數  
 *持續時間*  
 轉換的持續時間。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE 從 SetDuration 方法，它會傳回 E_FAIL。  
  
##  <a name="setinitialvalueandvelocity"></a>  CInterpolatorBase::SetInitialValueAndVelocity  
 Interpolator 的起始值和速度設定。  
  
```  
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue, 
  __in DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>參數  
 *initialValue*  
 在開始轉換的變數的值。  
  
 *initialVelocity*  
 在開始轉換的變數的速度。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 如果未設定 CCustomInterpolator，或自訂實作會傳回 FALSE 從 SetInitialValueAndVelocity 方法，它會傳回 E_FAIL。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
