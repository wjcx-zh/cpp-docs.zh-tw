---
title: "ConvertBSTRToString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ConvertBSTRToString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConvertBSTRToString 函式"
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ConvertBSTRToString
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將 `BSTR` 值轉換為 **char \***。  
  
## 語法  
  
```  
  
      char* __stdcall ConvertBSTRToString(  
   BSTR pSrc  
);  
```  
  
#### 參數  
 `pSrc`  
 BSTR 變數。  
  
## 備註  
 `ConvertBSTRToString` 會配置您必須刪除的字串。  
  
## 範例  
  
```  
// ConvertBSTRToString.cpp  
#include <comutil.h>  
#include <stdio.h>  
  
#pragma comment(lib, "comsuppw.lib")  
  
int main() {  
   BSTR bstrText = ::SysAllocString(L"Test");  
   wprintf_s(L"BSTR text: %s\n", bstrText);  
  
   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);  
   printf_s("char * text: %s\n", lpszText2);  
  
   SysFreeString(bstrText);  
   delete[] lpszText2;  
}  
```  
  
  **BSTR text: Test**  
**char \* text: Test**   
## END Microsoft 特定的  
  
## 需求  
 **標頭：**comutil.h。  
  
 **Lib：**comsuppw.lib 或 comsuppwd.lib \(如需詳細資訊，請參閱 [\/Zc:wchar\_t \(wchar\_t 是原生類型\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)\)  
  
## 請參閱  
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)