---
title: "not_equal_to 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.not_equal_to
- std::not_equal_to
- not_equal_to
- xfunctional/std::not_equal_to
dev_langs:
- C++
helpviewer_keywords:
- not_equal_to function
- not_equal_to struct
ms.assetid: 333fce09-4f51-44e0-ba26-533bccffd485
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 741c899479f89845a2be8e68e133a48b7d99e7c3
ms.lasthandoff: 02/24/2017

---
# <a name="notequalto-struct"></a>not_equal_to 結構
在其引數上執行不等比較運算 ( `operator!=`) 的二元述詞。  
  
## <a name="syntax"></a>語法  
  
```
template <class Type = void>
struct not_equal_to : public binary_function<Type, Type, bool>  
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator!=
template <>
struct not_equal_to<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) != std::forward<U>(Right));
};
```  
  
#### <a name="parameters"></a>參數  
 `Type`, `T`, `U`  
 支援 `operator!=` 的任何類型，其接受指定或推斷類型的運算元。  
  
 `Left`  
 不等比較運算的左運算元。 此未特製化的範本接受 `Type` 類型的左值參考引數。 此特製化的範本會完美地轉送 `T` 推斷類型的左值和右值參考引數。  
  
 `Right`  
 不等比較運算的右運算元。 此未特製化的範本接受 `Type` 類型的左值參考引數。 此特製化的範本會完美地轉送 `U` 推斷類型的左值和右值參考引數。  
  
## <a name="return-value"></a>傳回值  
 `Left``!=``Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator!=` 所傳回的類型。  
  
## <a name="remarks"></a>備註  
 `Type` 類型的物件必須可進行等號比較。 在物件集合上定義的 `operator!=` 必須符合等價關聯的數學屬性，才能進行此作業。 所有內建的數字和指標類型皆符合這項需求。  
  
## <a name="example"></a>範例  
  
```cpp  
// functional_not_equal_to.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <double> v1, v2, v3 (6);  
   vector <double>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i+=2 )  
   {  
      v1.push_back( 2.0 *i );  
      v1.push_back( 2.0 * i + 1.0 );  
   }  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j+=2 )  
   {  
      v2.push_back( - 2.0 * j );  
      v2.push_back( 2.0 * j + 1.0 );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Testing for the element-wise equality between v1 & v2  
   transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin ( ),   
      not_equal_to<double>( ) );  
  
   cout << "The result of the element-wise not_equal_to comparsion\n"  
      << "between v1 & v2 is: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
/* Output:  
The vector v1 = ( 0 1 4 5 8 9 )  
The vector v2 = ( -0 1 -4 5 -8 9 )  
The result of the element-wise not_equal_to comparsion  
between v1 & v2 is: ( 0 0 1 0 1 0 )  
*/  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<functional>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)




