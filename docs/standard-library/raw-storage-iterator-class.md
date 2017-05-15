---
title: "raw_storage_iterator 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- raw_storage_iterator
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
dev_langs:
- C++
helpviewer_keywords:
- raw_storage_iterator class
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
caps.latest.revision: 17
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
ms.openlocfilehash: 46bfc6bc42e09348d0760f7d03d70c816fde31ed
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="rawstorageiterator-class"></a>raw_storage_iterator 類別
提供的配接器類別，可讓演算法將其結果儲存至未初始化的記憶體。  
  
## <a name="syntax"></a>語法  
  
```
template <class OutputIterator, class Type>  
class raw_storage_iterator
```  
  
#### <a name="parameters"></a>參數  
 `OutputIterator`  
 指定要儲存之物件的輸出迭代器。  
  
 *Type*  
 正在配置儲存體的物件類型。  
  
## <a name="remarks"></a>備註  
 此類別說明輸出迭代器，該迭代器會在它產生的序列中建構 **Type** 類型的物件。 `raw_storage_iterator`\< **ForwardIterator**, **Type**> 類別的物件會透過 **ForwardIterator** 類別 (此類別是您在建構物件時所指定) 的正向迭代器物件來存取儲存體。 針對 **ForwardIterator** 類別的第一個物件，運算式 **&\*first** 必須將未建構的儲存體指定給所產生序列中下一個類型為 **Type** 的物件。  
  
 當有需要分隔記憶體配置和物件建構時，會使用此配接器類別。 `raw_storage_iterator` 可以用來將物件複製到未初始化的儲存體，例如使用`malloc` 函式配置的記憶體。  
  
## <a name="members"></a>成員  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[raw_storage_iterator](#raw_storage_iterator)|藉由指定的基礎輸出迭代器建構原始儲存體迭代器。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[element_type](#element_type)|提供一個類型，其描述要儲存在原始儲存體的項目。|  
|[iter_type](#iter_type)|提供一個類型，其描述為原始儲存體迭代器基礎的迭代器。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator*](#op_star)|取值運算子，用來實作輸出迭代器運算式 * `ii` = `x`。|  
|[operator=](#op_eq)|指派運算子，用來實作原始儲存體迭代器運算式 * `i` = `x` 以儲存於記憶體中。|  
|[operator++](#op_add_add)|原始儲存體迭代器的前置遞增和後置遞增運算子。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<memory>  
  
 **命名空間：** std  
  
##  <a name="element_type"></a>  raw_storage_iterator::element_type  
 提供一個類型，其描述要儲存在原始儲存體的項目。  
  
```
typedef Type element_type;
```  
  
### <a name="remarks"></a>備註  
 此類型與 raw_storage_iterator 類別範本參數 **Type** 同義。  
  
##  <a name="iter_type"></a>  raw_storage_iterator::iter_type  
 提供一個類型，其描述為原始儲存體迭代器基礎的迭代器。  
  
```
typedef ForwardIterator iter_type;
```  
  
### <a name="remarks"></a>備註  
 此類型與範本參數 **ForwardIterator** 同義。  
  
##  <a name="op_star"></a>  raw_storage_iterator::operator*  
 取值運算子，用來實作原始儲存體迭代器運算式 \* *ii* = *x*。  
  
```
raw_storage_iterator<ForwardIterator, Type>& operator*();
```  
  
### <a name="return-value"></a>傳回值  
 原始儲存體迭代器的參考  
  
### <a name="remarks"></a>備註  
 **ForwardIterator** 的需求是原始儲存體迭代器必須確信只要求運算式 \* *ii* = *t* 有效，且本身不涉及**運算子**或 `operator=`。 此實作中的成員運算子會傳回 **\*this**，因此，[operator=](#op_eq)( **constType**&) 可以在運算式中執行實際儲存，例如 \* *ptr* = `val`。  
  
### <a name="example"></a>範例  
  
```cpp  
// raw_storage_iterator_op_deref.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iterator>  
#include <memory>  
#include <list>  
using namespace std;  
  
class Int   
{  
public:  
   Int(int i)   
   {  
      cout << "Constructing " << i << endl;   
      x = i;  
      bIsConstructed = true;  
   };  
  
   Int &operator=(int i)   
   {  
      if (!bIsConstructed)  
         cout << "Not constructed.\n";  
      cout << "Copying " << i << endl;    
      x = i;   
      return *this;  
   };  
  
   int x;  
  
private:  
   bool bIsConstructed;  
};  
  
int main( void)   
{  
   Int *pInt = ( Int* ) malloc( sizeof( Int ) );  
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;  
 *pInt = 5;  
   raw_storage_iterator< Int*, Int > it( pInt );  
 *it = 5;  
}  
\* Output:   
Not constructed.  
Copying 5  
Constructing 5  
*\  
```  
  
##  <a name="op_eq"></a>  raw_storage_iterator::operator=  
 指派運算子，用來實作原始儲存體迭代器運算式 \* *i* = *x* 以儲存於記憶體中。  
  
```
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```  
  
### <a name="parameters"></a>參數  
 `val`  
 要插入記憶體且類型為 **Type** 的物件值。  
  
### <a name="return-value"></a>傳回值  
 運算子會將 `val` 插入記憶體，然後傳回原始儲存體迭代器的參考。  
  
### <a name="remarks"></a>備註  
 **ForwardIterator** 的需求說明原始儲存體迭代器必須確信只要求運算式 \* *ii* = *t* 有效，且本身不涉及**運算子**或 `operator=`。 這些成員運算子會傳回 **\*this**。  
  
 指派運算子會先使用預存的迭代器值來建構輸出序列中的下一個物件，方法是評估新運算式 **new** ( ( `void` \*)&\* **first**) **Type**( `val`) 的放置。  
  
### <a name="example"></a>範例  
  
```cpp  
// raw_storage_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iterator>  
#include <memory>  
#include <list>  
using namespace std;  
  
class Int   
{  
public:  
   Int( int i )   
   {  
      cout << "Constructing " << i << endl;   
      x = i;  
      bIsConstructed = true;  
   };  
   Int &operator=( int i )   
   {  
      if ( !bIsConstructed )  
         cout << "Not constructed.\n";  
      cout << "Copying " << i << endl; x = i;  
      return *this;  
   };  
   int x;  
private:  
   bool bIsConstructed;  
};  
  
int main( void )  
{  
   Int *pInt = ( Int* )malloc( sizeof( Int ) );  
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;  
  
 *pInt = 5;  
  
   raw_storage_iterator<Int*, Int> it( pInt );  
 *it = 5;  
}  
\* Output:   
Not constructed.  
Copying 5  
Constructing 5  
*\  
```  
  
##  <a name="op_add_add"></a>  raw_storage_iterator::operator++  
 原始儲存體迭代器的前置遞增和後置遞增運算子。  
  
```
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```  
  
### <a name="return-value"></a>傳回值  
 原始儲存體迭代器或原始儲存體迭代器的參考。  
  
### <a name="remarks"></a>備註  
 第一個運算子最後會嘗試從關聯的輸入資料流中擷取並儲存 **CharType** 類型的物件。 第二個運算子會複製物件、遞增物件，然後傳回複本。  
  
 第一個前置遞增運算子會遞增預存的輸出迭代器物件，然後傳回 **\*this**。  
  
 第二個後置遞增運算子則會複製 **\*this**、遞增預存的輸出迭代器物件，然後傳回複本。  
  
 建構函式會儲存 **first** 做為輸出迭代器物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// raw_storage_iterator_op_incr.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iterator>  
#include <memory>  
#include <list>  
using namespace std;  
  
int main( void )  
{  
   int *pInt = new int[5];  
   std::raw_storage_iterator<int*,int> it( pInt );  
   for ( int i = 0; i < 5; i++, it++ ) {  
 *it = 2 * i;  
};  
  
   for ( int i = 0; i < 5; i++ ) cout << "array " << i << " = " << pInt[i] << endl;;  
  
   delete[] pInt;  
}  
\* Output:   
array 0 = 0  
array 1 = 2  
array 2 = 4  
array 3 = 6  
array 4 = 8  
*\  
```  
  
##  <a name="raw_storage_iterator"></a>  raw_storage_iterator::raw_storage_iterator  
 藉由指定的基礎輸出迭代器建構原始儲存體迭代器。  
  
```
explicit raw_storage_iterator(ForwardIterator first);
```  
  
### <a name="parameters"></a>參數  
 `first`  
 正向迭代器，是構成要建構之 `raw_storage_iterator` 物件的基礎。  
  
### <a name="example"></a>範例  
  
```cpp  
// raw_storage_iterator_ctor.cpp  
// compile with: /EHsc /W3  
#include <iostream>  
#include <iterator>  
#include <memory>  
#include <list>  
using namespace std;  
  
class Int  
{  
public:  
   Int(int i)  
   {  
      cout << "Constructing " << i << endl;  
      x = i;  
      bIsConstructed = true;  
   };  
   Int &operator=( int i )  
   {  
      if (!bIsConstructed)  
         cout << "Error! I'm not constructed!\n";  
      cout << "Copying " << i << endl;  x = i; return *this;  
   };  
   int x;  
   bool bIsConstructed;  
};  
  
int main( void )  
{  
   std::list<int> l;  
   l.push_back( 1 );  
   l.push_back( 2 );  
   l.push_back( 3 );  
   l.push_back( 4 );  
  
   Int *pInt = (Int*)malloc(sizeof(Int)*l.size( ));  
   memset (pInt, 0, sizeof(Int)*l.size( ));  
   // Hack: make sure bIsConstructed is false  
  
   std::copy( l.begin( ), l.end( ), pInt );  // C4996  
   for (unsigned int i = 0; i < l.size( ); i++)  
      cout << "array " << i << " = " << pInt[i].x << endl;;  
  
   memset (pInt, 0, sizeof(Int)*l.size( ));  
   // hack: make sure bIsConstructed is false  
  
   std::copy( l.begin( ), l.end( ),  
      std::raw_storage_iterator<Int*,Int>(pInt));  // C4996  
   for (unsigned int i = 0; i < l.size( ); i++ )  
      cout << "array " << i << " = " << pInt[i].x << endl;  
  
   free(pInt);  
}  
\* Output:   
Error! I'm not constructed!  
Copying 1  
Error! I'm not constructed!  
Copying 2  
Error! I'm not constructed!  
Copying 3  
Error! I'm not constructed!  
Copying 4  
array 0 = 1  
array 1 = 2  
array 2 = 3  
array 3 = 4  
Constructing 1  
Constructing 2  
Constructing 3  
Constructing 4  
array 0 = 1  
array 1 = 2  
array 2 = 3  
array 3 = 4  
*\  
```  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




