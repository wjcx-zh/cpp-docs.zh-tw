---
title: 轉型運算子 |Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d64a25475ad7ac40f63d29798768f8f57866b3c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941621"
---
# <a name="casting-operators"></a>轉型運算子
C++ 語言有幾個特有的轉型運算子。 這些運算子的目的在於移除舊式 C 語言轉型固有的模稜兩可和危險。 這些運算子如下所列：  
  
-   [dynamic_cast](../cpp/dynamic-cast-operator.md)用於多型類型的轉換。  
  
-   [static_cast](../cpp/static-cast-operator.md)用於非多型類型的轉換。  
  
-   [const_cast](../cpp/const-cast-operator.md)用來移除**const**， **volatile**，和 **__unaligned**屬性。  
  
-   [reinterpret_cast](../cpp/reinterpret-cast-operator.md)用於簡單精進的位元。  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md)用來產生可驗證的 MSIL。  
  
 `const_cast` 和 `reinterpret_cast` 建議做為最後手段使用，因為這些運算子與舊類型轉換存在相同危險。 然而，為了完全取代舊類型轉換，這些運算子仍有其必要。  
  
## <a name="see-also"></a>另請參閱  
 [轉型](../cpp/casting.md)