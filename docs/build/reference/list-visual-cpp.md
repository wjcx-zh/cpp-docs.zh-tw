---
title: '&lt;列出> (c + + 檔批註) '
ms.date: 11/04/2016
f1_keywords:
- list
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: 24f9b17c67b8f951743fd51c04266b05dad235c7
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041961"
---
# <a name="ltlistgt-and-ltlistheadergt"></a>&lt;列出 &gt; 和 &lt; listheader&gt;

\<listheader>區塊是用來定義資料表或定義清單的標題資料列。 定義資料表時，您只需要提供標題中詞彙的項目。

## <a name="syntax"></a>語法

```xml
<list type="bullet" | "number" | "table">
   <listheader>
      <term>term</term>
      <description>description</description>
   </listheader>
   <item>
      <term>term</term>
      <description>description</description>
   </item>
</list>
```

#### <a name="parameters"></a>參數

*術語*<br/>
要定義的詞彙，可定義於 `description` 中。

*description*<br/>
項目符號或編號清單中的項目或者 `term` 的定義。

## <a name="remarks"></a>備註

清單中的每個專案都是以 \<item> 區塊來指定。 建立定義清單時，您需要同時指定 `term` 和 `description`。 不過，針對資料表、項目符號清單或編號清單，您只需要提供 `description` 的項目。

清單或資料表可以視需要擁有多個 \<item> 區塊。

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 編譯，可處理檔案的文件註解。

## <a name="example"></a>範例

```cpp
// xml_list_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_list_tag.dll
/// <remarks>Here is an example of a bulleted list:
/// <list type="bullet">
/// <item>
/// <description>Item 1.</description>
/// </item>
/// <item>
/// <description>Item 2.</description>
/// </item>
/// </list>
/// </remarks>
class MyClass {};
```

## <a name="see-also"></a>另請參閱

[XML 檔](xml-documentation-visual-cpp.md)
