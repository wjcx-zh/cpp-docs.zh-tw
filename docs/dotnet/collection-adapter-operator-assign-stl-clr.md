---
title: "collection_adapter::operator= (STL/CLR) | Microsoft Docs"
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
  - "cliext::collection_adapter::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 成員 [STL/CLR]"
ms.assetid: 45365a33-3b56-4cb7-962f-81c20d8901d3
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# collection_adapter::operator= (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取代儲存的 BCL 控制代碼。  
  
## 語法  
  
```  
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);  
```  
  
#### 參數  
 right  
 要複製的配接器。  
  
## 備註  
 成員運算子複製 `right` 到物件後，再傳回 `*this`。  您可以使用它來將儲存在 `right`的 BCL 控制代碼的複本取代為儲存的 BCL 控制代碼。  
  
## 範例  
  
```  
// cliext_collection_adapter_operator_as.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mycoll c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**   
## 需求  
 **標頭:** \<cliext\/adapter\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)