---
title: delegate (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: 388ccb28c9311b4727199e6b7324771c24c2906d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172434"
---
# <a name="delegate--ccli-and-ccx"></a>delegate (C++/CLI 和 C++/CX)

宣告代表函式指標的型別。

## <a name="all-runtimes"></a>所有執行階段

Windows 執行階段和 Common Language Runtime 均支援委派。

### <a name="remarks"></a>備註

**delegate** 是內容相關性關鍵字。 如需詳細資訊，請參閱[即時線上關鍵字](context-sensitive-keywords-cpp-component-extensions.md)。

若要在編譯時間偵測某個型別是否為委派，請使用 `__is_delegate()` 型別特性。 如需詳細資訊，請參閱[型別特性的編譯器支援](compiler-support-for-type-traits-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 執行階段

C++/CX 透過下列語法來支援委派。

### <a name="syntax"></a>語法

```cpp
access
delegate
return-type
delegate-type-identifier
(
[ parameters ]
)
```

### <a name="parameters"></a>參數

*access*<br/>
(選擇性) 委派的可及性，可以是 **public** (預設值) 或 **private**。 函式原型也可以使用 **const** 或 **volatile** 關鍵字來限定。

*return-type*<br/>
函式原型的傳回型別。

*delegate-type-identifier*<br/>
宣告之委派型別的名稱。

*parameters*<br/>
(選擇性) 函式原型的型別和識別碼。

### <a name="remarks"></a>備註

使用 *delegate-type-identifier* 來宣告原型與委派相同的事件。 如需詳細資訊，請參閱[委派 (C++/CX)](../cppcx/delegates-c-cx.md)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Common Language Runtime 透過下列語法來支援委派。

### <a name="syntax"></a>語法

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>參數

*access*<br/>
(選擇性) 委派在組件外部的可及性可以是 public 或 private。  預設值是 private。  在類別內部，委派可以具有任意的可及性。

*function_declaration*<br/>
可繫結至委派的函式簽章。 委派的傳回型別可以是任意的受控型別。 基於互通性考量，建議委派的傳回型別為 CLS 型別。

若要定義未繫結的委派，*function_declaration* 中的第一個參數應該是物件的 **this** 指標的型別。

### <a name="remarks"></a>備註

委派是多點傳送的：「函式指標」可以繫結至受控類別內的一或多個方法。 **delegate** 關鍵字會使用特定方法簽章來定義多點傳送的委派型別。

委派也可以繫結至實值類別的方法，例如靜態方法。

委派具有下列特性：

- 它繼承自 `System::MulticastDelegate`。

- 它具有可接受兩個引數的建構函式：指向受控類別或 NULL (適用於繫結至靜態方法的情況) 的指標，以及指定型別的完整限定方法。

- 它擁有稱為 `Invoke` 的方法，其簽章與宣告的委派簽章相符。

叫用委派時，會依照附加函式的順序來呼叫它們。

委派的傳回值是從其最後一個附加成員函式傳回的值。

委派不可以多載。

委派可以是繫結或未繫結的。

當您將繫結的委派具現化時，第一個引數應該是物件參考。 委派具現化的第二個引數應該是受控類別物件的方法位址或指向實值型別方法的指標。 委派具現化的第二個引數必須使用完整類別範圍語法來為方法命名，並套用傳址運算子。

當您將未繫結的委派具現化時，第一個引數應該是受控類別物件的方法位址或指向實值型別方法的指標。 此引數必須使用完整類別範圍語法來為方法命名，並套用傳址運算子。

建立靜態或全域函式的委派時，只有一個必要參數：函式 (選擇性，函式的位址)。

如需委派的詳細資訊，請參閱

- [如何：定義和使用委派 (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [泛型委派 (C++/CLI)](generic-delegates-visual-cpp.md)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列範例示範如何宣告、初始化及叫用委派。

```cpp
// mcppv2_delegate.cpp
// compile with: /clr
using namespace System;

// declare a delegate
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      Console::WriteLine("in func1 {0}", i);
   }

   void func2(int i) {
      Console::WriteLine("in func2 {0}", i);
   }

   static void func3(int i) {
      Console::WriteLine("in static func3 {0}", i);
   }
};

int main () {
   A ^ a = gcnew A;

   // declare a delegate instance
   MyDel^ DelInst;

   // test if delegate is initialized
   if (DelInst)
      DelInst(7);

   // assigning to delegate
   DelInst = gcnew MyDel(a, &A::func1);

   // invoke delegate
   if (DelInst)
      DelInst(8);

   // add a function
   DelInst += gcnew MyDel(a, &A::func2);

   DelInst(9);

   // remove a function
   DelInst -= gcnew MyDel(a, &A::func1);

   // invoke delegate with Invoke
   DelInst->Invoke(10);

   // make delegate to static function
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);
   StaticDelInst(11);
}
```

```Output
in func1 8

in func1 9

in func2 9

in func2 10

in static func3 11
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)
