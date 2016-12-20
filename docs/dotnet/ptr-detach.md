---
title: "ptr::Detach | Microsoft Docs"
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
  - "ptr.Detach"
  - "msclr.com.ptr.Detach"
  - "ptr::Detach"
  - "msclr::com::ptr::Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::Detach"
ms.assetid: 23370c8a-8f79-4880-9fa1-46e110c1a92c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ptr::Detach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

中止 COM 物件的擁有權，傳回物件指標。  
  
## 語法  
  
```  
_interface_type * Detach();  
```  
  
## 傳回值  
 COM 物件的指標。  
  
 如果物件不被擁有，則會傳回 null。  
  
## 例外狀況  
 在內部，呼叫 `QueryInterface` 所擁有的 COM 物件，以及任何錯誤的 `HRESULT` 轉換為例外狀況的 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>。  
  
## 備註  
 `Detach` 表示呼叫端先將 COM 物件的參考會釋放 `com::ptr`所擁有的所有參考。呼叫端必須最後釋放所傳回的物件終結。  
  
## 範例  
 這個範例會使用 `com::ptr` 包裝其私用成員 `IXMLDOMDocument` 物件的 CLR 類別。`DetachDocument` 成員函式呼叫中止 COM 物件的擁有權和傳回指標的 `Detach` 至呼叫端。  
  
```  
// comptr_detach.cpp  
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
  
   // detach the COM object and return it  
   // this releases the internal reference to the object  
   IXMLDOMDocument* DetachDocument() {  
      return m_ptrDoc.Detach();  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// unmanaged function that loads XML into a raw XML DOM Document object  
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {  
   HRESULT hr = S_OK;  
   VARIANT_BOOL bSuccess;  
   hr = pDoc->loadXML(bstrXml, &bSuccess);  
   if (S_OK == hr && !bSuccess) {  
      hr = E_FAIL;  
   }  
   return hr;  
}  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   IXMLDOMDocument* pDoc = NULL;  
   BSTR bstrXml = NULL;  
  
   try {  
      // create the class from a progid string  
      XmlDocument doc("Msxml2.DOMDocument.3.0");  
  
      bstrXml = ::SysAllocString(L"<word>persnickety</word>");  
      if (NULL == bstrXml) {  
         throw gcnew OutOfMemoryException("bstrXml");  
      }  
      // detach the document object from the ref class  
      pDoc = doc.DetachDocument();  
      // use unmanaged function and raw object to load xml  
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));  
      // release document object as the ref class no longer owns it  
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
 **標頭檔** \<msclr \\ com \\ ptr.h\>  
  
 **命名空間** msclr::com  
  
## 請參閱  
 [ptr 成員](../dotnet/ptr-members.md)   
 [ptr::Release](../dotnet/ptr-release.md)   
 [ptr::Attach](../dotnet/ptr-attach.md)