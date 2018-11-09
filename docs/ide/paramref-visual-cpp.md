---
title: '&lt;paramref&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- paramref C++ XML tag
- <paramref> C++ XML tag
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
ms.openlocfilehash: 32ed64bc4d76e75dc7de47f8f3bd3c7ab5823cdc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586299"
---
# <a name="ltparamrefgt-visual-c"></a>&lt;paramref&gt; (Visual C++)

\<paramref> 標記可讓您指出某個單字是參數。 可以處理 .xml 檔案，以醒目的方式格式化此參數。

## <a name="syntax"></a>語法

```
<paramref name="name"/>
```

#### <a name="parameters"></a>參數

*name*<br/>
要參考的參數名稱。  以單引號或雙引號將名稱括起來。  如果編譯器找不到 `name`，它會發出警告。

## <a name="remarks"></a>備註

編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。

## <a name="example"></a>範例

```
// xml_paramref_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_paramref_tag.dll
/// Text for class MyClass.
public ref class MyClass {
   /// <summary>MyMethod is a method in the MyClass class.
   /// The <paramref name="Int1"/> parameter takes a number.
   /// </summary>
   void MyMethod(int Int1) {}
};
```

## <a name="see-also"></a>請參閱

[XML 文件](../ide/xml-documentation-visual-cpp.md)