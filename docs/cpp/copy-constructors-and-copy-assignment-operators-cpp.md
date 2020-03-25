---
title: 複製建構函式和複製指派運算子 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
ms.openlocfilehash: beabe4c6219975d33c7af98a94498188c9abfa55
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189523"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>複製建構函式和複製指派運算子 (C++)

> [!NOTE]
> 從 c + + 11 開始，語言中支援兩種指派：*複製指派*和*移動指派*。 在本文中，除非明確指定，否則「指派」表示複製指派。 如需移動指派的詳細資訊，請參閱[移動函數和移動C++指派運算子（）](move-constructors-and-move-assignment-operators-cpp.md)。
>
> 指派作業和初始化作業都會導致複製物件。

- **指派**：將一個物件的值指派給另一個物件時，第一個物件會複製到第二個物件。 因此，

    ```cpp
    Point a, b;
    ...
    a = b;
    ```

   會導致 `b` 的值複製到 `a`。

- **初始化**：當宣告新物件、引數以傳值方式傳遞至函式，或從函式依值傳回值時，就會進行初始化。

您可以定義類別類型物件的「複製」語意。 例如，請思考下列程式碼：

```cpp
TextFile a, b;
a.Open( "FILE1.DAT" );
b.Open( "FILE2.DAT" );
b = a;
```

上述程式碼可能表示「將 FILE1.DAT 的內容複製到 FILE2.DAT」，也可能表示「忽略 FILE2.DAT 並且讓 `b` 成為 FILE1.DAT 的第二個控制代碼」。 您必須將適當的複製語意附加至每一個類別，如下所示。

- 藉由使用指派運算子**operator =** 搭配類別類型的參考做為傳回型別，以及由**const**參考所傳遞的參數（例如 `ClassName& operator=(const ClassName& x);`）。

- 使用複製建構函式。

如果您未宣告複製建構函式，則編譯器會產生一個成員複製建構函式。  如果您未宣告複製指派建構函式，則編譯器會產生一個成員複製指派運算子。 宣告複製建構函式不會隱藏編譯器產生的複製指派運算子，反之亦然。 如果您實作任一種，建議您一併實作另一種，如此程式碼的意義才會明確。

複製的函式會採用類型為<em>類別名稱</em>的引數<strong>&</strong>，其中*類別名稱*是已定義其函式的類別名稱。 例如：

```cpp
// spec1_copying_class_objects.cpp
class Window
{
public:
    Window( const Window& ); // Declare copy constructor.
    // ...
};

int main()
{
}
```

> [!NOTE]
> 盡可能將複製參數的引數**常數**<em>類別名稱</em><strong>&</strong>類型。 這樣可避免複製建構函式意外變更做為複製來源的物件。 它也可讓您從**const**物件複製。

## <a name="compiler-generated-copy-constructors"></a>編譯器產生的複製建構函式

編譯器產生的複製函數（例如使用者定義的複製函式）具有「*類別名稱*的參考」類型的單一引數。 當所有基類和成員類別都有宣告為採用**const** <em>類別名稱</em><strong>&</strong>的單一引數時，就會發生例外狀況。 在這種情況下，編譯器產生的複製函式的引數也會是**const**。

當複製參數化的引數類型不是**const**時，藉由複製**const**物件進行初始化會產生錯誤。 反向不成立：如果引數為**const**，您可以藉由複製不是**const**的物件進行初始化。

編譯器產生的指派運算子會遵循與 const 有關的相同模式 **。** 除非所有基底和成員類別中的指派運算子接受**const** <em>類別名稱</em><strong>&</strong>的引數，否則它們會<em>採用類型的單一引數</em><strong>&</strong> 。 在此情況下，類別產生的指派運算子會接受**const**引數。

> [!NOTE]
> 虛擬基底類別是由複製建構函式進行初始化、由編譯器所產生或使用者所定義時，只會在建構時初始化一次。

這些影響類似複製建構函式的影響。 當引數類型不是**const**時，從**const**物件指派就會產生錯誤。 相反的情況：如果將**const**值指派給不是**const**的值，則指派會成功。

如需多載指派運算子的詳細資訊，請參閱[指派](../cpp/assignment.md)。
