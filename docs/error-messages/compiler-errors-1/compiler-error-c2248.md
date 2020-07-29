---
title: 編譯器錯誤 C2248
ms.date: 11/04/2016
f1_keywords:
- C2248
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
ms.openlocfilehash: d35ded4b06423be53911f3efd0b55d75cb979773
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212809"
---
# <a name="compiler-error-c2248"></a>編譯器錯誤 C2248

'*member*'：無法存取類別 '*class*' 中宣告的 '*access_level*' 成員

衍生類別的成員無法存取 **`private`** 基類的成員。 您無法存取 **`private`** 或 **`protected`** 類別實例的成員。

## <a name="example"></a>範例

下列範例會在從類別外部存取類別的私用或受保護成員時，產生 C2248。 若要修正此問題，請不要直接在類別之外存取這些成員。 使用公用成員資料和成員函式來與類別互動。

```cpp
// C2248_access.cpp
// compile with: cl /EHsc /W4 C2248_access.cpp
#include <stdio.h>

class X {
public:
    int  m_publicMember;
    void setPrivateMember( int i ) {
        m_privateMember = i;
        printf_s("\n%d", m_privateMember);
    }
protected:
    int  m_protectedMember;

private:
    int  m_privateMember;
} x;

int main() {
    x.m_publicMember = 4;
    printf_s("\n%d", x.m_publicMember);
    x.m_protectedMember = 2; // C2248 m_protectedMember is protected
    x.m_privateMember = 3;   // C2248  m_privMemb is private
    x.setPrivateMember(0);   // OK uses public access function
}
```

另一個公開 C2248 的一致性問題，就是使用範本朋友和特製化。 若要修正此問題，請使用空白範本參數清單 <> 或特定範本參數來宣告 friend 範本函式。

```cpp
// C2248_template.cpp
// compile with: cl /EHsc /W4 C2248_template.cpp
template<class T>
void f(T t) {
    t.i;   // C2248
}

struct S {
private:
    int i;

public:
    S() {}
    friend void f(S);   // refer to the non-template function void f(S)
    // To fix, comment out the previous line and
    // uncomment the following line.
    // friend void f<S>(S);
};

int main() {
    S s;
    f<S>(s);
}
```

公開 C2248 的另一個一致性問題是當您嘗試宣告類別的 friend，以及類別的範圍中的 friend 宣告看不到該類別時。 若要修正此問題，請對封入類別授與更好的關係。

```cpp
// C2248_enclose.cpp
// compile with: cl /W4 /c C2248_enclose.cpp
class T {
    class S {
        class E {};
    };
    friend class S::E;   // C2248
};

class A {
    class S {
        class E {};
        friend class A;  // grant friendship to enclosing class
    };
    friend class S::E;   // OK
};
```
