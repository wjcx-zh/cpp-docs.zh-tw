---
title: "SafeModulus |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SafeModulus
dev_langs: C++
helpviewer_keywords: SafeModulus function
ms.assetid: ae5c81eb-5dcf-45a5-aa76-465fdfe68654
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 383382de2720ac7a72403bd3578e235af7bdbe05
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="safemodulus"></a>SafeModulus
執行兩個數字的模數作業。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T, typename U>  
inline bool SafeModulus (  
   const T t,  
   const U u,  
   T& result  
) throw ();  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `t`  
 除數。 這必須為類型 T。  
  
 [輸入] `u`  
 被除數。 這必須為類型 U。  
  
 [輸出] `result`  
 參數所在`SafeModulus`儲存結果。  
  
## <a name="return-value"></a>傳回值  
 `true`如果沒有發生錯誤。`false`如果發生錯誤。  
  
## <a name="remarks"></a>備註  
 這個方法是一部分[SafeInt 程式庫](../windows/safeint-library.md)，而不需要建立的執行個體適用於單一的模數運算[SafeInt 類別](../windows/safeint-class.md)。  
  
> [!NOTE]
>  此方法應只有在必須保護單一數學作業時才使用。 如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。  
  
 如需範本型別 T 和 U，請參閱[SafeInt 函式](../windows/safeint-functions.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** safeint.h  
  
 **命名空間：** Microsoft::Utilities  
  
## <a name="see-also"></a>請參閱  
 [SafeInt 函式](../windows/safeint-functions.md)   
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)   
 [SafeDivide](../windows/safedivide.md)