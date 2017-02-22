---
title: "bad_alloc 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::bad_alloc"
  - "new/std:bad_alloc"
  - "bad_alloc"
  - "std.bad_alloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_alloc 類別"
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# bad_alloc 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述擲回例外狀況的類別，該例外狀況表示配置要求失敗。  
  
## <a name="syntax"></a>語法  
  
```  
class bad_alloc : public exception {  
    bad_alloc();
virtual ~bad_alloc();

};  
```  
  
## <a name="remarks"></a>備註  
 所傳回的值 **什麼** 為實作所定義的 C 字串。 所有成員函式都不會擲回任何例外狀況。  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 新>  
  
 **命名空間︰** std  
  
## <a name="example"></a>範例  
  
```  
// bad_alloc.cpp  
// compile with: /EHsc  
#include<new>  
#include<iostream>  
using namespace std;  
  
int main() {  
   char* ptr;  
   try {  
      ptr = new char[(~unsigned int((int)0)/2) - 1];  
      delete[] ptr;  
   }  
   catch( bad_alloc &ba) {  
      cout << ba.what( ) << endl;  
   }  
}  
```  
  
## <a name="sample-output"></a>範例輸出  
  
```  
bad allocation  
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 新>  
  
## <a name="see-also"></a>請參閱
 [例外狀況類別](../standard-library/exception-class1.md)  
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

