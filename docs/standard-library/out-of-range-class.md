---
title: "out_of_range 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "out_of_range"
  - "stdexcept/std::out_of_range"
  - "std.out_of_range"
  - "std::out_of_range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "out_of_range 類別"
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# out_of_range 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告引數超出其有效範圍。  
  
## <a name="syntax"></a>語法  
  
```  
class out_of_range : public logic_error {  
public:  
    explicit out_of_range(const string& message);

    explicit out_of_range(const char *message);

};  
```  
  
## <a name="remarks"></a>備註  
 所傳回的值 [什麼](../standard-library/exception-class1.md) 是一份 **訊息**`.`[資料](../standard-library/basic-string-class.md#basic_string__data)。  
  
## <a name="example"></a>範例  
  
```  
// out_of_range.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
int main() {  
// out_of_range  
   try {  
      string str( "Micro" );  
      string rstr( "soft" );  
      str.append( rstr, 5, 3 );  
      cout << str << endl;  
   }  
   catch ( exception &e ) {  
      cerr << "Caught: " << e.what( ) << endl;  
   };  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
Caught: invalid string position  
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< stdexcept>  
  
 **命名空間︰** std  
  
## <a name="see-also"></a>請參閱  
 [logic_error 類別](../standard-library/logic-error-class.md)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

