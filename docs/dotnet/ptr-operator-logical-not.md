---
title: ptr::operator!
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ptr::operator!
- msclr::com::ptr::operator!
- ptr.operator!
- msclr.com.ptr.operator!
helpviewer_keywords:
- ptr::operator!
ms.assetid: 7f4101dc-2045-42e7-abb1-6a30e17147f2
ms.openlocfilehash: 8527afe20bf0b0896f2bd433b3dd3e4e8057357b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580891"
---
# <a name="ptroperator"></a>ptr::operator!

若要判斷是否擁有的 COM 物件無效的運算子。

## <a name="syntax"></a>語法

```
bool operator!();
```

## <a name="return-value"></a>傳回值

**true**自有的 COM 物件是否無效;**false**否則。

## <a name="remarks"></a>備註

擁有的 COM 物件時如果不是有效**nullptr**。

## <a name="example"></a>範例

這個範例實作 CLR 類別，此類別使用 `com::ptr` 來包裝其私用成員 `IXMLDOMDocument` 物件。  `CreateInstance`成員函式使用`operator!`以判斷文件物件被人擁有，且只會建立新的執行個體，如果物件是無效。

```cpp
// comptr_op_not.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) {
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```

## <a name="requirements"></a>需求

**標頭檔** \<msclr\com\ptr.h >

**命名空間**msclr::com

## <a name="see-also"></a>另請參閱

[ptr 成員](../dotnet/ptr-members.md)<br/>
[ptr::operator bool](../dotnet/ptr-operator-bool.md)