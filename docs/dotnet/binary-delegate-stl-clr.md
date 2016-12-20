---
title: "binary_delegate (STL/CLR) | Microsoft Docs"
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
  - "cliext::binary_delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary_delegate 函式 [STL/CLR]"
ms.assetid: 52a9291a-e354-4b9e-a035-78dac1179ec5
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# binary_delegate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

genereic 類別會描述兩個引數的委派。  您會用它來指定委派根據它的引數和傳回型別。  
  
## 語法  
  
```  
generic<typename Arg1,  
    typename Arg2,  
    typename Result>  
    delegate Result binary_delegate(Arg1, Arg2);  
```  
  
#### 參數  
 Arg1  
 第一個引數的型別。  
  
 Arg2  
 第二個引數的型別。  
  
 結果  
 傳回類型。  
  
## 備註  
 genereic 委派描述一或兩個引數的函式。  
  
 請注意，下列：  
  
 `binary_delegate<int, int, int> Fun1;`  
  
 `binary_delegate<int, int, int> Fun2;`  
  
 型別 `Fun1` 和 `Fun2` 是同義字，而下列：  
  
 `delegate int Fun1(int, int);`  
  
 `delegate int Fun2(int, int);`  
  
 它們不是相同型別。  
  
## 範例  
  
```  
// cliext_binary_delegate.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
bool key_compare(wchar_t left, wchar_t right)   
    {   
    return (left < right);   
    }   
  
typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **compare\(L'a', L'a'\) \= False**  
**compare\(L'a', L'b'\) \= True**  
**compare\(L'b', L'a'\) \= False**   
## 需求  
 **標頭：** \<cliext\/functional\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [binary\_delegate\_noreturn](../dotnet/binary-delegate-noreturn-stl-clr.md)   
 [unary\_delegate](../dotnet/unary-delegate-stl-clr.md)   
 [unary\_delegate\_noreturn](../dotnet/unary-delegate-noreturn-stl-clr.md)