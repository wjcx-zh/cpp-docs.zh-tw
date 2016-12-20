---
title: "ptr::~ptr | Microsoft Docs"
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
  - "msclr.com.ptr.~ptr"
  - "ptr.~ptr"
  - "msclr::com.ptr::~ptr"
  - "~ptr"
  - "ptr::~ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::~ptr"
ms.assetid: 5f644aa5-fe66-4992-a5f8-13ec1292c949
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ptr::~ptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

解構 `com::ptr`。  
  
## 語法  
  
```  
~ptr();  
```  
  
## 備註  
 在終結時，`com::ptr` 釋放所有它擁有對其 COM 物件的參考。  假設沒有其他參考會保存至 COM 物件， COM 物件將刪除而且其記憶體要釋放。  
  
## 範例  
 這個範例會使用 `com::ptr` 包裝其私用成員 `IXMLDOMDocument` 物件的 CLR 類別。在 `main` 函式中，兩個 `XmlDocument` 物件的解構函式將會在他們超出 `try` 區塊範圍時呼叫，造成構成 `com::ptr` 解構函式被呼叫，並釋放所有對 COM 物件的參考。  
  
```  
// comptr_dtor.cpp  
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
  
   // construct the internal com::ptr with a COM object  
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   IXMLDOMDocument* pDoc = NULL;  
  
   try {  
      // create an XML DOM document object  
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,   
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));  
      // construct the ref class with the COM object  
      XmlDocument doc1(pDoc);  
  
      // or create the class from a progid string  
      XmlDocument doc2("Msxml2.DOMDocument.3.0");  
   }  
   // doc1 and doc2 destructors are called when they go out of scope  
   // and the internal com::ptr releases its reference to the COM object  
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
 **標頭檔** \<msclr\\com\\ptr.h\>  
  
 **命名空間** msclr::com  
  
## 請參閱  
 [ptr 成員](../dotnet/ptr-members.md)   
 [ptr::ptr](../dotnet/ptr-ptr.md)   
 [ptr::CreateInstance](../dotnet/ptr-createinstance.md)