---
title: typeid  (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
ms.openlocfilehash: ec64388d5f71cff01207129e337cf20bb151db1a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515983"
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

`typeid` 可在編譯時間用來取得類型的 <xref:System.Type>。

`typeid` 類似於在執行階段使用 <xref:System.Type.GetType%2A> 或 <xref:System.Object.GetType%2A> 取得類型的 System::Type。 但 typeid 只接受類型名稱做為參數。  如果想要使用某一類型的執行個體來取得其 System:: Type 名稱，請使用 GetType。

`typeid` 必須能夠在編譯時間評估類型名稱 (type)，而 GetType 則評估要在執行階段傳回的類型。

`typeid` 可使用原生類型名稱或通用語言執行階段別名作為原生類型名稱；如需詳細資訊，請參閱 [C++ 原生類型 (C++/CLI) 的 .NET Framework 對應項](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。

`typeid` 也可以搭配原生類型運作，雖然它仍會傳回 System::Type。  若要取得 type_info 結構，請使用 [typeid 運算子](../cpp/typeid-operator.md)。

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

以下範例說明類型 System::Type 的變數可用來取得類型的屬性。  它也會說明對於某些類型，您必須建立使用 `typeid` 的 typedef。

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

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)