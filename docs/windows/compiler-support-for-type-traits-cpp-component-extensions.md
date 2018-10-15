---
title: 類型特性的編譯器支援 (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __is_simple_value_class
- __has_trivial_destructor
- __has_assign
- __is_union
- __is_class
- __is_abstract
- __has_trivial_assign
- __has_virtual_destructor
- __is_ref_array
- __is_base_of
- __has_copy
- __is_polymorphic
- __has_nothrow_constructor
- __is_ref_class
- __is_delegate
- __is_convertible_to
- __is_value_class
- __is_interface_class
- __has_nothrow_copy
- __is_sealed
- __has_trivial_constructor
- __has_trivial_copy
- __is_enum
- __has_nothrow_assign
- __has_finalizer
- __is_empty
- __is_pod
- __has_user_destructor
dev_langs:
- C++
helpviewer_keywords:
- __is_class keyword [C++]
- __is_pod keyword [C++]
- __is_delegate keyword [C++]
- __is_value_class keyword [C++]
- __has_copy keyword [C++]
- __has_nothrow_copy keyword [C++]
- __is_interface_class keyword [C++]
- __is_sealed keyword [C++]
- __is_convertible_to keyword [C++]
- __is_ref_class keyword [C++]
- __has_trivial_copy keyword [C++]
- __has_user_destructor keyword [C++]
- __is_abstract keyword [C++]
- __is_empty keyword [C++]
- __has_trivial_assign keyword [C++]
- __has_nothrow_constructor keyword [C++]
- __is_ref_array keyword [C++]
- __is_base_of keyword [C++]
- __has_nothrow_assign keyword [C++]
- __has_virtual_destructor keyword [C++]
- __has_finalizer keyword [C++]
- __is_union keyword [C++]
- __has_assign keyword [C++]
- __has_trivial_destructor keyword [C++]
- __is_polymorphic keyword [C++]
- __is_enum keyword [C++]
- __is_simple_value_class keyword [C++]
- __has_trivial_constructor keyword [C++]
ms.assetid: cd440630-0394-48c0-a16b-1580b6ef5844
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dfa3f599da4594e9cb0d416def1846b9937664f8
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328530"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>類型特性的編譯器支援 (C + + /cli 和 C + + /CX)

Microsoft c + + 編譯器支援*類型特性*C + /cli 和 C + + /CX 延伸模組，這表示在編譯時期的各種類型的特性。

## <a name="all-runtimes"></a>所有執行階段

### <a name="remarks"></a>備註

類型特性特別適用於撰寫程式庫的程式設計人員。

下列清單包含編譯器所支援的類型特性。 所有類型特性都會傳回**false**如果不符合類型特性的名稱所指定的條件。

(在下列清單中，程式碼範例會寫入只在 C + + /cli CLI。 但對應的類型特性也支援在 C + + /CX 除非另外註明否則。 詞彙 「 平台類型 」 是指 Windows 執行階段類型或 common language runtime 類型。）

- `__has_assign(` *型別* `)`

   傳回 **，則為 true**如果平台或原生類型具有複製指派運算子。

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- `__has_copy(` *型別* `)`

   傳回 **，則為 true**如果平台或原生類型具有複製建構函式。

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- `__has_finalizer(` *型別* `)`

   (不支援在 C + + /CX。)傳回 **，則為 true**如果 CLR 類型具有完成項。 請參閱[解構函式和完成項中如何： 定義和使用類別和結構 (C + + /cli CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)如需詳細資訊。

    ```cpp
    using namespace System;
    ref struct R {
    ~R() {}
    protected:
    !R() {}
    };

    int main() {
    Console::WriteLine(__has_finalizer(R));
    }
    ```

- `__has_nothrow_assign(` *型別* `)`

   傳回 **，則為 true**如果複製指派運算子具有空的例外狀況規格。

    ```cpp
    #include <stdio.h>
    struct S {
    void operator=(S& r) throw() {}
    };

    int main() {
    __has_nothrow_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_constructor(` *型別* `)`

   傳回 **，則為 true**如果預設建構函式具有空的例外狀況規格。

    ```cpp
    #include <stdio.h>
    struct S {
    S() throw() {}
    };

    int main() {
    __has_nothrow_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_copy(` *型別* `)`

   傳回 **，則為 true**如果複製建構函式具有空的例外狀況規格。

    ```cpp
    #include <stdio.h>
    struct S {
    S(S& r) throw() {}
    };

    int main() {
    __has_nothrow_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_assign(` *型別* `)`

   傳回 **，則為 true**類型是否為 trivial，編譯器產生的指派運算子。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_constructor(` *型別* `)`

   傳回 **，則為 true**類型是否為 trivial，編譯器產生的建構函式。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_copy(` *型別* `)`

   傳回 **，則為 true**類型是否為 trivial，編譯器產生的複製建構函式。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_destructor(` *型別* `)`

   傳回 **，則為 true**類型是否為 trivial，編譯器產生的解構函式。

    ``` cpp 
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_user_destructor(` *型別* `)`

   傳回 **，則為 true**如果平台或原生類型具有使用者宣告解構函式。

    ```cpp
    // has_user_destructor.cpp

    using namespace System;
    ref class R {
    ~R() {}
    };

    int main() {
    Console::WriteLine(__has_user_destructor(R));
    }
    ```

- `__has_virtual_destructor(` *型別* `)`

   傳回 **，則為 true**如果類型具有虛擬解構函式。

   `__has_virtual_destructor` 也適用於平台類型，且任何平台類型中的使用者定義解構函式都是虛擬解構函式。

    ```cpp
    // has_virtual_destructor.cpp
    #include <stdio.h>
    struct S {
    virtual ~S() {}
    };

    int main() {
    __has_virtual_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_abstract(` *型別* `)`

   傳回 **，則為 true**如果類型是抽象型別。 如需有關原生抽象類型的詳細資訊，請參閱 <<c0> [ 抽象類別](../cpp/abstract-classes-cpp.md)。

   `__is_abstract` 也適用於平台類型。 至少有一個成員的介面是參考類型，至少有一個抽象成員的介面是參考類型。 如需抽象平台類型的詳細資訊，請參閱[抽象](../windows/abstract-cpp-component-extensions.md)。

    ```cpp
    // is_abstract.cpp
    #include <stdio.h>
    struct S {
    virtual void Test() = 0;
    };

    int main() {
    __is_abstract(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_base_of(` `base` `,` `derived` `)`

   傳回 **，則為 true**第二個類型的基底類別的第一個類型時，如果這兩種類型的相同。

   `__is_base_of` 也適用於平台類型。 比方說，它會傳回**真**如果第一個類型為[介面類別](../windows/interface-class-cpp-component-extensions.md)和第二個類型實作介面。

    ```cpp
    // is_base_of.cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    __is_base_of(S, T) == true ?
    printf("true\n") : printf("false\n");

    __is_base_of(S, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_class(` *型別* `)`

   傳回 **，則為 true**如果類型是原生類別或結構。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,`  `to` `)`

   傳回 **，則為 true**如果第一個類型可轉換成第二個型別。

    ```cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    S * s = new S;
    T * t = new T;
    s = t;
    __is_convertible_to(T, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_delegate(` *型別* `)`

   傳回**真**如果`type`是一種委派。 如需詳細資訊，請參閱 <<c0> [ 委派 (C + + /cli 和 C + + /CX)](../windows/delegate-cpp-component-extensions.md)。

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- `__is_empty(` *型別* `)`

   傳回 **，則為 true**如果類型沒有執行個體資料成員。

    ```cpp
    #include <stdio.h>
    struct S {
    int Test() {}
    static int i;
    };
    int main() {
    __is_empty(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_enum(` *型別* `)`

   傳回 **，則為 true**類型是否為原生列舉。

    ```cpp
    // is_enum.cpp
    #include <stdio.h>
    enum E { a, b };

    struct S {
    enum E2 { c, d };
    };

    int main() {
    __is_enum(E) == true ?
    printf("true\n") : printf("false\n");

    __is_enum(S::E2) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_interface_class(` *型別* `)`

   傳回 **，則為 true**如果傳遞平台介面。 如需詳細資訊，請參閱 <<c0> [ 介面類別](../windows/interface-class-cpp-component-extensions.md)。

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- `__is_pod(` *型別* `)`

   傳回 **，則為 true**如果類型是類別或等位沒有建構函式或私用或受保護的非靜態成員、 沒有基底類別，並沒有虛擬函式。 如需 POD 的詳細資訊，請參閱 C++ 標準的 8.5.1/1、9/4 和 3.9/10 小節。

   `__is_pod` 對於基本類型會傳回 false。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_polymorphic(` *型別* `)`

   傳回 **，則為 true**如果原生類型具有虛擬函式。

    ```cpp
    #include <stdio.h>
    struct S {
    virtual void Test(){}
    };

    int main() {
    __is_polymorphic(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_ref_array(` *型別* `)`

   傳回 **，則為 true**如果傳遞平台陣列。 如需詳細資訊，請參閱 <<c0> [ 陣列](../windows/arrays-cpp-component-extensions.md)。

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- `__is_ref_class(` *型別* `)`

   傳回 **，則為 true**如果傳遞參考類別。 如需有關使用者定義的參考類型的詳細資訊，請參閱 <<c0> [ 類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)。

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- `__is_sealed(` *型別* `)`

   傳回 **，則為 true**如果傳遞平台或標示為密封的原生型別。 如需詳細資訊，請參閱 <<c0> [ 密封](../windows/sealed-cpp-component-extensions.md)。

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- `__is_simple_value_class(` *型別* `)`

   傳回 **，則為 true**如果傳遞實值型別，其中包含不到記憶體回收堆積的參考。 如需有關使用者定義的實值類型的詳細資訊，請參閱[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)。

    ```cpp
    using namespace System;
    ref class R {};
    value struct V {};
    value struct V2 {
    R ^ r;   // not a simnple value type
    };

    int main() {
    Console::WriteLine(__is_simple_value_class(V));
    Console::WriteLine(__is_simple_value_class(V2));
    }
    ```

- `__is_union(` *型別* `)`

   傳回 **，則為 true**如果類型是等位。

    ```cpp
    #include <stdio.h>
    union A {
    int i;
    float f;
    };

    int main() {
    __is_union(A) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_value_class(` *型別* `)`

   傳回 **，則為 true**如果傳遞實值型別。 如需有關使用者定義的實值類型的詳細資訊，請參閱[類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)。

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="remarks"></a>備註

`__has_finalizer(`*型別*`)`不支援類型特性，因為這個平台不支援完成項。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>備註

(沒有這項功能的平台特定備註。)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

**範例**

下列程式碼範例說明如何使用類別範本來公開 `/clr` 編譯的編譯器類型特性。 如需詳細資訊，請參閱 < [Windows 執行階段和 Managed 樣板](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)。

```cpp
// compiler_type_traits.cpp
// compile with: /clr
using namespace System;

template <class T>
ref struct is_class {
   literal bool value = __is_ref_class(T);
};

ref class R {};

int main () {
   if (is_class<R>::value)  
      Console::WriteLine("R is a ref class");
   else
      Console::WriteLine("R is not a ref class");
}
```

```Output
R is a ref class
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)