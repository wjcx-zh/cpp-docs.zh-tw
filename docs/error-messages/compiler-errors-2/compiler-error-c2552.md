---
title: "編譯器錯誤 C2552 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2552
dev_langs: C++
helpviewer_keywords: C2552
ms.assetid: 0e0ab759-788a-4faf-9337-80d4b9e2e8c9
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c1a438d602c23d15a1196fe4d40a5cca98867828
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2552"></a>編譯器錯誤 C2552
'identifier'：非彙總無法以初始設定式清單初始化  
  
 彙總識別項未經正確初始化。  
  
 [彙總](../../c-language/initializing-aggregate-types.md)定義為：  
  
-   陣列  
  
-   不具有下列項目的類別、結構和等位：  
  
    -   建構函式  
  
    -   private 或 protected 成員  
  
    -   基底類別  
  
    -   虛擬函式  
  
 此外，Visual C++ 不允許彙總中包含建構函式的資料類型。  
  
 在下列類型嘗試進行彙總初始化時，有可能會引發 C2552：  
  
-   該類型具有一個或多個使用者定義的建構函式。  
  
-   該類型具有一個或多個非靜態、私用資料成員。  
  
-   該類型具有一個或多個虛擬函式。  
  
-   該類型具有基底類別。  
  
-   該類型是一種 ref 類別或 CLR 介面。  
  
-   該類型具有其項目包含解構函式的非固定維度陣列 (零陣列)。  
  
 下列範例會產生 C2552：  
  
```  
// C2552.cpp  
// compile with: /clr  
#include <string>  
using namespace std;  
  
struct Pair_Incorrect {  
private:  
   string m_name;  
   double m_val;  
};  
  
struct Pair_Correct1 {  
public:  
   Pair_Correct1(string name, double val)  
      : m_name(name), m_val(val) {}  
  
private:  
   string m_name;  
   double m_val;  
};  
  
struct Pair_Correct2 {  
public:  
   string m_name;  
   double m_val;  
};  
  
int main() {  
   // To fix, add a constructor to this class and use it for   
   // initializing the data members, see Pair_Correct1 (below)  
   // or  
   // Do not have any private or protected non-static data members,   
   // see Pair_Correct2 (below).  Pair_Correct2 is not recommended in   
   // case your object model requires some non-static data members to   
   // be private or protected  
  
   string name("John");  
   Pair_Incorrect pair1 = { name, 0.0 };   // C2552  
  
   // initialize a CLR immutable value type that has a constructor  
   System::DateTime dt = {2001, 4, 12, 22, 16, 49, 844};   // C2552   
  
   Pair_Correct1 pair2( name, 0.0 );  
   Pair_Correct1 pair3 = Pair_Correct1( name, 0.0 );  
   Pair_Correct2 pair4 = { name, 0.0 };  
   System::DateTime dt2(2001, 4, 12, 22, 16, 49, 844);  
}  
```