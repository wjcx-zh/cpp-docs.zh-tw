---
title: "C 複合指派 | Microsoft Docs"
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
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b8b9166c1beae167f6d31913c3df10a8f57bbef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-compound-assignment"></a>C 複合指派
複合指派運算子可結合簡單指派運算子和另一個二元運算子。 複合指派運算子會執行其他運算子指定的作業，然後將結果指派給左運算元。 例如，如下所示的複合指派運算式  
  
```  
  
expression1  
+=  
expression2  
  
```  
  
 等同於  
  
```  
  
expression1  
=  
expression1  
+  
expression2  
  
```  
  
 不過，複合指派運算式與展開的版本不同，因為複合指派運算式只會評估 *expression1* 一次，而展開版本會評估 *expression1* 兩次：在加法作業和指派作業中。  
  
 複合指派運算子的運算元必須為整數類型或浮點類型。 每個複合指派運算子會執行對應的二元運算子所執行的轉換，並且據以限制其運算元的類型。 加法指派 (`+=`) 和減法指派 (**-=**) 運算子也可以有指標類型的左運算元，在這種情況下，右運算元必須為整數類型。 複合指派作業的結果為左運算元的值和類型。  
  
```  
#define MASK 0xff00  
  
n &= MASK;  
```  
  
 在此範例中，是在 `n` 和 `MASK` 執行位元包含 AND 作業，並將結果指派給 `n`。 資訊清單常數 `MASK` 是以 [#define](../preprocessor/hash-define-directive-c-cpp.md) 前置處理器指示詞所定義。  
  
## <a name="see-also"></a>請參閱  
 [C 指派運算子](../c-language/c-assignment-operators.md)