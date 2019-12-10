---
title: '&lt;備註 > （C++檔批註）'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: 096280526b12feff33377a705f7c03548a1f0f13
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988657"
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

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 編譯，可處理檔案的文件註解。

## <a name="example"></a>範例

```cpp
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

## <a name="see-also"></a>請參閱

[XML 文件](xml-documentation-visual-cpp.md)
