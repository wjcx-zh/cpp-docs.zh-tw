---
title: "range_error 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdexcept/std::range_error
- range_error
dev_langs:
- C++
helpviewer_keywords:
- range_error class
ms.assetid: 8afb3e88-fc49-4213-b096-ed63d7aea37c
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 41b99edfa9b99802b2d54b977a17a51678fb2b4d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="rangeerror-class"></a>range_error 類別
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
 [what](../standard-library/exception-class.md) 所傳回的值為 **message**`.`[data](../standard-library/basic-string-class.md#data) 的複本。  
  
## <a name="example"></a>範例  
  
```cpp  
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
 **標頭：**\<stdexcept>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [runtime_error 類別](../standard-library/runtime-error-class.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


