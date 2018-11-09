---
title: '&lt;see&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: f5fa63f2dbd97f0a2da98a5a31a1192e40599738
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461356"
---
# <a name="ltseegt-visual-c"></a>&lt;see&gt; (Visual C++)

\<see> 標記可讓您在文字內指定連結。 使用 [\<seealso>](../ide/seealso-visual-cpp.md) 表示要顯示在＜另請參閱＞一節中的文字。

## <a name="syntax"></a>語法

```
<see cref="member"/>
```

#### <a name="parameters"></a>參數

*成員*<br/>
可從目前編譯環境呼叫的成員或欄位參考。  以單引號或雙引號將名稱括起來。

編譯器會檢查指定的程式碼項目是否存在，並將 `member` 解析為輸出 XML 中的項目名稱。  如果編譯器找不到 `member`，它會發出警告。

## <a name="remarks"></a>備註

編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。

如需使用 \<see> 的範例，請參閱 [\<summary>](../ide/summary-visual-cpp.md)。

Visual C++ 編譯器會透過文件註解嘗試一次解決 cref 參考。  因此，如果使用 C++ 查閱規則，當編譯器找不到符號時，參考就會被標記為無法解析。 如需詳細資訊，請參閱 [\<seealso>](../ide/seealso-visual-cpp.md)。

## <a name="example"></a>範例

下列範例示範如何建立泛型型別的 cref 參考，如此一來，編譯器就會解析參考。

```
// xml_see_cref_example.cpp
// compile with: /LD /clr /doc
// the following cref shows how to specify the reference, such that,
// the compiler will resolve the reference
/// <see cref="C{T}">
/// </see>
ref class A {};

// the following cref shows another way to specify the reference,
// such that, the compiler will resolve the reference
/// <see cref="C < T >"/>

// the following cref shows how to hard-code the reference
/// <see cref="T:C`1">
/// </see>
ref class B {};

/// <see cref="A">
/// </see>
/// <typeparam name="T"></typeparam>
generic<class T>
ref class C {};
```

## <a name="see-also"></a>請參閱

[XML 文件](../ide/xml-documentation-visual-cpp.md)