---
title: "length_error 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdexcept/std::length_error
- length_error
dev_langs:
- C++
helpviewer_keywords:
- length_error class
ms.assetid: d53c46c5-4626-400d-bd76-bf3e1e0f64ae
caps.latest.revision: 21
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 3846e5efd8c93d74e196cd31890b484f4befbca4
ms.lasthandoff: 02/24/2017

---
# <a name="lengtherror-class"></a>length_error 類別
此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告嘗試產生的物件太長而無法指定。  
  
## <a name="syntax"></a>語法  
  
```  
class length_error : public logic_error {  
public:  
    explicit length_error(const string& message);

    explicit length_error(const char *message);

};  
```  
  
## <a name="remarks"></a>備註  
 [what](../standard-library/exception-class.md) 所傳回的值為 **message**`.`[data](../standard-library/basic-string-class.md#basic_string__data) 的複本。  
  
## <a name="example"></a>範例  
  
```cpp  
// length_error.cpp  
// compile with: /EHsc /GR /MDd  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
template<class  T>  
class stingyallocator : public allocator< T>  
{  
public:  
   template <class U>  
      struct rebind { typedef stingyallocator<U> other; };  
   _SIZT max_size( ) const  
   {  
         return 10;  
   };  
  
};  
  
int main( )  
{  
   try  
   {  
      vector<int, stingyallocator< int > > myv;  
      for ( int i = 0; i < 11; i++ ) myv.push_back( i );  
   }  
   catch ( exception &e )  
   {  
      cerr << "Caught " << e.what( ) << endl;  
      cerr << "Type " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught vector<T> too long  
Type class std::length_error  
*\  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<stdexcept>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [logic_error 類別](../standard-library/logic-error-class.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


