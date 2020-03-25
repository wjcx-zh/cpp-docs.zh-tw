---
title: 運算子多載的一般規則
ms.date: 11/04/2016
helpviewer_keywords:
- operator overloading [C++], rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
ms.openlocfilehash: 0c8cbea3411acd50be376ae0853a143af57458f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188585"
---
# <a name="general-rules-for-operator-overloading"></a>運算子多載的一般規則

下列規則限制多載運算子的實作方式。 不過，它們不會套用至個別涵蓋的[new](../cpp/new-operator-cpp.md)和[delete](../cpp/delete-operator-cpp.md)運算子。

- 您不能定義新的運算子，例如 **.** 。

- 將運算子套用於內建資料類型時，您就無法重新定義運算子的意義。

- 多載運算子必須為非靜態類別成員函式或全域函式。 全域函式需要存取私用的或受保護的類別成員，必須宣告為該類別的 friend。 全域函式必須至少接受一個為類別或列舉類型或為類別或列舉類型參考的引數。 例如：

    ```cpp
    // rules_for_operator_overloading.cpp
    class Point
    {
    public:
        Point operator<( Point & );  // Declare a member operator
                                     //  overload.
        // Declare addition operators.
        friend Point operator+( Point&, int );
        friend Point operator+( int, Point& );
    };

    int main()
    {
    }
    ```

   上述程式碼範例將小於運算子宣告為成員函式；不過，加法運算子會宣告為具有 friend 存取權限的全域函式。 請注意，可以對指定運算子提供一個以上的實作。 上述加法運算子的範例中，提供了兩個實作以協助交替。 將 `Point` 新增至 `Point`、 **int**至 `Point`等等的運算子，可能會被實作為。

- 運算子會遵守其優先順序、群組，以及其搭配內建類型使用時指定的運算元數目。 因此，沒有任何方法可以表達「add 2」和「3」型別的物件，`Point`」，「必須將2加入*x*座標，而3則會加入到*y*座標中。

- 宣告為成員函式的一元運算子不接受任何引數；如果宣告為全域函式，則會接受一個引數。

- 宣告為成員函式的二元運算子接受一個引數；如果宣告為全域函式，則會接受兩個引數。

- 如果運算子可以當做一元或二元運算子（ __&__ 、 __*__ 、 __+__ 和 __-__ ）使用，您可以分別多載每個使用。

- 多載運算子不可以有預設引數。

- 衍生類別會繼承除了指派（**operator =** ）以外的所有多載運算子。

- 成員函式多載運算子的第一個引數，一定是叫用運算子之物件的類別類型 (宣告該運算子的類別，或者從該類別衍生的類別)。 不會對第一個引數提供任何轉換。

請注意，您可以完全改變任何運算子的意義。 其中包括位址（ **&** ）、指派（ **=** ）和函式呼叫運算子的意義。 此外，還可使用運算子多載變更內建類型所依賴的識別。 例如，下列四個陳述式若進行完整評估，通常是相等的：

```cpp
var = var + 1;
var += 1;
var++;
++var;
```

多載運算子的類別類型無法依賴這個識別。 此外，就多載運算子而言，基本類型使用這些運算子的某些隱含條件比較不嚴謹。 例如，當套用至基本類型時， **+=** 的加法/指派運算子會要求左運算元是左值;當運算子超載時，沒有這項需求。

> [!NOTE]
> 為求一致，最好的作法通常是在定義多載運算子時遵循內建類型的模型。 如果多載運算子的語意與其在其他內容中的意義大不相同，可能會比較容易混淆。

## <a name="see-also"></a>另請參閱

[運算子多載](../cpp/operator-overloading.md)
