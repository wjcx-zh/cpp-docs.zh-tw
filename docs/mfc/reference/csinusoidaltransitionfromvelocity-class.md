---
title: CSinusoidalTransitionFromVelocity 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_period
dev_langs:
- C++
helpviewer_keywords:
- CSinusoidalTransitionFromVelocity [MFC], CSinusoidalTransitionFromVelocity
- CSinusoidalTransitionFromVelocity [MFC], Create
- CSinusoidalTransitionFromVelocity [MFC], m_duration
- CSinusoidalTransitionFromVelocity [MFC], m_period
ms.assetid: cc885f17-b84b-45ee-8f1f-36a8bbb7adad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9833607065407e66473a9fab1907bf2262816296
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370636"
---
# <a name="csinusoidaltransitionfromvelocity-class"></a>CSinusoidalTransitionFromVelocity 類別
封裝由動畫變數的初始速度決定其幅度的正弦曲線速度轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CSinusoidalTransitionFromVelocity : public CBaseTransition;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity](#csinusoidaltransitionfromvelocity)|建構轉換物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::m_duration](#m_duration)|轉換的持續時間。|  
|[CSinusoidalTransitionFromVelocity::m_period](#m_period)|以秒為單位的正弦曲線 wave 振動期間。|  
  
## <a name="remarks"></a>備註  
 動畫變數的值會在整個持續期間內的正弦曲線範圍轉換 oscillates 周圍的起始值。 在轉換開始時由動畫變數的速度決定振動的幅度。 由於所有轉換會自動都清除，建議來配置它們使用新的運算子。 封裝的 IUIAnimationTransition COM 物件會建立 CAnimationController::AnimateGroup，直到然後它便是 NULL。 變更成員變數之後這個 COM 物件建立沒有任何作用。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSinusoidalTransitionFromVelocity](../../mfc/reference/csinusoidaltransitionfromvelocity-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="create"></a>  CSinusoidalTransitionFromVelocity::Create  
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
  
##  <a name="csinusoidaltransitionfromvelocity"></a>  CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity  
 建構轉換物件。  
  
```  
CSinusoidalTransitionFromVelocity(
    UI_ANIMATION_SECONDS duration,  
    UI_ANIMATION_SECONDS period);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
 `period`  
 以秒為單位的正弦曲線 wave 振動期間。  
  
##  <a name="m_duration"></a>  CSinusoidalTransitionFromVelocity::m_duration  
 轉換的持續時間。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_period"></a>  CSinusoidalTransitionFromVelocity::m_period  
 以秒為單位的正弦曲線 wave 振動期間。  
  
```  
UI_ANIMATION_SECONDS m_period;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
