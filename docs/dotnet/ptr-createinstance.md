---
title: "ptr::CreateInstance | Microsoft Docs"
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
  - "ptr.CreateInstance"
  - "msclr::com::ptr::CreateInstance"
  - "msclr.com.ptr.CreateInstance"
  - "ptr::CreateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ptr::CreateInstance"
ms.assetid: 9e8e4c4c-1651-4839-8829-5857d74470fe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ptr::CreateInstance
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用`com::ptr`建立COM物件的執行個體。  
  
## 語法  
  
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
  
#### 參數  
 `progid`  
 `ProgID` 字串。  
  
 `pouter`  
 對彙總物件的 IUnknown 介面 \(控制項\) 的 IUnknown 指標。  如果`pouter`未指定，就會使用`NULL`。  
  
 `cls_context`  
 程式碼處理新建立的物件時所執行的內容。  值是取自 `CLSCTX` 列舉。  如果沒有指定`cls_context`，則會使用值 CLSCTX\_ALL。  
  
 `rclsid`  
 `CLSID`與用來建立物件之資料及程式碼相關聯。  
  
## 例外狀況  
 如果 `com::ptr` 已經擁有對 COM 物件的參考， `CreateInstance` 會擲回 <xref:System.InvalidOperationException>。  
  
 這個函式呼叫 `CoCreateInstance` 並使用 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 轉換任何錯誤的 `HRESULT` 至適當的例外狀況。  
  
## 備註  
 `CreateInstance` 使用 `CoCreateInstance` 建立指定之物件的新執行個體，識別與 CLSID 或 ProgID。  `com::ptr` 參考新建立的物件，並自動釋放所有擁有的參考在解構函式。  
  
## 範例  
 這個範例會使用 `com::ptr` 包裝其私用成員 `IXMLDOMDocument` 物件的 CLR 類別。  類別建構函式會使用 `CreateInstance` 的兩個不同表單建立資料物件從 ProgID 或從 CLSID 加上 CLSCTX。  
  
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
  
## 需求  
 **標頭檔**\<msclr \\ com \\ ptr.h\>  
  
 **命名空間** msclr::com  
  
## 請參閱  
 [ptr 成員](../dotnet/ptr-members.md)