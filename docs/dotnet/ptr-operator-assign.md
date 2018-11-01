---
title: ptr::operator=
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ptr.operator=
- msclr.com.ptr.operator=
- msclr::com::ptr::operator=
- ptr::operator=
helpviewer_keywords:
- operator=
ms.assetid: 58619910-46c0-4db8-b183-c811b23b2df1
ms.openlocfilehash: c127d2d599be48d4dc406f6e326211591cc8bc66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527916"
---
# <a name="ptroperator"></a>ptr::operator=

附加至 COM 物件`com::ptr`。

## <a name="syntax"></a>語法

```
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

#### <a name="parameters"></a>參數

*右方 （_r)*<br/>
要附加的 COM 介面指標。

## <a name="return-value"></a>傳回值

追蹤參考上的`com::ptr`。

## <a name="exceptions"></a>例外狀況

如果`com::ptr`已經擁有的 COM 物件的參考`operator=`就會擲回<xref:System.InvalidOperationException>。

## <a name="remarks"></a>備註

若要將 COM 物件指派`com::ptr`參考 COM 物件，但不會釋放呼叫者的參考。

此運算子具有相同的效果`Attach`。

## <a name="example"></a>範例

這個範例實作 CLR 類別，此類別使用 `com::ptr` 來包裝其私用成員 `IXMLDOMDocument` 物件。  `ReplaceDocument`成員函式會先呼叫`Release`任何先前擁有物件，然後使用`operator=`附加新的文件物件。

```
// comptr_op_assign.cpp
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
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc = pDoc;
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by the ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="requirements"></a>需求

**標頭檔** \<msclr\com\ptr.h >

**命名空間**msclr::com

## <a name="see-also"></a>另請參閱

[ptr 成員](../dotnet/ptr-members.md)<br/>
[ptr::Attach](../dotnet/ptr-attach.md)<br/>
[ptr::Detach](../dotnet/ptr-detach.md)<br/>
[ptr::Release](../dotnet/ptr-release.md)