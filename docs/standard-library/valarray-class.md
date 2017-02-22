---
title: "valarray 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "valarray"
  - "std.valarray"
  - "std::valarray"
  - "valarray/std::valarray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "valarray 類別"
ms.assetid: 19b862f9-5d09-4003-8844-6ddd02c1a3a7
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# valarray 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此樣板類別描述控制序列的項目類型的物件 **類型** ，儲存為陣列，針對執行高速的數學運算，而計算的效能最佳化。  
  
## <a name="remarks"></a>備註  
 此類別是一組值的已排序集合之數學概念表示，而此項目是從零開始循序編號。 此類別稱為附近的容器，因為它支援一些，但不是的所有功能，第一級的序列容器，例如 [向量](../standard-library/vector-class.md), ，支援。 它與範本類別向量有兩個重大差異：  
  
-   它會定義許多對應項目之間的算術運算 **valarray \< 類型>** 物件相同的類型和長度，例如 *xarr* = cos ( *yarr*) + sin ( *zarr*)。  
  
-   它會定義各種有趣的方式，以訂閱 **valarray \< 類型>** 物件，透過多載 [運算子 &#91; &#93;](#valarray__operator_at)。  
  
 類別的物件 **類型**:  
  
-   具有公用預設建構函式、解構函式、複製建構函式和指派運算子，且這些都具有傳統行為。  
  
-   視需要定義算術運算子和數學函式，這些函式定義為具有傳統行為的浮點類型。  
  
 特別是在指派之後，細微的差異可能不存在於複製建構和預設建構之間。 類別的物件上作業都不 **類型** 可能會擲回例外狀況。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[valarray](#valarray__valarray)|建構具有特定大小或具有特定值之項目的 `valarray`，或建構為另一個 `valarray` 的複本或另一個 `valarray` 的子集。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[value_type](#valarray__value_type)|代表儲存在 `valarray` 中之項目類型的類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[適用於](#valarray__apply)|將指定的函式套用至 `valarray` 的每個項目。|  
|[cshift](#valarray__cshift)|定期依指定的位置數目將 `valarray` 中的所有項目移位。|  
|[免費](#valarray__free)|釋放 `valarray` 所使用的記憶體。|  
|[最大值](#valarray__max)|尋找 `valarray` 中的最大項目。|  
|[最小值](#valarray__min)|尋找 `valarray` 中的最小項目。|  
|[調整大小](#valarray__resize)|將 `valarray` 中的項目數目變更為指定的數目，視需要加入或移除項目。|  
|[shift 鍵](#valarray__shift)|依指定的位置數目將 `valarray` 中的所有項目移位。|  
|[大小](#valarray__size)|尋找 `valarray` 中的項目數目。|  
|[總和](#valarray__sum)|判斷非零長度的 `valarray` 中所有項目的總和。|  
|[交換](#valarray__swap)||  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 ！](#valarray__operator_not)|可取得 `valarray` 中每個項目邏輯 `NOT` 值的一元運算子。|  
|[operator %=](#valarray__operator_mod_eq)|取得陣列項目除以指定的 `valarray` 或除以此項目類型之值的餘數。|  
|[運算子 & =](#valarray__operator_amp__eq)|取得陣列中項目的位元 `AND` 與指定的 `valarray` 中對應之項目或項目類型的值。|  
|[運算子 >> =](#valarray__operator_gt__gt__eq)|依位置的指定數目或依第二個 `valarray` 指定的項目數量，將 `valarray` 運算元的每個項目之位元右移。|  
|[運算子 << =](#valarray__operator_lt__lt__eq)|依位置的指定數目或依第二個 `valarray` 指定的項目數量，將 `valarray` 運算元的每個項目之位元左移。|  
|[運算子 * =](#valarray__operator_star_eq)|將指定之 `valarray` 的項目或此項目類型的值和運算元 `valarray` 相乘。|  
|[運算子 +](#valarray__operator_add)|對 `valarray` 中每個項目套用加號的一元運算子。|  
|[operator + =](#valarray__operator_add_eq)|將指定之 `valarray` 的項目或此項目類型的值加到運算元 `valarray`。|  
|[operator-](#valarray__operator-)|對 `valarray` 中每個項目套用減號的一元運算子。|  
|[運算子 =](#valarray__operator-_eq)|將運算元 `valarray` 減去指定之 `valarray` 的項目或此項目類型的值。|  
|[運算子 / =](#valarray__operator__eq)|將運算元 `valarray` 除以指定之 `valarray` 的項目或此項目類型的值。|  
|[運算子 =](#valarray__operator_eq)|指派項目至 `valarray`，其值直接受到指定或指定為其他 `valarray` 的一部份，或由 `slice_array`、`gslice_array`、`mask_array` 或 `indirect_array` 指定。|  
|[運算子 &#91; & #93。](#valarray__operator_at)|傳回項目參考或其指定索引處的值或指定的子集。|  
|[運算子 ^ =](#valarray__operator_xor_eq)|取得 element-wise 獨佔邏輯 or 運算子 ( `XOR`) 的陣列指定的 valarray 或項目類型的值。|  
|[運算子 &#124; =](#valarray__operator_or_eq)|取得陣列中項目的位元 `OR` 與指定的 `valarray` 中對應之項目或項目類型的值。|  
|[運算子 ~](#valarray__operator_dtor)|可取得 `valarray` 中每個項目位元 `NOT` 值的一元運算子。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< valarray>  
  
 **命名空間：** std  
  
##  <a name="a-namevalarrayapplya-valarrayapply"></a><a name="valarray__apply"></a>  valarray:: apply  
 適用於 valarray 的每個項目指定的函式。  
  
```  
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```  
  
### <a name="parameters"></a>參數  
 *_Func(Type)*  
 要套用至每個項目運算元 valarray 的函式物件。  
  
 *_Func(const Type&)*  
 要套用至運算元 valarray 的每個元素的 const 函式物件。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目有 `_Func` element-wise 套用至運算元 valarray 的項目。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回類別的物件 [valarray](../standard-library/valarray-class.md)**\< 類型>**, ，長度為 [大小](#valarray__size), ，每個項目 `I` 是 **func**(( **\*這**) [ `I`])。  
  
### <a name="example"></a>範例  
  
```  
// valarray_apply.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
using namespace std;  
  
int __cdecl MyApplyFunc( int n )  
{  
   return n*2;  
}  
  
int main( int argc, char* argv[] )  
{  
   valarray<int> vaR(10), vaApplied(10);  
   int i;  
  
   for ( i = 0; i < 10; i += 3 )  
      vaR[i] = i;  
  
   for ( i = 1; i < 10; i += 3 )  
      vaR[i] = 0;  
  
   for ( i = 2; i < 10; i += 3 )  
      vaR[i] = -i;  
  
   cout << "The initial Right valarray is: (";  
   for   ( i=0; i < 10; ++i )  
      cout << " " << vaR[i];  
   cout << " )" << endl;  
  
   vaApplied = vaR.apply( MyApplyFunc );  
  
   cout << "The element-by-element result of "  
       << "applying MyApplyFunc to vaR is the\nvalarray: ( ";  
   for ( i = 0; i < 10; ++i )  
      cout << " " << vaApplied[i];  
   cout << " )" << endl;  
}  
\* Output:   
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )  
The element-by-element result of applying MyApplyFunc to vaR is the  
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )  
*\  
```  
  
##  <a name="a-namevalarraycshifta-valarraycshift"></a><a name="valarray__cshift"></a>  valarray:: cshift  
 循環 valarray 中的所有項目移位指定的位置數目。  
  
```  
valarray<Type> cshift(int count) const;
```  
  
### <a name="parameters"></a>參數  
 ` count`  
 項目會向前移動的位置數目。  
  
### <a name="return-value"></a>傳回值  
 已移動之項目的所有新 valarray ` count` 循環朝 valarray，左運算元 valarray 中的位置方面的最上層的位置。  
  
### <a name="remarks"></a>備註  
 正值的 ` count` 切換項目循環左 ` count` 放置。  
  
 負值的 ` count` 移位循環右項目 ` count` 放置。  
  
### <a name="example"></a>範例  
  
```  
// valarray_cshift.cpp  
// compile with: /EHsc  
  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
  
    valarray<int> va1(10), va2(10);  
    for (i = 0; i < 10; i+=1)  
        va1[i] = i;  
    for (i = 0; i < 10; i+=1)  
        va2[i] = 10 - i;  
  
    cout << "The operand valarray va1 is: (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va1[i];  
    cout << ")" << endl;  
  
    // A positive parameter shifts elements right  
    va1 = va1.cshift(4);  
    cout << "The cyclically shifted valarray va1 is:\nva1.cshift (4) = (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va1[i];  
    cout << ")" << endl;  
  
    cout << "The operand valarray va2 is: (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va2[i];  
    cout << ")" << endl;  
  
    // A negative parameter shifts elements left  
    va2 = va2.cshift(-4);  
    cout << "The cyclically shifted valarray va2 is:\nva2.shift (-4) = (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va2[i];  
    cout << ")" << endl;  
}  
\* Output:   
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)  
The cyclically shifted valarray va1 is:  
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)  
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)  
The cyclically shifted valarray va2 is:  
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)  
*\  
```  
  
##  <a name="a-namevalarrayfreea-valarrayfree"></a><a name="valarray__free"></a>  valarray:: free  
 釋出 valarray 所使用的記憶體。  
  
```  
void free();
```  
  
### <a name="remarks"></a>備註  
 這個非標準函式相當於指派的空白 valarray。 例如:   
  
```  
valarray<T> v;  
v = valarray<T>();

// equivalent to v.free()  
```  
  
##  <a name="a-namevalarraymaxa-valarraymax"></a><a name="valarray__max"></a>  valarray:: max  
 Valarray 中尋找最大項目。  
  
```  
Type max() const;
```  
  
### <a name="return-value"></a>傳回值  
 運算元 valarray 中的項目最大值。  
  
### <a name="remarks"></a>備註  
 成員函式比較值，藉由套用 **運算子 \<** 或 **運算子 >** 類別的項目組之間 **類型**, ，哪個運算子必須提供項目的 **類型**。  
  
### <a name="example"></a>範例  
  
```  
// valarray_max.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i, MaxValue;  
  
   valarray<int> vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  2*i - 1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  10 - i;  
  
   cout << "The operand valarray is: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   MaxValue = vaR.max (  );  
   cout << "The largest element in the valarray is: "  
        << MaxValue  << "." << endl;  
}  
\* Output:   
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).  
The largest element in the valarray is: 13.  
*\  
```  
  
##  <a name="a-namevalarraymina-valarraymin"></a><a name="valarray__min"></a>  valarray:: min  
 Valarray 中尋找最小項目。  
  
```  
Type min() const;
```  
  
### <a name="return-value"></a>傳回值  
 運算元 valarray 中的項目最小值。  
  
### <a name="remarks"></a>備註  
 成員函式比較值，藉由套用 **運算子 \<** 或 **運算子 >** 類別的項目組之間 **類型**, ，哪個運算子必須提供項目的 **類型**。  
  
### <a name="example"></a>範例  
  
```  
// valarray_min.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i, MinValue;  
  
   valarray<int> vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  2*i;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  5 - i;  
  
   cout << "The operand valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   MinValue = vaR.min ( );  
   cout << "The smallest element in the valarray is: "  
        << MinValue  << "." << endl;  
}  
\* Output:   
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).  
The smallest element in the valarray is: -9.  
*\  
```  
  
##  <a name="a-namevalarrayoperatornota-valarrayoperator"></a><a name="valarray__operator_not"></a>  valarray:: operator ！  
 取得邏輯的一元運算子 **不** valarray 中的每個項目的值。  
  
```  
valarray<bool> operator!() const;
```  
  
### <a name="return-value"></a>傳回值  
 否定運算元 valarray 的項目值的布林值的 valarray。  
  
### <a name="remarks"></a>備註  
 邏輯作業 **不** 否定的項目，因為轉換變成全部為零，將儲存的所有非零的值並將它們轉換成零。 傳回布林值的 valarray 是大小的運算元 valarray 相同。  
  
 另外還有位元 **不**[valarray:: ~](#valarray__operator_dtor) ，層級的二進位表示法中的個別位元否定運算 `char` 和 `int` valarray 的項目。  
  
### <a name="example"></a>範例  
  
```  
// valarray_op_lognot.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<bool> vaNOT ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT = !vaL;  
   cout << "The element-by-element result of "  
        << "the logical NOT operator! is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The element-by-element result of the logical NOT operator! is the  
 valarray: ( 1 1 1 0 1 0 1 0 1 0 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatormodeqa-valarrayoperator"></a><a name="valarray__operator_mod_eq"></a>  valarray:: operator %=  
 取得部分 element-wise 除以陣列的元素，指定 valarray 或項目類型的值。  
  
```  
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 Valarray 或相同的是要 element-wise，將運算元 valarray 運算元 valarray 的項目型別的值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其元素為運算元 valarray element-wise 除法的餘數的 ` right.`  
  
### <a name="example"></a>範例  
  
```  
// valarray_class_op_rem.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 6 ), vaR ( 6 );  
   for ( i = 0 ; i < 6 ; i += 2 )  
      vaL [ i ] =  53;  
   for ( i = 1 ; i < 6 ; i += 2 )  
      vaL [ i ] =  -67;  
   for ( i = 0 ; i < 6 ; i++ )  
      vaR [ i ] =  3*i+1;  
  
   cout << "The initial valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL %= vaR;  
   cout << "The remainders from the element-by-element "  
        << "division is the\n valarray: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 53 -67 53 -67 53 -67 ).  
The initial  right valarray is: ( 1 4 7 10 13 16 ).  
The remainders from the element-by-element division is the  
 valarray: ( 0 -3 4 -7 1 -3 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorampeqa-valarrayoperatoramp"></a><a name="valarray__operator_amp__eq"></a>  valarray::&amp;=  
 取得位元 **AND** 的項目陣列中指定的 valarray 中的對應項目或項目類型的值。  
  
```  
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 Valarray 或值的項目型別相同的是結合運算元 valarray、 element-wise，由邏輯 **AND** 與運算元 valarray。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其元素為 element-wise 邏輯 **AND** 的運算元 valarray 的 ` right.`  
  
### <a name="remarks"></a>備註  
 位元運算可以只用來操作中的位元 `char` 和 `int` 資料型別和變化而不是在 **float**, ，**double**, ，**longdouble**, ，`void`, ，`bool`, ，或其他更複雜的資料類型。  
  
 位元 AND 具有相同事實資料表的邏輯 **AND** ，但適用於個別位元的層級的資料型別。 指定位元 *b*1 和 *b*2， *b*1 **AND** *b*2 是 **true** 兩個位元皆為 true，如果 **false** 如果至少一個為 false。  
  
### <a name="example"></a>範例  
  
```  
// valarray_class_op_bitand.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL &= vaR;  
   cout << "The element-by-element result of "  
        << "the logical AND operator&= is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the logical AND operator&= is the  
 valarray: ( 0 0 0 2 0 4 0 6 0 8 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorgtgteqa-valarrayoperatorgtgt"></a><a name="valarray__operator_gt__gt__eq"></a>  valarray::&gt;&gt;=  
 右移位的位元 valarray 運算元指定數目的位置，或指定的第二個 valarray element-wise 量的每個項目。  
  
```  
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 值，指出量向右移位或 valarray，其元素表示向右移位 element-wise 數量。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目已向右移位指定的數量 ` right`。  
  
### <a name="remarks"></a>備註  
 帶正負號的數字的保留其符號。  
  
### <a name="example"></a>範例  
  
```  
// valarray_class_op_rs.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  64;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -64;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial operand valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL >>= vaR;  
   cout << "The element-by-element result of "  
        << "the right shift is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).  
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the right shift is the  
 valarray: ( 64 -32 16 -8 4 -2 1 -1 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorltlteqa-valarrayoperatorltlt"></a><a name="valarray__operator_lt__lt__eq"></a>  valarray::&lt;&lt;=  
 左移位的位元 valarray 運算元指定數目的位置，或指定的第二個 valarray element-wise 量的每個項目。  
  
```  
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 值，指出量左的移或 valarray，其元素表示向左移位 element-wise 數量。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目已移位保留指定的數量 ` right`。  
  
### <a name="remarks"></a>備註  
 帶正負號的數字的保留其符號。  
  
### <a name="example"></a>範例  
  
```  
// valarray_class_op_ls.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial operand valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL <<= vaR;  
   cout << "The element-by-element result of "  
        << "the left shift\n on the operand array is the valarray:\n ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).  
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the left shift  
 on the operand array is the valarray:  
 ( 1 -2 4 -8 16 -32 64 -128 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorstareqa-valarrayoperator"></a><a name="valarray__operator_star_eq"></a>  valarray:: operator * =  
 以運算元 valarray element-wise，乘以指定 valarray 的項目或項目類型的值。  
  
```  
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 Valarray 或相同的運算元 valarray element-wise，乘以運算元 valarray 的項目型別的值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其元素為運算元 valarray 的項目乘積和 ` right.`  
  
### <a name="example"></a>範例  
  
```  
// valarray_op_emult.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  2;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL *= vaR;  
   cout << "The element-by-element result of "  
        << "the multiplication is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the multiplication is the  
 valarray: ( 0 -1 4 -3 8 -5 12 -7 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoradda-valarrayoperator"></a><a name="valarray__operator_add"></a>  valarray:: operator +  
 適用於在 valarray 中的每個項目正一元運算子。  
  
```  
valarray<Type> operator+() const;
```  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目會加上這些運算元的陣列。  
  
### <a name="example"></a>範例  
  
```  
// valarray_op_eplus.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<int> vaPLUS ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaPLUS = +vaL;  
   cout << "The element-by-element result of "  
        << "the operator+ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaPLUS [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
The element-by-element result of the operator+ is the  
 valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoraddeqa-valarrayoperator"></a><a name="valarray__operator_add_eq"></a>  valarray:: operator + =  
 將指定 valarray 的項目或項目型別的值 element-wise，運算元 valarray。  
  
```  
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 Valarray 或相同的已加入，element-wise，運算元 valarray 運算元 valarray 的項目型別的值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其元素為運算元 valarray element-wise sum 和 ` right.`  
  
### <a name="example"></a>範例  
  
```  
// valarray_op_eadd.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  2;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL += vaR;  
   cout << "The element-by-element result of "  
        << "the sum is the\n valarray: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the sum is the  
 valarray: ( 2 0 4 2 6 4 8 6 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperator-a-valarrayoperator-"></a><a name="valarray__operator-"></a>  valarray:: operator-  
 適用於在 valarray 中的每個項目是減號，一元運算子。  
  
```  
valarray<Type> operator-() const;
```  
  
### <a name="return-value"></a>傳回值  
 Valarray，其項目是減號的運算元陣列。  
  
### <a name="example"></a>範例  
  
```  
// valarray_op_eminus.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<int> vaMINUS ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaMINUS = -vaL;  
   cout << "The element-by-element result of "  
        << "the operator+ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaMINUS [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
The element-by-element result of the operator+ is the  
 valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperator-eqa-valarrayoperator-"></a><a name="valarray__operator-_eq"></a>  valarray:: operator =  
 從運算元 valarray element-wise，減去指定的 valarray 的項目或項目類型的值。  
  
```  
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 Valarray 或相同的運算元 valarray 要相減，element-wise，運算元 valarray 的項目型別的值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其元素為運算元 valarray element-wise 差異， ` right.`  
  
### <a name="example"></a>範例  
  
```  
// valarray_op_esub.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  10;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL -= vaR;  
   cout << "The element-by-element result of "  
        << "the difference is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).  
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the difference is the  
 valarray: ( 10 -1 8 -3 6 -5 4 -7 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoreqa-valarrayoperator"></a><a name="valarray__operator__eq"></a>  valarray:: operator / =  
 將運算元 valarray element-wise 除以指定 valarray 的項目或項目類型的值。  
  
```  
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 Valarray 或相同的運算元 valarray 分成，element-wise，運算元 valarray 的項目型別的值。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其元素為運算元 valarray element-wise 商數除以 ` right.`  
  
### <a name="example"></a>範例  
  
```  
// valarray_op_ediv.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<double> vaL ( 6 ), vaR ( 6 );  
   for ( i = 0 ; i < 6 ; i += 2 )  
      vaL [ i ] =  100;  
   for ( i = 1 ; i < 6 ; i += 2 )  
      vaL [ i ] =  -100;  
   for ( i = 0 ; i < 6 ; i++ )  
      vaR [ i ] =  2*i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL /= vaR;  
   cout << "The element-by-element result of "  
        << "the quotient is the\n valarray: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 100 -100 100 -100 100 -100 ).  
The initial Right valarray is: ( 0 2 4 6 8 10 ).  
The element-by-element result of the quotient is the  
 valarray: ( 1.#INF -50 25 -16.6667 12.5 -10 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoreqa-valarrayoperator"></a><a name="valarray__operator_eq"></a>  valarray:: operator =  
 將項目指派給 valarray，直接或某些其他 valarray 或 slice_array、 gslice_array、 mask_array 或 indirect_array 所指定的值。  
  
```  
valarray<Type>& operator=(const valarray<Type>& right);

valarray<Type>& operator=(valarray<Type>&& right);

valarray<Type>& operator=(const Type& val);

valarray<Type>& operator=(const slice_array<Type>& _Slicearray);

valarray<Type>& operator=(const gslice_array<Type>& _Gslicearray);

valarray<Type>& operator=(const mask_array<Type>& _Maskarray);

valarray<Type>& operator=(const indirect_array<Type>& _Indarray);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 要複製到運算元 valarray valarray。  
  
 ` val`  
 要指派給運算元 valarray 的項目值。  
  
 `_Slicearray`  
 要複製到運算元 valarray slice_array。  
  
 `_Gslicearray`  
 要複製到運算元 valarray gslice_array。  
  
 `_Maskarray`  
 要複製到運算元 valarray mask_array。  
  
 `_Indarray`  
 要複製到運算元 valarray indirect_array。  
  
### <a name="return-value"></a>傳回值  
 第一個成員運算子所控制之序列的複本取代受控制的序列 ` right`。  
  
 第二個成員運算子是第一次，但具有相同 [右值參考宣告子︰ & &](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
 第三個成員運算子的複本來取代受控制序列的每個項目 ` val`。  
  
 其餘成員運算子來取代這些項目，其引數會產生只有所選取的受控制序列的 [運算子 &#91; &#93;](#valarray__operator_at)。  
  
 如果取代受控制序列中的值取決於初始受控制序列中的成員，則結果會是成員的未定義。  
  
### <a name="remarks"></a>備註  
 如果變更受控制序列的長度，結果是通常未定義。 在此實作中，不過，結果是只是要使其失效的任何指標或控制序列中項目的參考。  
  
### <a name="example"></a>範例  
  
```  
// valarray_op_assign.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va [ i ] = i;  
   for ( i = 0 ; i < 10 ; i+=1 )  
      vaR [ i ] = 10 -  i;  
  
   cout << "The operand valarray va is:";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << " " << va [ i ];  
   cout << endl;  
  
   cout << "The operand valarray vaR is:";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << " " << vaR [ i ];  
   cout << endl;  
  
   // Assigning vaR to va with the first member functon  
   va = vaR;  
   cout << "The reassigned valarray va is:";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << " " << va [ i ];  
   cout << endl;  
  
   // Assigning elements of value 10 to va  
   // with the second member functon  
   va = 10;  
   cout << "The reassigned valarray va is:";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << " " << va [ i ];  
   cout << endl;  
}  
\* Output:   
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9  
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1  
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1  
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10  
*\  
```  
  
##  <a name="a-namevalarrayoperatorata-valarrayoperator"></a><a name="valarray__operator_at"></a>  valarray:: operator]  
 傳回項目參考或其指定索引處的值或指定的子集。  
  
```  
Type& operator[](size_t _Off);

slice_array<Type> operator[](slice _Slicearray);

gslice_array<Type> operator[](const gslice& _Gslicearray);

mask_array<Type> operator[](const valarray<bool>& _Boolarray);

indirect_array<Type> operator[](const valarray<size_t>& _Indarray);

Type operator[](size_t _Off) const;

 
valarray<Type> operator[](slice _Slice) const;

 
valarray<Type> operator[](const gslice& _Gslicearray) const;

 
valarray<Type> operator[](const valarray<bool>& _Boolarray) const;

 
valarray<Type> operator[](const valarray<size_t>& _Indarray) const;
```  
  
### <a name="parameters"></a>參數  
 `_Off`  
 要指派值的項目索引。  
  
 `_Slicearray`  
 指定要選取或新 valarray 傳回到子集 valarray 的 slice_array。  
  
 `_Gslicearray`  
 指定要選取或新 valarray 傳回到子集 valarray 的 gslice_array。  
  
 *_Boolarray*  
 指定要選取或新 valarray 傳回到子集 valarray 的 bool_array。  
  
 `_Indarray`  
 Indirect_array，指定要選取或新 valarray 傳回到子集 valarray。  
  
### <a name="return-value"></a>傳回值  
 參考項目或其值在指定的索引或指定的子集。  
  
### <a name="remarks"></a>備註  
 成員運算子多載之後可提供數種方式選取項目，從所控制的序列 *\****這**。 第五個成員運算子一組與合作的各種多載 [運算子 =](#valarray__operator_eq) （和其他指派運算子） 以允許選擇性取代 （配量） 的受控制序列。 選取的項目必須存在。  
  
 使用 _SECURE_SCL 1 編譯時，如果您嘗試存取超出界限的 valarray 的項目，會發生執行階段錯誤。  如需詳細資訊，請參閱 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>範例  
  請參閱範例 [slice:: slice](../standard-library/slice-class.md#slice__slice) 和 [gslice:: gslice](../standard-library/gslice-class.md#gslice__gslice) 如需如何宣告和使用運算子的範例。  
  
##  <a name="a-namevalarrayoperatorxoreqa-valarrayoperator"></a><a name="valarray__operator_xor_eq"></a>  valarray:: operator ^ =  
 取得 element-wise 獨佔邏輯 or 運算子 ( **XOR**) 的陣列指定的 valarray 或項目類型的值。  
  
```  
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 Valarray 或相同的是結合運算元 valarray、 element-wise 邏輯專用的項目型別的值 **XOR** 與運算元 valarray。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其元素為 element-wise，專用邏輯 **XOR** 運算元 valarray 的 ` right.`  
  
### <a name="remarks"></a>備註  
 獨佔邏輯或，稱為 **XOR**, ，具有下列語意︰ 提供項目 *e*1 和 *e*2， *e*1 **XOR** *e*2 是 **true** 只有其中一個項目是否為 true， **false** 如果這兩個項目，則為 false，或如果兩個項目，則為 true。  
  
### <a name="example"></a>範例  
  
```  
// valarray_op_exor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
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
  
   cout << "The initial operand valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL ^= vaR;  
   cout << "The element-by-element result of "  
        << "the bitwise XOR operator^= is the\n valarray: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).  
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the bitwise XOR operator^= is the  
 valarray: ( 1 0 0 3 2 4 7 6 6 9 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatororeqa-valarrayoperator124"></a><a name="valarray__operator_or_eq"></a>  valarray:: &#124; =  
 取得位元 `OR` 的項目陣列中指定的 valarray 中的對應項目或項目類型的值。  
  
```  
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 Valarray 或值的項目型別相同的是結合運算元 valarray、 element-wise 的位元 `OR` 與運算元 valarray。  
  
### <a name="return-value"></a>傳回值  
 Valarray，其元素為位元 element-wise `OR` 的運算元 valarray 的 ` right.`  
  
### <a name="remarks"></a>備註  
 位元運算可以只用來操作中的位元 `char` 和 `int` 資料型別和變化而不是在 **float**, ，**double**, ，**longdouble**, ，`void`, ，`bool`, ，或其他更複雜的資料類型。  
  
 位元 `OR` 具有相同事實資料表的邏輯 `OR` ，但適用於個別位元的層級的資料型別。 指定位元 *b*1 和 *b*2， *b*1 `OR` *b*2 是 **true** 至少其中一個位元則為 true; 如果 **false** 如果兩個位元皆為 false。  
  
### <a name="example"></a>範例  
  
```  
// valarray_class_op_bitor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
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
  
   cout << "The initial operand valarray is:\n ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is:\n ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL |= vaR;  
   cout << "The element-by-element result of "  
        << "the logical OR\n operator|= is the valarray:\n ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  
 ( 1 0 1 0 1 0 1 0 1 0 ).  
The  right valarray is:  
 ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the logical OR  
 operator|= is the valarray:  
 ( 1 0 1 3 3 4 7 6 7 9 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatordtora-valarrayoperator"></a><a name="valarray__operator_dtor"></a>  valarray:: ~  
 取得位元的一元運算子 **不** valarray 中的每個項目的值。  
  
```  
valarray<Type> operator~() const;
```  
  
### <a name="return-value"></a>傳回值  
 布林值的位元的 valarray **不** 運算元 valarray 的項目值。  
  
### <a name="remarks"></a>備註  
 位元運算可以只用來操作中的位元 `char` 和 `int` 資料型別和變化而不是在 **float**, ，**double**, ，**longdouble**, ，`void`, ，`bool` 或其他更複雜的資料類型。  
  
 位元 **不** 具有相同事實資料表的邏輯 **不** ，但適用於個別位元的層級的資料型別。 指定元 *b*, ，~ *b* 成立如果 *b* 為 true，false *b* 為 true。 邏輯 **不**[運算子 ！](#valarray__operator_not) 計算所有非零的值做為項目層級上套用 **true**, ，且結果為布林值的 valarray。 位元 **NOToperator ~**, ，相較之下，可能會導致 valarray 的值不是 0 或 1，根據位元運算的結果。  
  
### <a name="example"></a>範例  
  
```  
// valarray_op_bitnot.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<unsigned short int> vaL1 ( 10 );  
   valarray<unsigned short int> vaNOT1 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL1 [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL1 [ i ] =  5*i;  
  
   cout << "The initial valarray <unsigned short int> is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL1 [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT1 = ~vaL1;  
   cout << "The element-by-element result of "  
        << "the bitwise NOT operator~ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT1 [ i ] << " ";  
   cout << ")." << endl << endl;  
  
   valarray<int> vaL2 ( 10 );  
   valarray<int> vaNOT2 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL2 [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL2 [ i ] =  -2 * i;  
  
   cout << "The initial valarray <int> is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL2 [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT2 = ~vaL2;  
   cout << "The element-by-element result of "  
        << "the bitwise NOT operator~ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT2 [ i ] << " ";  
   cout << ")." << endl;  
  
   // The negative numbers are represented using  
   // the two's complement approach, so adding one  
   // to the flipped bits returns the negative elements  
   vaNOT2 = vaNOT2 + 1;  
   cout << "The element-by-element result of "  
        << "adding one\n is the negative of the "  
        << "original elements the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT2 [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).  
The element-by-element result of the bitwise NOT operator~ is the  
 valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).  
  
The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).  
The element-by-element result of the bitwise NOT operator~ is the  
 valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).  
The element-by-element result of adding one  
 is the negative of the original elements the  
 valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).  
*\  
```  
  
##  <a name="a-namevalarrayresizea-valarrayresize"></a><a name="valarray__resize"></a>  valarray:: resize  
 將 valarray 中的項目數變更為指定的數字。  
  
```  
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,   
    const Type val);
```  
  
### <a name="parameters"></a>參數  
 `_Newsize`  
 重新調整大小的 valarray 中的項目數。  
  
 ` val`  
 要指定給重新調整大小的 valarray 項目的值。  
  
### <a name="remarks"></a>備註  
 第一個成員函式會使用其預設建構函式來初始化項目。  
  
 控制序列中項目的任何指標或參考都會失效。  
  
### <a name="example"></a>範例  
  下列範例示範 valarray::resize 成員函式的使用。  
  
```  
// valarray_resize.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
    size_t size1, sizeNew;  
  
    valarray<int> va1(10);  
    for (i = 0; i < 10; i+=1)  
        va1[i] = i;  
  
    cout << "The valarray contains ( ";  
        for (i = 0; i < 10; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
  
    size1 = va1.size();  
    cout << "The number of elements in the valarray is: "  
         << size1  << "." <<endl << endl;  
  
    va1.resize(15, 10);  
  
    cout << "The valarray contains ( ";  
        for (i = 0; i < 15; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
    sizeNew = va1.size();  
    cout << "The number of elements in the resized valarray is: "  
         << sizeNew  << "." <<endl << endl;  
}  
\* Output:   
The valarray contains ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray is: 10.  
  
The valarray contains ( 10 10 10 10 10 10 10 10 10 10 10 10 10 10 10 ).  
The number of elements in the resized valarray is: 15.  
*\  
```  
  
##  <a name="a-namevalarrayshifta-valarrayshift"></a><a name="valarray__shift"></a>  valarray:: shift  
 將指定的數位數 valarray 中的所有項目。  
  
```  
valarray<Type> shift(int count) const;
```  
  
### <a name="parameters"></a>參數  
 ` count`  
 項目會向前移動的位置數目。  
  
### <a name="return-value"></a>傳回值  
 已移動之項目的所有新 valarray ` count` valarray，左運算元 valarray 中的位置方面的前端的位置。  
  
### <a name="remarks"></a>備註  
 正值的 ` count` 將元素向左 ` count` 地方，使用零填滿。  
  
 負值的 ` count` 切換項目靠右 ` count` 地方，使用零填滿。  
  
### <a name="example"></a>範例  
  
```  
// valarray_shift.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va1 ( 10 ), va2 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va1 [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va2 [ i ] = 10 -  i;  
  
   cout << "The operand valarray va1(10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va1 [ i ] << " ";  
   cout << ")." << endl;  
  
   // A positive parameter shifts elements left  
   va1 = va1.shift ( 4 );  
   cout << "The shifted valarray va1 is: va1.shift (4) = ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va1 [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The operand valarray va2(10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va2 [ i ] << " ";  
   cout << ")." << endl;  
  
   // A negative parameter shifts elements right  
   va2 = va2.shift ( - 4 );  
   cout << "The shifted valarray va2 is: va2.shift (-4) = ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va2 [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).  
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).  
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).  
*\  
```  
  
##  <a name="a-namevalarraysizea-valarraysize"></a><a name="valarray__size"></a>  valarray:: size  
 尋找 valarray 中的項目數目。  
  
```  
size_t size() const;
```  
  
### <a name="return-value"></a>傳回值  
 運算元 valarray 中的項目數目。  
  
### <a name="example"></a>範例  
  下列範例示範 valarray::size 成員函式的使用。  
  
```  
// valarray_size.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
    size_t size1, size2;  
  
    valarray<int> va1(10), va2(12);  
    for (i = 0; i < 10; i += 1)  
        va1[i] =  i;  
    for (i = 0; i < 10; i += 1)  
        va2[i] =  i;  
  
    cout << "The operand valarray va1(10) is: ( ";  
        for (i = 0; i < 10; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
  
    size1 = va1.size();  
    cout << "The number of elements in the valarray va1 is: va1.size = "  
         << size1  << "." <<endl << endl;  
  
    cout << "The operand valarray va2(12) is: ( ";  
        for (i = 0; i < 10; i++)  
            cout << va2[i] << " ";  
    cout << ")." << endl;  
  
    size2 = va2.size();  
    cout << "The number of elements in the valarray va2 is: va2.size = "  
         << size2  << "." << endl << endl;  
  
    // Initializing two more elements to va2  
    va2[10] = 10;  
    va2[11] = 11;  
    cout << "After initializing two more elements,\n "  
         << "the operand valarray va2(12) is now: ( ";  
        for (i = 0; i < 12; i++)  
            cout << va2[i] << " ";  
    cout << ")." << endl;  
    cout << "The number of elements in the valarray va2 is still: "  
         << size2  << "." << endl;  
}  
\* Output:   
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray va1 is: va1.size = 10.  
  
The operand valarray va2(12) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray va2 is: va2.size = 12.  
  
After initializing two more elements,  
 the operand valarray va2(12) is now: ( 0 1 2 3 4 5 6 7 8 9 10 11 ).  
The number of elements in the valarray va2 is still: 12.  
*\  
```  
  
##  <a name="a-namevalarraysuma-valarraysum"></a><a name="valarray__sum"></a>  valarray:: sum  
 判斷為非零長度的 valarray 中的所有項目的總和。  
  
```  
Type sum() const;
```  
  
### <a name="return-value"></a>傳回值  
 運算元 valarray 的項目的總和。  
  
### <a name="remarks"></a>備註  
 長度大於一，如果成員函式中加入值總和藉由套用 `operator+=` 類別的項目組之間 **類型**, ，哪個運算子，因此，需要提供類型項目的 **類型**。  
  
### <a name="example"></a>範例  
  
```  
// valarray_sum.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   int sumva = 0;  
  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i+=1 )  
      va [ i ] =  i;  
  
   cout << "The operand valarray va (10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   sumva = va.sum ( );  
   cout << "The sum of elements in the valarray is: "  
        << sumva  << "." <<endl;  
}  
\* Output:   
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The sum of elements in the valarray is: 45.  
*\  
```  
  
##  <a name="a-namevalarrayswapa-valarrayswap"></a><a name="valarray__swap"></a>  valarray:: swap  
 交換兩個 `valarray` 的項目。  
  
```  
void swap(valarray& right);
```  
  
### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|` right`|`valarray`，提供要交換的項目。|  
  
### <a name="remarks"></a>備註  
 成員函式會交換 `*this` 和 ` right` 之間受控制的序列。 它以常數時間如此執行，不擲回例外狀況，並且不會使指定此兩個受控制序列中項目的任何參考、指標或迭代器失效。  
  
##  <a name="a-namevalarrayvalarraya-valarrayvalarray"></a><a name="valarray__valarray"></a>  valarray:: valarray  
 建構 valarray，其具有特定大小或具有特定值之項目，或做為另一個 valarray 的複本或另一個 valarray 的子集。  
  
```  
valarray();

explicit valarray(
    size_t Count);

valarray(
    const Type& Val,   
    size_t Count);

valarray(
    const Type* Ptr,   
    size_t Count);

valarray(
    const valarray<Type>& Right);

valarray(
    const slice_array<Type>& SliceArray);

valarray(
    const gslice_array<Type>& GsliceArray);

valarray(
    const mask_array<Type>& MaskArray);

valarray(
    const indirect_array<Type>& IndArray);

valarray(
    valarray<Type>&& Right);

valarray(
    initializer_list<Type> IList);
```  
  
### <a name="parameters"></a>參數  
 `Count`  
 要放在 valarray 中的項目數目。  
  
 `Val`  
 用來初始化 valarray 中之項目的值。  
  
 `Ptr`  
 值指標，這些值要用來初始化 valarray 中之項目。  
  
 `Right`  
 用來初始化新 valarray 的現有 valarray。  
  
 `SliceArray`  
 slice_array，其項目值要用來初始化建構中 valarray 的項目。  
  
 `GsliceArray`  
 gslice_array，其項目值要用來初始化建構中 valarray 的項目。  
  
 `MaskArray`  
 mask_array，其項目值要用來初始化建構中 valarray 的項目。  
  
 `IndArray`  
 indirect_array，其項目值要用來初始化建構中 valarray 的項目。  
  
 `IList`  
 initializer_list，包含欲複製的項目。  
  
### <a name="remarks"></a>備註  
 第一個 (預設) 建構函式將物件初始化為空陣列。 接下來的三個建構函式個別初始化物件為 `Count` 項目的陣列，如下：  
  
-   如果是明確 `valarray(size_t Count)`，以預設建構函式初始化每個項目。  
  
-   對於 `valarray(const Type& Val, Count)`，以 `Val` 初始化每個項目。  
  
-   如 `valarray(const Type* Ptr, Count)`, ，位置的項目 `I` 初始化 `Ptr`[ `I`]。  
  
 每個剩餘的建構函式初始化物件為 valarray \< 類型> 物件由引數所指定的子集所決定。  
  
 最後一個建構函式相當於下一步] 上一次，但 [右值參考宣告子︰ & &](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
### <a name="example"></a>範例  
  
```  
// valarray_ctor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
  
    // The second member function  
    valarray<int> va(10);  
    for (auto i : va){  
        va[i] = 2 * (i + 1);  
    }  
  
    cout << "The operand valarray va is:\n(";  
    for (auto i : va) {  
        cout << " " << va[i];  
    }  
    cout << " )" << endl;  
  
    slice Slice(2, 4, 3);  
  
    // The fifth member function  
    valarray<int> vaSlice = va[Slice];  
  
    cout << "The new valarray initialized from the slice is vaSlice ="  
        << "\nva[slice( 2, 4, 3)] = (";  
    for (int i = 0; i < 3; i++) {  
        cout << " " << vaSlice[i];  
    }  
    cout << " )" << endl;  
  
    valarray<int> va2{{ 1, 2, 3, 4 }};  
    for (auto& v : va2){  
        cout << v << " ";  
    }  
    cout << endl;  
}  
  
```  
  
```Output  
The operand valarray va is:( 0 2 2 2 2 2 2 2 2 2 )The new valarray initialized from the slice is vaSlice =va[slice( 2, 4, 3)] = ( 0 0 0 )1 2 3 4  
```  
  
##  <a name="a-namevalarrayvaluetypea-valarrayvaluetype"></a><a name="valarray__value_type"></a>  valarray:: value_type  
 表示儲存在 valarray 中的項目類型的類型。  
  
```  
typedef Type value_type;  
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **類型**。  
  
### <a name="example"></a>範例  
  
```  
// valarray_value_type.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      va [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      va [ i ] =  -1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   // value_type declaration and initialization:  
   valarray<int>::value_type Right = 10;  
  
   cout << "The decalared value_type Right is: "   
           << Right << endl;  
   va *= Right;  
   cout << "The resulting valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).  
The decalared value_type Right is: 10  
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).  
*\  
```  
  
## <a name="see-also"></a>另請參閱  
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

