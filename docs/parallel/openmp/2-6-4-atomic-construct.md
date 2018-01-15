---
title: "2.6.4 atomic 建構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 629fff5b0bef507b775fbe1b5bfabadd50b790be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="264-atomic-construct"></a>2.6.4 atomic 建構
`atomic`指示詞可確保特定的記憶體位置會以不可分割方式，更新，而不是公開多個可能性同時撰寫執行緒。 語法`atomic`指示詞時，如下所示：  
  
```  
#pragma omp atomic new-lineexpression-stmt  
```  
  
 在運算式陳述式必須具有下列格式之一：  
  
 *x binop*= *expr*  
  
 x + +  
  
 + + x  
  
 x-  
  
 --x  
  
 在上述的運算式：  
  
-   *x*是純量型別左值運算式。  
  
-   *expr*具有純量類型的運算式，且未參考指定之物件*x*。  
  
-   `binop`多載的運算子並不是其中一個 +、 *、-，/，&、 ^，&#124;，<\<，或 >>。  
  
 雖然它是由實作定義是否實作會取代所有`atomic`指示詞與**重大**指示詞具有相同的唯一*名稱*、`atomic`指示詞允許更佳的最佳化。 使用的硬體指示通常可執行不可部分完成的更新具有最少額外負荷。  
  
 只有負載和所指定的物件存放區*x*是不可部分完成; 評估*expr*不是不可部分完成。 若要避免競爭情形，所有更新的位置，以平行方式應該都受到`atomic`指示詞，除了已知為免費提供的競爭情形。  
  
 若要限制`atomic`指示詞如下：  
  
-   在整個程式的儲存位置 x 不可部分完成的所有參考都需要有相容的類型。  
  
## <a name="examples"></a>例如：  
  
```  
extern float a[], *p = a, b;  
/* Protect against races among multiple updates. */  
#pragma omp atomic  
a[index[i]] += b;  
/* Protect against races with updates through a. */  
#pragma omp atomic  
p[i] -= 1.0f;  
  
extern union {int n; float x;} u;  
/* ERROR - References through incompatible types. */  
#pragma omp atomic  
u.n++;  
#pragma omp atomic  
u.x -= 1.0f;  
```