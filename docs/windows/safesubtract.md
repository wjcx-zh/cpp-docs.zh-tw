---
title: SafeSubtract |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeSubtract
dev_langs:
- C++
helpviewer_keywords:
- SafeSubtract function
ms.assetid: c2712ddc-173f-46a1-b09c-e7ebbd9e68b2
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a82281f1078acd5e3ed0662964a0171ccd72c336
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018370"
---
# <a name="safesubtract"></a>SafeSubtract
兩個數字的方式防止溢位。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<typename T, typename U>  
inline bool SafeSubtract (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
### <a name="parameters"></a>參數  
 [in]*t*  
 減法運算中的第一個數字。 這必須是型別`T`。  
  
 [in]*u*  
 要減去的數字*t*。 這必須是型別`U`。  
  
 [out]*結果*  
 參數所在**SafeSubtract**儲存結果。  
  
## <a name="return-value"></a>傳回值  
 **true**如果沒有發生錯誤;**false**發生錯誤。  
  
## <a name="remarks"></a>備註  
 這個方法屬於[SafeInt 程式庫](../windows/safeint-library.md)而設計的單一的減法運算，而不需要建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。  
  
> [!NOTE]
>  此方法應只有在必須保護單一數學作業時才使用。 如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。  
  
 如需範本類型的詳細資訊`T`並`U`，請參閱[SafeInt 函式](../windows/safeint-functions.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** safeint.h  
  
 **命名空間：** Microsoft::Utilities  
  
## <a name="see-also"></a>另請參閱  
 [SafeInt 函式](../windows/safeint-functions.md)   
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)   
 [SafeAdd](../windows/safeadd.md)