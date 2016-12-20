---
title: "underflow_error 類別 | Microsoft Docs"
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
  - "stdexcept/std::underflow_error"
  - "underflow_error"
  - "std.underflow_error"
  - "std::underflow_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "underflow_error 類別"
ms.assetid: d632f1f9-9c6c-4954-b96b-03041bfab22d
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# underflow_error 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告算術反向溢位。  
  
## <a name="syntax"></a>語法  
  
```  
class underflow_error : public runtime_error {  
public:  
    explicit underflow_error(const string& message);

    explicit underflow_error(const char *message);

};  
```  
  
## <a name="remarks"></a>備註  
 所傳回的值 [什麼](../standard-library/exception-class1.md) 是一份 **訊息**`.`[資料](../standard-library/basic-string-class.md#basic_string__data)。  
  
## <a name="example"></a>範例  
  
```  
// underflow_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   try   
   {  
      throw underflow_error( "The number's a bit small, captain!" );  
   }  
   catch ( exception &e ) {  
      cerr << "Caught: " << e.what( ) << endl;  
      cerr << "Type: " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught: The number's a bit small, captain!  
Type: class std::underflow_error  
*\  
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< stdexcept>  
  
 **命名空間︰** std  
  
## <a name="see-also"></a>請參閱  
 [\< stdexcept> 成員](http://msdn.microsoft.com/zh-tw/7b6b0a73-916e-44aa-9a3f-f5b6b3ce98e6)   
 [runtime_error 類別](../standard-library/runtime-error-class.md)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

