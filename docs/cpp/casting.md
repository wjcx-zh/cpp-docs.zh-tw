---
title: 轉型
ms.date: 11/19/2018
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
ms.openlocfilehash: bb06db3af6aee031b6cb2d69b38a9404304420fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190120"
---
# <a name="casting"></a>轉型

C++ 語言會假設，如果類別是從包含虛擬函式的基底類別衍生，則該基底類別類型的指標可以用來呼叫衍生類別物件內虛擬函式的實作。 包含虛擬函式的類別有時稱為「多型類別」(Polymorphic Class)。

由於衍生類別完全包含本身從中衍生之所有基底類別的定義，因此可以放心在類別階層中將指標向上轉型至任何這類基底類別。 假設有基底類別的指標，在階層中向下轉型指標可能是安全的。 如果所指向的物件實際上是從基底類別衍生的類型，則是安全的。 在這種情況下，實際物件會視為「完整物件」(Complete Object)。 而基底類別的指標會指向完整物件的「子物件」(Subobject)。 例如，以下圖顯示的類別階層為例。

![類別階層](../cpp/media/vc38zz1.gif "類別階層") <br/>
類別階層

如下圖所示，`C` 類型的物件可以視覺化。

![具有子&#45;物件 B 和 A 的類別 C](../cpp/media/vc38zz2.gif "具有子&#45;物件 B 和 A 的類別 C") <br/>
具有 B 和 A 兩個子物件的類別 C

假設有 `C` 類別的執行個體，則會有 `B` 子物件和 `A` 子物件。 `C` 的執行個體 (包括 `A` 和 `B` 子物件) 就是「完整物件」。

若使用執行階段類型資訊，就可以檢查指標是否確實指向完整物件，並且可以安全地轉型為指向其階層中的另一個物件。 [Dynamic_cast](../cpp/dynamic-cast-operator.md)運算子可以用來進行這些類型的轉換。 它也會執行安全作業所必要的執行階段檢查。

若要轉換非多型類型，您可以使用[static_cast](../cpp/static-cast-operator.md)運算子（本主題將說明靜態和動態轉換轉換之間的差異，以及何時適合使用）。

本節包含下列主題：

- [轉型運算子](../cpp/casting-operators.md)

- [執行時間類型資訊](../cpp/run-time-type-information.md)

## <a name="see-also"></a>另請參閱

[運算式](../cpp/expressions-cpp.md)
