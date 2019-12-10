---
title: '&lt;seealso > （C++檔批註）'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: 698db2df462f561acd897d0d0e56b3106a915466
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988613"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

\<seealso> 標記可讓您指定要顯示在＜請參閱＞一節中的文字。 使用 [\<see>](see-visual-cpp.md)，以在文字內指定連結。

## <a name="syntax"></a>語法

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>參數

*成員*<br/>
可從目前編譯環境呼叫的成員或欄位參考。  以單引號或雙引號將名稱括起來。

編譯器會檢查指定的程式碼項目是否存在，並將 `member` 解析為輸出 XML 中的項目名稱。  如果編譯器找不到 `member`，它會發出警告。

如需如何建立泛型型別 cref 參考的資訊，請參閱[\<see>](see-visual-cpp.md)。

## <a name="remarks"></a>備註

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 編譯，可處理檔案的文件註解。

如需使用 \<seealso> 的範例，請參閱 [\<summary>](summary-visual-cpp.md)。

MSVC 編譯器會嘗試透過檔批註來解析一次中的 cref 參考。  因此，如果使用 C++ 查閱規則，當編譯器找不到符號時，參考就會被標記為無法解析。

## <a name="example"></a>範例

在下列範例中，cref 中參考了無法解析的符號。 B::Test 之 cref 的 XML 註解會是 `<seealso cref="!:B::Test" />`，而 A::Test 的參考是語式正確的 `<seealso cref="M:A.Test" />`。

```cpp
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

[XML 文件](xml-documentation-visual-cpp.md)
