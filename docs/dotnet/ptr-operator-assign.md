---
title: "ptr::operator= | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ptr.operator="
  - "msclr.com.ptr.operator="
  - "msclr::com::ptr::operator="
  - "ptr::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator="
ms.assetid: 58619910-46c0-4db8-b183-c811b23b2df1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ptr::operator=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

附加至 `com::ptr`的 COM 物件。  
  
## 語法  
  
```  
ptr<_interface_type> % operator=(  
   _interface_type * _right  
);  
```  
  
#### 參數  
 `_right`  
 COM 介面要附加的指標。  
  
## 傳回值  
 在 `com::ptr`的追蹤參考。  
  
## 例外狀況  
 如果 `com::ptr` 已經擁有對 COM 物件的參考， `operator=` 會擲回 <xref:System.InvalidOperationException>。  
  
## 備註  
 指派 COM 物件給 `com::ptr` 參考 COM 物件，但是不會釋放它呼叫端的參考。  
  
 這個運算子的作用與 `Attach`相同。  
  
## 範例  
 這個範例會使用 `com::ptr` 包裝其私用成員 `IXMLDOMDocument` 物件的 CLR 類別。`ReplaceDocument` 成員函式第一次在任何先前的物件呼叫 `Release`，然後使用 `operator=` 附加新的文件物件。  
  
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
  
## 需求  
 **標頭檔**\<msclr \\ com \\ ptr.h\>  
  
 **命名空間** msclr::com  
  
## 請參閱  
 [ptr 成員](../dotnet/ptr-members.md)   
 [ptr::Attach](../dotnet/ptr-attach.md)   
 [ptr::Detach](../dotnet/ptr-detach.md)   
 [ptr::Release](../dotnet/ptr-release.md)