---
title: "SafeAdd |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeAdd
dev_langs:
- C++
helpviewer_keywords:
- SafeAdd function
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e8b668f5b164934cff6643d73d9b4b6169a9d4b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="safeadd"></a>SafeAdd
兩個數字相加，以防止溢位的方式。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T, typename U>  
inline bool SafeAdd (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `t`  
 要加入的第一個數字。 這必須為類型 T。  
  
 [輸入] `u`  
 若要加入第二個數字。 這必須為類型 U。  
  
 [輸出] `result`  
 參數所在`SafeAdd`儲存結果。  
  
## <a name="return-value"></a>傳回值  
 `true`如果沒有發生錯誤。`false`如果發生錯誤。  
  
## <a name="remarks"></a>備註  
 這個方法是一部分[SafeInt 程式庫](../windows/safeint-library.md)，而不需要建立的執行個體適用於單一加法運算[SafeInt 類別](../windows/safeint-class.md)。  
  
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
 [SafeSubtract](../windows/safesubtract.md)