---
title: '&lt;範例&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C++ XML tag
- example C++ XML tag
ms.assetid: c821aaa7-7ea7-4bee-9922-6705ad57f877
ms.openlocfilehash: b1511bb77b35b054d83a64c1a832843e62a8daa9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744016"
---
# <a name="ltexamplegt-visual-c"></a>&lt;範例&gt; (Visual C++)

\<example> 標記可讓您指定如何使用方法或其他程式庫成員的範例。 通常，這也會涉及使用 [\<程式碼>](../ide/code-visual-cpp.md) 標記。

## <a name="syntax"></a>語法

```
<example>description</example>
```

#### <a name="parameters"></a>參數

*description*<br/>
程式碼範例的描述。

## <a name="remarks"></a>備註

編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。

## <a name="example"></a>範例

```
// xml_example_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_example_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>
   /// GetZero method
   /// </summary>
   /// <example> This sample shows how to call the GetZero method.
   /// <code>
   /// int main()
   /// {
   ///    return GetZero();
   /// }
   /// </code>
   /// </example>
   static int GetZero() {
      return 0;
   }
};
```

## <a name="see-also"></a>另請參閱

[XML 文件](../ide/xml-documentation-visual-cpp.md)
