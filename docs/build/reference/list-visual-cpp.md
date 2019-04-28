---
title: '&lt;清單 > (C++文件註解)'
ms.date: 11/04/2016
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
ms.openlocfilehash: fd5b97ac518bc4075697da7b6ed88ed46bdd8814
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305264"
---
# <a name="ltlistgt"></a>&lt;list&gt;

\<listheader> 區塊用來定義資料表或定義清單的標題資料列。 定義資料表時，您只需要提供標題中詞彙的項目。

## <a name="syntax"></a>語法

```
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

*term*<br/>
要定義的詞彙，可定義於 `description` 中。

*description*<br/>
項目符號或編號清單中的項目或者 `term` 的定義。

## <a name="remarks"></a>備註

清單中的每個項目都是使用 \<item> 區塊所指定。 建立定義清單時，您需要同時指定 `term` 和 `description`。 不過，針對資料表、項目符號清單或編號清單，您只需要提供 `description` 的項目。

清單或資料表可以有所需的多個 \<item> 區塊。

編譯搭配 [/doc](doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。

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

[XML 文件](xml-documentation-visual-cpp.md)
