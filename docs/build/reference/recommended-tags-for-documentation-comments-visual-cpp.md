---
title: 建議的文件註解標記 (C++文件註解)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 2a6a2c3983c10579a6cd96b69be81aa7df8b8ee7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027892"
---
# <a name="recommended-tags-for-documentation-comments"></a>建議使用的文件註解標籤

MSVC 編譯器將會處理您的程式碼中的文件註解，並建立.xdc 檔案以供每個編譯模組中，而且 xdcmake.exe 會處理至.xml 檔案的.xdc 檔案。 處理 .xml 檔以建立文件是必須在您網站實作的細部工作。

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

目前的版本中，在 MSVC 編譯器不支援`<paramref>`，其他 Visual Studio 編譯器所支援的標記。 Visual C++ 可能在未來的版本支援 `<paramref>`。

## <a name="see-also"></a>另請參閱

[XML 文件](xml-documentation-visual-cpp.md)