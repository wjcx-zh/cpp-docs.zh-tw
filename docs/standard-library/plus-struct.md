---
title: "plus 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xfunctional/std::plus
dev_langs:
- C++
helpviewer_keywords:
- plus class
- plus struct
ms.assetid: 4594abd5-b2f2-4fac-9b6b-fc9a2723f8cf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e40ad97ac315e368d05b62424da2f094da4beaf5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="plus-struct"></a>plus 結構
在其引數執行加法運算 (二元 `operator+`) 的預先定義函式物件。  
  
## <a name="syntax"></a>語法  
  
```
template <class Type = void>
struct plus : public binary_function <Type, Type, Type>  
{
    Type operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator+
template <>  
struct plus<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) + std::forward<U>(Right));
 };
```  
  
#### <a name="parameters"></a>參數  
 `Type`, `T`, `U`  
 支援二元 `operator+` 的任何類型，接受指定或推斷類型的運算元。  
  
 `Left`  
 加法運算的左運算元。 此未特製化的範本接受 `Type` 類型的左值參考引數。 此特製化的範本會完美地轉送 `T` 推斷類型的左值和右值參考引數。  
  
 `Right`  
 加法運算的右運算元。 此未特製化的範本接受 `Type` 類型的左值參考引數。 此特製化的範本會完美地轉送 `U` 推斷類型的左值和右值參考引數。  
  
## <a name="return-value"></a>傳回值  
 `Left + Right` 的結果。 此特製化的範本會完美地轉送結果，具有二元 `operator+` 所傳回的類型。  
  
## <a name="example"></a>範例  
  
```cpp  
// functional_plus.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <double> v1, v2, v3 ( 6 );  
   vector <double>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i++ )  
      v1.push_back( 4 * i );  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j++ )  
      v2.push_back( -2.0 * j - 4 );  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Finding the element-wise sums of the elements of v1 & v2  
   transform (v1.begin( ), v1.end( ), v2.begin( ), v3.begin ( ), plus<double>( ) );  
  
   cout << "The element-wise sums are: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
\* Output:   
The vector v1 = ( 0 4 8 12 16 20 )  
The vector v2 = ( -4 -6 -8 -10 -12 -14 )  
The element-wise sums are: ( -4 -2 0 2 4 6 )  
*\  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<functional>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)



