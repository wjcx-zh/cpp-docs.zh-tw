---
title: CParabolicTransitionFromAcceleration 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::Create
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalVelocity
dev_langs:
- C++
helpviewer_keywords:
- CParabolicTransitionFromAcceleration [MFC], CParabolicTransitionFromAcceleration
- CParabolicTransitionFromAcceleration [MFC], Create
- CParabolicTransitionFromAcceleration [MFC], m_dblAcceleration
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalValue
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalVelocity
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02cf84f2774a10ec0ca2751dbeffd4eb3c52e8a2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370971"
---
# <a name="cparabolictransitionfromacceleration-class"></a>CParabolicTransitionFromAcceleration 類別
封裝拋物線加速轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CParabolicTransitionFromAcceleration : public CBaseTransition;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](#cparabolictransitionfromacceleration)|建構拋物線加速轉換，並將它初始化以指定的參數。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::m_dblAcceleration](#m_dblacceleration)|在轉換期間動畫變數的加速。|  
|[CParabolicTransitionFromAcceleration::m_dblFinalValue](#m_dblfinalvalue)|結尾的轉換動畫變數的值。|  
|[CParabolicTransitionFromAcceleration::m_dblFinalVelocity](#m_dblfinalvelocity)|結尾的轉換動畫變數的速度。|  
  
## <a name="remarks"></a>備註  
 拋物線加速轉換，期間動畫變數的值變更的起始值的結束時間指定速度的最終值。 您可以控制變數速度藉由指定的加速速率達到最後的值。 由於所有轉換會自動都清除，建議來配置它們使用新的運算子。 封裝的 IUIAnimationTransition COM 物件會建立 CAnimationController::AnimateGroup，直到然後它便是 NULL。 變更成員變數之後這個 COM 物件建立沒有任何作用。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="cparabolictransitionfromacceleration"></a>  CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration  
 建構拋物線加速轉換，並將它初始化以指定的參數。  
  
```  
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,  
    DOUBLE dblFinalVelocity,  
    DOUBLE dblAcceleration);
```  
  
### <a name="parameters"></a>參數  
 `dblFinalValue`  
 結尾的轉換動畫變數的值。  
  
 `dblFinalVelocity`  
 結尾的轉換動畫變數的速度。  
  
 `dblAcceleration`  
 在轉換期間動畫變數的加速。  
  
##  <a name="create"></a>  CParabolicTransitionFromAcceleration::Create  
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
  
##  <a name="m_dblacceleration"></a>  CParabolicTransitionFromAcceleration::m_dblAcceleration  
 在轉換期間動畫變數的加速。  
  
```  
DOUBLE m_dblAcceleration;  
```  
  
##  <a name="m_dblfinalvalue"></a>  CParabolicTransitionFromAcceleration::m_dblFinalValue  
 結尾的轉換動畫變數的值。  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_dblfinalvelocity"></a>  CParabolicTransitionFromAcceleration::m_dblFinalVelocity  
 結尾的轉換動畫變數的速度。  
  
```  
DOUBLE m_dblFinalVelocity;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
