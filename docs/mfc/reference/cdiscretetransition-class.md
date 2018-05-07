---
title: CDiscreteTransition 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::Create
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_delay
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_hold
dev_langs:
- C++
helpviewer_keywords:
- CDiscreteTransition [MFC], CDiscreteTransition
- CDiscreteTransition [MFC], Create
- CDiscreteTransition [MFC], m_dblFinalValue
- CDiscreteTransition [MFC], m_delay
- CDiscreteTransition [MFC], m_hold
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 858304a41cb015711393ea6cc41e73ddbcc8cd8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition 類別
封裝離散的轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CDiscreteTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|建構離散的轉換物件並初始化其參數。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDiscreteTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|結尾的轉換動畫變數的值。|  
|[CDiscreteTransition::m_delay](#m_delay)|所要依據的延遲時間的瞬間交換器的最終值的時間量。|  
|[CDiscreteTransition::m_hold](#m_hold)|用來保存變數，在最後一個值的時間量。|  
  
## <a name="remarks"></a>備註  
 離散的轉換期間動畫變數會保持為初始值為指定的延遲時間，然後立即交換器指定的最終值以及該值維持給定的保留時間。 由於所有轉換會自動都清除，建議來配置它們使用新的運算子。 封裝的 IUIAnimationTransition COM 物件會建立 CAnimationController::AnimateGroup，直到然後它便是 NULL。 變更成員變數之後這個 COM 物件建立沒有任何作用。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="cdiscretetransition"></a>  CDiscreteTransition::CDiscreteTransition  
 建構離散的轉換物件並初始化其參數。  
  
```  
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,  
    DOUBLE dblFinalValue,  
    UI_ANIMATION_SECONDS hold);
```  
  
### <a name="parameters"></a>參數  
 `delay`  
 所要依據的延遲時間的瞬間交換器的最終值的時間量。  
  
 `dblFinalValue`  
 結尾的轉換動畫變數的值。  
  
 `hold`  
 用來保存變數，在最後一個值的時間量。  
  
##  <a name="create"></a>  CDiscreteTransition::Create  
 呼叫轉換程式庫來建立封裝的轉換 COM 物件。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
`pLibrary`  
 指標[IUIAnimationTransitionLibrary 介面](https://msdn.microsoft.com/library/windows/desktop/dd371897)，其定義的標準轉換程式庫。  

  
### <a name="return-value"></a>傳回值  
 如果轉換成功; 建立，則為 TRUE。否則為 FALSE。  
  
##  <a name="m_dblfinalvalue"></a>  CDiscreteTransition::m_dblFinalValue  
 結尾的轉換動畫變數的值。  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_delay"></a>  CDiscreteTransition::m_delay  
 所要依據的延遲時間的瞬間交換器的最終值的時間量。  
  
```  
UI_ANIMATION_SECONDS m_delay;  
```  
  
##  <a name="m_hold"></a>  CDiscreteTransition::m_hold  
 用來保存變數，在最後一個值的時間量。  
  
```  
UI_ANIMATION_SECONDS m_hold;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
