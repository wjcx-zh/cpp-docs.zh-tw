---
title: "&lt;valarray&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a53562c-90ab-4eb3-85d3-ada5259d90b0
caps.latest.revision: 8
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: c2d2d523f8085db02336be1efc80f34b5cf62b27
ms.lasthandoff: 02/24/2017

---
# <a name="ltvalarraygt-operators"></a>&lt;valarray&gt; 運算子
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator&amp;](#operator_amp_)|  
|[operator&amp;&amp;](#operator_amp__amp_)|[operator&gt;](#operator_gt_)|[operator&gt;&gt;](#operator_gt__gt_)|  
|[operator&gt;=](#operator_gt__eq)|[operator&lt;](#operator_lt_)|[operator&lt;&lt;](#operator_lt__lt_)|  
|[operator&lt;=](#operator_lt__eq)|[operator*](#operator_star)|[operator+](#operator_add)|  
|[operator-](#operator-)|[operator/](#operator_)|[operator==](#operator_eq_eq)|  
|[operator^](#operator_xor)|[operator|](#operator_or)|[operator||](#operator_lor)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 測試兩個大小相等之 valarray 的對應項目是否不相等，或測試 valarray 的所有項目是否都和指定值不相等。  
  
```  
template <class Type>  
valarray<bool>  
operator!=(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<bool>  
operator!=(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<bool>  
operator!=(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要測試不相等項目之兩個 valarray 的第一個。  
  
 ` right`  
 要測試不相等項目之兩個 valarray 的第二個。  
  
### <a name="return-value"></a>傳回值  
 布林值的 valarray，其中每個為：  
  
- 如果對應的項目不相等，則為 **true**。  
  
- 如果對應的項目相等，則為 **false**。  
  
### <a name="remarks"></a>備註  
 第一個範本運算子會傳回 [valarray\<bool>](../standard-library/valarray-bool-class.md) 類別物件，其中每個項目 `I` 為 ` left`[ `I`] != ` right`[ `I`]。  
  
 第二個範本運算子會儲存於項目 *I  left*[ `I`] != _ *Right*。  
  
 第三個範本運算子會儲存於項目 *I  left* != ` right`[ `I`]。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_ne.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaNE ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL != vaR );  
   cout << "The element-by-element result of "  
        << "the not equal comparison test is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the not equal comparison test is the  
 valarray: ( 0 0 1 0 1 0 1 0 1 0 ).  
*\  
```  
  
##  <a name="a-nameoperatormoda--operator"></a><a name="operator_mod"></a>  operator%  
 取得兩個相等大小 valarray 之對應項目相除的餘數，或 valarray 除以指定值的餘數，或指定值除以 valarray 的餘數。  
  
```  
template <class Type>  
valarray<Type>  
operator%(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<Type>  
operator%(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<Type>  
operator%(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 當作被除數的值或是 valarray，除以另一個值或 valarray。  
  
 ` right`  
 當作除數的值或 valarray，除另一個值或 valarray。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其元素為 ` left` 除以 ` right.` 的餘數。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_rem.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 6 ), vaR ( 6 );  
   valarray<int> vaREM ( 6 );  
   for ( i = 0 ; i < 6 ; i += 2 )  
      vaL [ i ] =  53;  
   for ( i = 1 ; i < 6 ; i += 2 )  
      vaL [ i ] =  -67;  
   for ( i = 0 ; i < 6 ; i++ )  
      vaR [ i ] =  3*i+1;  
  
   cout << "The initial Left valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaREM = ( vaL % vaR );  
   cout << "The remainders from the element-by-element "  
        << "division is the\n valarray: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaREM [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 53 -67 53 -67 53 -67 ).  
The initial Right valarray is: ( 1 4 7 10 13 16 ).  
The remainders from the element-by-element division is the  
 valarray: ( 0 -3 4 -7 1 -3 ).  
*\  
```  
  
##  <a name="a-nameoperatorampa--operatoramp"></a><a name="operator_amp_"></a>  operator&amp;  
 取得兩個相同大小 valarray 對應項目之間，或 valarray 和該項目型別指定值之間的位元 **AND**。  
  
```  
template <class Type>  
valarray<Type>  
operator&(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<Type>  
operator&(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<Type>  
operator&(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要使用位元 **AND** 合併其中每個項目之兩個 valarray 的第一個，或是要與 valarray 中每個項目合併位元的項目型別指定值。  
  
 ` right`  
 要使用位元 **AND** 合併其中每個項目之兩個 valarray 的第二個，或是要與 valarray 中每個項目合併位元的項目型別指定值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目為 ` left` 和 ` right.` 位元 AND 作業的合併項目。  
  
### <a name="remarks"></a>備註  
 位元運算僅能用於操作 `char` 和 `int` 資料型別及變體的位元，並且無法用於 **float**、**double**、**longdouble**、`void``bool`，或是其他更複雜的資料型別。  
  
 位元 **AND** 與邏輯 **AND** 有相同的真值表，但是適用於個別位元層級上的資料型別。 [operator&&](../standard-library/valarray-operators.md#operator_amp__amp_) 適用於項目層級，會將所有非零的值視為 true，且結果為布林值的 valarray。 相反地，位元 **ANDoperator&** 會導致 valarray 的值非 0 即 1，取決於位元運算的結果。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_bitand.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<int> vaBWA ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i+1;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaBWA = ( vaL & vaR );  
   cout << "The element-by-element result of "  
        << "the bitwise operator & is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaBWA [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is:  ( 0 2 0 4 0 6 0 8 0 10 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the bitwise operator & is the  
 valarray: ( 0 0 0 0 0 4 0 0 0 8 ).  
*\  
```  
  
##  <a name="a-nameoperatorampampa--operatorampamp"></a><a name="operator_amp__amp_"></a>  operator&amp;&amp;  
 取得兩個相同大小 valarray 對應項目之間，或 valarray 和該 valarray 的項目型別指定值之間的邏輯 **AND**。  
  
```  
template <class Type>  
valarray<bool>  
operator&&(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<bool>  
operator&&(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<bool>  
operator&&(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要使用邏輯 **AND** 合併其中每個項目之兩個 valarray 的第一個，或是要與 valarray 中每個項目合併的項目型別指定值。  
  
 ` right`  
 要使用邏輯 **AND** 合併其中每個項目之兩個 valarray 的第二個，或是要與 valarray 中每個項目合併的項目型別指定值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目為布林值型別，並且為 ` left` 與 ` right.` 的邏輯 **AND** 作業的合併項目。  
  
### <a name="remarks"></a>備註  
 邏輯 **ANDoperator&&** 適用於項目層級，會將所有非零的值視為 true，且結果為布林值的 valarray。 相反地，位元版本的 **AND**、[operator&](../standard-library/valarray-operators.md#operator_amp_)，會導致 valarray 的值非 0 即 1，取決於位元運算的結果。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_logand.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaLAA ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaLAA = ( vaL && vaR );  
   cout << "The element-by-element result of "  
        << "the logical AND operator&& is the\n valarray: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaLAA [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the logical AND operator&& is the  
 valarray: ( 0 0 0 1 0 1 0 1 0 1 ).  
*\  
```  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>  operator&gt;  
 測試一個 valarray 的項目是否大於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或小於指定值。  
  
```  
template <class Type>  
valarray<bool>  
operator>(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<bool>  
operator>(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<bool>  
operator>(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要比較其項目之兩個 valarray 的第一個，或是要與 valarray 比較每個項目的指定值。  
  
 ` right`  
 要比較其項目之兩個 valarray 的第二個，或是要與 valarray 比較每個項目的指定值。  
  
### <a name="return-value"></a>傳回值  
 布林值的 valarray，其中每個為：  
  
- 如果 ` left` 項目或值大於對應的 ` right` 項目或值，則為 **true**。  
  
- 如果 ` left` 項目或值不大於對應的 ` right` 項目或值，則為 **false**。  
  
### <a name="remarks"></a>備註  
 如果兩個 valarray 中的項目數量不相等，則結果為未定義。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_gt.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaNE ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i - 1;  
  
   cout << "The initial Left valarray is: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL > vaR );  
   cout << "The element-by-element result of "  
        << "the greater than comparison test is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).  
The element-by-element result of the greater than comparison test is the  
 valarray: ( 1 1 0 1 0 1 0 1 0 1 ).  
*\  
```  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>  operator&gt;=  
 測試一個 valarray 的項目是否大於或等於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或等於、小於或等於指定值。  
  
```  
template <class Type>  
valarray<bool>  
operator>=(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<bool>  
operator>=(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<bool>  
operator>=(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要比較其項目之兩個 valarray 的第一個，或是要與 valarray 比較每個項目的指定值。  
  
 ` right`  
 要比較其項目之兩個 valarray 的第二個，或是要與 valarray 比較每個項目的指定值。  
  
### <a name="return-value"></a>傳回值  
 布林值的 valarray，其中每個為：  
  
- 如果 ` left` 項目或值大於或等於對應的 ` right` 項目或值，則為 **true**。  
  
- 如果 ` left` 項目或值小於對應的 ` right` 項目或值，則為 **false**。  
  
### <a name="remarks"></a>備註  
 如果兩個 valarray 中的項目數量不相等，則結果為未定義。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_ge.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaNE ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i - 1;  
  
   cout << "The initial Left valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL >= vaR );  
   cout << "The element-by-element result of "  
        << "the greater than or equal test is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).  
The element-by-element result of the greater than or equal test is the  
 valarray: ( 1 1 0 1 0 1 0 1 0 1 ).  
*\  
```  
  
##  <a name="a-nameoperatorgtgta--operatorgtgt"></a><a name="operator_gt__gt_"></a>  operator&gt;&gt;  
 依位置的指定數目或依第二個 valarray 指定的項目數量，將 valarray 的每個項目之位元右移。  
  
```  
template <class Type>  
valarray<Type>  
operator>>(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<Type>  
operator>>(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<Type>  
operator>>(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要移位的值，或是其項目要移位的 valarray。  
  
 ` right`  
 指出右移數量的值，或是其項目指出項目右移數量的 valarray。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目已經右移指定數量。  
  
### <a name="remarks"></a>備註  
 帶正負號的數字會保留其符號。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_rs.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   valarray<int> vaNE ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  64;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -64;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL >> vaR );  
   cout << "The element-by-element result of "  
        << "the right shift is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the right shift is the  
 valarray: ( 64 -32 16 -8 4 -2 1 -1 ).  
*\  
```  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>  operator&lt;  
 測試一個 valarray 的項目是否小於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或小於指定值。  
  
```  
template <class Type>  
valarray<bool>  
operator<(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<bool>  
operator<(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<bool>  
operator<(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要比較其項目之兩個 valarray 的第一個，或是要與 valarray 比較每個項目的指定值。  
  
 ` right`  
 要比較其項目之兩個 valarray 的第二個，或是要與 valarray 比較每個項目的指定值。  
  
### <a name="return-value"></a>傳回值  
 布林值的 valarray，其中每個為：  
  
- 如果 ` left` 項目或值小於對應的 ` right` 項目或值，則為 **true**。  
  
- 如果 ` left` 項目或值不小於對應的 ` right` 項目或值，則為 **false**。  
  
### <a name="remarks"></a>備註  
 如果兩個 valarray 的項目數量不相等，則結果為未定義。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_lt.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaNE ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL < vaR );  
   cout << "The element-by-element result of "  
        << "the less-than comparson test is the\n valarray: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the less-than comparson test is the  
 valarray: ( 0 0 1 0 1 0 1 0 1 0 ).  
*\  
```  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>  operator&lt;=  
 測試一個 valarray 的項目是否小於或等於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或等於、小於或等於指定值。  
  
```  
template <class Type>  
valarray<bool>  
operator<=(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<bool>  
operator<=(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<bool>  
operator<=(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要比較其項目之兩個 valarray 的第一個，或是要與 valarray 比較每個項目的指定值。  
  
 ` right`  
 要比較其項目之兩個 valarray 的第二個，或是要與 valarray 比較每個項目的指定值。  
  
### <a name="return-value"></a>傳回值  
 布林值的 valarray，其中每個為：  
  
- 如果 ` left` 項目或值小於或等於對應的 ` right` 項目或值，則為 **true**。  
  
- 如果 ` left` 項目或值大於對應的 ` right` 項目或值，則為 **false**。  
  
### <a name="remarks"></a>備註  
 如果兩個 valarray 的項目數量不相等，則結果為未定義。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_le.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaNE ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i - 1;  
  
   cout << "The initial Left valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL <= vaR );  
   cout << "The element-by-element result of "  
        << "the less than or equal test is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).  
The element-by-element result of the less than or equal test is the  
 valarray: ( 0 0 1 0 1 0 1 0 1 0 ).  
*\  
```  
  
##  <a name="a-nameoperatorltlta--operatorltlt"></a><a name="operator_lt__lt_"></a>  operator&lt;&lt;  
 依位置的指定數目或依第二個 valarray 指定的項目數量，將 valarray 的每個項目之位元左移。  
  
```  
template <class Type>  
valarray<Type>  
operator<<(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<Type>  
operator<<(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<Type>  
operator<<(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要移位的值，或是其項目要移位的 valarray。  
  
 ` right`  
 指出左移數量的值，或是其項目指出項目左移數量的 valarray。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目已經左移指定數量。  
  
### <a name="remarks"></a>備註  
 帶正負號的數字會保留其符號。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_ls.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   valarray<int> vaNE ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL << vaR );  
   cout << "The element-by-element result of "  
        << "the left shift is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the left shift is the  
 valarray: ( 1 -2 4 -8 16 -32 64 -128 ).  
*\  
```  
  
##  <a name="a-nameoperatorstara--operator"></a><a name="operator_star"></a>  operator*  
 取得兩個相同大小 valarray 對應項目之間，或 valarray 和該 valarray 的項目型別指定值之間項目的乘積。  
  
```  
template <class Type>  
valarray<Type>  
operator*(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<Type>  
operator*(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<Type>  
operator*(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要相乘其項目之兩個 valarray 的第一個，或是 valarray 每個項目要乘以的指定值。  
  
 ` right`  
 要相乘其項目之兩個 valarray 的第二個，或是 valarray 每個項目要乘以的指定值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目為 ` left` 和 ` right.` 的項目乘積。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_eprod.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   valarray<int> vaNE ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  2;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL * vaR );  
   cout << "The element-by-element result of "  
        << "the multiplication is the\n valarray: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the multiplication is the  
 valarray: ( 0 -1 4 -3 8 -5 12 -7 ).  
*\  
```  
  
##  <a name="a-nameoperatoradda--operator"></a><a name="operator_add"></a>  operator+  
 取得兩個相同大小 valarray 對應項目之間，或 valarray 和該 valarray 的項目型別指定值之間項目的總和。  
  
```  
template <class Type>  
valarray<Type>  
operator+(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<Type>  
operator+(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<Type>  
operator+(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要相加其項目之兩個 valarray 的第一個，或是要加上 valarray 每個項目的指定值。  
  
 ` right`  
 要相加其項目之兩個 valarray 的第二個，或是要加上 valarray 每個項目的指定值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目為 ` left` 和 ` right.` 的項目總和。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_esum.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   valarray<int> vaNE ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  2;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL + vaR );  
   cout << "The element-by-element result of "  
        << "the sum is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the sum is the  
 valarray: ( 2 0 4 2 6 4 8 6 ).  
*\  
```  
  
##  <a name="a-nameoperator-a--operator-"></a><a name="operator-"></a>  operator-  
 取得兩個相同大小 valarray 對應項目之間，或 valarray 和該 valarray 的項目型別指定值之間項目的差。  
  
```  
template <class Type>  
valarray<Type>  
operator-(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<Type>  
operator-(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<Type>  
operator-(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 當作被減數的值或 valarray，要減去其他值或 valarray 以得出差。  
  
 ` right`  
 當作減數的值或 valarray，要與其他值或 valarray 相減以得出差。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目為 ` left` 和 ` right.` 項目的差。  
  
### <a name="remarks"></a>備註  
 用於描述減法的算數術語：  
  
 差 = 被減數 - 減數  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_ediff.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   valarray<int> vaNE ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  10;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL - vaR );  
   cout << "The element-by-element result of "  
        << "the difference is the\n valarray: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 10 0 10 0 10 0 10 0 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the difference is the  
 valarray: ( 10 -1 8 -3 6 -5 4 -7 ).  
*\  
```  
  
##  <a name="a-nameoperatora--operator"></a><a name="operator_"></a>  operator/  
 取得兩個相同大小 valarray 對應項目之間，或 valarray 和該 valarray 的項目型別指定值之間項目的商。  
  
```  
template <class Type>  
valarray<Type>  
operator/(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<Type>  
operator/(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<Type>  
operator/(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 當作被除數的值或是 valarray，除以另一個值或 valarray 以得出商。  
  
 ` right`  
 當作除數的值或 valarray，除另一個值或 valarray 以得出商。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其元素為 ` left` 除以 ` right.` 的商。  
  
### <a name="remarks"></a>備註  
 用於描述除法的算數術語：  
  
 商 = 被除數 / 除數  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_equo.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<double> vaL ( 6 ), vaR ( 6 );  
   valarray<double> vaNE ( 6 );  
   for ( i = 0 ; i < 6 ; i += 2 )  
      vaL [ i ] =  100;  
   for ( i = 1 ; i < 6 ; i += 2 )  
      vaL [ i ] =  -100;  
   for ( i = 0 ; i < 6 ; i++ )  
      vaR [ i ] =  2*i;  
  
   cout << "The initial Left valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL / vaR );  
   cout << "The element-by-element result of "  
        << "the quotient is the\n valarray: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 100 -100 100 -100 100 -100 ).  
The initial Right valarray is: ( 0 2 4 6 8 10 ).  
The element-by-element result of the quotient is the  
 valarray: ( 1.#INF -50 25 -16.6667 12.5 -10 ).  
*\  
```  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 測試兩個大小相等之 valarray 的對應項目是否相等，或測試 valarray 的所有項目是否都和指定值相等。  
  
```  
template <class Type>  
valarray<bool>  
operator==(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<bool>  
operator==(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<bool>  
operator==(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要測試相等項目之兩個 valarray 的第一個。  
  
 ` right`  
 要測試相等項目之兩個 valarray 的第二個。  
  
### <a name="return-value"></a>傳回值  
 布林值的 valarray，其中每個為：  
  
- 如果對應的項目相等，則為 **true**。  
  
- 如果對應的項目不相等，則為 **false**。  
  
### <a name="remarks"></a>備註  
 第一個範本運算子會傳回 [valarray\<bool>](../standard-library/valarray-bool-class.md) 類別物件，其中每個項目 `I` 為 _ *Left*[ `I`] == \_ *Right*[ `I`]。 第二個範本運算子會儲存於項目 `I`` left`[ `I`] == \_ *Right*。 第三個範本運算子會儲存於項目 `I`` left` == ` right`[ `I`]。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_eq.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaNE ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNE = ( vaL == vaR );  
   cout << "The element-by-element result of "  
        << "the equality comparison test is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNE [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the equality comparison test is the  
 valarray: ( 1 1 0 1 0 1 0 1 0 1 ).  
*\  
```  
  
##  <a name="a-nameoperatorxora--operator"></a><a name="operator_xor"></a>  operator^  
 取得兩個相同大小 valarray 項目之間，或 valarray 和該項目型別指定值之間的位元互斥 `OR` (**XOR**)。  
  
```  
template <class Type>  
valarray<Type>  
operator^(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<Type>  
operator^(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<Type>  
operator^(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要使用位元 **XOR** 合併其中每個項目之兩個 valarray 的第一個，或是要與 valarray 中每個項目合併位元的項目型別指定值。  
  
 ` right`  
 要使用位元 **XOR** 合併其中每個項目之兩個 valarray 的第二個，或是要與 valarray 中每個項目合併位元的項目型別指定值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目為 ` left` 和 ` right.` 位元 **XOR** 作業的合併項目。  
  
### <a name="remarks"></a>備註  
 位元運算僅能用於操作 `char` 和 `int` 資料型別及變體的位元，並且無法用於 **float**、**double**、`long double`、`void``bool`，或是其他更複雜的資料型別。  
  
 位元互斥 `OR` (**XOR**) 具有下列語意：假設位元 *b*1 和 *b*2，如果其中只有一個位元為 true，則 *b*1 **XOR** *b*2 為 **true**；如果兩個位元均為 true 或 false，則為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_xor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<int> vaLAA ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
  
   cout << "The initial Left valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaLAA = ( vaL ^ vaR );  
   cout << "The element-by-element result of "  
        << "the bitwise XOR operator^ is the\n valarray: ( ";  
           for ( i = 0 ; i < 10 ; i++ )  
         cout << vaLAA [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).  
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the bitwise XOR operator^ is the  
 valarray: ( 1 0 0 3 2 4 7 6 6 9 ).  
*\  
```  
  
##  <a name="a-nameoperatorora--operator124"></a><a name="operator_or"></a>  operator&#124;  
 取得兩個相同大小 valarray 項目之間、或 valarray 和該項目類型指定值之間的位元 `OR`。  
  
```  
template <class Type>  
valarray<Type>  
operator|(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<Type>  
operator|(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<Type>  
operator|(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要使用位元 `OR` 合併其中每個項目之兩個 valarray 的第一個，或是要與 valarray 中每個項目合併位元的項目型別指定值。  
  
 ` right`  
 要使用位元 `OR` 合併其中每個項目之兩個 valarray 的第二個，或是要與 valarray 中每個項目合併位元的項目型別指定值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目為 ` left` 和 ` right.` 位元 `OR` 作業的合併項目。  
  
### <a name="remarks"></a>備註  
 位元運算僅能用於操作 `char` 和 `int` 資料型別及變體的位元，並且無法用於 **float**、**double**、**longdouble**、`void`、`bool`，或是其他更複雜的資料型別。  
  
 位元 OR 與邏輯 `OR` 有相同的真值表，但是適用於個別位元層級上的資料型別。 假設位元 *b*1 和 *b*2，如果至少有一個位元為 true，則 *b*1 `OR` *b*2 為 **true**，或如果兩個位元均為 false，則為 **false**。 邏輯 `OR`[operator&#124;&#124;](../standard-library/valarray-operators.md#operator_lor) 適用於項目層級，會將所有非零的值視為 **true**，且結果為布林值的 valarray。 相反地，位元 OR `operator|` 會導致 valarray 的值非 0 即 1，取決於位元運算的結果。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_bitor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<int> vaLAA ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
  
   cout << "The initial Left valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaLAA = ( vaL | vaR );  
   cout << "The element-by-element result of "  
        << "the bitwise OR operator| is the\n valarray: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaLAA [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).  
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the bitwise OR operator| is the  
 valarray: ( 1 0 1 3 3 4 7 6 7 9 ).  
*\  
```  
  
##  <a name="a-nameoperatorlora--operator124124"></a><a name="operator_lor"></a>  operator&#124;&#124;  
 取得兩個相同大小 valarray 項目之間，或 valarray 和該 valarray 的項目類型指定值之間的邏輯 `OR`。  
  
```  
template <class Type>  
valarray<bool>  
operator||(
    const valarray<Type>& left,  
    const valarray<Type>& right);

template <class Type>  
valarray<bool>  
operator||(
    const valarray<Type>& left,  
    const Type& right);

template <class Type>  
valarray<bool>  
operator||(
    const Type& left,  
    const valarray<Type>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 要使用邏輯 `OR` 合併其中每個項目之兩個 valarray 的第一個，或是要與 valarray 中每個項目合併的項目型別指定值。  
  
 ` right`  
 要使用邏輯 `OR` 合併其中每個項目之兩個 valarray 的第二個，或是要與 valarray 中每個項目合併的項目型別指定值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目為 `bool` 型別，並且為 ` left` 與 ` right.` 的邏輯 OR 作業的合併項目。  
  
### <a name="remarks"></a>備註  
 邏輯 `OR``operator||` 適用於項目層級，會將所有非零的值視為 **true**，且結果為布林值的 valarray。 相反地，位元版本的 `OR`、[operator&#124;](../standard-library/valarray-operators.md#operator_or)，會導致 valarray 的值非 0 即 1，取決於位元運算的結果。  
  
### <a name="example"></a>範例  
  
```cpp  
// valarray_op_logor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaLOR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  0;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  0;  
  
   cout << "The initial Left valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaLOR = ( vaL || vaR );  
   cout << "The element-by-element result of "  
        << "the logical OR operator|| is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaLOR [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The initial Right valarray is: ( 0 0 0 3 0 0 6 0 0 9 ).  
The element-by-element result of the logical OR operator|| is the  
 valarray: ( 0 0 0 1 0 1 1 1 0 1 ).  
*\  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<valarray>](../standard-library/valarray.md)


