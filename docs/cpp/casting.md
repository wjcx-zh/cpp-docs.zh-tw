---
title: "轉型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9974b86f99164257e854bffd07393b96998040ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="casting"></a>轉型
C++ 語言會假設，如果類別是從包含虛擬函式的基底類別衍生，則該基底類別類型的指標可以用來呼叫衍生類別物件內虛擬函式的實作。 包含虛擬函式的類別有時稱為「多型類別」(Polymorphic Class)。  
  
 由於衍生類別完全包含本身從中衍生之所有基底類別的定義，因此可以放心在類別階層中將指標向上轉型至任何這類基底類別。 假設有基底類別的指標，在階層中向下轉型指標可能是安全的。 如果所指向的物件實際上是從基底類別衍生的類型，則是安全的。 在這種情況下，實際物件會視為「完整物件」(Complete Object)。 而基底類別的指標會指向完整物件的「子物件」(Subobject)。 例如，以下圖顯示的類別階層為例。  
  
 ![類別階層](../cpp/media/vc38zz1.gif "vc38ZZ1")  
類別階層  
  
 如下圖所示，`C` 類型的物件可以視覺化。  
  
 ![類別 C 子 &#45; 物件 B 和 A](../cpp/media/vc38zz2.gif "vc38ZZ2")  
具備 B 子物件和 A 子物件的類別 C  
  
 假設有 `C` 類別的執行個體，則會有 `B` 子物件和 `A` 子物件。 `C` 的執行個體 (包括 `A` 和 `B` 子物件) 就是「完整物件」。  
  
 若使用執行階段類型資訊，就可以檢查指標是否確實指向完整物件，並且可以安全地轉型為指向其階層中的另一個物件。 [Dynamic_cast](../cpp/dynamic-cast-operator.md)運算子可用來進行這些類型的轉換 （cast）。 它也會執行安全作業所必要的執行階段檢查。  
  
 對於非多型類型轉換，您可以使用[static_cast](../cpp/static-cast-operator.md)運算子 （本主題將說明靜態和動態轉型轉換之間，則會適當地使用每個差異）。  
  
 本章節涵蓋下列主題：  
  
-   [轉型運算子](../cpp/casting-operators.md)  
  
-   [執行階段類型資訊](../cpp/run-time-type-information.md)  
  
## <a name="see-also"></a>請參閱  
 [運算式](../cpp/expressions-cpp.md)