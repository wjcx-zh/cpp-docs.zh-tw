---
title: for each, in
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
ms.openlocfilehash: f1f5523eb22bd8a839da9b3f73dd6c3718b4fd63
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825785"
---
# <a name="for-each-in"></a>for each, in

逐一查看陣列或集合。 此非標準關鍵字在 C++/CLI 和原生 C++ 專案中皆可用。 但是，不建議使用。 請考慮改用以標準[範圍為基礎的 For 語句（c + +）](../cpp/range-based-for-statement-cpp.md) 。

## <a name="all-runtimes"></a>所有執行階段

### <a name="syntax"></a>語法

> **針對每個（** *運算式***中**的*類型**識別碼* **） {**\
> &nbsp;&nbsp;&nbsp;&nbsp;*報表*\
> **}**

### <a name="parameters"></a>參數

*type*<br/>
`identifier` 的類型。

*識別碼 (identifier)*<br/>
表示集合項目的反覆項目變數。  當`identifier`是[追蹤參考運算子](../extensions/tracking-reference-operator-cpp-component-extensions.md)時，您可以修改元素。

*expression*<br/>
陣列運算式或集合。 集合項目必須如此，編譯器才能將其轉換為 `identifier` 類型。

*報表*<br/>
要執行的一個或多個陳述式。

### <a name="remarks"></a>備註

`for each` 陳述式可用來逐一查看集合。 您可以修改集合中的項目，不過，您無法加入或刪除項目。

系統會針對陣列或集合中的每個元素執行*語句*。 在完成集合中所有項目的反覆項目之後，程式控制權會轉移到 `for each` 區塊之後的下一個陳述式。

`for each`和`in`都是[內容相關的關鍵字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。

如需詳細資訊：

- [使用 for each 反覆查看 C++ 標準程式庫集合](../dotnet/iterating-over-stl-collection-by-using-for-each.md)

- [如何：使用 for each 反覆查看陣列](../dotnet/how-to-iterate-over-arrays-with-for-each.md)

- [如何：使用 for each 反覆查看泛型集合](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)

- [如何：使用 for each 反覆查看使用者定義的集合](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="requirements"></a>需求

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

**輸出**

```Output
abcd

Testing
```

## <a name="common-language-runtime"></a>Common Language Runtime

**備註**

CLR 語法與**所有運行**時間語法相同，但如下所示。

*expression*<br/>
Managed 陣列運算式或集合。 集合元素必須是，編譯器才能將它從<xref:System.Object>轉換為*識別碼*類型。

*運算式*會評估為可執行檔<xref:System.Collections.IEnumerable>類型<xref:System.Collections.Generic.IEnumerable%601>，或定義`GetEnumerator`方法的類型，而此方法會傳回可執行<xref:System.Collections.IEnumerator>或宣告中`IEnumerator`所定義之所有方法的類型。

### <a name="requirements"></a>需求

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

**輸出**

```Output
abcd

Testing
```

## <a name="see-also"></a>請參閱

[執行階段平台的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)
