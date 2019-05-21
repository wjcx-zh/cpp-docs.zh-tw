---
title: 型別特性的編譯器支援 (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
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
ms.openlocfilehash: d068917a02fef0f1d4b7fd46fd6978da2d358872
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516213"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>型別特性的編譯器支援 (C++/CLI 和 C++/CX)

Microsoft C++ 編譯器支援適用於 C++/CLI 和 C++/CX 擴充功能的「型別特性」，可指出型別在編譯時間的各種特性。

## <a name="all-runtimes"></a>所有執行階段

### <a name="remarks"></a>備註

類型特性特別適用於撰寫程式庫的程式設計人員。

下表列出編譯器所支援的型別特性。 如果不符合型別特性名稱所指定的條件，所有型別特性都會傳回 **false**。

(在下列清單中，程式碼範例都只以 C++/CLI 撰寫。 但除非另有說明，否則 C++/CX 中也支援對應的型別特性。 「平台型別」一詞是指 Windows 執行階段型別或 Common Language Runtime 型別。)

- `__has_assign(` *type* `)`

   如果平台或原生型別具有複製指派運算子，即會傳回 **true**。

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- `__has_copy(` *type* `)`

   如果平台或原生類型具有複製建構函式，即會傳回 **true**。

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- `__has_finalizer(` *type* `)`

   (C++/CX 中不支援。)如果 CLR 型別具有完成項，即會傳回 **true**。 如需詳細資訊，請參閱 [HOW TO：定義和使用類別和結構 (C++/CLI) 中的「解構函式和完成項」](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

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

- `__has_nothrow_assign(` *type* `)`

   如果複製指派運算子具有空的例外狀況規格，即會傳回 **true**。

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

- `__has_nothrow_constructor(` *type* `)`

   如果預設建構函式具有空的例外狀況規格，即會傳回 **true**。

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

- `__has_nothrow_copy(` *type* `)`

   如果複製建構函式具有空的例外狀況規格，即會傳回 **true**。

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

- `__has_trivial_assign(` *type* `)`

   如果型別具有編譯器產生的一般指派運算子，即會傳回 **true**。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_constructor(` *type* `)`

   如果型別具有編譯器產生的一般建構函式，即會傳回 **true**。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_copy(` *type* `)`

   如果型別具有編譯器產生的複製建構函式，即會傳回 **true**。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_destructor(` *type* `)`

   如果型別具有編譯器產生的一般解構函式，即會傳回 **true**。

    ``` cpp
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_user_destructor(` *type* `)`

   如果平台或原生型別具有使用者宣告的解構函式，即會傳回 **true**。

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

- `__has_virtual_destructor(` *type* `)`

   如果型別具有虛擬解構函式，即會傳回 **true**。

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

- `__is_abstract(` *type* `)`

   如果型別是抽象型別，即會傳回 **true**。 如需原生抽象型別的詳細資訊，請參閱[抽象類別](../cpp/abstract-classes-cpp.md)。

   `__is_abstract` 也適用於平台類型。 至少有一個成員的介面是參考類型，至少有一個抽象成員的介面是參考類型。 如需抽象平台型別的詳細資訊，請參閱 [abstract](abstract-cpp-component-extensions.md)。

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

   如果第一個型別為第二個型別的基底類別，或者這兩個型別相同，即會傳回 **true**。

   `__is_base_of` 也適用於平台類型。 例如，如果第一個型別為[介面類別](interface-class-cpp-component-extensions.md)，且第二個型別會實作該介面，即會傳回 **true**。

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

- `__is_class(` *type* `)`

   如果型別是原生類別或結構，即會傳回 **true**。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,`  `to` `)`

   如果第一個型別可轉換成第二個型別，即會傳回 **true**。

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

- `__is_delegate(` *type* `)`

   如果 `type` 是委派，即會傳回 **true**。 如需詳細資訊，請參閱 [delegate (C++/CLI 和 C++/CX)](delegate-cpp-component-extensions.md)。

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- `__is_empty(` *type* `)`

   如果型別沒有執行個體資料成員，即會傳回 **true**。

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

- `__is_enum(` *type* `)`

   如果型別是原生列舉，即會傳回 **true**。

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

- `__is_interface_class(` *type* `)`

   如果傳遞了平台介面，即會傳回 **true**。 如需詳細資訊，請參閱[介面類別](interface-class-cpp-component-extensions.md)。

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- `__is_pod(` *type* `)`

   如果型別是類別或等位，且不具建構函式、私人或受保護的非靜態成員、不具基底類別且沒有虛擬函式，即會傳回 **true**。 如需 POD 的詳細資訊，請參閱 C++ 標準的 8.5.1/1、9/4 和 3.9/10 小節。

   `__is_pod` 對於基本類型會傳回 false。

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_polymorphic(` *type* `)`

   如果原生型別具有虛擬函式，即會傳回 **true**。

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

- `__is_ref_array(` *type* `)`

   如果傳遞了平台陣列，即會傳回 **true**。 如需詳細資訊，請參閱[陣列](arrays-cpp-component-extensions.md)。

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- `__is_ref_class(` *type* `)`

   如果傳遞了參考類別，即會傳回 **true**。 如需使用者定義的參考型別的詳細資訊，請參閱[類別和結構](classes-and-structs-cpp-component-extensions.md)。

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- `__is_sealed(` *type* `)`

   如果傳遞了標示為密封的平台或原生型別，即會傳回 **true**。 如需詳細資訊，請參閱 [sealed](sealed-cpp-component-extensions.md)。

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- `__is_simple_value_class(` *type* `)`

   如果傳遞了實值型別，且其中不含對記憶體回收堆積的參考，即會傳回 **true**。 如需使用者定義的實值型別的詳細資訊，請參閱[類別和結構](classes-and-structs-cpp-component-extensions.md)。

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

- `__is_union(` *type* `)`

   如果型別是等位，即會傳回 **true**。

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

- `__is_value_class(` *type* `)`

   如果傳遞了實值型別，即會傳回 **true**。 如需使用者定義的實值型別的詳細資訊，請參閱[類別和結構](classes-and-structs-cpp-component-extensions.md)。

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="remarks"></a>備註

不支援 `__has_finalizer(`*type*`)` 型別特性，因為此平台不支援完成項。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>備註

(沒有此功能的平台特定備註。)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

**範例**

下列程式碼範例說明如何使用類別範本來公開 `/clr` 編譯的編譯器類型特性。 如需詳細資訊，請參閱 [Windows 執行階段與受控範本](windows-runtime-and-managed-templates-cpp-component-extensions.md)。

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

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)