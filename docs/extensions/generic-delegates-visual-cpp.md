---
title: 泛型委派 (C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
ms.openlocfilehash: 449659126f52997d548ebd7785a78c1200038ee6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515763"
---
# <a name="generic-delegates-ccli"></a>泛型委派 (C++/CLI)

您可以使用具有委派的泛型型別參數。 如需委派的詳細資訊，請參閱[委派 (C++/CLI 和 C++/CX)](delegate-cpp-component-extensions.md)。

## <a name="syntax"></a>語法

```cpp
[attributes]
generic < [class | typename] type-parameter-identifiers>
[type-parameter-constraints-clauses]
[accessibility-modifiers] delegate result-type identifier
([formal-parameters]);
```

### <a name="parameters"></a>參數

*屬性*<br/>
(選擇性) 其他宣告資訊。 如需關於屬性及屬性類別的詳細資訊，請參閱＜屬性＞。

*type-parameter-identifier(s)*<br/>
以逗號分隔的型別參數識別項清單。

*type-parameter-constraints-clauses*<br/>
採用[泛型類型參數的條件約束 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md) 中指定的格式

*accessibility-modifiers*<br/>
(選擇性) 存取範圍修飾詞 (例如 **public** 和 **private**)。

*result-type*<br/>
委派的傳回類型。

*identifier*<br/>
委派的名稱。

*formal-parameters*<br/>
(選擇性) 委派的參數清單。

## <a name="example"></a>範例

委派型別參數是在委派物件建立時指定。 委派以及與其相關聯的方法必須擁有相同的簽章。 以下為泛型委派宣告的範例。

```cpp
// generics_generic_delegate1.cpp
// compile with: /clr /c
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);
```

## <a name="example"></a>範例

以下範例將示範

- 您不能使用不同結構類型的相同委派物件。 為不同的類型建立不同的委派物件。

- 泛型委派可以與泛型方法產生關聯。

- 若呼叫泛型方法時沒有指定類型引數，則編譯器會嘗試推斷呼叫的類型引數。

```cpp
// generics_generic_delegate2.cpp
// compile with: /clr
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);

generic <class ItemType>
ref struct MyGenClass {
   ItemType MyMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

ref struct MyClass {
   generic <class ItemType>
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

int main() {
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();
   GenDelegate<int>^ myDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   GenDelegate<double>^ myDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   GenDelegate<int>^ myDelegate =
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);
}
```

## <a name="example"></a>範例

下列範例會宣告泛型委派 `GenDelegate<ItemType>`，接著將它與使用類型參數 `MyMethod` 的方法 `ItemType` 產生關聯，藉此將它具現化。 將會建立並叫用委派的兩個執行個體 (一個整數和一個雙精度浮點數)。

```cpp
// generics_generic_delegate.cpp
// compile with: /clr
using namespace System;

// declare generic delegate
generic <typename ItemType>
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);

// Declare a generic class:
generic <typename ItemType>
ref class MyGenClass {
public:
   ItemType MyMethod(ItemType p1, ItemType% p2) {
      p2 = p1;
      return p1;
    }
};

int main() {
   int i = 0, j = 0;
   double m = 0.0, n = 0.0;

   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();

   // Instantiate a delegate using int.
   GenDelegate<int>^ MyDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   i = MyDelegate1(123, j);

   Console::WriteLine(
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);

   // Instantiate a delegate using double.
   GenDelegate<double>^ MyDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   m = MyDelegate2(0.123, n);

   Console::WriteLine(
      "Invoking the double delegate: m = {0}, n = {1}", m, n);
}
```

```Output
Invoking the integer delegate: i = 123, j = 123
Invoking the double delegate: m = 0.123, n = 0.123
```

## <a name="see-also"></a>另請參閱

[泛型](generics-cpp-component-extensions.md)