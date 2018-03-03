---
title: "SafeCast |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeCast
dev_langs:
- C++
helpviewer_keywords:
- SafeCast function
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4c3c9bb208cc2be2f91d8a464787d3299cd0b386
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="safecast"></a>SafeCast
會轉換成其他類型的數字的一種類型。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T, typename U>  
inline bool SafeCast (  
   const T From,  
   U& To  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `From`  
 要轉換的來源點數。 這必須為類型 T。  
  
 [輸出] `To`  
 新的數字類型的參考。 這必須為類型 U。  
  
## <a name="return-value"></a>傳回值  
 `true`如果沒有發生錯誤。`false`如果發生錯誤。  
  
## <a name="remarks"></a>備註  
 這個方法是一部分[SafeInt 程式庫](../windows/safeint-library.md)，適用於單一的轉型作業而不需要建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。  
  
> [!NOTE]
>  必須保護單一作業時，才應該使用這個方法。 如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。  
  
 如需範本型別 T 和 U，請參閱[SafeInt 函式](../windows/safeint-functions.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** safeint.h  
  
 **命名空間：** Microsoft::Utilities  
  
## <a name="see-also"></a>請參閱  
 [SafeInt 函式](../windows/safeint-functions.md)   
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)