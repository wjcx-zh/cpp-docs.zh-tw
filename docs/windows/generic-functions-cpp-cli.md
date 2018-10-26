---
title: 泛型函式 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4e5305aaa35064c26a78cbd4654c27a0d608d70c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067900"
---
# <a name="generic-functions-ccli"></a>泛型函式 (C++/CLI)

泛型函式會宣告具有型別參數的函式。 呼叫時，會使用實際的類型，而不是類型參數。

## <a name="all-platforms"></a>所有平台

### <a name="remarks"></a>備註

這項功能不適用於所有平台。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="remarks"></a>備註

在 Windows 執行階段不支援此功能。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

泛型函式會宣告具有型別參數的函式。 呼叫時，會使用實際的類型，而不是類型參數。

### <a name="syntax"></a>語法

```cpp
[attributes] [modifiers]
return-type identifier<type-parameter identifier(s)>
[type-parameter-constraints clauses]

([formal-parameters])
{function-body}
```

### <a name="parameters"></a>參數

*屬性*<br/>
（選擇性）其他宣告資訊。 如需有關屬性和屬性類別的詳細資訊，請參閱屬性。

*修飾詞*<br/>
（選擇性）函式，例如靜態修飾詞。  **虛擬**不能，因為虛擬方法不可為泛型。

*傳回型別*<br/>
此方法傳回的型別。 如果傳回的型別為 void，沒有傳回值，則需要的。

*identifier*<br/>
函式名稱。

*型別參數識別項*<br/>
以逗號分隔的識別碼清單。

*型式參數*<br/>
（選擇性）參數清單。

*類型參數條件約束-子句*<br/>
這可作為類型引數，類型上指定的限制，並會在指定的格式[泛型類型參數的條件約束 (C + + /cli CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)。

*函式主體*<br/>
的方法，可能會參考的型別參數識別的主體。

### <a name="remarks"></a>備註

泛型函式會宣告為泛型類型參數的函式。 它們可能在類別或結構或獨立的函式的方法。 單一泛型宣告隱含宣告了一系列的差異只在於不同的實際類型為泛型類型參數的替代的函式。

類別或結構的建構函式不可以宣告泛型型別參數使用。

呼叫時，實際的類型取代泛型類型參數。 實際的型別可以明確指定使用類似於範本函式呼叫語法的角括號括住。 如果呼叫不具型別參數，編譯器會嘗試推斷實際的型別，從函式呼叫中所提供的參數。 如果預期的類型引數無法推算所使用的參數，編譯器會報告錯誤。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列程式碼範例示範泛型函式。

```cpp
// generics_generic_function_1.cpp
// compile with: /clr
generic <typename ItemType>
void G(int i) {}

ref struct A {
   generic <typename ItemType>
   void G(ItemType) {}

   generic <typename ItemType>
   static void H(int i) {}
};

int main() {
   A myObject;

   // generic function call
   myObject.G<int>(10);

   // generic function call with type parameters deduced
   myObject.G(10);

   // static generic function call
   A::H<int>(10);

   // global generic function call
   G<int>(10);
}
```

泛型函式可以根據簽章或套組 arity、 函式的型別參數數目來多載。 此外，泛型函式可以多載具有相同名稱的非泛型函式，只要函式中某些型別參數的差異。 例如，下列函式可以多載：

```cpp
// generics_generic_function_2.cpp
// compile with: /clr /c
ref struct MyClass {
   void MyMythod(int i) {}

   generic <class T>
   void MyMythod(int i) {}

   generic <class T, class V>
   void MyMythod(int i) {}
};
```

下列範例會使用泛型函式，若要尋找陣列中的第一個項目。 它會宣告`MyClass`，該項則繼承自基底類別`MyBaseClass`。 `MyClass` 包含泛型的函式中， `MyFunction`，它會呼叫另一個的泛型函式， `MyBaseClassFunction`，基底類別內。 在  `main`，泛型的函式， `MyFunction`，使用不同的型別引數來呼叫。

```cpp
// generics_generic_function_3.cpp
// compile with: /clr
using namespace System;

ref class MyBaseClass {
protected:
   generic <class ItemType>
   ItemType MyBaseClassFunction(ItemType item) {
      return item;
   }
};

ref class MyClass: public MyBaseClass {
public:
   generic <class ItemType>
   ItemType MyFunction(ItemType item) {
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);
   }
};

int main() {
   MyClass^ myObj = gcnew MyClass();

   // Call MyFunction using an int.
   Console::WriteLine("My function returned an int: {0}",
                           myObj->MyFunction<int>(2003));

   // Call MyFunction using a string.
   Console::WriteLine("My function returned a string: {0}",
   myObj->MyFunction<String^>("Hello generic functions!"));
}
```

```Output
My function returned an int: 2003
My function returned a string: Hello generic functions!
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)<br/>
[泛型](../windows/generics-cpp-component-extensions.md)
