---
title: "複製建構函式和複製指派運算子 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= 運算子, 複製物件"
  - "指派值以複製物件"
  - "指派運算子, 複製物件的"
  - "指派陳述式, 複製物件"
  - "複製物件"
  - "初始化物件, 透過複製物件"
  - "物件 [C++], 複製"
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 複製建構函式和複製指派運算子 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  從 C\+\+11 開始，語言支援兩種指派：*「複製指派」*\(Copy Assignment\) 和*「移動指派」*\(Move Assignment\)。  在本文中，除非明確指定，否則「指派」表示複製指派。  如需移動指派的詳細資訊，請參閱[移動建構函式和移動指派運算子 \(C\+\+\)](http://msdn.microsoft.com/zh-tw/1442de5f-37a5-42a1-83a6-ec9cfe0414db)。  
>   
>  指派作業和初始化作業都會導致複製物件。  
  
-   **指派**：將某一個物件的值指派給另一個物件時，第一個物件會複製到第二個物件。  因此，  
  
    ```cpp  
    Point a, b;  
    ...  
    a = b;  
    ```  
  
     會導致 `b` 的值複製到 `a`。  
  
-   **初始化**：初始化是在宣告新物件、引數以傳值方式傳遞至函式，或是以傳值方式從函式傳回值時發生。  
  
 您可以定義類別類型物件的「複製」語意。  例如，請參考這個程式碼：  
  
```cpp  
TextFile a, b;  
a.Open( "FILE1.DAT" );  
b.Open( "FILE2.DAT" );  
b = a;  
```  
  
 上述程式碼可能表示「將 FILE1.DAT 的內容複製到 FILE2.DAT」，也可能表示「忽略 FILE2.DAT 並且讓 `b` 成為 FILE1.DAT 的第二個控制代碼」。 您必須將適當的複製語意附加至每一個類別，如下所示。  
  
-   將指派運算子 `operator=` 與類別類型的參考一起做為傳回類型和 `const` 所傳遞的參數使用，例如 `ClassName& operator=(const ClassName& x);`。  
  
-   使用複製建構函式。  如需複製建構函式的詳細資訊，請參閱[宣告建構函式的規則](../misc/rules-for-declaring-constructors.md)。  
  
 如果您未宣告複製建構函式，則編譯器會產生一個成員複製建構函式。  如果您未宣告複製指派建構函式，則編譯器會產生一個成員複製指派運算子。 宣告複製建構函式不會隱藏編譯器產生的複製指派運算子，反之亦然。  如果您實作任一種，建議您一併實作另一種，如此程式碼的意義才會明確。  
  
 成員指派將在[\(NOTINBUILD\) Memberwise Assignment and Initialization](http://msdn.microsoft.com/zh-tw/94048213-8b49-4416-8069-b1b7a6f271f9)中詳細說明。  
  
 複製建構函式接受類型 *class\-name***&** 的引數，其中 *class\-name* 是為其定義建構函式的類別名稱。  例如:  
  
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
>  盡可能讓複製建構函式引數的類型為 *const class\-name***&**。  這樣可避免複製建構函式意外變更做為複製來源的物件。  另外也可以從 **const** 物件複製。  
  
## 編譯器產生的複製建構函式  
 編譯器產生的複製建構函式 \(像是使用者定義的複製建構函式\) 具有「*class\-name* 參考」類型的單一引數。 但是當所有基底類別和成員類別將複製建構函式宣告為接受 **const** *class\-name***&** 類型的單一引數時例外。  在這種情況下，編譯器產生之複製建構函式的引數也會是 **const**。  
  
 當複製建構函式的引數類型不是 **const** 時，藉由複製 **const** 物件進行初始化就會產生錯誤。  反向執行則不成立：如果引數為 **const**，您可以藉由複製不是 **const** 的物件進行初始化。  
  
 編譯器產生的指派運算子在 **const** 方面會遵循相同的模式。 除非所有基底和成員類別中的指派運算子都接受 **const** *class\-name&* 類型的引數，否則這類運算子會接受 *class\-name***&** 類型的單一引數。 在這種情況下，類別產生的指派運算子會接受 **const** 引數。  
  
> [!NOTE]
>  虛擬基底類別是由複製建構函式進行初始化、由編譯器所產生或使用者所定義時，只會在建構時初始化一次。  
  
 這些影響類似複製建構函式的影響。  如果引數的類型不是 **const**，從 **const** 物件指派就會產生錯誤。  反向執行則不成立：如果將 **const** 值指派至不是 **const** 的值，指派會成功。  
  
 如需多載指派運算子的詳細資訊，請參閱[指派](../cpp/assignment.md)。  
  
## 請參閱  
 [特殊成員函式](../misc/special-member-functions-cpp.md)