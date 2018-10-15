---
title: 委派 (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
dev_langs:
- C++
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2281dfb6648f9c4756800a0693f184ccaa7435d7
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327956"
---
# <a name="delegate--ccli-and-ccx"></a>委派 (C + + /cli 和 C + + /CX)

宣告表示的函式指標的類型。

## <a name="all-runtimes"></a>所有執行階段

在 Windows 執行階段和通用語言執行平台支援委派。

### <a name="remarks"></a>備註

**委派**是內容相關性關鍵字。 如需詳細資訊，請參閱 <<c0> [ 即時線上關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。

若要在編譯時期偵測，如果類型是委派，使用`__is_delegate()`類型特性。 如需詳細資訊，請參閱 <<c0> [ 類型特性的編譯器支援](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 執行階段

C + + /CX 支援使用下列語法的委派。

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
（選擇性）委派，可協助工具**公開金鑰**（預設值） 或**私人**。 函式原型也可以與限定**const**或是**volatile**關鍵字。

*傳回型別*<br/>
函式原型的傳回型別。

*委派型別識別項*<br/>
宣告的委派類型的名稱。

*參數*<br/>
（選擇性）型別和函式原型的識別項。

### <a name="remarks"></a>備註

使用*委派型別識別項*來宣告具有與委派相同原型的事件。 如需詳細資訊，請參閱 <<c0> [ 委派 (C + + /CX)](../cppcx/delegates-c-cx.md)。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Common language runtime 支援使用下列語法的委派。

### <a name="syntax"></a>語法

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>參數

*access*<br/>
（選擇性）外部組件的存取範圍可以是委派的公用或私用。  預設為私用。  在類別中，委派可以有任何存取範圍。

*function_declaration*<br/>
可以繫結至委派的函式簽章。 委派的傳回型別可以是任何 managed 型別。 基於互通性考量，建議您使用委派的傳回型別是 CLS 類型。

若要定義繫結的委派中的第一個參數*function_declaration*的類型應要**這**物件的指標。

### <a name="remarks"></a>備註

委派是多點傳送: 「 函式指標 」 可以繫結至受管理的類別內的一或多個方法。 **委派**關鍵字定義的特定方法簽章的多點傳送的委派類型。

委派也繫結至方法的實值類別，例如靜態方法。

委派會具有下列特性：

- 它繼承自`System::MulticastDelegate`。

- 它有兩個引數的建構函式： 受管理的類別或 NULL （如果是靜態方法的繫結），且指定型別的完整限定的方法的指標。

- 它擁有稱為 `Invoke` 的方法，其簽章與宣告的委派簽章相符。

叫用委派時，其函式會呼叫它們所附加的順序。

委派的傳回值是從其最後一個附加的成員函式的傳回值。

委派無法多載。

委派可以繫結或解除繫結。

當您具現化繫結的委派時，第一個引數都應該是物件參考。 委派具現化的第二個引數必須是實值類型的方法是方法的 managed 的類別物件或指標的位址。 委派具現化的第二個引數必須具有完整的類別範圍語法方法命名，並套用傳址運算子。

當您具現化繫結的委派時，第一個引數必須是方法的 managed 的類別物件或方法的實值類型的指標的位址。 引數必須具有完整的類別範圍語法方法命名，並套用傳址運算子。

當建立靜態或全域函式的委派，只能有一個參數是必要： 函式 （選擇性，函式的位址）。

如需有關委派的詳細資訊，請參閱

- [如何：定義和使用委派 (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [泛型委派 (C + + /cli CLI)](../windows/generic-delegates-visual-cpp.md)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

下列範例示範如何宣告、 初始化及叫用委派。

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

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)