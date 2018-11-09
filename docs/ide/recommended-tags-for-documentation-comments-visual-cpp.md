---
title: 建議使用的文件註解標記 (Visual C++)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 251baedbf37901a58b34b66b7a10bbdcf5d66557
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564186"
---
# <a name="recommended-tags-for-documentation-comments-visual-c"></a>建議使用的文件註解標記 (Visual C++)

Visual C++ 編譯器將會處理您程式碼中的文件註解，並為每個編譯單位建立 .xdc 檔案，而 xdcmake.exe 會將 .xdc 檔處理成 .xml 檔。 處理 .xml 檔以建立文件是必須在您網站實作的細部工作。

標記是在類型和類型成員這類建構上處理。

標記必須緊接在類型或成員之前。

> [!NOTE]
>  文件註解無法套用至命名空間，或針對屬性和事件的非常規定義；文件註解必須是針對類別內宣告。

編譯器會處理任何為有效 XML 的標記。 下列標記提供使用者文件中的常用功能：

||||
|-|-|-|
|[\<c>](../ide/c-visual-cpp.md)|[\<code>](../ide/code-visual-cpp.md)|[\<example>](../ide/example-visual-cpp.md)|
|[\<exception>](../ide/exception-visual-cpp.md)1|[\<include>](../ide/include-visual-cpp.md)1|[\<list>](../ide/list-visual-cpp.md)|
|[\<para>](../ide/para-visual-cpp.md)|[\<param>](../ide/param-visual-cpp.md)1|[\<paramref>](../ide/paramref-visual-cpp.md)1|
|[\<permission>](../ide/permission-visual-cpp.md)1|[\<remarks>](../ide/remarks-visual-cpp.md)|[\<returns>](../ide/returns-visual-cpp.md)|
|[\<see>](../ide/see-visual-cpp.md)1|[\<seealso>](../ide/seealso-visual-cpp.md)1|[\<summary>](../ide/summary-visual-cpp.md)|
|[\<value>](../ide/value-visual-cpp.md)|||

1. 編譯器會驗證語法。

在目前版本中，Visual C++ 編譯器不支援 `<paramref>`，其他 Visual Studio 編譯器支援此標記。 Visual C++ 可能在未來的版本支援 `<paramref>`。

## <a name="see-also"></a>請參閱

[XML 文件](../ide/xml-documentation-visual-cpp.md)