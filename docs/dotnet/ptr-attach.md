---
title: "ptr::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::com::ptr::Attach"
  - "ptr::Attach"
  - "ptr.Attach"
  - "msclr.com.ptr.Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach 方法"
ms.assetid: 81d930de-cb2a-4c30-9bd6-94d65942c47a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ptr::Attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

附加至 `com::ptr`的 COM 物件。  
  
## 語法  
  
```  
void Attach(  
   _interface_type * _right  
);  
```  
  
#### 參數  
 `_right`  
 COM 介面要附加的指標。  
  
## 例外狀況  
 如果 `com::ptr` 已經擁有對 COM 物件的參考， `Attach` 會擲回 <xref:System.InvalidOperationException>。  
  
## 備註  
 呼叫 `Attach` 的方式參考 COM 物件，但是不會釋放它的呼叫端的參考。  
  
 傳遞 `NULL` 給 `Attach` 產生不會採取的動作。  
  
## 範例  
 這個範例會使用 `com::ptr` 包裝其私用成員 `IXMLDOMDocument` 物件的 CLR 類別。  在任何的 `ReplaceDocument` 成員函式會先呼叫 `Release` 之前主控物件接著會呼叫 `Attach` 附加新的資料物件。  
  
```  
// comptr_attach.cpp  
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
      m_ptrDoc.Attach(pDoc);  
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
      // store it in place of the one held by our ref class  
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
  
## 需求  
 **標頭檔**\<msclr \\ com \\ ptr.h\>  
  
 **命名空間** msclr::com  
  
## 請參閱  
 [ptr 成員](../dotnet/ptr-members.md)   
 [ptr::operator\=](../dotnet/ptr-operator-assign.md)   
 [ptr::Release](../dotnet/ptr-release.md)