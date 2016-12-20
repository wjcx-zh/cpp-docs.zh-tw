---
title: "unary_delegate (STL/CLR) | Microsoft Docs"
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
  - "cliext::unary_delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unary_delegate 函式 [STL/CLR]"
ms.assetid: b3ee253c-98e8-466e-a272-505e47aed061
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# unary_delegate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

genereic 類別會描述一個引數的委派。  您會用它來指定委派根據它的引數和傳回型別。  
  
## 語法  
  
```  
generic<typename Arg,  
    typename Result>  
    delegate Result unary_delegate(Arg);  
```  
  
#### 參數  
 Arg  
 引數型別。  
  
 結果  
 傳回類型。  
  
## 備註  
 genereic 委派描述單一引數的函式。  
  
 請注意，為:  
  
 `unary_delegare<int, int> Fun1;`  
  
 `unary_delegare<int, int> Fun2;`  
  
 型別為 `Fun1` 和 `Fun2` 是同義字，，當為時:  
  
 `delegate int Fun1(int);`  
  
 `delegate int Fun2(int);`  
  
 它們不是相同型別。  
  
## 範例  
  
```  
// cliext_unary_delegate.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
int hash_val(wchar_t val)   
    {   
    return ((val * 17 + 31) % 67);   
    }   
  
typedef cliext::unary_delegate<wchar_t, int> Mydelegate;   
int main()   
    {   
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
  **雜湊 \(L'a\) \= 5**  
**雜湊 \(L'b\) \= 22**   
## 需求  
 **標題:** \<cliext\/功能\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [binary\_delegate](../dotnet/binary-delegate-stl-clr.md)   
 [binary\_delegate\_noreturn](../dotnet/binary-delegate-noreturn-stl-clr.md)   
 [unary\_delegate\_noreturn](../dotnet/unary-delegate-noreturn-stl-clr.md)