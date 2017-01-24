---
title: "domain_error 類別 | Microsoft Docs"
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
  - "domain_error"
  - "std::domain_error"
  - "std.domain_error"
  - "stdexcept/std::domain_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "domain_error 類別"
ms.assetid: a1d8245d-61c2-4d1e-973f-073bd5dd5fa3
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# domain_error 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告網域錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
class domain_error : public logic_error {  
public:  
    explicit domain_error(const string& message);

    explicit domain_error(const char *message);

};  
```  
  
## <a name="remarks"></a>備註  
 所傳回的值 [什麼](../standard-library/exception-class1.md) 是一份 **訊息**`.`[資料](../standard-library/basic-string-class.md#basic_string__data)。  
  
## <a name="example"></a>範例  
  
```  
// domain_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   try   
   {  
      throw domain_error( "Your domain is in error!" );  
   }  
   catch (exception &e)   
   {  
      cerr << "Caught: " << e.what( ) << endl;  
      cerr << "Type: " << typeid(e).name( ) << endl;  
   };  
}  
\* Output:   
Caught: Your domain is in error!  
Type: class std::domain_error  
*\  
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< stdexcept>  
  
 **命名空間︰** std  
  
## <a name="see-also"></a>請參閱  
 [logic_error 類別](../standard-library/logic-error-class.md)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

