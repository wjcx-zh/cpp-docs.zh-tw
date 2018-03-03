---
title: "CReversalTransition 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::Create
- AFXANIMATIONCONTROLLER/CReversalTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CReversalTransition [MFC], CReversalTransition
- CReversalTransition [MFC], Create
- CReversalTransition [MFC], m_duration
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fdce13f41e95cda592fec03fcedb01984fb34ab9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creversaltransition-class"></a>CReversalTransition 類別
封裝反轉的轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class CReversalTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CReversalTransition::CReversalTransition](#creversaltransition)|建構反轉的轉換物件並初始化其持續時間。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CReversalTransition::Create](#create)|呼叫轉換程式庫來建立封裝的轉換 COM 物件。 (覆寫[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CReversalTransition::m_duration](#m_duration)|轉換的持續時間。|  
  
## <a name="remarks"></a>備註  
 反轉的轉換順暢地變更指定的持續期間內的方向。 最終的值將會是相同的起始值和最終的速度將會是負的初始速度。 由於所有轉換會自動都清除，建議來配置它們使用新的運算子。 封裝的 IUIAnimationTransition COM 物件會建立 CAnimationController::AnimateGroup，直到然後它便是 NULL。 變更成員變數之後這個 COM 物件建立沒有任何作用。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CReversalTransition](../../mfc/reference/creversaltransition-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxanimationcontroller.h  
  
##  <a name="create"></a>CReversalTransition::Create  
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
  
##  <a name="creversaltransition"></a>CReversalTransition::CReversalTransition  
 建構反轉的轉換物件並初始化其持續時間。  
  
```  
CReversalTransition(UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>參數  
 `duration`  
 轉換的持續時間。  
  
##  <a name="m_duration"></a>CReversalTransition::m_duration  
 轉換的持續時間。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
