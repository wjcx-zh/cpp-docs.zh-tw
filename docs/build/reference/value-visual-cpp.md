---
title: '&lt;值 > （c + + 文件註解）'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: c0863b41791254992d16d373328ff6c8a5d6f94f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824777"
---
# <a name="ltvaluegt"></a>&lt;value&gt;

\<value> 標記可讓您描述屬性和屬性存取子方法。 請注意，當您在 Visual Studio 整合式開發環境中使用程式碼精靈新增屬性時，會新增新屬性的 [\<summary>](summary-visual-cpp.md) 標記。 您接著應該手動新增 \<value> 標記，來描述屬性所代表的值。

## <a name="syntax"></a>語法

```
<value>property-description</value>
```

#### <a name="parameters"></a>參數

*property-description*<br/>
屬性的描述。

## <a name="remarks"></a>備註

編譯搭配 [/doc](doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。

## <a name="example"></a>範例

```
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

## <a name="see-also"></a>另請參閱

[XML 文件](xml-documentation-visual-cpp.md)
