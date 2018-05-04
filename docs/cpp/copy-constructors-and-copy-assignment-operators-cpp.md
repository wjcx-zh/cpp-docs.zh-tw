---
title: 複製建構函式和複製指派運算子 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1292240e5343c461142e8c6029c277175f6a62f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>複製建構函式和複製指派運算子 (C++)
> [!NOTE]
>  從 C + + 11 開始，兩種指派支援的語言：*複製指派*和*移動指派*。 在本文中，除非明確指定，否則「指派」表示複製指派。 如需移動指派，請參閱[移動建構函式和移動指派運算子 （c + +）](http://msdn.microsoft.com/en-us/1442de5f-37a5-42a1-83a6-ec9cfe0414db)。  
>   
>  指派作業和初始化作業都會導致複製物件。  
  
-   **指派**： 當一個物件的值指派到另一個物件時，第一個物件會複製到第二個物件。 因此，  
  
    ```cpp  
    Point a, b;  
    ...  
    a = b;  
    ```  
  
     會導致 `b` 的值複製到 `a`。  
  
-   **初始化**： 在宣告新物件、 引數會傳遞至函式，依據值或傳值方式從函式傳回值時，會進行初始化。  
  
 您可以定義類別類型物件的「複製」語意。 例如，請參考這個程式碼：  
  
```cpp  
TextFile a, b;  
a.Open( "FILE1.DAT" );  
b.Open( "FILE2.DAT" );  
b = a;  
```  
  
 上述程式碼可能表示「將 FILE1.DAT 的內容複製到 FILE2.DAT」，也可能表示「忽略 FILE2.DAT 並且讓 `b` 成為 FILE1.DAT 的第二個控制代碼」。 您必須將適當的複製語意附加至每一個類別，如下所示。  
  
-   將指派運算子 `operator=` 與類別類型的參考一起做為傳回類型和 `const` 所傳遞的參數使用，例如 `ClassName& operator=(const ClassName& x);`。  
  
-   使用複製建構函式。   
  
 如果您未宣告複製建構函式，則編譯器會產生一個成員複製建構函式。  如果您未宣告複製指派建構函式，則編譯器會產生一個成員複製指派運算子。 宣告複製建構函式不會隱藏編譯器產生的複製指派運算子，反之亦然。 如果您實作任一種，建議您一併實作另一種，如此程式碼的意義才會明確。  
   
 複製建構函式接受類型引數 * 類別-name ***&**，其中*類別名稱*是為其定義建構函式的類別名稱。 例如:   
  
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
>  讓複製建構函式的引數的型別*const 類別-名稱 * * * （& s)** 請盡可能。 這樣可避免複製建構函式意外變更做為複製來源的物件。 它也可讓複製**const**物件。  
  
## <a name="compiler-generated-copy-constructors"></a>編譯器產生的複製建構函式  
 編譯器產生的複製建構函式，像是使用者定義的複製建構函式中，有類型的單一引數 」 參考*類別名稱*。 」 例外狀況是當所有的基底類別和成員類別將複製建構函式宣告為接受單一引數的型別**const** * 類別-name ***&**。 在這種情況下，編譯器產生的複製建構函式的引數也是**const**。  
  
 當複製建構函式的引數類型不**const**，藉由複製初始化**const**物件會產生錯誤。 反向執行則不成立： 如果引數是**const**，您可以藉由複製不是物件初始化**const**。  
  
 編譯器產生的指派運算子遵循相同的模式與**const。** 則會接受單一引數的型別*類別-名稱 * * * （& s)** 除非所有基底和成員類別中的指派運算子的型別引數**const** *類別名稱 （& s)。* 在此情況下，類別產生的指派運算子會接受**const**引數。  
  
> [!NOTE]
>  虛擬基底類別是由複製建構函式進行初始化、由編譯器所產生或使用者所定義時，只會在建構時初始化一次。  
  
 這些影響類似複製建構函式的影響。 當引數類型不是**const**，指派從**const**物件會產生錯誤。 反向執行則不成立： 如果**const**值指派給值不是**const**，指派會成功。  
  
 如需有關多載的指派運算子的詳細資訊，請參閱[指派](../cpp/assignment.md)。  
  
