---
title: '建議使用的檔註解標記 (c + + 檔批註) '
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 9f41e450215e2bce02dbaf66910fc2fc1a131a99
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836851"
---
# <a name="recommended-tags-for-documentation-comments"></a>建議使用的文件註解標籤

MSVC 編譯器將會處理您程式碼中的檔批註，並為每個編譯單位建立一個 .xdc 檔案，而且 xdcmake.exe 會將 .xdc 檔案處理成 .xml 檔案。 處理 .xml 檔以建立文件是必須在您網站實作的細部工作。

標記是在類型和類型成員這類建構上處理。

標記必須緊接在類型或成員之前。

> [!NOTE]
> 文件註解無法套用至命名空間，或針對屬性和事件的非常規定義；文件註解必須是針對類別內宣告。

編譯器會處理任何為有效 XML 的標記。 下列標記提供使用者文件中的常用功能：

[`<c>`](c-visual-cpp.md)
[`<code>`](code-visual-cpp.md)
[`<example>`](example-visual-cpp.md)
[`<exception>`](exception-visual-cpp.md)<sup>1</sup> 
 1 [`<include>`](include-visual-cpp.md)<sup>1</sup> 
 [`<list>`](list-visual-cpp.md) 1 
 [`<para>`](para-visual-cpp.md) 
 [`<param>`](param-visual-cpp.md)<sup>1</sup> 
 1 [`<paramref>`](paramref-visual-cpp.md)<sup>1</sup> 
 1 [`<permission>`](permission-visual-cpp.md)<sup>1</sup> 
 [`<remarks>`](remarks-visual-cpp.md) 1 
 [`<returns>`](returns-visual-cpp.md) 
 [`<see>`](see-visual-cpp.md)<sup>1</sup> 
 1 [`<seealso>`](seealso-visual-cpp.md)<sup>1</sup>
[`<summary>`](summary-visual-cpp.md)
[`<value>`](value-visual-cpp.md)

1. 編譯器會驗證語法。

在目前的版本中，MSVC 編譯器不支援 `<paramref>` ，其他 Visual Studio 編譯器支援的標記。 Visual C++ 可能在未來的版本支援 `<paramref>`。

## <a name="see-also"></a>另請參閱

[XML 文件](xml-documentation-visual-cpp.md)
