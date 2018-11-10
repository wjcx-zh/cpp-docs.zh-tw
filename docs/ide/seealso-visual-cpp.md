---
title: '&lt;seealso&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: 788c2502574cb06ee92a4ef7341eae4868211fda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517776"
---
# <a name="ltseealsogt-visual-c"></a>&lt;seealso&gt; (Visual C++)

\<seealso> 標記可讓您指定要顯示在＜請參閱＞一節中的文字。 使用 [\<see>](../ide/see-visual-cpp.md)，以在文字內指定連結。

## <a name="syntax"></a>語法

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>參數

*成員*<br/>
可從目前編譯環境呼叫的成員或欄位參考。  以單引號或雙引號將名稱括起來。

編譯器會檢查指定的程式碼項目是否存在，並將 `member` 解析為輸出 XML 中的項目名稱。  如果編譯器找不到 `member`，它會發出警告。

如需如何建立泛型型別 cref 參考的資訊，請參閱[\<see>](../ide/see-visual-cpp.md)。

## <a name="remarks"></a>備註

編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。

如需使用 \<seealso> 的範例，請參閱 [\<summary>](../ide/summary-visual-cpp.md)。

Visual C++ 編譯器會透過文件註解嘗試一次解決 cref 參考。  因此，如果使用 C++ 查閱規則，當編譯器找不到符號時，參考就會被標記為無法解析。

## <a name="example"></a>範例

在下列範例中，cref 中參考了無法解析的符號。 B::Test 之 cref 的 XML 註解會是 `<seealso cref="!:B::Test" />`，而 A::Test 的參考是語式正確的 `<seealso cref="M:A.Test" />`。

```
// xml_seealso_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_seealso_tag.dll

/// Text for class A.
public ref struct A {
   /// <summary><seealso cref="A::Test"/>
   /// <seealso cref="B::Test"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void Test() {}
};

/// Text for class B.
public ref struct B {
   void Test() {}
};
```

## <a name="see-also"></a>請參閱

[XML 文件](../ide/xml-documentation-visual-cpp.md)