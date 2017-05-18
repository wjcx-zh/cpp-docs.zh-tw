---
title: "CCustomTransition 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- CCustomTransition class
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: 483fb2ab84d2c41fe4666a4ea333c0be8b07caee
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ccustomtransition-class"></a>CCustomTransition 類別
實作自訂的轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CCustomTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CCustomTransition::CCustomTransition](#ccustomtransition)|建構自訂的轉換物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CCustomTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
|[CCustomTransition::SetInitialValue](#setinitialvalue)|設定初始的值，將會套用至這項轉換相關聯的動畫變數。|  
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|設定將套用至這項轉換相關聯的動畫變數的初始速度。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|指定與 SetInitialValue 是否已指定的初始值。|  
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|指定與 SetInitialVelocity 是否已指定初始的速度。|  
|[CCustomTransition::m_initialValue](#m_initialvalue)|儲存的起始值。|  
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|儲存初始的速度。|  
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|儲存自訂 interpolator 的指標。|  
  
## <a name="remarks"></a>備註  
 CCustomTransitions 類別可讓開發人員實作自訂的轉換。 它必須先建立並做為標準轉換，但其建構函式做為參數會接受自訂 interpolator 的指標。 執行下列步驟，以使用自訂的轉換︰ 1。 從 CCustomInterpolator 衍生類別，並至少實作 InterpolateValue 方法。 2. 確定在自訂 interpolator 物件的存留期超過動畫的持續時間使用的位置。 3. 具現化 （新使用運算子） CCustomTransition 物件，並將指標傳遞給建構函式中的自訂 interpolator。 4. 如果所需的自訂插補這些參數，呼叫 CCustomTransition::SetInitialValue 和 CCustomTransition::SetInitialVelocity。 5. 將指標傳遞給還得方法應該使用自訂演算法動畫顯示其值的動畫物件的自訂轉換。 6. 當動畫物件的值應該變更 Windows 動畫 API 會以 CCustomInterpolator 呼叫 InterpolateValue （和其他相關的方法）。  
  
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
 轉換處理站負責建立的自訂轉換指標。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 這個方法也可以設定初始值和套用至動畫變數，也就是這項轉換相關聯的初始速度。 針對此目的，您必須呼叫 SetInitialValue 和 SetInitialVelocity 之前此架構會建立封裝的轉換 COM 物件 （它會呼叫 CAnimationController::AnimateGroup 時）。  
  
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
 設定初始的值，將會套用至這項轉換相關聯的動畫變數。  
  
```  
void SetInitialValue(DOUBLE initialValue);
```  
  
### <a name="parameters"></a>參數  
 `initialValue`  
  
##  <a name="setinitialvelocity"></a>CCustomTransition::SetInitialVelocity  
 設定將套用至這項轉換相關聯的動畫變數的初始速度。  
  
```  
void SetInitialVelocity(DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>參數  
 `initialVelocity`  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

