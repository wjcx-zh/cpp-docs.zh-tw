---
title: 泛型函式 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
ms.openlocfilehash: a4a1702c8b9902f5265a8a5f92316d7c82751609
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516373"
---
# <a name="generic-functions-ccli"></a>泛型函式 (C++/CLI)

泛型函式是使用型別參數宣告的函式。 呼叫時，會使用實際型別，而不是型別參數。

## <a name="all-platforms"></a>所有平台

### <a name="remarks"></a>備註

此功能並不適用於所有平台。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="remarks"></a>備註

Windows 執行階段不支援此功能。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

泛型函式是使用型別參數宣告的函式。 呼叫時，會使用實際型別，而不是型別參數。

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
(選擇性) 其他宣告資訊。 如需關於屬性及屬性類別的詳細資訊，請參閱＜屬性＞。

*modifiers*<br/>
(選擇性) 函式的修飾詞，例如 static。  不允許使用 **virtual**，因為虛擬方法可能不是泛型。

*return-type*<br/>
此方法傳回的型別。 若傳回型別為 void，便不需要任何傳回值。

*identifier*<br/>
函式名稱。

*type-parameter identifier(s)*<br/>
以逗號分隔的識別碼清單。

*formal-parameters*<br/>
(選擇性) 參數清單。

*type-parameter-constraints-clauses*<br/>
這在型別上指定可作為型別引數使用的限制，並且會採用[泛型型別參數的條件約束 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md) 中指定的格式。

*function-body*<br/>
這是方法的主體，可能會參考型別參數識別碼。

### <a name="remarks"></a>備註

泛型函式為使用泛型型別參數宣告的函式。 它們可能是類別或結構中的方法，或是獨立函式。 單一泛型宣告會以隱含方式宣告一系列函式，各函式之間的差異只在於將泛型型別參數取代為不同的實際型別。

類別或結構的建構函式不可以使用泛型型別參數宣告。

呼叫時，泛型型別參數會被實際型別取代。 您可以使用與範本函式呼叫類似的語法，用角括號括住實際型別來指定它。 如果在沒有型別參數的情況下呼叫，編譯器會嘗試從函式呼叫中提供的參數推算實際型別。 如果無法從使用的參數推算預定的型別引數，編譯器將會回報錯誤。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

以下程式碼範例會說明泛型函式。

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

泛型函式可以根據簽章或 Arity、函式的型別參數數目來多載。 此外，只要函式的部分型別參數不一樣，就可以將名稱相同的泛型函式與非泛型函式一起多載。 例如，可以多載下列函式：

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

以下範例會使用泛型函式尋找陣列中的第一個元素。 它會宣告繼承自基底類別 `MyBaseClass` 的 `MyClass`。 `MyClass` 包含一個泛型函式 `MyFunction`，它會呼叫基底類別內的另一個泛型函式 `MyBaseClassFunction`。 在 `main` 中則會使用不同的型別引數呼叫泛型函式 `MyFunction`。

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

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)<br/>
[泛型](generics-cpp-component-extensions.md)
