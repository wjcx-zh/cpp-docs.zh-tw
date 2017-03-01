---
title: "less 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::less
- std.less
- less
- xfunctional/std::less
dev_langs:
- C++
helpviewer_keywords:
- less struct
- less function
ms.assetid: 39349da3-11cd-4774-b2cc-b46af5aae5d7
caps.latest.revision: 24
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
ms.openlocfilehash: ff9530d08066cf0cf9b9421ac8b1b72d1a229bbe
ms.lasthandoff: 02/24/2017

---
# <a name="less-struct"></a>less 結構
在其引數上執行小於運算 ( `operator<`) 的二元述詞。  
  
## <a name="syntax"></a>語法  
  
```
template <class Type = void>
struct less : public binary_function <Type, Type, bool>  
{
    bool operator()(const Type& Left, const Type& Right) const;
 };

// specialized transparent functor for operator<
template <>
struct less<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) <std::forward<U>(Right));
 };
```  
  
#### <a name="parameters"></a>參數  
 `Type`, `T`, `U`  
 支援 `operator<` 的任何類型，其接受指定或推斷類型的運算元。  
  
 `Left`  
 小於運算的左運算元。 此未特製化的範本接受 `Type` 類型的左值參考引數。 此特製化的範本會完美地轉送 `T` 推斷類型的左值和右值參考引數。  
  
 `Right`  
 小於運算的右運算元。 此未特製化的範本接受 `Type` 類型的左值參考引數。 此特製化的範本會完美地轉送 `U` 推斷類型的左值和右值參考引數。  
  
## <a name="return-value"></a>傳回值  
 `Left``<``Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator<` 所傳回的類型。  
  
## <a name="remarks"></a>備註  
 二元述詞 `less`< `Type`> 會提供嚴格弱式排序來將一組 `Type` 類型的元素值分割成等價類別，但只有在此類型滿足以此方式排序的標準數學需求時，才會這麼做。 任何指標類型的特製化都會產生元素的總排序，其中所有不同值的元素都會依照彼此的相關順序排序。  
  
## <a name="example"></a>範例  
  
```cpp  
// functional_less.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
struct MyStruct {  
   MyStruct(int i) : m_i(i){}  
  
   bool operator < (const MyStruct & rhs) const {  
      return m_i < rhs.m_i;  
   }     
  
   int m_i;  
};  
  
int main() {  
   using namespace std;  
   vector <MyStruct> v1;  
   vector <MyStruct>::iterator Iter1;  
   vector <MyStruct>::reverse_iterator rIter1;  
  
   int i;  
   for ( i = 0 ; i < 7 ; i++ )       
       v1.push_back( MyStruct(rand()));  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )   
cout << Iter1->m_i << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   sort( v1.begin( ), v1.end( ), less<MyStruct>());  
  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )   
cout << Iter1->m_i << " ";  
   cout << ")" << endl;  
 }  
```  
  
## <a name="output"></a>輸出  
  
```
Original vector v1 = (41 18467 6334 26500 19169 15724 11478)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500)
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<functional>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)




