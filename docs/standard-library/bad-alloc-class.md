---
title: "bad_alloc 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- new/std::bad_alloc
dev_langs:
- C++
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d338b155eaebd7678e611dd38b8e1ef230545eb5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="badalloc-class"></a>bad_alloc 類別
描述擲回例外狀況的類別，該例外狀況表示配置要求失敗。  
  
## <a name="syntax"></a>語法  
  
```  
class bad_alloc : public exception {  
    bad_alloc();
virtual ~bad_alloc();

};  
```  
  
## <a name="remarks"></a>備註  
 **what** 所傳回的值是一個實作定義的 C 字串。 所有成員函式都不會擲回任何例外狀況。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<new>  
  
 **命名空間：** std  
  
## <a name="example"></a>範例  
  
```cpp  
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
 **標頭：**\<new>  
  
## <a name="see-also"></a>請參閱
 [exception 類別](../standard-library/exception-class.md)  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

