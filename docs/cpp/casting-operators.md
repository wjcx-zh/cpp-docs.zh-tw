---
title: "轉型運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5bc7f1b0c2df820c3dc9e76b76dfcc72794e1906
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="casting-operators"></a>轉型運算子
C++ 語言有幾個特有的轉型運算子。 這些運算子的目的在於移除舊式 C 語言轉型固有的模稜兩可和危險。 這些運算子如下所列：  
  
-   [dynamic_cast](../cpp/dynamic-cast-operator.md)用來進行轉換的多型型別。  
  
-   [static_cast](../cpp/static-cast-operator.md)用於非多型類型轉換。  
  
-   [const_cast](../cpp/const-cast-operator.md)用來移除`const`， `volatile`，和`__unaligned`屬性。  
  
-   [reinterpret_cast](../cpp/reinterpret-cast-operator.md)用於簡單的位元的解譯。  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md)用來產生可驗證的 MSIL。  
  
 `const_cast` 和 `reinterpret_cast` 建議做為最後手段使用，因為這些運算子與舊類型轉換存在相同危險。 然而，為了完全取代舊類型轉換，這些運算子仍有其必要。  
  
## <a name="see-also"></a>請參閱  
 [轉型](../cpp/casting.md)