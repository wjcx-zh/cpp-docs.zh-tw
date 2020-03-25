---
title: 建議使用的檔註解標記C++ （檔批註）
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 4e0937b79012f65ba136e18ac81f014be23688f8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168859"
---
# <a name="recommended-tags-for-documentation-comments"></a>建議使用的文件註解標籤

MSVC 編譯器會處理您程式碼中的檔批註，並為每個編譯模組建立一個 .xdc 檔案，而 xdcmake 會將 .xdc 檔案處理成 .xml 檔案。 處理 .xml 檔以建立文件是必須在您網站實作的細部工作。

標記是在類型和類型成員這類建構上處理。

標記必須緊接在類型或成員之前。

> [!NOTE]
>  文件註解無法套用至命名空間，或針對屬性和事件的非常規定義；文件註解必須是針對類別內宣告。

編譯器會處理任何為有效 XML 的標記。 下列標記提供使用者文件中的常用功能：

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<code>](code-visual-cpp.md)|[\<example>](example-visual-cpp.md)|
|[\<exception>](exception-visual-cpp.md)1|[\<include>](include-visual-cpp.md)1|[\<list>](list-visual-cpp.md)|
|[\<para>](para-visual-cpp.md)|[\<param>](param-visual-cpp.md)1|[\<paramref>](paramref-visual-cpp.md)1|
|[\<permission>](permission-visual-cpp.md)1|[\<remarks>](remarks-visual-cpp.md)|[\<returns>](returns-visual-cpp.md)|
|[\<see>](see-visual-cpp.md)1|[\<seealso>](seealso-visual-cpp.md)1|[\<summary>](summary-visual-cpp.md)|
|[\<value>](value-visual-cpp.md)|||

1. 編譯器會驗證語法。

在目前的版本中，MSVC 編譯器不支援 `<paramref>`，也就是其他 Visual Studio 編譯器所支援的標記。 Visual C++ 可能在未來的版本支援 `<paramref>`。

## <a name="see-also"></a>另請參閱

[XML 文件](xml-documentation-visual-cpp.md)
