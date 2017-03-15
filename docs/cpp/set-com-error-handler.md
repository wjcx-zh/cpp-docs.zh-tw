---
title: "_set_com_error_handler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_com_error_handler 函式"
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# _set_com_error_handler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 取代 COM 錯誤處理所使用的預設函式。  
  
## 語法  
  
```  
void __stdcall _set_com_error_handler(  
   void (__stdcall *pHandler)(  
      HRESULT hr,   
      IErrorInfo* perrinfo  
   )  
);  
```  
  
#### 參數  
 `pHandler`  
 取代函式的指標。  
  
 `hr`  
 `HRESULT` 資訊。  
  
 `perrinfo`  
 `IErrorInfo` 物件  
  
## 備註  
 根據預設，[\_com\_raise\_error](../cpp/com-raise-error.md) 會處理所有 COM 錯誤。  您可以使用 `_set_com_error_handler` 呼叫您自己的錯誤處理函式來變更這個行為。  
  
 取代函式擁有的簽章必須相當於 `_com_raise_error` 的簽章。  
  
## 範例  
  
```  
// _set_com_error_handler.cpp  
// compile with /EHsc  
#include <stdio.h>  
#include <comdef.h>  
#include <comutil.h>  
  
// Importing ado dll to attempt to establish an ado connection.  
// Not related to _set_com_error_handler   
#import "C:\Program Files\Common Files\System\ado\msado15.dll" no_namespace rename("EOF", "adoEOF")  
  
void __stdcall _My_com_raise_error(HRESULT hr, IErrorInfo* perrinfo)  
{  
   throw "Unable to establish the connection!";  
}  
  
int main()  
{  
   _set_com_error_handler(_My_com_raise_error);  
   _bstr_t bstrEmpty(L"");  
   _ConnectionPtr Connection = NULL;  
   try  
   {  
      Connection.CreateInstance(__uuidof(Connection));  
      Connection->Open(bstrEmpty, bstrEmpty, bstrEmpty, 0);   
   }  
   catch(char* errorMessage)  
   {  
      printf("Exception raised: %s\n", errorMessage);  
   }  
  
   return 0;  
}  
```  
  
  **發生例外狀況：無法建立連接！**   
## 需求  
 **標頭：**comdef.h  
  
 **Lib：**如果 \[wchar\_t 為原生類型\] 編譯器選項為開啟狀態，請使用 comsuppw.lib 或 comsuppwd.lib。  如果 \[wchar\_t 原生類型\] 為關閉狀態，請使用 comsupp.lib。  如需詳細資訊，請參閱 [\/Zc:wchar\_t \(wchar\_t 是原生類型\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
## 請參閱  
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)