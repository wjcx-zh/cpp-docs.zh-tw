---
title: SafeGreaterThanEquals |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeGreaterThanEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeGreaterThanEquals function
ms.assetid: 43312fa9-d925-4f9f-a352-a190c02b3005
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c8b08e9262c1fc251de9ce2e23ba37783e97ab9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="safegreaterthanequals"></a>SafeGreaterThanEquals
比較兩個數字。  
  
## <a name="syntax"></a>語法  
  
```  
template <typename T, typename U>  
inline bool SafeGreaterThanEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `t`  
 要比較的第一個數字。 這必須為類型 T。  
  
 [輸入] `u`  
 要比較的第二個數字。 這必須為類型 U。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果`t`大於或等於`u`，否則為`false`。  
  
## <a name="remarks"></a>備註  
 `SafeGreaterThanEquals` 增強的一般比較運算子，因為它可讓您比較兩個不同類型的數字。  
  
 這個方法是一部分[SafeInt 程式庫](../windows/safeint-library.md)，適用於單一比對作業不需要建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。  
  
> [!NOTE]
>  此方法應只有在必須保護單一數學作業時才使用。 如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。  
  
 如需範本型別 T 和 U，請參閱[SafeInt 函式](../windows/safeint-functions.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** safeint.h  
  
 **命名空間：** Microsoft::Utilities  
  
## <a name="see-also"></a>另請參閱  
 [SafeInt 函式](../windows/safeint-functions.md)   
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)   
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeLessThanEquals](../windows/safelessthanequals.md)   
 [SafeLessThan](../windows/safelessthan.md)