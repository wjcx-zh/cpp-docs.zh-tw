---
title: '&lt;returns&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- returns C++ XML tag
- <returns> C++ XML tag
ms.assetid: 5e3b0ed9-838d-4953-a93e-76d2d0a19fb9
ms.openlocfilehash: 7861d57d474db3c45b2c773a057a545c15602822
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740853"
---
# <a name="ltreturnsgt-visual-c"></a>&lt;returns&gt; (Visual C++)

\<returns> 標記應該用於方法宣告的註解中，以描述傳回值。

## <a name="syntax"></a>語法

```
<returns>description</returns>
```

#### <a name="parameters"></a>參數

*description*<br/>
傳回值的描述。

## <a name="remarks"></a>備註

編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。

## <a name="example"></a>範例

```
// xml_returns_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_returns_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <returns>Returns zero.</returns>
   int GetZero() { return 0; }
};
```

## <a name="see-also"></a>另請參閱

[XML 文件](../ide/xml-documentation-visual-cpp.md)
