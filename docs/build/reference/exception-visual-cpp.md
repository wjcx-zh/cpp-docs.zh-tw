---
title: '&lt;例外狀況> (c + + 檔批註) '
ms.date: 11/04/2016
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: 7e4b2276ecf5f4f4c4c05b389eb98a0f572f8027
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042104"
---
# <a name="ltexceptiongt-tag"></a>&lt;例外狀況 &gt; 標記

\<exception>標記可讓您指定可擲回的例外狀況。 此標記會套用到方法定義。

## <a name="syntax"></a>語法

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>參數

*成員*<br/>
可從目前編譯環境取得之例外狀況的參考。 使用名稱查閱規則，編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。  如果編譯器找不到 `member`，它會發出警告。

以單引號或雙引號將名稱括起來。

如需如何建立泛型型別 cref 參考的詳細資訊，請參閱 [\<see>](see-visual-cpp.md) 。

*description*<br/>
描述。

## <a name="remarks"></a>備註

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 編譯，可處理檔案的文件註解。

MSVC 編譯器會嘗試透過檔批註來解析一個傳遞中的 cref 參考。  因此，如果使用 C++ 查閱規則，當編譯器找不到符號時，參考就會被標記為無法解析。 如需詳細資訊，請參閱 [\<seealso>](seealso-visual-cpp.md) 。

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

[XML 檔](xml-documentation-visual-cpp.md)
