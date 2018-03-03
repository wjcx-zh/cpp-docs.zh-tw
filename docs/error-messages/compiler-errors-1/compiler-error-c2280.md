---
title: "編譯器錯誤 C2280 |Microsoft 文件"
ms.custom: 
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
dev_langs:
- C++
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 10bfe6701c6f2465bcc37e4fadf71c796664b59e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2280"></a>編譯器錯誤 C2280  
  
'*宣告*': 嘗試參考已刪除的函式  
  
編譯器偵測到嘗試參考`deleted`函式。 這個錯誤可能因呼叫成員函式已被明確標示為`= deleted`的原始程式碼中。 這項錯誤也可能因結構或類別，會自動宣告並標示為隱含的特殊成員函式呼叫`deleted`編譯器。 如需有關當編譯器自動產生`default`或`deleted`特殊成員函式，請參閱[特殊成員函式](../../cpp/special-member-functions.md)。  
  
## <a name="example-explicitly-deleted-functions"></a>範例： 明確刪除函式  

呼叫明確`deleted`函式會造成這個錯誤。 明確`deleted`成員函式，表示類別或結構故意設計來防止其使用，因此若要修正此問題，您應該變更程式碼以避免它。  
  
```cpp  
// C2280_explicit.cpp
// compile with: cl /c /W4 C2280_explicit.cpp
struct A {
    A();
    A(int) = delete;
};

struct B {
    A a1;
    A a2 = A(3); // C2280, calls deleted A::A(int)
    // To fix, remove the call to A(int)
};

void f() {
    B b;    // calls implicit B::B(void)
}
```  
  
## <a name="example-uninitialized-data-members"></a>範例： 未初始化的資料成員  
  
未初始化的參考型別資料成員或`const`資料成員會造成編譯器隱含地宣告`deleted`預設建構函式。 若要修正此問題，在宣告時初始化資料成員。  
  
```cpp  
// C2280_uninit.cpp
// compile with: cl /c C2280_uninit.cpp
struct A {
    const int i; // uninitialized const-qualified data
    // members or reference type data members cause
    // the implicit default constructor to be deleted.
    // To fix, initialize the value in the declaration:
    // const int i = 42;
} a;    // C2280
```  
  
## <a name="example-reference-and-const-data-members"></a>範例： 參考和常數的資料成員  
  
A`const`或參考類型的資料成員會造成編譯器宣告`deleted`複製指派運算子。 一旦初始化，這些成員無法指派給，因此無法運作的簡單複製或移動。 若要修正此問題，我們建議您變更程式邏輯，以移除造成錯誤的指派作業。  
  
```cpp  
// C2280_ref.cpp
// compile with: cl /c C2280_ref.cpp
extern int k;
struct A {
    A();
    int& ri = k; // a const or reference data member causes 
    // implicit copy assignment operator to be deleted.
};

void f() {
    A a1, a2;
    // To fix, consider removing this assignment.
    a2 = a1;    // C2280
}
```  
  
## <a name="example-movable-deletes-implicit-copy"></a>範例： 可移動刪除隱含複製  
  
如果在類別宣告移動建構函式或移動指派運算子，但未明確宣告複製建構函式，編譯器隱含地宣告複製建構函式和其定義為`deleted`。 同樣地，如果在類別宣告移動建構函式或移動指派運算子，但未明確宣告複製指派運算子，編譯器隱含地宣告複製指派運算子和其定義為`deleted`。 若要修正此問題，您必須明確宣告這些成員。  
 
當您看到錯誤 C2280 與`unique_ptr`，都是因為您嘗試叫用其複製建構函式，也就是`deleted`函式。 根據設計，`unique_ptr`無法複製。 使用移動建構函式，改為傳送擁有權。  

```cpp  
// C2280_move.cpp
// compile with: cl /c C2280_move.cpp
class base  
{  
public:  
    base();  
    ~base(); 
    base(base&&); 
    // Move constructor causes copy constructor to be
    // implicitly declared as deleted. To fix this 
    // issue, you can explicitly declare a copy constructor:
    // base(base&);
    // If you want the compiler default version, do this:
    // base(base&) = default;
};  

void copy(base *p)  
{  
    base b{*p};  // C2280
}  
```  

## <a name="example-variant-and-volatile-members"></a>範例： Variant 和動態成員  
  
Visual Studio 2015 Update 2 之前的編譯器版本已不合格和產生預設建構函式和解構函式的匿名等位。 這些會立即以隱含方式宣告為`deleted`。 這些版本也允許不合格的隱含定義`default`複製和移動建構函式和`default`複製和移動指派運算子中類別和結構具有`volatile`成員變數。 編譯器現在會考量這些具有非一般建構函式和指派運算子，並不會產生`default`實作。 這種類別時是等位或在類別內的匿名等位的成員，複製和移動建構函式和等位或類別的複製和移動指派運算子隱含定義為`deleted`。 若要修正此問題，您必須明確宣告的所需的特殊成員函式。  
  
```cpp  
// C2280_variant.cpp
// compile with: cl /c C2280_variant.cpp
struct A {  
    A() = default;
    A(const A&);
};  

struct B {  
    union {  
        A a;  
        int i;  
    };
    // To fix this issue, declare the required 
    // special member functions:
    // B(); 
    // B(const B& b);
};  

int main() {
    B b1;  
    B b2(b1);  // C2280  
}
```  
  
## <a name="example-indirect-base-members-deleted"></a>間接範例： 刪除基底成員  
  
Visual Studio 2015 Update 2 之前的編譯器版本已不合格，並允許衍生的類別呼叫特殊成員函式的間接衍生`private virtual`基底類別。 編譯器現在會發出編譯器錯誤 C2280 時進行這類呼叫。  
  
在此範例中，類別`top`間接衍生自私用虛擬`base`。 這可讓合格的程式碼中的成員`base`存取`top`; 物件類型的`top`無法預設建構或終結。 若要依賴舊的編譯器行為的程式碼中修正此問題，變更 可用的中繼類別`protected virtual`衍生或變更`top`使用直接衍生的類別：  

```cpp  
// C2280_indirect.cpp
// compile with: cl /c C2280_indirect.cpp
class base  
{  
protected:  
    base();  
    ~base();  
};  

class middle : private virtual base {}; 
// Possible fix: Replace line above with:
// class middle : protected virtual base {};
class top : public virtual middle {};    // C4594, C4624
// Another possible fix: use direct derivation:
// class top : public virtual middle, private virtual base {};   

void destroy(top *p)  
{  
    delete p;  // C2280  
}  
```  
  