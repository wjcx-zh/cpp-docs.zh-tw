---
title: SafeCast |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeCast
dev_langs:
- C++
helpviewer_keywords:
- SafeCast function
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95a3f8508c17936626558ecc6a8d01e21688d403
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892448"
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
 `true` 如果沒有發生錯誤。`false`如果發生錯誤。  
  
## <a name="remarks"></a>備註  
 這個方法是一部分[SafeInt 程式庫](../windows/safeint-library.md)，適用於單一的轉型作業而不需要建立的執行個體[SafeInt 類別](../windows/safeint-class.md)。  
  
> [!NOTE]
>  必須保護單一作業時，才應該使用這個方法。 如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。  
  
 如需範本型別 T 和 U，請參閱[SafeInt 函式](../windows/safeint-functions.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** safeint.h  
  
 **命名空間：** Microsoft::Utilities  
  
## <a name="see-also"></a>另請參閱  
 [SafeInt 函式](../windows/safeint-functions.md)   
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)