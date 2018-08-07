---
title: SafeAdd |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeAdd
dev_langs:
- C++
helpviewer_keywords:
- SafeAdd function
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8686d0ef990e9be22ec4ebe1c81c737df9b15812
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607400"
---
# <a name="safeadd"></a>SafeAdd
兩個數字相加來防止溢位。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T, typename U>  
inline bool SafeAdd (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
### <a name="parameters"></a>參數  
 [in]*t*  
 要新增的第一個數字。 這必須為類型 T。  
  
 [in]*u*  
 若要新增第二個數字。 這必須為類型 U。  
  
 [out]*結果*  
 參數所在**SafeAdd**儲存結果。  
  
## <a name="return-value"></a>傳回值  
 **true**如果沒有發生錯誤;**false**發生錯誤。  
  
## <a name="remarks"></a>備註  
 這個方法屬於[SafeInt 程式庫](../windows/safeint-library.md)而設計的單一的加法運算，而不需要建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。  
  
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
 [SafeSubtract](../windows/safesubtract.md)