---
title: ptr::CreateInstance |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr.CreateInstance
- msclr::com::ptr::CreateInstance
- msclr.com.ptr.CreateInstance
- ptr::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- ptr::CreateInstance
ms.assetid: 9e8e4c4c-1651-4839-8829-5857d74470fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 56034267c40e34c2a88295e27372b96c8d32b675
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409736"
---
# <a name="ptrcreateinstance"></a>ptr::CreateInstance

建立 COM 物件內的執行個體`com::ptr`。

## <a name="syntax"></a>語法

```
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   System::String ^ progid
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   const wchar_t * progid
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter
);
void CreateInstance(
   REFCLSID rclsid
);
```

#### <a name="parameters"></a>參數

*progid*<br/>
`ProgID` 字串。

*pouter*<br/>
(Controlling IUnknown) 的彙總物件的 IUnknown 介面指標。 如果`pouter`未指定，`NULL`用。

*cls_context*<br/>
管理新建立的物件的程式碼將在其中執行的內容。 值取自`CLSCTX`列舉型別。 如果`cls_context`未指定，則在使用 CLSCTX_ALL 的值。

*rclsid*<br/>
`CLSID` 相關聯的資料和將用來建立物件的程式碼。

## <a name="exceptions"></a>例外狀況

如果`com::ptr`已經擁有的 COM 物件的參考`CreateInstance`就會擲回<xref:System.InvalidOperationException>。

此函式會呼叫`CoCreateInstance`並用<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>要轉換的任何錯誤`HRESULT`至適當的例外狀況。

## <a name="remarks"></a>備註

`CreateInstance` 使用`CoCreateInstance`建立指定的物件，識別從 ProgID 或 CLSID 的新執行個體。 `com::ptr`參考新建立的物件，並會自動釋放所有已擁有在解構時的參考。

## <a name="example"></a>範例

這個範例實作 CLR 類別，此類別使用 `com::ptr` 來包裝其私用成員 `IXMLDOMDocument` 物件。 類別建構函式使用兩種不同形式的`CreateInstance`ProgID 或 CLSID 加上 CLSCTX 建立文件物件。

```
// comptr_createinstance.cpp
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
   XmlDocument(REFCLSID clsid, DWORD clsctx) {
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc1("Msxml2.DOMDocument.3.0");

      // or from a clsid with specific CLSCTX
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

## <a name="requirements"></a>需求

**標頭檔** \<msclr\com\ptr.h >

**命名空間**msclr::com

## <a name="see-also"></a>另請參閱

[ptr 成員](../dotnet/ptr-members.md)