---
title: '&lt;例外狀況 >C++ （檔批註）'
ms.date: 11/04/2016
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: d56e0ce7c892cfd9fd909b5268043d77929bd43c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439870"
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;

\<exception> 標記可讓您指定可以擲回的例外狀況。 此標記會套用到方法定義。

## <a name="syntax"></a>語法

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>參數

*成員*<br/>
可從目前編譯環境取得之例外狀況的參考。 使用名稱查閱規則，編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。  如果編譯器找不到 `member`，它會發出警告。

以單引號或雙引號將名稱括起來。

如需如何建立泛型型別 cref 參考的資訊，請參閱[\<see>](see-visual-cpp.md)。

*description*<br/>
描述。

## <a name="remarks"></a>備註

編譯搭配 [/doc](doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。

MSVC 編譯器會嘗試透過檔批註來解析一次中的 cref 參考。  因此，如果使用 C++ 查閱規則，當編譯器找不到符號時，參考就會被標記為無法解析。 如需詳細資訊，請參閱 [\<seealso>](seealso-visual-cpp.md)。

## <a name="example"></a>範例

```cpp
// xml_exception_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_exception_tag.dll
using namespace System;

/// Text for class EClass.
public ref class EClass : public Exception {
   // class definition ...
};

/// <exception cref="System.Exception">Thrown when... .</exception>
public ref class TestClass {
   void Test() {
      try {
      }
      catch(EClass^) {
      }
   }
};
```

## <a name="see-also"></a>另請參閱

[XML 文件](xml-documentation-visual-cpp.md)
