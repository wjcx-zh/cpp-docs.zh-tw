---
title: nullptr (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 05aaaa8a0d0056e0f5318f5e9329d90824760728
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515633"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C++/CLI 和 C++/CX)

**nullptr** 關鍵字代表一個「null 指標值」。 使用 null 指標值來指出物件控制代碼、內部指標或原生指標型別並未指向物件。

搭配受控碼或機器碼來使用 **nullptr**。 編譯器會針對受控和原生的 null 指標值發出適當但不同的指示。 如需使用此關鍵字的 ISO 標準 C++ 版本相關資訊，請參閱 [nullptr](../cpp/nullptr.md)。

**__nullptr** 關鍵字是 Microsoft 特定的關鍵字，其意義與 **nullptr** 相同，但只適用於機器碼。 如果您搭配 C/C++ 機器碼使用 **nullptr**，然後使用 [/clr](../build/reference/clr-common-language-runtime-compilation.md) 編譯器選項進行編譯，則編譯器無法判斷 **nullptr** 所指出的是原生還是受控的 null 指標值。 為了讓編譯器清楚您的意圖，請使用 **nullptr** 來指定受控值，或使用 **__nullptr** 來指定原生值。

**nullptr** 關鍵字相當於 Visual Basic 中的 **Nothing** 及 C# 中的 **null**。

## <a name="usage"></a>使用量

**nullptr** 關鍵字可用於任何可使用控制代碼、原生指標或函式引數的地方。

**nullptr** 關鍵字不是型別且不支援與下列項目搭配使用：

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (儘管 `throw (Object^)nullptr;` 將能運作)

**nullptr** 關鍵字可用來將下列指標型別初始化：

- 原生指標

- Windows 執行階段控制代碼

- 受控的控制代碼

- 受控的內部指標

**nullptr** 關鍵字可在使用參考之前，用來測試指標或控制代碼參考是否為 Null。

在語言之間使用 null 指標值來檢查錯誤的函式呼叫應會正確解譯。

您無法將控制代碼初始化為零；只能使用 **nullptr**。 為物件控制代碼指派常數 0 會產生 Boxed 的 `Int32` 及 `Object^` 的轉換。

## <a name="example"></a>範例

下列程式碼範例示範 **nullptr** 關鍵字可用於任何可使用控制代碼、原生指標或函式引數的地方。 此外，此範例示範可以使用 **nullptr** 關鍵字來檢查參考，然後再使用它。

```cpp
// mcpp_nullptr.cpp
// compile with: /clr
value class V {};
ref class G {};
void f(System::Object ^) {}

int main() {
// Native pointer.
   int *pN = nullptr;
// Managed handle.
   G ^pG = nullptr;
   V ^pV1 = nullptr;
// Managed interior pointer.
   interior_ptr<V> pV2 = nullptr;
// Reference checking before using a pointer.
   if (pN == nullptr) {}
   if (pG == nullptr) {}
   if (pV1 == nullptr) {}
   if (pV2 == nullptr) {}
// nullptr can be used as a function argument.
   f(nullptr);   // calls f(System::Object ^)
}
```

## <a name="example"></a>範例

下列程式碼範例示範 **nullptr** 和零可在原生指標上交換使用。

```cpp
// mcpp_nullptr_1.cpp
// compile with: /clr
class MyClass {
public:
   int i;
};

int main() {
   MyClass * pMyClass = nullptr;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");

   pMyClass = 0;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");
}
```

```Output
pMyClass == nullptr

pMyClass == 0

pMyClass == nullptr

pMyClass == 0
```

## <a name="example"></a>範例

下列程式碼範例示範會將 **nullptr** 解譯為任意型別的控制代碼或任意型別的原生指標。 如果使用不同型別的控制代碼進行函式多載，將產生模稜兩可錯誤。 **nullptr** 必須明確轉換為某種型別。

```cpp
// mcpp_nullptr_2.cpp
// compile with: /clr /LD
void f(int *){}
void f(int ^){}

void f_null() {
   f(nullptr);   // C2668
   // try one of the following lines instead
   f((int *) nullptr);
   f((int ^) nullptr);
}
```

## <a name="example"></a>範例

下列程式碼範例示範允許轉換 **nullptr**，並傳回包含 **nullptr** 值之轉換型別的指標或控制代碼。

```cpp
// mcpp_nullptr_3.cpp
// compile with: /clr /LD
using namespace System;
template <typename T>
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type

int main() {
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)

   // Delete the following line to resolve.
   f(nullptr);

   f(0);   // T = int, call f(int)
}
```

## <a name="example"></a>範例

下列程式碼範例示範可以使用 **nullptr** 作為函式參數。

```cpp
// mcpp_nullptr_4.cpp
// compile with: /clr
using namespace System;
void f(Object ^ x) {
   Console::WriteLine("test");
}

int main() {
   f(nullptr);
}
```

```Output
test
```

## <a name="example"></a>範例

下列程式碼範例示範，當控制代碼已宣告且未明確初始化時，預設會將它們初始化為 **nullptr**。

```cpp
// mcpp_nullptr_5.cpp
// compile with: /clr
using namespace System;
ref class MyClass {
public:
   void Test() {
      MyClass ^pMyClass;   // gc type
      if (pMyClass == nullptr)
         Console::WriteLine("NULL");
   }
};

int main() {
   MyClass ^ x = gcnew MyClass();
   x -> Test();
}
```

```Output
NULL
```

## <a name="example"></a>範例

下列程式碼範例示範，當您使用 `/clr` 進行編譯時，可將 **nullptr** 指派給原生指標。

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>需求

編譯器選項：(不需要；所有程式碼產生選項都支援，包括 `/ZW` 和 `/clr`)

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)