---
title: "overflow_error 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- stdexcept/std::overflow_error
dev_langs:
- C++
helpviewer_keywords:
- overflow_error class
ms.assetid: bae7128d-e36b-4a45-84f1-2f89da441d20
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 723870d89c087924cc4d9a13a0b9fa47988cfb2d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="overflowerror-class"></a>overflow_error 類別
此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告算術溢位。  
  
## <a name="syntax"></a>語法  
  
```  
class overflow_error : public runtime_error {  
public:  
    explicit overflow_error(const string& message);

    explicit overflow_error(const char *message);

};  
```  
  
## <a name="remarks"></a>備註  
 [what](../standard-library/exception-class.md) 所傳回的值為 **message**`.`[data](../standard-library/basic-string-class.md#data) 的複本。  
  
## <a name="example"></a>範例  
  
```cpp  
// overflow_error.cpp  
// compile with: /EHsc /GR  
#include <bitset>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   try   
   {  
      bitset< 33 > bitset;  
      bitset[32] = 1;  
      bitset[0] = 1;  
      unsigned long x = bitset.to_ulong( );  
   }  
   catch ( exception &e )   
   {  
      cerr << "Caught " << e.what( ) << endl;  
      cerr << "Type " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught bitset<N> overflow  
Type class std::overflow_error  
*\  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<stdexcept>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [runtime_error 類別](../standard-library/runtime-error-class.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

