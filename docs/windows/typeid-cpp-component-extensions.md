---
title: typeid (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b31344b1ba72b37bcfff45a3fd4feefda85f6a7a
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327579"
---
# <a name="typeid--ccli-and-ccx"></a>typeid (C + + /cli 和 C + + /CX)

取得值，指出物件類型。

> [!NOTE]
> 本主題是指 typeid 的 C++ 元件擴充功能版本。 如需這個關鍵字的 ISO c + + 版本，請參閱[typeid 運算子](../cpp/typeid-operator.md)。

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

在 C + + /CX 中，typeid 會傳回[platform:: type](../cppcx/platform-type-class.md) ，建構自執行階段類型資訊。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>語法

```
type::typeid
```

### <a name="parameters"></a>參數

*type*<br/>
在您要為其類型 （抽象宣告子） 的名稱`System::Type`物件。

### <a name="remarks"></a>備註

`typeid` 用來取得<xref:System.Type>在編譯時期類型。

`typeid` 類似於在執行的階段使用的型別取得 system:: type<xref:System.Type.GetType%2A>或<xref:System.Object.GetType%2A>。 不過，typeid 只會接受型別名稱做為參數。  如果您想要取得其 system:: type 名稱中使用型別的執行個體，使用 GetType。

`typeid` 必須要能夠在編譯時期評估的類型名稱 （類型），而 GetType 評估要在執行階段傳回的型別。

`typeid` 可能需要原生型別名稱或通用語言執行階段原生型別名稱別名;請參閱[c + + 原生類型的.NET Framework 對應項 (C + + /cli CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)如需詳細資訊。

`typeid` 也可以搭配原生類型，但它仍會傳回 system:: type。  若要取得 type_info 結構，請使用[typeid 運算子](../cpp/typeid-operator.md)。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列範例會比較所要的 typeid 關鍵字`GetType()`成員。

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

下列範例會顯示 system:: type 可以用來取得型別上的屬性類型的變數。  它也會顯示，對於某些類型，您必須建立使用 typedef `typeid`。

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

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)