---
title: "C 序列點 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- sequence points
ms.assetid: c84885a5-4336-4eba-a643-058df4249903
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a9c874c0093b55c44f900e7eab06019d75cb930
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-sequence-points"></a>C 序列點
在連續「序列點」之間，只能以運算式修改物件的值一次。 C 語言定義下列序列點：  
  
-   邏輯 AND 運算子 (**&&**) 的左運算元。 繼續之前會完整評估邏輯 AND 運算子的左運算元，並且完成所有副作用。 如果左運算元判斷值為 false (0)，便不會評估另一個運算元。  
  
-   邏輯 OR 運算子 (`||`) 的左運算元。 繼續之前會完整評估邏輯 OR 運算子的左運算元，並且完成所有副作用。 如果左運算元判斷值為 true (非零)，便不會評估另一個運算元。  
  
-   逗號運算子的左運算元。 繼續之前會完整評估逗號運算子的左運算元，並且完成所有副作用。 逗號運算子的兩個運算元會一律進行評估。 請注意，函式呼叫中的逗號運算子不保證評估順序。  
  
-   函式呼叫運算子。 函式的所有引數均會評估，並且所有副作用會在輸入函式之前完成。 不會指定這些引數的評估順序。  
  
-   條件運算子的第一個運算元。 繼續之前會完整評估條件運算子的第一運算元，並且完成所有副作用。  
  
-   完整初始化運算式的結尾 (即不屬於另一個運算式的運算式，例如宣告陳述式中初始化的結尾)。  
  
-   運算陳述式中的運算式。 運算式陳述式包含選擇性運算式且後面加上分號 (**;**)。 會評估運算式的副作用，而且在此項評估之後會有一個序列點。  
  
-   選取範圍 (**if** 或 `switch`) 陳述式中的控制運算式。 會完整評估運算式，並且其所有副作用會在執行與選取範圍相關的程式碼執行之前完成。  
  
-   `while` 或 **do** 陳述式的控制運算式。 會完整評估運算式，並且所有副作用會在執行 `while` 或 **do** 迴圈的下一個反覆項目中的任何陳述式之前完成。  
  
-   **for** 陳述式的三個運算式中的每一個。 會完整評估運算式，並且所有副作用會在執行 **for** 迴圈的下一個反覆項目中的任何陳述式之前完成。  
  
-   `return` 陳述式中的運算式。 會完整評估運算式，並且所有副作用會在控制項回到呼叫函式之前完成。  
  
## <a name="see-also"></a>請參閱  
 [運算式評估](../c-language/expression-evaluation-c.md)