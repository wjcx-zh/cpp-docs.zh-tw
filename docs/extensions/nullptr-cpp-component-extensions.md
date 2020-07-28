---
title: nullptr (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 5e7a5d3f9a42968dee35f82d3f19d0fdb6da5d0c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214226"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C++/CLI 和 C++/CX)

**`nullptr`** 關鍵字代表*null 指標值*。 使用 null 指標值來指出物件控制代碼、內部指標或原生指標型別並未指向物件。

搭配 **`nullptr`** managed 或機器碼使用。 編譯器會針對受控和原生的 null 指標值發出適當但不同的指示。 如需使用此關鍵字的 ISO 標準 C++ 版本相關資訊，請參閱 [nullptr](../cpp/nullptr.md)。

**__Nullptr**關鍵字是與有相同意義 **`nullptr`** ，但僅適用于機器碼的 Microsoft 特定關鍵字。 如果您使用搭配 **`nullptr`** 原生 C/c + + 程式碼，然後以[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項進行編譯，則編譯器無法判斷是否 **`nullptr`** 表示原生或 managed null 指標值。 若要將您的意圖清楚地提供給編譯器，請使用 **`nullptr`** 來指定受控值或 **__nullptr**來指定原生值。

**`nullptr`** 關鍵字相當於 Visual Basic 中的**任何內容**，而在 c # 中為**null** 。

## <a name="usage"></a>使用方式

**`nullptr`** 關鍵字可以在任何可使用控制碼、原生指標或函式引數的位置使用。

**`nullptr`** 關鍵字不是類型，而且不支援搭配使用：

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (儘管 `throw (Object^)nullptr;` 將能運作)

**`nullptr`** 關鍵字可用於下列指標類型的初始化中：

- 原生指標

- Windows 執行階段控制代碼

- 受控的控制代碼

- 受控的內部指標

**`nullptr`** 關鍵字可以在使用參考之前，用來測試指標或控制碼參考是否為 null。

在語言之間使用 null 指標值來檢查錯誤的函式呼叫應會正確解譯。

您不能將控制碼初始化為零。只有 **`nullptr`** 可以使用。 為物件控制代碼指派常數 0 會產生 Boxed 的 `Int32` 及 `Object^` 的轉換。

## <a name="example"></a>範例

下列程式碼範例示範在 **`nullptr`** 可以使用控制碼、原生指標或函式引數的任何地方都可以使用關鍵字。 這個範例示範 **`nullptr`** 關鍵字可以用來檢查參考，然後再使用它。

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

下列程式碼範例顯示， **`nullptr`** 和零可以在原生指標上交替使用。

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

下列程式碼範例顯示，它會被視為任何類型 **`nullptr`** 的控制碼或任何類型的原生指標。 如果使用不同型別的控制代碼進行函式多載，將產生模稜兩可錯誤。 必須 **`nullptr`** 明確轉換成類型。

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

下列程式碼範例顯示允許轉換 **`nullptr`** ，並將指標或控制碼傳回包含值的轉換類型 **`nullptr`** 。

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

下列程式碼範例顯示， **`nullptr`** 可做為函式參數使用。

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

下列程式碼範例顯示當控制碼宣告且未明確初始化時，它們預設會初始化為 **`nullptr`** 。

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

下列程式碼範例顯示 **`nullptr`** 當您使用進行編譯時，可以指派給原生指標 `/clr` 。

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>需求

編譯器選項：（並非必要; 由所有程式碼產生選項支援，包括 `/ZW` 和 `/clr` ）

## <a name="see-also"></a>另請參閱

[適用于 .NET 和 UWP 的元件擴充功能](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)
