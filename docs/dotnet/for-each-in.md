---
title: for each, in
description: C + +/CLI 適用于語句說明和範例中的每個。
ms.date: 09/25/2020
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
ms.openlocfilehash: 7f228a773dfcbe791e26ea3e1bd8cfba7f3ab028
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413915"
---
# <a name="for-each-in"></a>for each, in

逐一查看陣列或集合。 此非標準關鍵字在 C++/CLI 和原生 C++ 專案中皆可用。 但是，不建議使用它。 請考慮改用以標準 [範圍為基礎的 For 語句 (c + +) ](../cpp/range-based-for-statement-cpp.md) 。

## <a name="all-runtimes"></a>所有執行階段

### <a name="syntax"></a>語法

> 針對*運算式***中****的每個 (** *類型**識別碼* **) {**\
> &nbsp;&nbsp;&nbsp;&nbsp;*語句*\
> **}**

### <a name="parameters"></a>參數

*type*<br/>
`identifier` 的類型。

*識別碼*<br/>
表示集合項目的反覆項目變數。  當 `identifier` 是 [追蹤參考運算子](../extensions/tracking-reference-operator-cpp-component-extensions.md)時，您可以修改元素。

*expression*<br/>
陣列運算式或集合。 集合項目必須如此，編譯器才能將其轉換為 `identifier` 類型。

*語句*<br/>
要執行的一個或多個陳述式。

### <a name="remarks"></a>備註

`for each` 陳述式可用來逐一查看集合。 您可以修改集合中的元素，但無法新增或刪除專案。

系統會針對陣列或集合中的每個元素執行這些 *語句* 。 在完成集合中所有項目的反覆項目之後，程式控制權會轉移到 `for each` 區塊之後的下一個陳述式。

`for each` 和 `in` 都是 [內容相關的關鍵字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="requirements"></a>規格需求

編譯器選項： **/ZW**

### <a name="example"></a>範例

本範例示範如何使用 `for each` 逐一查看字串。

```cpp
// for_each_string1.cpp
// compile with: /ZW
#include <stdio.h>
using namespace Platform;

ref struct MyClass {
   property String^ MyStringProperty;
};

int main() {
   String^ MyString = ref new String("abcd");

   for each ( char c in MyString )
      wprintf("%c", c);

   wprintf("/n");

   MyClass^ x = ref new MyClass();
   x->MyStringProperty = "Testing";

   for each( char c in x->MyStringProperty )
      wprintf("%c", c);
}
```

```Output
abcd

Testing
```

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>備註

CLR 語法與 **所有運行** 時間語法相同，不同之處如下。

*expression*<br/>
Managed 陣列運算式或集合。 Collection 元素必須如此，編譯器才能將它從轉換成 <xref:System.Object> *識別碼* 型別。

*運算式* 會評估為型別，這個型別會定義方法，這個型別會傳回型別，而該型別會傳回實 <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> 或宣告 `GetEnumerator` <xref:System.Collections.IEnumerator> 中定義的所有方法 `IEnumerator` 。

### <a name="requirements"></a>規格需求

編譯器選項： **/clr**

### <a name="example"></a>範例

本範例示範如何使用 `for each` 逐一查看字串。

```cpp
// for_each_string2.cpp
// compile with: /clr
using namespace System;

ref struct MyClass {
   property String ^ MyStringProperty;
};

int main() {
   String ^ MyString = gcnew String("abcd");

   for each ( Char c in MyString )
      Console::Write(c);

   Console::WriteLine();

   MyClass ^ x = gcnew MyClass();
   x->MyStringProperty = "Testing";

   for each( Char c in x->MyStringProperty )
      Console::Write(c);
}
```

```Output
abcd

Testing
```

## <a name="see-also"></a>另請參閱

[執行時間平臺的元件擴充功能](../extensions/component-extensions-for-runtime-platforms.md)\
[以範圍為基礎的 for 語句 (c + +) ](../cpp/range-based-for-statement-cpp.md)
