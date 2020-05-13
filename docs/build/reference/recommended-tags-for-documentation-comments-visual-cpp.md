---
title: 文件註解的建議標籤 (C++文件註解)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 1648d0eb019a3aad25641d7f6a7edd1ba26acf7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336164"
---
# <a name="recommended-tags-for-documentation-comments"></a>建議使用的文件註解標籤

MSVC 編譯器將處理代碼中的文檔註釋,並為每個編譯和創建一個 .xdc 檔,xdcmake.exe 將處理 .xdc 檔到 .xml 檔案。 處理 .xml 檔以建立文件是必須在您網站實作的細部工作。

標記是在類型和類型成員這類建構上處理。

標記必須緊接在類型或成員之前。

> [!NOTE]
> 文件註解無法套用至命名空間，或針對屬性和事件的非常規定義；文件註解必須是針對類別內宣告。

編譯器會處理任何為有效 XML 的標記。 下列標記提供使用者文件中的常用功能：

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<代碼>](code-visual-cpp.md)|[\<範例>](example-visual-cpp.md)|
|例外>[ \< ](exception-visual-cpp.md) 1|包括>[ \< ](include-visual-cpp.md) 1|[\<清單>](list-visual-cpp.md)|
|[\<第>段](para-visual-cpp.md)|參數>[ \< ](param-visual-cpp.md) 1|[ \<>](paramref-visual-cpp.md)1|
|權限>[ \< ](permission-visual-cpp.md) 1|[\<評論>](remarks-visual-cpp.md)|[\<傳回>](returns-visual-cpp.md)|
|參見>[ \< ](see-visual-cpp.md) 1|另見>[ \< ](seealso-visual-cpp.md) 1|[\<摘要>](summary-visual-cpp.md)|
|[\<值>](value-visual-cpp.md)|||

1. 編譯器會驗證語法。

在當前版本中,MSVC 編譯器不`<paramref>`支援 ,該標記由其他 Visual Studio 編譯器支援。 Visual C++ 可能在未來的版本支援 `<paramref>`。

## <a name="see-also"></a>另請參閱

[XML 文件](xml-documentation-visual-cpp.md)
