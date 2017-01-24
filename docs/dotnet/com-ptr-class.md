---
title: "com::ptr 類別 | Microsoft Docs"
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
  - "com::ptr"
  - "msclr::com::ptr"
  - "msclr.com.ptr"
  - "com.ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr 類別"
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# com::ptr 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以當做 CLR 類別成員的 COM 物件的包裝函式。在呼叫其解構函式時，包裝函式自動化 COM 物件的存留期管理，釋出物件的任何擁有的參考。  類似於 [CComPtr Class](../atl/reference/ccomptr-class.md)。  
  
## 語法  
  
```  
template<class _interface_type>  
ref class ptr;  
```  
  
#### 參數  
 `_interface_type`  
 COM 介面  
  
## 備註  
 `com::ptr` 也可以用於本機變數功能簡化了各種 COM 工作和自動化存留期管理。  
  
 `com::ptr` 無法直接做為函式參數；請使用 [Tracking Reference Operator](../windows/tracking-reference-operator-cpp-component-extensions.md) 或 [物件控制代碼運算子 \(^\)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md) 。  
  
 `com::ptr` 無法從函式直接傳回；請使用控制代碼。  
  
## 範例  
 這個範例會使用 `com::ptr` 包裝其私用成員 `IXMLDOMDocument` 物件的 CLR 類別。呼叫類別結果的公用方法在呼叫中包含的 `IXMLDOMDocument` 物件。這個範例會建立 XML 文件，填滿的執行個體與一些簡單的 XML，然後進行節點的簡化查核行程在剖析的文件樹狀結構的 XML 列印到主控台。  
  
```  
// comptr.cpp  
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
  
   void LoadXml(String^ xml) {  
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);  
      BSTR bstr = NULL;  
  
      try {  
         // load some XML into the document  
         bstr = ::SysAllocString(pinnedXml);  
         if (NULL == bstr) {  
            throw gcnew OutOfMemoryException;  
         }  
         VARIANT_BOOL bIsSuccessful = false;  
         // use operator -> to call IXMODOMDocument member function  
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));  
      }  
      finally {  
         ::SysFreeString(bstr);  
      }  
   }  
  
   // simplified function to write just the first xml node to the console  
   void WriteXml() {  
      IXMLDOMNode* pNode = NULL;  
  
      try {  
         // the first child of the document is the first real xml node  
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));  
         if (NULL != pNode) {  
            WriteNode(pNode);  
         }  
      }  
      finally {  
         if (NULL != pNode) {  
            pNode->Release();  
         }  
      }  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   // simplified function that only writes the node  
   void WriteNode(IXMLDOMNode* pNode) {  
      BSTR bstr = NULL;  
  
      try {  
         // write out the name and text properties  
         Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));  
         String^ strName = gcnew String(bstr);  
         Console::Write("<{0}>", strName);  
         ::SysFreeString(bstr);  
         bstr = NULL;  
  
         Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));  
         Console::Write(gcnew String(bstr));  
         ::SysFreeString(bstr);  
         bstr = NULL;  
  
         Console::WriteLine("</{0}>", strName);  
      }  
      finally {  
         ::SysFreeString(bstr);  
      }  
   }  
  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   try {  
      // create the class from a progid string  
      XmlDocument doc("Msxml2.DOMDocument.3.0");  
  
      // stream some xml into the document  
      doc.LoadXml("<word>persnickety</word>");  
  
      // write the document to the console  
      doc.WriteXml();  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
}  
```  
  
  **\<word\>persnickety\<\/word\>**   
## 需求  
 **標頭檔**\<msclr \\ com \\ ptr.h\>  
  
 **命名空間** msclr::com  
  
## 請參閱  
 [C\+\+ 支援程式庫](../dotnet/cpp-support-library.md)   
 [ptr 成員](../dotnet/ptr-members.md)