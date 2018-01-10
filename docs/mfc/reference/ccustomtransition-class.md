---
title: "CCustomTransition 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
dev_langs: C++
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b94fd32bd00a484c5f8e3ba9e86efc5a9637e4e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccustomtransition-class"></a>CCustomTransition 類別
實作自訂的轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CCustomTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CCustomTransition::CCustomTransition](#ccustomtransition)|建構自訂的轉換物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CCustomTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
|[CCustomTransition::SetInitialValue](#setinitialvalue)|設定初始的值，將會套用到這項轉換相關聯的動畫變數。|  
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|設定初始的速度，將會套用到這項轉換相關聯的動畫變數。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|指定與 SetInitialValue 是否已指定的初始值。|  
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|指定與 SetInitialVelocity 是否已指定初始的速度。|  
|[CCustomTransition::m_initialValue](#m_initialvalue)|儲存的起始值。|  
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|儲存初始的速度。|  
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|儲存自訂 interpolator 的指標。|  
  
## <a name="remarks"></a>備註  
 CCustomTransitions 類別可讓開發人員實作自訂的轉換。 它必須先建立並做為標準轉換，但其建構函式做為參數會接受自訂 interpolator 的指標。 執行下列步驟，以使用自訂的轉換： 1。 CCustomInterpolator 從衍生類別並實作至少 InterpolateValue 方法。 2. 請確認自訂 interpolator 物件的存留期必須超過動畫的持續時間使用的位置。 3. 具現化 （使用運算子 new） CCustomTransition 物件，並將指標傳遞至建構函式中的自訂 interpolator。 4. CCustomTransition::SetInitialValue 和 CCustomTransition::SetInitialVelocity 如果呼叫這些參數所需的自訂的插補。 5. 將指標傳遞給自訂轉換還得方法的動畫物件，其值應該繪製自訂演算法。 6. 當動畫之物件的值應該變更 Windows 動畫 API 會呼叫 InterpolateValue （和其他相關的方法） CCustomInterpolator 中。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CCustomTransition`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="ccustomtransition"></a>CCustomTransition::CCustomTransition  
 建構自訂的轉換物件。  
  
```  
CCustomTransition(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>參數  
 `pInterpolator`  
 自訂 interpolator 指標。  
  
##  <a name="create"></a>CCustomTransition::Create  
 呼叫轉換程式庫來建立封裝的轉換 COM 物件。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,  
    IUIAnimationTransitionFactory* pFactory);
```  
  
### <a name="parameters"></a>參數  
 `pFactory`  
 轉換處理站，也就是負責建立的自訂轉換指標。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 這個方法也可以設定初始值和要套用至動畫變數，也就是這項轉換相關聯的初始速度。 針對此目的，您必須呼叫 SetInitialValue 和 SetInitialVelocity，架構會建立封裝的轉換 COM 物件 （它時不會呼叫 CAnimationController::AnimateGroup） 之前。  
  
##  <a name="m_binitialvaluespecified"></a>CCustomTransition::m_bInitialValueSpecified  
 指定與 SetInitialValue 是否已指定的初始值。  
  
```  
BOOL m_bInitialValueSpecified;  
```  
  
##  <a name="m_binitialvelocityspecified"></a>CCustomTransition::m_bInitialVelocitySpecified  
 指定與 SetInitialVelocity 是否已指定初始的速度。  
  
```  
BOOL m_bInitialVelocitySpecified;  
```  
  
##  <a name="m_initialvalue"></a>CCustomTransition::m_initialValue  
 儲存的起始值。  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>CCustomTransition::m_initialVelocity  
 儲存初始的速度。  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="m_pinterpolator"></a>CCustomTransition::m_pInterpolator  
 儲存自訂 interpolator 的指標。  
  
```  
CCustomInterpolator* m_pInterpolator;  
```  
  
##  <a name="setinitialvalue"></a>CCustomTransition::SetInitialValue  
 設定初始的值，將會套用到這項轉換相關聯的動畫變數。  
  
```  
void SetInitialValue(DOUBLE initialValue);
```  
  
### <a name="parameters"></a>參數  
 `initialValue`  
  
##  <a name="setinitialvelocity"></a>CCustomTransition::SetInitialVelocity  
 設定初始的速度，將會套用到這項轉換相關聯的動畫變數。  
  
```  
void SetInitialVelocity(DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>參數  
 `initialVelocity`  
  
## <a name="see-also"></a>請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
