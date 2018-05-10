---
title: 2.7.2.8 copyprivate |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c809f297da5059a98915e8055dfe23f45074366f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="2728-copyprivate"></a>2.7.2.8 copyprivate
**Copyprivate**子句提供一個機制，從一個小組成員的值廣播到的其他成員使用私用變數。 它會提供這類共用的變數會很難 （例如，在需要不同的變數在每個層級的遞迴函式） 時，使用共用的變數值的替代方案。 **Copyprivate**子句只能出現在**單一**指示詞。  
  
 語法**copyprivate**子句如下所示：  
  
```  
  
copyprivate(  
variable-list  
)  
  
```  
  
 效果**copyprivate**變數清單中的變數上的子句執行相關聯的結構化區塊後，就會發生**單一**建構，並在任何中的執行緒之前小組已離開屏障建構結尾。 然後，在小組中，針對每個變數中的其他所有執行緒在*變數清單*，該變數會變成 （如同依指派） 已定義的對應值的結構化之執行緒的執行建構中的變數區塊。  
  
 若要限制**copyprivate**子句如下：  
  
-   中指定的變數**copyprivate**子句不能出現在**私人**或**firstprivate**子句相同**單一**指示詞。  
  
-   如果**單一**指示詞與**copyprivate**中遇到子句時，在平行區域的動態範圍中，所有的變數指定**copyprivate**子句必須在封入內容中的私用。  
  
-   中指定的變數**copyprivate**子句必須有存取模稜兩可的複製指派運算子。