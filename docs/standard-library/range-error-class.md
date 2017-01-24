---
title: "range_error 類別 | Microsoft Docs"
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
  - "stdexcept/std::range_error"
  - "std.range_error"
  - "range_error"
  - "std::range_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "range_error 類別"
ms.assetid: 8afb3e88-fc49-4213-b096-ed63d7aea37c
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# range_error 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告報告範圍錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
class range_error : public runtime_error {  
public:  
    explicit range_error(const string& message);

    explicit range_error(const char *message);

};  
```  
  
## <a name="remarks"></a>備註  
 所傳回的值 [什麼](../standard-library/exception-class1.md) 是一份 **訊息**`.`[資料](../standard-library/basic-string-class.md#basic_string__data)。  
  
## <a name="example"></a>範例  
  
```  
// range_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
using namespace std;  
int main()  
{  
   try   
   {  
      throw range_error( "The range is in error!" );  
   }  
   catch (exception &e)   
   {  
      cerr << "Caught: " << e.what( ) << endl;  
      cerr << "Type: " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught: The range is in error!  
Type: class std::range_error  
*\  
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< stdexcept>  
  
 **命名空間︰** std  
  
## <a name="see-also"></a>請參閱  
 [runtime_error 類別](../standard-library/runtime-error-class.md)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

