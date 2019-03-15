---
title: '&lt;備註 > （c + + 文件註解）'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: 0d0c63d55de80f498498a6873dacb5e83fc956b7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824976"
---
# <a name="ltremarksgt"></a>&lt;remarks&gt;

\<remarks> 標記是用來新增類型的資訊，以補充使用 [\<summary>](summary-visual-cpp.md) 所指定的資訊。 這項資訊會顯示在[物件瀏覽器](/visualstudio/ide/viewing-the-structure-of-code)和程式碼結構 Web 報告中。

## <a name="syntax"></a>語法

```
<remarks>description</remarks>
```

#### <a name="parameters"></a>參數

*description*<br/>
成員的描述。

## <a name="remarks"></a>備註

編譯搭配 [/doc](doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。

## <a name="example"></a>範例

```
// xml_remarks_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_remarks_tag.dll

using namespace System;

/// <summary>
/// You may have some primary information about this class.
/// </summary>
/// <remarks>
/// You may have some additional information about this class.
/// </remarks>
public ref class MyClass {};
```

## <a name="see-also"></a>另請參閱

[XML 文件](xml-documentation-visual-cpp.md)
