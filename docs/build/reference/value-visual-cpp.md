---
title: '&lt;值 > （C++檔批註）'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: de84d1faca59a6c8e4f82fba3605cbd54a05bd2e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988589"
---
# <a name="ltvaluegt"></a>&lt;值&gt;

\<value> 標記可讓您描述屬性和屬性存取子方法。 請注意，當您在 Visual Studio 整合式開發環境中使用程式碼精靈新增屬性時，會新增新屬性的 [\<summary>](summary-visual-cpp.md) 標記。 您接著應該手動新增 \<value> 標記，來描述屬性所代表的值。

## <a name="syntax"></a>語法

```
<value>property-description</value>
```

#### <a name="parameters"></a>參數

*property-description*<br/>
屬性的描述。

## <a name="remarks"></a>備註

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 編譯，可處理檔案的文件註解。

## <a name="example"></a>範例

```cpp
// xml_value_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_value_tag.dll
using namespace System;
/// Text for class Employee.
public ref class Employee {
private:
   String ^ name;
   /// <value>Name accesses the value of the name data member</value>
public:
   property String ^ Name {
      String ^ get() {
         return name;
      }
      void set(String ^ i) {
         name = i;
      }
   }
};
```

## <a name="see-also"></a>請參閱

[XML 文件](xml-documentation-visual-cpp.md)
