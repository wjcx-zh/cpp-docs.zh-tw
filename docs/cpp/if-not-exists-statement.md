---
title: "__if_not_exists 陳述式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __if_not_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 5eff74bd6405d7ec63b3cc8fbea968df984fddb8
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="ifnotexists-statement"></a>__if_not_exists 陳述式
`__if_not_exists` 陳述式會測試指定識別項是否存在。 如果識別項不存在，就會執行指定的陳述式區塊。  
  
## <a name="syntax"></a>語法  
  
```  
__if_not_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`identifier`|要測試其是否存在的識別項。|  
|`statements`|如果執行的一或多個陳述式`identifier`不存在。|  
  
## <a name="remarks"></a>備註  
  
> [!CAUTION]
>  為取得最可靠的結果，使用 `__if_not_exists` 陳述式時請遵循下列條件約束。  
  
-   只能將 `__if_not_exists` 陳述式套用至簡單類型，而不能套用於範本。  
  
-   將 `__if_not_exists` 陳述式套用至類別內外的識別項。 勿將 `__if_not_exists` 陳述式套用至區域變數。  
  
-   只在函式本體中使用 `__if_not_exists` 陳述式。 在函式的主體之外，`__if_not_exists` 陳述式只能測試完整定義的類型。  
  
-   當您對多載函式進行測試時，無法對特定形式的多載進行測試。  
  
 補數`__if_not_exists`陳述式是[__if_exists](../cpp/if-exists-statement.md)陳述式。  
  
## <a name="example"></a>範例  
 如需如何使用`__if_not_exists`，請參閱[__if_exists 陳述式](../cpp/if-exists-statement.md)。  
  
## <a name="see-also"></a>另請參閱  
 [選擇陳述式](../cpp/selection-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [__if_exists 陳述式](../cpp/if-exists-statement.md)
