---
title: "2.6.4 atomic 建構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.4 atomic 建構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

 `atomic` 指示詞可確保特定記憶體位置會更新以不可分割的方式，而不是公開的多個可能性同時寫入的執行緒。 語法 `atomic` 指示詞時，如下所示︰  
  
```  
#pragma omp atomic new-lineexpression-stmt  
```  
  
 運算陳述式必須具有下列格式之一︰  
  
 *x binop*= *expr*  
  
 x + +  
  
 + + x  
  
 x-  
  
 --x  
  
 在上述的運算式︰  
  
-   *x* 是左值運算式，具有純量型別。  
  
-   *expr* 是運算式，具有純量型別，並不會參考所指定的物件 *x*。  
  
-   `binop` 多載的運算子並不是其中一個 +、 *、-、 /、 &、 ^，（& s) #124;，<\<，或 >>。  
  
 雖然它是由實作定義是否實作會取代所有 `atomic` 指示詞與 **重大** 指示詞具有相同的唯一 *名稱*, 、 `atomic` 指示詞允許更好的最佳化。 硬體指示通常可以執行具有最少負荷的不可部分完成更新。  
  
 只有負載和指定之物件的存放區 *x* 是不可部分完成; 評估 *expr* 不是不可部分完成。 若要避免競爭情形，平行的位置中的所有更新應受到都保護以 `atomic` 指示詞，除了已知為免費的競爭情形。  
  
 若要限制 `atomic` 指示詞會如下所示︰  
  
-   整個程式的儲存位置 x 不可部分完成的所有參考都需要有相容的型別。  
  
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