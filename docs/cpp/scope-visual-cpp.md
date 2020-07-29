---
title: 範圍 (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
ms.openlocfilehash: 5cff7a4607201175c7095a87134850583b76d636
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227084"
---
# <a name="scope-c"></a>範圍 (C++)

當您宣告程式元素（例如類別、函式或變數）時，其名稱只能是「可見」，並用於程式的特定部分。 顯示名稱的內容稱為其*範圍*。 例如，如果您在函式內宣告變數 `x` ， `x` 則只有在該函式主體內才會顯示。 它具有*區域範圍*。 您的程式中可能會有相同名稱的其他變數;只要它們位於不同的範圍內，它們就不會違反一個定義規則，也不會引發錯誤。

若是自動的非靜態變數，範圍也會決定在程式記憶體中建立和終結它們的時間。

範圍有六種：

- **全域範圍**全域名稱是在任何類別、函式或命名空間之外宣告的。 不過，在 c + + 中，即使這些名稱與隱含的全域命名空間同時存在也一樣。 全域名稱的範圍會從宣告的點延伸到宣告它們的目的檔案尾。 若為全域名稱，可見度也會受到[連結](program-and-linkage-cpp.md)規則的規範，判斷程式中其他檔案的名稱是否可見。

- **命名空間範圍**在[命名空間](namespaces-cpp.md)中，于任何類別或列舉定義或函式區塊外宣告的名稱，在命名空間結尾處可見。 命名空間可在不同檔案的多個區塊中定義。

- **區域範圍**在函式或 lambda 內宣告的名稱（包括參數名稱）具有區域範圍。 它們通常稱為「區域變數」。 只有從其宣告點到函式或 lambda 主體的結尾時，才會顯示它們。 區域範圍是一種區塊範圍，本文稍後會加以討論。

- **類別範圍**類別成員的名稱具有類別範圍，不論宣告點為何，它都會在整個類別定義中擴充。 類別成員存取範圍是由 **`public`** 、 **`private`** 和關鍵字進一步控制 **`protected`** 。 只能使用成員選取運算子（）來存取公用或受保護的成員 **。** 或 **->** ）或成員指標運算子（**.** <strong>\*</strong> 或 **->** <strong>\*</strong> ）。

- **語句範圍**在 **`for`** 、、或語句中宣告的名稱，會在 **`if`** **`while`** **`switch`** 語句區塊的結尾處顯示。

- **函數範圍**[標籤](labeled-statements.md)具有函式範圍，這表示它在函式主體中可見，甚至是在其宣告點之前。 函式範圍可以在宣告 `goto cleanup` 標籤之前撰寫語句 `cleanup` 。

## <a name="hiding-names"></a>隱藏名稱

您可以在封閉的區塊中宣告名稱，以隱藏該名稱。 下圖是在內層區塊中重新宣告 `i`，從而隱藏外層區塊範圍中與 `i` 相關的變數。

![封鎖&#45;範圍名稱隱藏](../cpp/media/vc38sf1.png "封鎖&#45;範圍名稱隱藏") <br/>
封鎖範圍和隱藏名稱

本圖所示的程式輸出為：

```cpp
i = 0
i = 7
j = 9
i = 0
```

> [!NOTE]
> `szWhat` 引數被視為在函式的範圍中。 因此，其會被視為已在函式的最外層區塊中宣告。

## <a name="hiding-class-names"></a>隱藏類別名稱

您可以藉由宣告函式、物件、變數或相同範圍中的列舉程式，隱藏類別名稱。 不過，在前面加上關鍵字時，仍然可以存取類別名稱 **`class`** 。

```cpp
// hiding_class_names.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

// Declare class Account at global scope.
class Account
{
public:
    Account( double InitialBalance )
        { balance = InitialBalance; }
    double GetBalance()
        { return balance; }
private:
    double balance;
};

double Account = 15.37;            // Hides class name Account

int main()
{
    class Account Checking( Account ); // Qualifies Account as
                                       //  class name

    cout << "Opening account with a balance of: "
         << Checking.GetBalance() << "\n";
}
//Output: Opening account with a balance of: 15.37
```

> [!NOTE]
> 針對呼叫類別名稱（）的任何位置 `Account` ，必須使用關鍵字類別來區別全域範圍的變數帳戶。 當類別名稱出現在範圍解析運算子 (::) 的左邊時，不適用這項規則。 範圍解析運算子左邊的名稱一律視為類別名稱。

下列範例示範如何使用關鍵字來宣告類型物件的指標 `Account` **`class`** ：

```cpp
class Account *Checking = new class Account( Account );
```

在 `Account` 上述語句中，初始化運算式中的（括弧中的）具有全域範圍; 其類型為 **`double`** 。

> [!NOTE]
> 重複使用識別項名稱 (如這個範例中所示) 會視為不良的程式設計風格。

如需類別物件之宣告和初始化的詳細資訊，請參閱[類別、結構和等](../cpp/classes-and-structs-cpp.md)位。 如需使用 **`new`** 和 **`delete`** 自由存放區運算子的詳細資訊，請參閱[new 和 delete 運算子](new-and-delete-operators.md)。

## <a name="hiding-names-with-global-scope"></a>隱藏具有全域範圍的名稱

您可以藉由在區塊範圍中明確宣告相同的名稱，隱藏具有全域範圍的名稱。 不過，您可以使用範圍解析運算子（）來存取全域範圍的名稱 `::` 。

```cpp
#include <iostream>

int i = 7;   // i has global scope, outside all blocks
using namespace std;

int main( int argc, char *argv[] ) {
   int i = 5;   // i has block scope, hides i at global scope
   cout << "Block-scoped i has the value: " << i << "\n";
   cout << "Global-scoped i has the value: " << ::i << "\n";
}
```

```Output
Block-scoped i has the value: 5
Global-scoped i has the value: 7
```

## <a name="see-also"></a>另請參閱

[基本概念](../cpp/basic-concepts-cpp.md)
