---
title: CCubicTransition 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::Create
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalVelocity
- AFXANIMATIONCONTROLLER/CCubicTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CCubicTransition [MFC], CCubicTransition
- CCubicTransition [MFC], Create
- CCubicTransition [MFC], m_dblFinalValue
- CCubicTransition [MFC], m_dblFinalVelocity
- CCubicTransition [MFC], m_duration
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 001a1e66707544f6446a5bc54e70269f94108654
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351904"
---
# <a name="ccubictransition-class"></a>CCubicTransition 類別
封裝立方轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CCubicTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CCubicTransition::CCubicTransition](#ccubictransition)|建構轉換物件並初始化其參數。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CCubicTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|結尾的轉換動畫變數的值。|  
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|在轉換結束變數的速度。|  
|[CCubicTransition::m_duration](#m_duration)|轉換的持續時間。|  
  
## <a name="remarks"></a>備註  
 三次方的轉換，期間動畫變數的值變更於其初始值為指定的最後一個值的轉換，結束時間指定速度持續期間內。 由於所有轉換會自動都清除，建議來配置它們使用新的運算子。 封裝的 IUIAnimationTransition COM 物件會建立 CAnimationController::AnimateGroup，直到然後它便是 NULL。 變更成員變數之後這個 COM 物件建立沒有任何作用。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CCubicTransition`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="ccubictransition"></a>  CCubicTransition::CCubicTransition  
 建構轉換物件並初始化其參數。  
  
```  
CCubicTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue,  
    DOUBLE finalVelocity);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
 `finalValue`  
 結尾的轉換動畫變數的值。  
  
 `finalVelocity`  
 在轉換結束變數的速度。  
  
##  <a name="create"></a>  CCubicTransition::Create  
 呼叫轉換程式庫來建立封裝的轉換 COM 物件。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>參數  
`pLibrary`  
 指標[IUIAnimationTransitionLibrary 介面](https://msdn.microsoft.com/library/windows/desktop/dd371897)，其定義的標準轉換程式庫。  

### <a name="return-value"></a>傳回值  
 如果轉換成功; 建立，則為 TRUE。否則為 FALSE。  
  
##  <a name="m_dblfinalvalue"></a>  CCubicTransition::m_dblFinalValue  
 結尾的轉換動畫變數的值。  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_dblfinalvelocity"></a>  CCubicTransition::m_dblFinalVelocity  
 在轉換結束變數的速度。  
  
```  
DOUBLE m_dblFinalVelocity;  
```  
  
##  <a name="m_duration"></a>  CCubicTransition::m_duration  
 轉換的持續時間。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
