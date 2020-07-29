---
title: 參考類型的 C++ 堆疊語意
ms.date: 11/04/2016
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
ms.openlocfilehash: 886d0d16d8b81364078db5604ab10d8dcc3fa561
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197835"
---
# <a name="c-stack-semantics-for-reference-types"></a>參考類型的 C++ 堆疊語意

在 Visual Studio 2005 之前，只能使用運算子來建立參考型別的實例 **`new`** ，而這會在垃圾收集堆積上建立物件。 不過，您現在可以使用與您用來在堆疊上建立原生類型之執行個體相同的語法建立參考類型的執行個體。 因此，您不需要使用[ref new、gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)來建立參考型別的物件。 然後，當物件超出範圍時，編譯器會呼叫物件的解構函式。

## <a name="remarks"></a>備註

當您使用堆疊語義建立參考型別的實例時，編譯器會在內部于垃圾收集堆積上建立實例（使用 **`gcnew`** ）。

當函式的簽章或傳回型別是一個傳值參考類型的執行個體時，函式在中繼資料中會被標記為需要進行特殊處理 (使用 modreq)。 這項特殊處理目前只提供給 Visual C++ 用戶端使用，其他語言目前不支援使用以堆疊語意建立之參考類型的函式或資料。

**`gcnew`** 如果類型沒有任何析構函式，則使用（動態配置）而非堆疊語義的其中一個原因是。 此外，如果想要讓 Visual C++ 以外的語言使用函式，則無法在函式簽章中使用以堆疊語意建立的參考類型。

編譯器不會為參考類型產生複製建構函式。 因此，如果您在簽章中定義了一個使用傳值參考類型的函式，則必須定義參考類型的複製建構函式。 參考類型的複製建構函式具有下列形式的簽章：`R(R%){}`。

編譯器不會為參考類型產生預設指派運算子。 指派運算子可讓您建立使用堆疊語意的物件，並以使用堆疊語意建立的現有物件對其進行初始化。 參考類型的指派運算子具有下列形式的簽章：`void operator=( R% ){}`。

如果您的型別的「析構函式」釋放重要資源，而且您對引用型別使用堆疊語義，則不需要明確地呼叫「析構函式」（或呼叫 **`delete`** ）。 如需參考型別中之析構函數的詳細資訊，請參閱[如何：定義和使用類別和結構（c + +/cli）中的析構函數和完成項](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。

由編譯器產生的指派運算子會遵循一般的標準 C++ 規則，並提供下列新增功能：

- 類型為參考類型之控制代碼的任何非靜態資料成員將會進行淺層複製 (視為指標類型的非靜態資料成員)。

- 類型為實值類型的任何非靜態資料成員都會進行淺層複製。

- 類型為參考類型之執行個體的任何非靜態資料成員都會叫用參考類型之複製建構函式的呼叫。

編譯器也提供 `%` 一元運算子，可將使用堆疊語意建立之參考類型的執行個體轉換為其基礎控制代碼類型。

下列參考類型不能與堆疊語意搭配使用：

- [delegate (C++ 元件擴充功能)](../extensions/delegate-cpp-component-extensions.md)

- [陣列](../extensions/arrays-cpp-component-extensions.md)

- <xref:System.String>

## <a name="example"></a>範例

### <a name="description"></a>描述

下列程式碼範例說明如何使用堆疊語意宣告參考類型的執行個體、指派運算子和複製建構函式的運作方式，以及如何初始化使用堆疊語意建立之參考類型的追蹤參考。

### <a name="code"></a>程式碼

```cpp
// stack_semantics_for_reference_types.cpp
// compile with: /clr
ref class R {
public:
   int i;
   R(){}

   // assignment operator
   void operator=(R% r) {
      i = r.i;
   }

   // copy constructor
   R(R% r) : i(r.i) {}
};

void Test(R r) {}   // requires copy constructor

int main() {
   R r1;
   r1.i = 98;

   R r2(r1);   // requires copy constructor
   System::Console::WriteLine(r1.i);
   System::Console::WriteLine(r2.i);

   // use % unary operator to convert instance using stack semantics
   // to its underlying handle
   R ^ r3 = %r1;
   System::Console::WriteLine(r3->i);

   Test(r1);

   R r4;
   R r5;
   r5.i = 13;
   r4 = r5;   // requires a user-defined assignment operator
   System::Console::WriteLine(r4.i);

   // initialize tracking reference
   R % r6 = r4;
   System::Console::WriteLine(r6.i);
}
```

### <a name="output"></a>輸出

```Output
98
98
98
13
13
```

## <a name="see-also"></a>另請參閱

[類別和結構](../extensions/classes-and-structs-cpp-component-extensions.md)
