---
title: '範圍解析運算子：::'
ms.date: 11/04/2016
f1_keywords:
- '::'
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
ms.openlocfilehash: e601bed976009a72a43545d8d38a38d75e93a137
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267363"
---
# <a name="scope-resolution-operator-"></a>範圍解析運算子：::

範圍解析運算子 **::** 用來識別及區分不同範圍內的識別項。 如需有關範圍的詳細資訊，請參閱 <<c0> [ 範圍](../cpp/scope-visual-cpp.md)。

## <a name="syntax"></a>語法

```
:: identifier
class-name :: identifier
namespace :: identifier
enum class :: identifier
enum struct :: identifier
```

## <a name="remarks"></a>備註

`identifier` 可以是變數、函式或列舉值。

## <a name="with-classes-and-namespaces"></a>搭配類別和命名空間

下列範例顯示範圍解析運算子如何與命名空間和類別搭配使用：

```cpp
namespace NamespaceA{
    int x;
    class ClassA {
    public:
        int x;
    };
}

int main() {

    // A namespace name used to disambiguate
    NamespaceA::x = 1;

    // A class name used to disambiguate
    NamespaceA::ClassA a1;
    a1.x = 2;
}
```

不含範圍限定詞的範圍解析運算子是指全域命名空間。

```cpp
namespace NamespaceA{
    int x;
}

int x;

int main() {
    int x;

    // the x in main()
    x = 0;
    // The x in the global namespace
    ::x = 1;

    // The x in the A namespace
    NamespaceA::x = 2;
}
```

您可以使用範圍解析運算子來識別命名空間的成員，或識別在使用指示詞中指定成員命名空間的命名空間。 在下面的範例中，即使已在命名空間 `NamespaceC` 中宣告 `ClassB`，您還是可以使用 `ClassB` 來限定 `NamespaceB`，因為使用指示詞已在 `NamespaceB` 中指定 `NamespaceC`。

```cpp
namespace NamespaceB {
    class ClassB {
    public:
        int x;
    };
}

namespace NamespaceC{
    using namespace B;
}
int main() {
    NamespaceB::ClassB c_b;
    NamespaceC::ClassB c_c;

    c_b.x = 3;
    c_c.x = 4;
}
```

您可以使用範圍解析運算子的鏈結。 在下列範例中，`NamespaceD::NamespaceD1` 會識別巢狀命名空間 `NamespaceD1`，而 `NamespaceE::ClassE::ClassE1` 會識別巢狀類別 `ClassE1`。

```cpp
namespace NamespaceD{
    namespace NamespaceD1{
        int x;
    }
}

namespace NamespaceE{
    class ClassE{
    public:
        class ClassE1{
        public:
            int x;
        };
    };
}

int main() {
    NamespaceD:: NamespaceD1::x = 6;
    NamespaceE::ClassE::ClassE1 e1;
    e1.x = 7  ;
}
```

## <a name="with-static-members"></a>搭配靜態成員

您必須使用範圍解析運算子來呼叫類別的靜態成員。

```cpp
class ClassG {
public:
    static int get_x() { return x;}
    static int x;
};

int ClassG::x = 6;

int main() {

    int gx1 = ClassG::x;
    int gx2 = ClassG::get_x();
}
```

## <a name="with-scoped-enumerations"></a>搭配限定範圍的列舉

範圍的解析運算子也可搭配限定範圍列舉的值[列舉型別宣告](../cpp/enumerations-cpp.md)，如下列範例所示：

```cpp
enum class EnumA{
    First,
    Second,
    Third
};

int main() {
    EnumA enum_value = EnumA::First;
}
```

## <a name="see-also"></a>另請參閱

[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[命名空間](../cpp/namespaces-cpp.md)