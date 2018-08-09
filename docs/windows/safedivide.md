---
title: SafeDivide |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeDivide
dev_langs:
- C++
helpviewer_keywords:
- SafeDivide function
ms.assetid: b5b27484-ad6e-46b1-ba9f-1c7120dd103b
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4d7c966db1193def6479ecfd231293212bca2b1f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018016"
---
# <a name="safedivide"></a>SafeDivide
兩數相除防止除以零的方式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<typename T, typename U>  
inline bool SafeDivide (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
### <a name="parameters"></a>參數  
 [in]*t*  
 除數。 這必須為類型 T。  
  
 [in]*u*  
 被除數。 這必須為類型 U。  
  
 [out]*結果*  
 參數所在**SafeDivide**儲存結果。  
  
## <a name="return-value"></a>傳回值  
 **true**如果沒有發生錯誤;**false**發生錯誤。  
  
## <a name="remarks"></a>備註  
 這個方法屬於[SafeInt 程式庫](../windows/safeint-library.md)而設計的單一除法運算，而不需要建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。  
  
> [!NOTE]
>  此方法應只有在必須保護單一數學作業時才使用。 如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。  
  
 如需範本類型 T 和 U 的詳細資訊，請參閱[SafeInt 函式](../windows/safeint-functions.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** safeint.h  
  
 **命名空間：** Microsoft::Utilities  
  
## <a name="see-also"></a>另請參閱  
 [SafeInt 函式](../windows/safeint-functions.md)   
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)   
 [SafeModulus](../windows/safemodulus.md)   
 [SafeMultiply](../windows/safemultiply.md)