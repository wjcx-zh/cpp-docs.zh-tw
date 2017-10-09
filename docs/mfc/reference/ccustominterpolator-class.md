---
title: "CCustomInterpolator 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
dev_langs:
- C++
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 4198e4b694356087cccad99d8ca62da3f23ba6ec
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

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
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|多載。 建構自訂 interpolator 物件，並初始化持續時間和指定的值的速度。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CCustomInterpolator::GetDependencies](#getdependencies)|取得 interpolator 的相依性。|  
|[CCustomInterpolator::GetDuration](#getduration)|取得 interpolator 的持續時間。|  
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|取得 interpolator 會導致的最終值。|  
|[CCustomInterpolator::Init](#init)|初始化持續時間和最後一個值。|  
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|進行插補在指定位移的值。|  
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|插補在指定位移的速度|  
|[CCustomInterpolator::SetDuration](#setduration)|Interpolator 的持續時間設定。|  
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Interpolator 的起始值和速度設定。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|插補的值。|  
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|插補的速度。|  
|[CCustomInterpolator::m_duration](#m_duration)|轉換的持續時間。|  
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|變數在轉換結束最後的值。|  
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|在開始轉換的變數的值。|  
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|在開始轉換的變數的速度。|  
  
## <a name="remarks"></a>備註  
 CCustomInterpolator 從衍生類別並覆寫所有必要的方法，以便實作自訂的插補演算法。 這個類別的指標應該當做參數傳遞給 CCustomTransition。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CCustomInterpolator`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="ccustominterpolator"></a>CCustomInterpolator::CCustomInterpolator  
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
 您可以使用 CCustomInterpolator::Init 初始化持續時間和更新版本中的程式碼的最終值。  
  
##  <a name="getdependencies"></a>CCustomInterpolator::GetDependencies  
 取得 interpolator 的相依性。  
  
```  
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,  
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,  
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>參數  
 `initialValueDependencies`  
 輸出。 Interpolator 的起始值而定的各個層面傳遞給 SetInitialValueAndVelocity。  
  
 `initialVelocityDependencies`  
 輸出。 Interpolator 的初始速度而定的部分傳遞至 SetInitialValueAndVelocity。  
  
 `durationDependencies`  
 輸出。 Interpolator 的持續時間而定的部分傳遞至 SetDuration。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一律會傳回 TRUE。 會傳回 FALSE 覆寫的實作如果您想要失敗事件。  
  
##  <a name="getduration"></a>CCustomInterpolator::GetDuration  
 取得 interpolator 的持續時間。  
  
```  
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 輸出。 轉換，以秒為單位的持續時間。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一律會傳回 TRUE。 會傳回 FALSE 覆寫的實作如果您想要失敗事件。  
  
##  <a name="getfinalvalue"></a>CCustomInterpolator::GetFinalValue  
 取得 interpolator 會導致的最終值。  
  
```  
virtual BOOL GetFinalValue(DOUBLE* value);
```  
  
### <a name="parameters"></a>參數  
 `value`  
 輸出。 變數在轉換結束最後的值。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一律會傳回 TRUE。 會傳回 FALSE 覆寫的實作如果您想要失敗事件。  
  
##  <a name="init"></a>CCustomInterpolator::Init  
 初始化持續時間和最後一個值。  
  
```  
void Init(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
 `finalValue`  
 變數在轉換結束最後的值。  
  
##  <a name="interpolatevalue"></a>CCustomInterpolator::InterpolateValue  
 進行插補在指定位移的值。  
  
```  
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* value);
```  
  
### <a name="parameters"></a>參數  
 `value`  
 輸出。 插補的值。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一律會傳回 TRUE。 會傳回 FALSE 覆寫的實作如果您想要失敗事件。  
  
##  <a name="interpolatevelocity"></a>CCustomInterpolator::InterpolateVelocity  
 插補在指定位移的速度  
  
```  
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* velocity);
```  
  
### <a name="parameters"></a>參數  
 `velocity`  
 輸出。 在位移變數的速度。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一律會傳回 TRUE。 會傳回 FALSE 覆寫的實作如果您想要失敗事件。  
  
##  <a name="m_currentvalue"></a>CCustomInterpolator::m_currentValue  
 插補的值。  
  
```  
DOUBLE m_currentValue;  
```  
  
##  <a name="m_currentvelocity"></a>CCustomInterpolator::m_currentVelocity  
 插補的速度。  
  
```  
DOUBLE m_currentVelocity;  
```  
  
##  <a name="m_duration"></a>CCustomInterpolator::m_duration  
 轉換的持續時間。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_finalvalue"></a>CCustomInterpolator::m_finalValue  
 變數在轉換結束最後的值。  
  
```  
DOUBLE m_finalValue;  
```  
  
##  <a name="m_initialvalue"></a>CCustomInterpolator::m_initialValue  
 在開始轉換的變數的值。  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>CCustomInterpolator::m_initialVelocity  
 在開始轉換的變數的速度。  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="setduration"></a>CCustomInterpolator::SetDuration  
 Interpolator 的持續時間設定。  
  
```  
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
### <a name="return-value"></a>傳回值  
 基本的實作一律會傳回 TRUE。 會傳回 FALSE 覆寫的實作如果您想要失敗事件。  
  
##  <a name="setinitialvalueandvelocity"></a>CCustomInterpolator::SetInitialValueAndVelocity  
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
 基本的實作一律會傳回 TRUE。 會傳回 FALSE 覆寫的實作如果您想要失敗事件。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

