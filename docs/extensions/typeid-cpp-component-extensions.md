---
title: typeid  (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
ms.openlocfilehash: 56319fb773b8398f85f5fd82c812f0efdb7dde15
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225107"
---
# <a name="typeid--ccli-and-ccx"></a>typeid  (C++/CLI 和 C++/CX)

取得指示物件類型的值。

> [!NOTE]
> 本主題是指 typeid 的 C++ 元件擴充功能版本。 如需這個關鍵字的 ISO C++ 版本，請參閱 [typeid 運算子](../cpp/typeid-operator.md)。

## <a name="all-runtimes"></a>所有執行階段

### <a name="syntax"></a>語法

```cpp
T::typeid
```

### <a name="parameters"></a>參數

*T*<br/>
類型名稱。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="syntax"></a>語法

```cpp
Platform::Type^ type = T::typeid;
```

### <a name="parameters"></a>參數

*T*<br/>
類型名稱。

### <a name="remarks"></a>備註

在 C++/CX 中，typeid 會傳回自執行階段類型資訊建構的 [Platform::Type](../cppcx/platform-type-class.md)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>語法

```
type::typeid
```

### <a name="parameters"></a>參數

*type*<br/>
您所需 `System::Type` 物件的類型名稱 (抽象宣告子)。

### <a name="remarks"></a>備註

**`typeid`** 是用來 <xref:System.Type> 在編譯時期取得型別的。

**`typeid`** 類似于 `System::Type` 使用或，在執行時間取得型別的 <xref:System.Type.GetType%2A> <xref:System.Object.GetType%2A> 。 不過， **`typeid`** 只接受型別名稱做為參數。  如果您想要使用類型的實例來取得其 `System::Type` 名稱，請使用 `GetType` 。

**`typeid`** 必須能夠在編譯時期評估型別名稱（型別），而 GetType 會評估要在執行時間傳回的型別。

**`typeid`** 可以採用原生類型名稱或 common language runtime 別名做為原生類型名稱;如需詳細資訊，請參閱[c + + 原生類型的 .NET Framework 對應專案（c + +/cli）](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)

**`typeid`** 也適用于原生類型，但它仍會傳回 `System::Type` 。  若要取得 type_info 結構，請使用[ `typeid` 運算子](../cpp/typeid-operator.md)。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

以下範例會比較 typeid 關鍵字和 `GetType()` 成員。

```cpp
// keyword__typeid.cpp
// compile with: /clr
using namespace System;

ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   Type ^ pType = pG->GetType();
   Type ^ pType2 = G::typeid;

   if (pType == pType2)
      Console::WriteLine("typeid and GetType returned the same System::Type");
   Console::WriteLine(G::typeid);

   typedef float* FloatPtr;
   Console::WriteLine(FloatPtr::typeid);
}
```

```Output
typeid and GetType returned the same System::Type
G

System.Single*
```

以下範例說明類型 System::Type 的變數可用來取得類型的屬性。  它也會顯示針對某些類型，您必須建立要使用的 typedef **`typeid`** 。

```cpp
// keyword__typeid_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

typedef int ^ handle_to_int;
typedef int * pointer_to_int;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref class AtClass {
public:
   AtClass(Type ^) {
      Console::WriteLine("in AtClass Type ^ constructor");
   }
};

[attribute(AttributeTargets::All)]
ref class AtClass2 {
public:
   AtClass2() {
      Console::WriteLine("in AtClass2 constructor");
   }
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
ref class B : Attribute {};

int main() {
   Type ^ MyType = B::typeid;

   Console::WriteLine(MyType->IsClass);

   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);
   for (int i = 0 ; i < MyArray->Length ; i++ )
      Console::WriteLine(MyArray[i]);

   if (int::typeid != pointer_to_int::typeid)
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");

   if (int::typeid == handle_to_int::typeid)
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");
}
```

```Output
True

in AtClass2 constructor

in AtClass Type ^ constructor

AtClass2

System.AttributeUsageAttribute

AtClass

int::typeid != pointer_to_int::typeid, as expected

int::typeid == handle_to_int::typeid, as expected
```

## <a name="see-also"></a>另請參閱

[適用于 .NET 和 UWP 的元件擴充功能](component-extensions-for-runtime-platforms.md)
