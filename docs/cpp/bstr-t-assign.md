---
title: "_bstr_t::Assign | Microsoft Docs"
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
  - "_bstr_t::Assign"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Assign 方法"
ms.assetid: 2e209bbe-77ca-4598-86d5-6c2ea213f43c
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::Assign
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將 `BSTR` 複製到 **\_**`bstr_t` 所包裝的 `BSTR` 中。  
  
## 語法  
  
```  
void Assign(  
   BSTR s  
);  
```  
  
#### 參數  
 `s`  
 要複製到 `_bstr_t` 所包裝之 `BSTR` 中的 `BSTR`。  
  
## 備註  
 `Assign` 會執行二進位複製，這表示不論內容為何，都會複製 `BSTR` 的整個長度。  
  
## 範例  
  
```  
// _bstr_t_Assign.cpp  
  
#include <comdef.h>  
#include <stdio.h>  
  
int main()  
{  
    // creates a _bstr_t wrapper  
    _bstr_t bstrWrapper;   
  
    // creates BSTR and attaches to it  
    bstrWrapper = "some text";  
    wprintf_s(L"bstrWrapper = %s\n",  
              static_cast<wchar_t*>(bstrWrapper));  
  
    // bstrWrapper releases its BSTR  
    BSTR bstr = bstrWrapper.Detach();  
    wprintf_s(L"bstrWrapper = %s\n",   
              static_cast<wchar_t*>(bstrWrapper));  
    // "some text"   
    wprintf_s(L"bstr = %s\n", bstr);  
  
    bstrWrapper.Attach(SysAllocString(OLESTR("SysAllocedString")));  
    wprintf_s(L"bstrWrapper = %s\n",   
              static_cast<wchar_t*>(bstrWrapper));  
  
    // assign a BSTR to our _bstr_t  
    bstrWrapper.Assign(bstr);  
    wprintf_s(L"bstrWrapper = %s\n",   
              static_cast<wchar_t*>(bstrWrapper));  
  
    // done with BSTR, do manual cleanup  
    SysFreeString(bstr);  
  
    // resuse bstr  
    bstr= SysAllocString(OLESTR("Yet another string"));  
    // two wrappers, one BSTR   
    _bstr_t bstrWrapper2 = bstrWrapper;     
  
    *bstrWrapper.GetAddress() = bstr;  
  
    // bstrWrapper and bstrWrapper2 do still point to BSTR  
    bstr = 0;     
    wprintf_s(L"bstrWrapper = %s\n",   
              static_cast<wchar_t*>(bstrWrapper));  
    wprintf_s(L"bstrWrapper2 = %s\n",   
              static_cast<wchar_t*>(bstrWrapper2));  
  
    // new value into BSTR  
    _snwprintf_s(bstrWrapper.GetBSTR(), 100, bstrWrapper.length(),  
                 L"changing BSTR");     
    wprintf_s(L"bstrWrapper = %s\n",   
              static_cast<wchar_t*>(bstrWrapper));  
    wprintf_s(L"bstrWrapper2 = %s\n",   
              static_cast<wchar_t*>(bstrWrapper2));  
}  
```  
  
  **bstrWrapper \= some text**  
**bstrWrapper \= \(null\)**  
**bstr \= some text**  
**bstrWrapper \= SysAllocedString**  
**bstrWrapper \= some text**  
**bstrWrapper \= Yet another string**  
**bstrWrapper2 \= some text**  
**bstrWrapper \= changing BSTR**  
**bstrWrapper2 \= some text**   
## END Microsoft 特定的  
  
## 請參閱  
 [\_bstr\_t 類別](../cpp/bstr-t-class.md)