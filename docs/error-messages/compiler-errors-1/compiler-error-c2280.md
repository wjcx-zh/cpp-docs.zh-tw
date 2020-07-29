---
title: 編譯器錯誤 C2280
ms.date: 04/25/2017
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
ms.openlocfilehash: 9ee5b8105241ee347812a0dcc083a4f1cc7dca49
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87208404"
---
# <a name="compiler-error-c2280"></a>編譯器錯誤 C2280

'*宣告 '：* 嘗試參考已刪除的函式

編譯器偵測到參考函數的嘗試 `deleted` 。 這個錯誤可能是因為呼叫已在原始程式碼中明確標示為的成員函式所造成 `= deleted` 。 呼叫由編譯器自動宣告並標示為的結構或類別的隱含特殊成員函式，也可能會造成這個錯誤 `deleted` 。 如需編譯器自動產生或特殊成員函式的詳細資訊 **`default`** `deleted` ，請參閱[特殊成員](../../cpp/special-member-functions.md)函式。

## <a name="example-explicitly-deleted-functions"></a>範例：明確刪除的函式

呼叫明確的函式 `deleted` 會導致此錯誤。 明確成員函式 `deleted` 暗示類別或結構是刻意設計來防止使用，因此若要修正這個問題，您應該變更程式碼以避免發生。

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

## <a name="example-uninitialized-data-members"></a>範例：未初始化的資料成員

未初始化的參考型別資料成員或 **`const`** 資料成員，會使編譯器隱含宣告預設的函式 `deleted` 。 若要修正此問題，請在宣告資料成員時將其初始化。

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

## <a name="example-reference-and-const-data-members"></a>範例： Reference 和 const 資料成員

**`const`** 或參考型別資料成員會使編譯器宣告 `deleted` 複製指派運算子。 一旦初始化之後，就無法將這些成員指派給，因此簡單的複製或移動作業將無法使用。 若要修正此問題，建議您變更邏輯，以移除造成錯誤的指派作業。

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

## <a name="example-movable-deletes-implicit-copy"></a>範例：可移動刪除隱含複製

如果類別宣告移動函數或移動指派運算子，但未明確宣告複製的函式，則編譯器會隱含宣告複製的建構函式，並將其定義為 `deleted` 。 同樣地，如果類別宣告移動函數或移動指派運算子，但未明確宣告複製指派運算子，則編譯器會隱含宣告複製指派運算子，並將其定義為 `deleted` 。 若要修正此問題，您必須明確宣告這些成員。

當您看到與的連接時發生錯誤 C2280 時 `unique_ptr` ，幾乎肯定是因為您嘗試叫用其複製的函式，這是函式 `deleted` 。 根據設計， `unique_ptr` 無法複製。 請改用 move 函式來轉移擁有權。

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

## <a name="example-variant-and-volatile-members"></a>範例： Variant 和 volatile 成員

Visual Studio 2015 Update 2 之前的編譯器版本，是不一致且產生的預設函式和匿名等位的析構函數。 這些現在已隱含宣告為 `deleted` 。 這些版本也允許 **`default`** 在具有成員變數的類別和結構中，複製和移動構造函式不符合規範的隱含定義，以及 **`default`** 複製和移動指派運算子 **`volatile`** 。 編譯器現在會將這些視為具有非一般的函式和指派運算子，而不會產生實作為 **`default`** 。 當這類類別是等位的成員或類別內的匿名等位時，會將等位或類別的複製和移動構造函式和複製和移動指派運算子隱含定義為 `deleted` 。 若要修正這個問題，您必須明確宣告必要的特殊成員函式。

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

## <a name="example-indirect-base-members-deleted"></a>範例：已刪除的間接基底成員

Visual Studio 2015 Update 2 之前的編譯器版本不符合規範，並允許衍生類別呼叫間接衍生基類的特殊成員函式 `private virtual` 。 在進行這類呼叫時，編譯器現在會發出編譯器錯誤 C2280。

在此範例中，類別 `top` 間接衍生自私用虛擬 `base` 。 在符合規範的程式碼中，這會讓的成員無法 `base` 存取 `top` ; 類型的物件無法預設為已建立 `top` 或損毀。 若要在依賴舊編譯器行為的程式碼中修正此問題，請將中繼類別變更為使用 `protected virtual` 衍生，或將 `top` 類別變更為使用直接衍生：

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
