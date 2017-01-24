---
title: "ConvertStringToBSTR | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ConvertStringToBSTR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConvertStringToBSTR 函式"
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ConvertStringToBSTR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將 **char \*** 值轉換為 `BSTR`。  
  
## 語法  
  
```  
  
      BSTR __stdcall ConvertStringToBSTR(  
   const char* pSrc  
)  
```  
  
#### 參數  
 `pSrc`  
 一個 **char \*** 變數。  
  
## 範例  
  
```  
// ConvertStringToBSTR.cpp  
#include <comutil.h>  
#include <stdio.h>  
  
#pragma comment(lib, "comsuppw.lib")  
#pragma comment(lib, "kernel32.lib")  
  
int main() {  
   char* lpszText = "Test";  
   printf_s("char * text: %s\n", lpszText);  
  
   BSTR bstrText = _com_util::ConvertStringToBSTR(lpszText);  
   wprintf_s(L"BSTR text: %s\n", bstrText);  
  
   SysFreeString(bstrText);  
}  
```  
  
  **char \* text: Test**  
**BSTR text: Test**   
## END Microsoft 特定的  
  
## 需求  
 **標頭：**comutil.h  
  
 **Lib：**comsuppw.lib 或 comsuppwd.lib \(如需詳細資訊，請參閱 [\/Zc:wchar\_t \(wchar\_t 是原生類型\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)\)  
  
## 請參閱  
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)