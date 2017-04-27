---
title: "bitset 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- bitset/std::bitset
- bitset
- bitset/std::bitset::element_type
- bitset/std::bitset::all
- bitset/std::bitset::any
- bitset/std::bitset::count
- bitset/std::bitset::flip
- bitset/std::bitset::none
- bitset/std::bitset::reset
- bitset/std::bitset::set
- bitset/std::bitset::size
- bitset/std::bitset::test
- bitset/std::bitset::to_string
- bitset/std::bitset::to_ullong
- bitset/std::bitset::to_ulong
- bitset/std::bitset::reference
dev_langs:
- C++
helpviewer_keywords:
- bitset class
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
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
ms.sourcegitcommit: 441f493d8ada3ef232f60d917dc3f95812ba9114
ms.openlocfilehash: 2e78e22c04bac149694a4c4f860074296c7b37fc
ms.lasthandoff: 02/24/2017

---
# <a name="bitset-class"></a>bitset 類別
描述物件類型，其可儲存由固定位元數所組成的序列，以提供精簡的方式，來保留一組項目或條件的旗標。 bitset 類別支援類型 bitset 物件上的作業，該作業包含位元的集合，並提供每一個位元的常數時間存取。  
  
## <a name="syntax"></a>語法  
  
```  
template <size_t N>  
class bitset  
```  
  
#### <a name="parameters"></a>參數  
 *N*  
 指定 bitset 物件中的位元數，搭配非零整數的類型 **size_t**，其在編譯時期必須為已知。  
  
## <a name="remarks"></a>備註  
 不同於類似的 [vector\<bool> 類別](../standard-library/vector-bool-class.md)，bitset 類別並沒有迭代器，而且不是 C++ 標準程式庫容器。 它也與 vector\<bool> 在編譯時期固定的指定大小相異，與樣板參數 **N** 在 **bitset\<N\>** 宣告時指定的大小一致。  
  
 如果位元值為 1 則設定位元，如果其值為 0 則重設。 若要翻轉或反轉位元，方法是從 1 到 0 或從 0 到 1 變更其值。 bitset 中的 **N** 位元會由從 0 到 **N** - 1 的整數值編製索引，其中 0 為第一個位元位置的索引，**N** - 1 是最終位元位置。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[bitset](#bitset__bitset)|建構 `bitset\<N>` 類別的物件並將此位元初始化為零、某指定值或字串字元中取得的值。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[element_type](#bitset__element_type)|資料類型 `bool` 同義字的類型，可以用來參考 `bitset` 中的項目位元。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[all](#bitset__all)|測試這個 `bitset` 中的所有位元，以判斷是否全部設定為 `true`。|  
|[any](#bitset__any)|此成員函式會測試該序列中的任何位元是否設為 1。|  
|[count](#bitset__count)|此成員函式會傳回位元序列中設定的位元數。|  
|[flip](#bitset__flip)|反轉 `bitset` 中的所有位元值，或在指定位置反轉單一位元。|  
|[none](#bitset__none)|測試在 `bitset` 物件中是否沒有已設為 1 的位元。|  
|[reset](#bitset__reset)|將 `bitset` 中的所有位元重設為 0，或將指定位置的位元重設為 0。|  
|[set](#bitset__set)|將 `bitset` 中的所有位元設為 1，或將指定位置的位元設為 1。|  
|[size](#bitset__size)|傳回 `bitset` 物件中的位元數。|  
|[test](#bitset__test)|測試位於 `bitset` 中指定位置的位元是否設為 1。|  
|[to_string](#bitset__to_string)|將 `bitset` 物件轉換為字串表示。|  
|[to_ullong](#bitset__to_ullong)|以 `unsigned long long` 傳回 `bitset` 中的位元值總和。|  
|[to_ulong](#bitset__to_ulong)|將 `bitset` 物件轉換成 `unsigned long`，如果用來初始化 `bitset`，其可能產生所包含位元的序列。|  
  
### <a name="member-classes"></a>成員類別  
  
|||  
|-|-|  
|[reference](#bitset__reference)|Proxy 類別，提供參考給包含於 `bitset` 中的位元，而 bitset 是用來存取及管理做為類別 `bitset` 之 `operator[]` 協助程式類別的個別位元。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator!=](#bitset__operator_neq)|測試目標 `bitset` 是否與指定的 `bitset` 不相等。|  
|[operator&=](#bitset__operator_and_eq)|以邏輯 `AND` 作業執行 bitset 的位元組合。|  
|[operator<<](#bitset__operator_lshift)|以位置的指定數目將 `bitset` 中的位元移位至左邊，並傳回結果至新的 `bitset`。|  
|[operator<<=](#bitset__operator_lshift_eq)|以位置的指定數目將 `bitset` 中的位元移位至左邊，並傳回結果至目標的 `bitset`。|  
|[operator==](#bitset__operator_eq_eq)|測試目標 `bitset` 是否與指定之 `bitset` 相等。|  
|[operator>>](#bitset__operator_rshift)|以位置的指定數目將 `bitset` 中的位元移位至右邊，並傳回結果至新的 `bitset`。|  
|[operator>>=](#bitset__operator_rshift_eq)|以位置的指定數目將 `bitset` 中的位元移位至右邊，並傳回結果至目標的 `bitset`。|  
|[operator&#91;&#93;](#bitset__operator_at)|如果 `bitset` 可修改，則傳回位於 `bitset` 中指定位置的位元參考；否則它會傳回該位置的位元值。|  
|[operator^=](#bitset__operator_xor_eq)|以互斥 `OR` 作業執行 bitset 的位元組合。|  
|[operator&#124;=](#bitset__operator_or_eq')|以包含 `OR` 作業執行 bitset 的位元組合。|  
|[operator~](#bitset__operator_dtor)|反轉目標 `bitset` 中的所有位元，並傳回結果。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<bitset>  
  
 **命名空間：** std  
  
##  <a name="bitset__all"></a>  bitset::all  
 測試這個位元集中的所有位元，以判斷是否全部設定為 true。  
  
```  
bool all() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果這個集合中的所有位元都為 true，則傳回 true。 如果一或多個位元為 false，則傳回 **false**。  
  
##  <a name="bitset__any"></a>  bitset::any  
 測試序列中是否有任何位元設為 1。  
  
```  
bool any() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果 bitset 中有任何位元設為 1，則為 **true**；如果所有位元都是 0，則為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_any.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 6 );  
   bool b, rb;  
  
   cout << "The original bitset b1( 6 ) is: ( "<< b1 << " )"  
        << endl;  
  
   b = b1.any ( );  
  
   if ( b )  
      cout << "At least one of the bits in bitset is set to 1."  
           << endl;  
   else  
      cout << "None of the bits in bitset are set to 1."  
           << endl;  
  
   bitset<5> rb1;  
   rb1 = b1.reset ( );  
  
   cout << "The reset bitset is: ( "<< b1 << " )"  
        << endl;  
  
   rb = rb1.any ( );  
  
   if ( rb )  
      cout << "At least one of the bits in the reset bitset "  
           << "are set to 1." << endl;  
   else  
      cout << "None of the bits in bitset b1 are set to 1."  
           << endl;  
}  
```  
  
```Output  
The original bitset b1( 6 ) is: ( 00110 )  
At least one of the bits in bitset is set to 1.  
The reset bitset is: ( 00000 )  
None of the bits in bitset b1 are set to 1.  
```  
  
##  <a name="bitset__bitset"></a>  bitset::bitset  
 建構 `bitset\<N>` 類別的物件，並將此位元初始化為零、某指定值或字串字元中取得的值。  
  
```  
bitset();

bitset(
    unsigned long long val);

explicit bitset(
    const char* _CStr);

template <class CharType,   
    class Traits,   
    class Allocator>  
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,  
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos = 0);

template <class CharType,  
    class Traits,  
    class Allocator>  
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,  
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos,  
    typename basic_string<CharType, Traits, Allocator>::size_type count,  
    CharType _Zero = CharType ('0'),   
    CharType _One = CharType ('1'));
```  
  
### <a name="parameters"></a>參數  
 `val`  
 不帶正負號的整數，其以&2; 為底數的表示可用來初始化所建構之 bitset 中的位元。  
  
 `str`  
 以零和一組成的字串，用來初始化 bitset 的位元值。  
  
 `_CStr`  
 以零和一組成的 C 樣式字串，用來初始化 bitset 的位元值。  
  
 `_Pos`  
 字串中的字元位置，由左到右算起並以零起始，用來初始化 bitset 中的第一個位元。  
  
 `count`  
 字串中的字元數，用來提供初始值給 bitset 中的位元。  
  
 `_Zero`  
 用來表示零的字元。 預設值為 '0'。  
  
 `_One`  
 用來表示一的字元。 預設值為 '1'。  
  
### <a name="remarks"></a>備註  
 三個建構函式可用來建構 `bitset\<N>` 類別的物件：  
  
-   第一個建構函式不會接受任何參數、會建構 `bitset\<N>` 類別的物件，並將所有 N 位元初始化為預設值零。  
  
-   第二個建構函式會建構 `bitset\<N>` 類別的物件，並使用單一 `unsigned long long` 參數將位元初始化。  
  
-   第三個建構函式會建構 `bitset\<N>` 類別的物件，並將 N 位元初始化為與由零和一組成之 C 樣式字元字串所提供的字元相對應的值。 您可以呼叫此建構函式，而不需要將字串轉換為字串類型︰`bitset<5> b5("01011");`  
  
 另外還提供兩個建構函式樣板：  
  
-   第一個建構函式樣板會建構 `bitset\<N>` 類別的物件，並從由零和一組成之字串所提供的字元，將位元初始化。 如果字串的任何字元不是 0 或 1，此建構函式會擲回 [invalid_argument](../standard-library/invalid-argument-class.md) 類別的物件。 如果指定的位置 (`_Pos`) 超過字串的長度，則此建構函式會擲回 [out_of_range](../standard-library/out-of-range-class.md) 類別的物件。 此建構函式只會設定位於 bitset 中 *j* 位置的這些位元，而位於 `_Pos + j` 位置的字串字元會是 1。 `_Pos` 預設為 0。  
  
-   第二個建構函式樣板類似於第一個建構函式樣板，但會包含一個額外的參數 (`count`)，以用來指定要初始化的位元數。 它也有兩個選擇性參數 `_Zero` 和 `_One`，表示 `str` 中要解譯以分別表示 0 位元和 1 位元的字元。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_bitset.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   // Using the default constructor  
   using namespace std;  
   bitset<2> b0;  
   cout << "The set of bits in bitset<2> b0 is: ( "  
        << b0 << " )." << endl;  
  
   // Using the second member function  
   bitset<5> b1 ( 6 );  
   cout << "The set of bits in bitset<5> b1( 6 ) is: ( "  
        << b1 << " )." << endl;  
  
   // The template parameter N can be an expresssion  
   bitset< 2 * sizeof ( int ) > b2;  
   cout << "The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( "  
        << b2 << " )." << endl;  
  
   // The base two representation will be truncated  
   // if its length exceeds the size of the bitset  
   bitset<3> b3 ( 6 );  
   cout << "The set of bits in bitset<3> b3( 6 ) is ( "  
        << b3 << " )." << endl;  
  
   // Using a c-style string to initialize the bitset  
    bitset<7> b3andahalf ( "1001001" );  
    cout << "The set of bits in bitset<7> b3andahalf ( \"1001001\" )"  
         << " is ( " << b3andahalf << " )." << endl;   
  
   // Using the fifth member function with the first parameter  
   string bitval4 ( "10011" );  
   bitset<5> b4 ( bitval4 );  
   cout << "The set of bits in bitset<5> b4( bitval4 ) is ( "  
        << b4 << " )." << endl;  
  
   // Only part of the string may be used for initialization  
  
   // Starting at position 3 for a length of 6 (100110)  
   string bitval5 ("11110011011");  
   bitset<6> b5 ( bitval5, 3, 6 );  
   cout << "The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( "  
        << b5 << " )." << endl;  
  
   // The bits not initialized with part of the string  
   // will default to zero  
   bitset<11> b6 ( bitval5, 3, 5 );  
   cout << "The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( "  
        << b6 << " )." << endl;  
  
   // Starting at position 2 and continue to the end of the string  
   bitset<9> b7 ( bitval5, 2 );  
   cout << "The set of bits in bitset<9> b7( bitval, 2 ) is ( "  
        << b7 << " )." << endl;  
}  
```  
  
```Output  
The set of bits in bitset<2> b0 is: ( 00 ).  
The set of bits in bitset<5> b1( 6 ) is: ( 00110 ).  
The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( 00000000 ).  
The set of bits in bitset<3> b3( 6 ) is ( 110 ).  
The set of bits in bitset<5> b4( bitval4 ) is ( 10011 ).  
The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( 100110 ).  
The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( 00000010011 ).  
The set of bits in bitset<9> b7( bitval, 2 ) is ( 110011011 ).  
```  
  
##  <a name="bitset__count"></a>  bitset::count  
 傳回位元序列中設定的位元數。  
  
```  
size_t count() const;
```  
  
### <a name="return-value"></a>傳回值  
  
位元序列中設定的位元數。  
  
### <a name="example"></a>範例  
  
下列範例示範如何使用 bitset::count 成員函式。  
  
```cpp  
// bitset_count.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
  
    bitset<5> b1(4);  
  
    cout << "The collection of bits in the original bitset is: ( "  
         << b1 << " )" << endl;  
  
    size_t i;  
    i = b1.count();  
    cout << "The number of bits in the bitset set to 1 is: "  
         << i << "." << endl;  
  
    bitset<5> fb1;  
    fb1 = b1.flip();  
  
    cout << "The collection of flipped bits in the modified bitset "  
         << "is: ( " << b1 << " )" << endl;  
  
    size_t ii;  
    ii = fb1.count();  
    cout << "The number of bits in the bitset set to 1 is: "  
         << ii << "." << endl;  
}  
```  
  
```Output  
The collection of bits in the original bitset is: ( 00100 )  
The number of bits in the bitset set to 1 is: 1.  
The collection of flipped bits in the modified bitset is: ( 11011 )  
The number of bits in the bitset set to 1 is: 4.  
```  
  
##  <a name="bitset__element_type"></a>  bitset::element_type  
 與資料類型 `bool` 同義的類型，可用來參考 bitset 中的元素位元。  
  
```  
typedef bool element_type;  
```  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_elem_type.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<3> b1 ( 2 );  
   cout << "Original bitset b1(6) is: ( "<< b1 << " )"  
        << endl;  
  
   //Compare two ways to reference bits in a bitset  
   bool b;  
   bitset<5>::element_type e;  
  
   b = b1.test ( 2 );  
   if ( b )  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 1." << endl;  
   else  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 0." << endl;  
   b1[2] = 1;  
   cout << "Bitset b1 modified by b1[2] = 1 is: ( "<< b1 << " )"  
        << endl;  
  
   e = b1.test ( 2 );  
   if ( e )  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 1." << endl;  
   else  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 0." << endl;  
}  
```  
  
```Output  
Original bitset b1(6) is: ( 010 )  
The bit at position 2 of bitset b1has a value of 0.  
Bitset b1 modified by b1[2] = 1 is: ( 110 )  
The bit at position 2 of bitset b1has a value of 1.  
```  
  
##  <a name="bitset__flip"></a>  bitset::flip  
 反轉 bitset 中的所有位元值，或在指定位置反轉單一位元。  
  
```  
bitset\<N>& flip();  
bitset\<N>& flip(size_t _Pos);
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 要反轉其值之位元的位置。  
  
### <a name="return-value"></a>傳回值  
 叫用成員函式之已修改的 bitset 複本。  
  
### <a name="remarks"></a>備註  
 如果指定為參數的位置大於已反轉其位元之 **bitset\<***N***>** 的大小 *N*，第二個成員函式會擲回 [out_of_range](../standard-library/out-of-range-class.md) 例外狀況。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_flip.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 6 );  
  
   cout << "The collection of bits in the original bitset is: ( "  
        << b1 << " )" << endl;  
  
   bitset<5> fb1;  
   fb1 = b1.flip ( );  
  
   cout << "After flipping all the bits, the bitset becomes: ( "  
        << fb1 << " )" << endl;  
  
   bitset<5> f3b1;  
   f3b1 = b1.flip ( 3 );  
  
   cout << "After flipping the fourth bit, the bitset becomes: ( "  
        << f3b1 << " )" << endl << endl;  
  
   bitset<5> b2;  
   int i;  
   for ( i = 0 ; i <= 4 ; i++ )  
   {  
      b2.flip(i);  
      cout << b2 << "  The bit flipped is in position "  
           << i << ".\n";  
   }  
}  
```  
  
```Output  
The collection of bits in the original bitset is: ( 00110 )  
After flipping all the bits, the bitset becomes: ( 11001 )  
After flipping the fourth bit, the bitset becomes: ( 10001 )  
  
00001  The bit flipped is in position 0.  
00011  The bit flipped is in position 1.  
00111  The bit flipped is in position 2.  
01111  The bit flipped is in position 3.  
11111  The bit flipped is in position 4.  
```  
  
##  <a name="bitset__none"></a>  bitset::none  
 測試在 bitset 物件中是否沒有已設為 1 的位元。  
  
```  
bool none() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果 bitset 中沒有已設為 1 的位元，則為 **true**；如果至少有一個位元已設為 1，則為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_none.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 6 );  
   bool b, rb;  
  
   cout << "Original bitset b1(6) is: ( " << b1 << " )"  
        << endl;  
  
   b = b1.none ( );  
  
   if ( b )  
      cout << "None of the bits in bitset b1 are set to 1."  
           << endl;  
   else  
      cout << "At least one of the bits in bitset b1 is set to 1."  
           << endl;  
  
   bitset<5> rb1;  
   rb1 = b1.reset ( );  
   rb = rb1.none ( );  
   if ( rb )  
      cout << "None of the bits in bitset b1 are set to 1."  
           << endl;  
   else  
      cout << "At least one of the bits in bitset b1 is set to 1."  
           << endl;  
}  
```  
  
```Output  
Original bitset b1(6) is: ( 00110 )  
At least one of the bits in bitset b1 is set to 1.  
None of the bits in bitset b1 are set to 1.  
```  
  
##  <a name="bitset__operator_neq"></a>  bitset::operator!=  
 測試目標 bitset 是否與指定的 bitset 不相等。  
  
```  
bool operator!=(const bitset\<N>& right) const;
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要與目標 bitset 比較是否不相等的 bitset。  
  
### <a name="return-value"></a>傳回值  
 如果 bitset 不同，則為 **true**；如果兩者相同，則為 **false**。  
  
### <a name="remarks"></a>備註  
 bitset 的大小必須相同，才能由成員運算子函式測試是否不相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_NE.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 7 );  
   bitset<5> b3 ( 2 );  
   bitset<4> b4 ( 7 );  
  
   if ( b1 != b2 )  
      cout << "Bitset b1 is different from bitset b2." << endl;  
   else  
      cout << "Bitset b1 is the same as bitset b2." << endl;  
  
   if ( b1 != b3 )  
      cout << "Bitset b1 is different from bitset b3." << endl;  
   else  
      cout << "Bitset b1 is the same as bitset b3." << endl;  
  
   // This would cause an error because bitsets must have the  
   // same size to be tested  
   // if ( b1 != b4 )  
   //   cout << "Bitset b1 is different from bitset b4." << endl;  
   // else  
   //   cout << "Bitset b1 is the same as bitset b4." << endl;  
}  
```  
  
```Output  
Bitset b1 is the same as bitset b2.  
Bitset b1 is different from bitset b3.  
```  
  
##  <a name="bitset__operator_and_eq"></a>  bitset::operator&amp;=  
 以邏輯 **AND** 運算執行 bitset 的位元組合。  
  
```  
bitset\<N>& operator&=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要與目標 bitset 進行位元結合的 bitset。  
  
### <a name="return-value"></a>傳回值  
 使用指定為參數的 bitset，從位元 **AND** 運算產生之已修改的目標 bitset。  
  
### <a name="remarks"></a>備註  
 如果每個位元都為 true，由 **AND** 運算子結合的兩個位元會傳回 **true**；否則，其組合會傳回 **false**。  
  
 bitset 的大小必須相同，才能由成員運算子函式透過 **AND** 運算子進行位元結合。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_bitwise.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 11 );  
   bitset<4> b3 ( 7 );  
  
   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;  
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;  
   cout << endl;  
  
   b1 &= b2;  
   cout << "After bitwise AND combination,\n"  
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
        << endl;  
  
   // Note that the parameter-specified bitset is unchanged  
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."   
        << endl;  
  
   // The following would cause an error because the bisets   
   // must be of the same size to be combined  
   // b1 &= b3;  
}  
```  
  
```Output  
The target bitset b1 is:    ( 00111 ).  
The parameter bitset b2 is: ( 01011 ).  
  
After bitwise AND combination,  
 the target bitset b1 becomes:   ( 00011 ).  
The parameter bitset b2 remains: ( 01011 ).  
```  

##  <a name="bitset__operator_lshift"></a> bitset::operator\<\<    
  
將 bitset 中的位元向左移位指定的位置數值，並將結果傳回至新的 bitset。  
  
```  
bitset\<N> operator<<(size_t _Pos) const;
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 bitset 中的位元向左移位的位置數值。  
  
### <a name="return-value"></a>傳回值  
 已修改的 bitset，其中的位元會向左移位必要的位置數值。  
  
### <a name="remarks"></a>備註  
 此成員運算子函式會傳回 **bitset**( **\*this**) **<<= pos**，其中 [<<=](#bitset__operator_lshift_eq) 會將 bitset 中的位元向左移位指定的位置數值，並將結果傳回至目標 bitset。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_LS.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
  
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;  
  
   bitset<5> b2;  
   b2 = b1 << 2;  
  
   cout << "After shifting the bits 2 positions to the left,\n"  
        << " the bitset b2 is: ( "<< b2 << " )."  
        << endl;  
  
   bitset<5> b3 = b2 >> 1;  
  
   cout << "After shifting the bits 1 position to the right,\n"  
        << " the bitset b3 is: ( " << b3 << " )."  
        << endl;  
}  
```  
  
##  <a name="bitset__operator_lshift_eq"></a>  bitset::operator&lt;&lt;=  
 將 bitset 中的位元向左移位指定的位置數值，並將結果傳回至目標 bitset。  
  
```  
bitset\<N>& operator<<=(size_t _Pos);
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 bitset 中的位元向左移位的位置數值。  
  
### <a name="return-value"></a>傳回值  
 已修改的目標 bitset，其中的位元已向左移位必要的位置數值。  
  
### <a name="remarks"></a>備註  
 如果沒有要移位至該位置的元素，此函式會將位元值清除成 0。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_LSE.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;  
   b1 <<= 2;  
   cout << "After shifting the bits 2 positions to the left,\n"  
        << " the target bitset b1 becomes: ( "<< b1 << " )."   
        << endl;  
}  
```  
  
```Output  
The target bitset b1 is: ( 00111 ).  
After shifting the bits 2 positions to the left,  
 the target bitset b1 becomes: ( 11100 ).  
```  
  
##  <a name="bitset__operator_eq_eq"></a>  bitset::operator==  
 測試目標 bitset 是否與指定的 bitset 相等。  
  
```  
bool operator==(const bitset\<N>& right) const;
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要與目標 bitset 比較是否相等的 bitset。  
  
### <a name="return-value"></a>傳回值  
 如果 bitset 相同，則為 **true**；如果兩者不同，則為 **false**。  
  
### <a name="remarks"></a>備註  
 bitset 的大小必須相同，才能由成員運算子函式測試是否相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_EQ.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 7 );  
   bitset<5> b3 ( 2 );  
   bitset<4> b4 ( 7 );  
  
   if ( b1 == b2 )  
      cout << "Bitset b1 is the same as bitset b2." << endl;  
   else  
      cout << "Bitset b1 is different from bitset b2." << endl;  
  
   if ( b1 == b3 )  
      cout << "Bitset b1 is the same as bitset b3." << endl;  
   else  
      cout << "Bitset b1 is different from bitset b3." << endl;  
  
   // This would cause an error because bitsets must have the   
   // same size to be tested  
   // if ( b1 == b4 )  
   //   cout << "Bitset b1 is the same as bitset b4." << endl;  
   // else  
   //   cout << "Bitset b1 is different from bitset b4." << endl;  
}  
```  
  
```Output  
Bitset b1 is the same as bitset b2.  
Bitset b1 is different from bitset b3.  
```  
  
##  <a name="bitset__operator_rshift"></a>  bitset::operator&gt;&gt;  
 將 bitset 中的位元向右移位指定的位置數值，並將結果傳回至新的 bitset。  
  
```  
bitset\<N> operator>>(size_t _Pos) const;
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 bitset 中的位元向右移位的位置數值。  
  
### <a name="return-value"></a>傳回值  
 新的 bitset，其中的位元已相對於目標 bitset 向右移位必要的位置數值。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_RS.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;  
  
   bitset<5> b2;  
   b2 = b1 << 2;  
  
   cout << "After shifting the bits 2 positions to the left,\n"  
        << " the bitset b2 is: ( "<< b2 << " )."  
        << endl;  
   bitset<5> b3 = b2 >> 1;  
  
   cout << "After shifting the bits 1 position to the right,\n"  
        << " the bitset b3 is: ( " << b3 << " )."  
        << endl;  
}  
```  
  
```Output  
The bitset b1 is: ( 00111 ).  
After shifting the bits 2 positions to the left,  
 the bitset b2 is: ( 11100 ).  
After shifting the bits 1 position to the right,  
 the bitset b3 is: ( 01110 ).  
```  
  
##  <a name="bitset__operator_rshift_eq"></a>  bitset::operator&gt;&gt;=  
 將 bitset 中的位元向右移位指定的位置數值，並將結果傳回至目標 bitset。  
  
```  
bitset\<N>& operator>>=(size_t _Pos);
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 bitset 中的位元向右移位的位置數值。  
  
### <a name="return-value"></a>傳回值  
 已修改的目標 bitset，其中的位元已向右移位必要的位置數值。  
  
### <a name="remarks"></a>備註  
 如果沒有要移位至該位置的元素，此函式會將位元值清除成 0。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_RSE.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 28 );  
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;  
  
   b1 >>= 2;  
   cout << "After shifting the bits 2 positions to the right,\n"  
        << " the target bitset b1 becomes: ( "<< b1 << " )."   
        << endl;  
}  
```  
  
```Output  
The target bitset b1 is: ( 11100 ).  
After shifting the bits 2 positions to the right,  
 the target bitset b1 becomes: ( 00111 ).  
```  
  
##  <a name="bitset__operator_at"></a>  bitset::operator[]  
 如果 bitset 可修改，則傳回位於 bitset 中指定位置的位元參考；否則會傳回該位置的位元值。  
  
```  
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 此位元在 bitset 中的位置。  
  
### <a name="remarks"></a>備註  
當您將組建中的 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) 定義為 1 或 2 時，如果嘗試存取 bitset 界限之外的元素，您的可執行檔中將會發生執行階段錯誤。 如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_REF.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bool b;  
   bitset<5> b1 ( 6 );  
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."  
        << endl;  
  
   int i;  
   for ( i = 0 ; i <= 4 ; i++ )  
   {  
      b = b1[ i ];  
      cout << "  The bit in position "  
           << i << " is " << b << ".\n";  
   }  
}  
```  
  
##  <a name="bitset__operator_xor_eq"></a>  bitset::operator^=  
 以互斥 `OR` 作業執行 bitset 的位元組合。  
  
```  
bitset\<N>& operator^=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要與目標 bitset 進行位元結合的 bitset。  
  
### <a name="return-value"></a>傳回值  
 使用指定為參數的 bitset，從位元排除 `OR` 運算產生之已修改的目標 bitset。  
  
### <a name="remarks"></a>備註  
 由排除 **OR** 運算子結合的兩個位元若至少其中之一 (而非兩者) 為 **true**，則會傳回 **true**；否則，其組合會傳回 **false**。  
  
 bitset 的大小必須相同，才能由成員運算子函式透過排除 `OR` 運算子進行位元結合。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_bitwiseOR.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 11 );  
   bitset<4> b3 ( 7 );  
  
   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;  
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;  
   cout << endl;  
  
   b1 ^= b2;  
   cout << "After bitwise exclusive OR combination,\n"  
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
        << endl;  
  
   // Note that the parameter-specified bitset in unchanged  
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."   
        << endl;  
  
   // The following would cause an error because the bisets   
   // must be of the same size to be combined  
   // b1 |= b3;  
}  
```  
  
```Output  
The target bitset b1 is:    ( 00111 ).  
The parameter bitset b2 is: ( 01011 ).  
  
After bitwise exclusive OR combination,  
 the target bitset b1 becomes:   ( 01100 ).  
The parameter bitset b2 remains: ( 01011 ).  
```  
  
##  <a name="bitset__operator_or_eq"></a>  bitset::operator&#124;=  
 以包含 `OR` 作業執行 bitset 的位元組合。  
  
```  
bitset\<N>& operator|=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要與目標 bitset 進行位元結合的 bitset。  
  
### <a name="return-value"></a>傳回值  
 使用指定為參數的 bitset，從位元包含 `OR` 運算產生之已修改的目標 bitset。  
  
### <a name="remarks"></a>備註  
 由包含 `OR` 運算子結合的兩個位元若至少其中之一為 **true**，則會傳回 **true**；如果兩個位元都是 **false**，則其組合會傳回 **false**。  
  
 bitset 的大小必須相同，才能由成員運算子函式透過包含 `OR` 運算子進行位元結合。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_BIO.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 11 );  
   bitset<4> b3 ( 7 );  
  
   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;  
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;  
   cout << endl;  
  
   b1 |= b2;  
   cout << "After bitwise inclusive OR combination,\n"  
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
        << endl;  
  
   // Note that the parameter-specified bitset in unchanged  
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."   
        << endl;  
  
   // The following would cause an error because the bisets   
   // must be of the same size to be combined  
   // b1 |= b3;  
}  
```  
  
```Output  
The target bitset b1 is:    ( 00111 ).  
The parameter bitset b2 is: ( 01011 ).  
  
After bitwise inclusive OR combination,  
 the target bitset b1 becomes:   ( 01111 ).  
The parameter bitset b2 remains: ( 01011 ).  
```  
  
##  <a name="bitset__operator_dtor"></a>  bitset::operator~  
 反轉目標 bitset 中的所有位元，並傳回結果。  
  
```  
bitset\<N> operator~() const;
```  
  
### <a name="return-value"></a>傳回值  
 其所有位元已根據目標 bitset 反轉的 bitset。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_invert.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
#include <bitset>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2;  
   b2 = ~b1;  
  
   cout << "Bitset b1 is: ( "<< b1 << " )." << endl;  
   cout << "Bitset b2 = ~b1 is: ( "<< b2 << " )." << endl;  
  
   // These bits could also be flipped using the flip member function  
   bitset<5> b3;  
   b3 = b1.flip( );  
   cout << "Bitset b3 = b1.flip( ) is: ( "<< b2 << " )." << endl;  
}  
```  
  
```Output  
Bitset b1 is: ( 00111 ).  
Bitset b2 = ~b1 is: ( 11000 ).  
Bitset b3 = b1.flip( ) is: ( 11000 ).  
```  
  
##  <a name="bitset__reference"></a>  bitset::reference  
 Proxy 類別，提供參考給包含於 bitset 中的位元，而 bitset 是用來存取及管理作為 bitset 類別之 `operator[]` 協助程式類別的個別位元。  
  
```  
class reference {  
   friend class bitset\<N>;  
public: 
   reference& operator=(bool val);
   reference& operator=(const reference& _Bitref);
   bool operator~() const;
   operator bool() const;
   reference& flip();
};  
```    
  
### <a name="parameters"></a>參數  
 `val`  
 要指派給 bitset 中位元之 `bool` 類型物件的值。  
  
 `_Bitref`  
 位於 bitset *x* 中 *i* 位置的位元參考，其格式為 *x [ i ]*。  
  
### <a name="return-value"></a>傳回值  
 針對類別參考的第一個、第二個和第五個成員函式，會是引數位置所指定之 bitset 中的位元參考；針對類別參考的第三個和第四個成員函式，會是 **true** 或 **false**，以反映 bitset 中已修改的位元值。  
  
### <a name="remarks"></a>備註  
 類別 `reference` 只有作為 bitset `operator[]` 的協助程式類別時才會出現。 此成員類別描述可存取 bitset 中個別位元的物件。 讓 *b* 成為 `bool` 類型的物件、讓 *x* 和 *y* 物件屬於 **bitset\<***N***>** 類型，並讓 *i* 和 *j* 成為這類物件中的有效位置。 標記法 *x [i]* 參考位於 bitset *x* 中位置 *i* 的位元。 `reference` 類別的成員函式會依序提供下列作業：  
  
|作業|定義|  
|---------------|----------------|  
|*x*[*i*] = *b*|將 `bool` 值 *b* 儲存在 bitset *x* 中的位元位置 *i*。|  
|*x*[*i*] = *y*[*j*]|將位元 *y*[ *j*] 的值儲存在 bitset *x* 中的位元位置 *i*。|  
|*b* = ~ *x*[*i*]|將位元 *x*[ *i*] 的翻轉值儲存在 `bool` *b*。|  
|*b* = *x*[*i*]|將位元 *x*[ *i*] 的值儲存在 `bool` *b*。|  
|*x*[*i*]. `flip`( )|將位元 *x*[ *i*] 的翻轉值儲存回 *x* 中的位元位置 *i*。|  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_reference.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 2 );  
   bitset<5> b2 ( 6 );  
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."  
        << endl;  
   cout << "The initialized bitset<5> b2( 6 ) is: ( "<< b2 << " )."  
        << endl;  
  
   // Example of x [i] = b storing bool b at bit position i  
   // in bitset x  
   b1[ 0 ] = true;  
   cout << "The bitset<5> b1 with the bit at position 0 set to 1"  
        << " is: ( "<< b1 << " )" << endl;  
  
   // Example of x [i] = y [j] storing the bool value of the  
   // bit at position j in bitset y at bit position i in bitset x  
   b2 [4] = b1 [0];      // b1 [0] = true  
   cout << "The bitset<5> b2 with the bit at position 4 set to the "  
        << "value\n of the bit at position 0 of the bit in "  
        << "bitset<5> b1 is: ( "<<  b2  << " )" << endl;  
  
   // Example of b = ~x [i] flipping the value of the bit at  
   // position i of bitset x and storing the value in an   
   // object b of type bool  
   bool b = ~b2 [4];      // b2 [4] = false  
   if ( b )  
      cout << "The value of the object b = ~b2 [4] "  
           << "of type bool is true." << endl;  
   else  
      cout << "The value of the object b = ~b2 [4] "  
           << "of type bool is false." << endl;  
  
   // Example of b = x [i] storing the value of the bit at  
   // position i of bitset x in the object b of type bool  
   b = b2 [4];  
   if ( b )  
      cout << "The value of the object b = b2 [4] "  
           << "of type bool is true." << endl;  
   else  
      cout << "The value of the object b = b2 [4] "  
           << "of type bool is false." << endl;  
  
   // Example of x [i] . flip ( ) toggling the value of the bit at  
   // position i of bitset x  
   cout << "Before flipping the value of the bit at position 4 in "  
        << "bitset b2,\n it is ( "<<  b2  << " )." << endl;  
   b2 [4].flip( );  
   cout << "After flipping the value of the bit at position 4 in "  
        << "bitset b2,\n it becomes ( "<<  b2  << " )." << endl;  
   bool c;  
   c = b2 [4].flip( );  
   cout << "After a second flip, the value of the position 4"  
        << " bit in b2 is now: " << c << ".";  
}  
```  
  
```Output  
The initialized bitset<5> b1( 2 ) is: ( 00010 ).  
The initialized bitset<5> b2( 6 ) is: ( 00110 ).  
The bitset<5> b1 with the bit at position 0 set to 1 is: ( 00011 )  
The bitset<5> b2 with the bit at position 4 set to the value  
 of the bit at position 0 of the bit in bitset<5> b1 is: ( 10110 )  
The value of the object b = ~b2 [4] of type bool is false.  
The value of the object b = b2 [4] of type bool is true.  
Before flipping the value of the bit at position 4 in bitset b2,  
 it is ( 10110 ).  
After flipping the value of the bit at position 4 in bitset b2,  
 it becomes ( 00110 ).  
After a second flip, the value of the position 4 bit in b2 is now: 1.  
```  
  
##  <a name="bitset__reset"></a>  bitset::reset  
 將 bitset 中的所有位元重設為 0，或將指定位置的位元重設為 0。  
  
```  
bitset\<N>& reset();  
bitset\<N>& reset(size_t _Pos);
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 bitset 中要重設為 0 的位元位置。  
  
### <a name="return-value"></a>傳回值  
 叫用成員函式的 bitset 複本。  
  
### <a name="remarks"></a>備註  
 如果指定的位置大於 bitset 的大小，第二個成員函式會擲回 [out_of_range](../standard-library/out-of-range-class.md) 例外狀況。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_reset.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 13 );  
   cout << "The set of bits in bitset<5> b1(13) is: ( "<< b1 << " )"  
        << endl;  
  
   bitset<5> b1r3;  
   b1r3 = b1.reset( 2 );  
   cout << "The collecion of bits obtained from resetting the\n"  
        << " third bit of bitset b1 is: ( "<< b1r3 << " )"   
        << endl;  
  
   bitset<5> b1r;  
   b1r = b1.reset( );  
   cout << "The collecion of bits obtained from resetting all\n"  
        << " the elements of the bitset b1 is: ( "<< b1r << " )"  
        << endl;  
}  
```  
  
```Output  
The set of bits in bitset<5> b1(13) is: ( 01101 )  
The collecion of bits obtained from resetting the  
 third bit of bitset b1 is: ( 01001 )  
The collecion of bits obtained from resetting all  
 the elements of the bitset b1 is: ( 00000 )  
```  
  
##  <a name="bitset__set"></a>  bitset::set  
 將 bitset 中的所有位元設為 1，或將指定位置的位元設為 1。  
  
```   
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,   
    bool val = true);
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 bitset 中要設定以指派值的位元位置。  
  
 `val`  
 要指派給位於指定位置之位元的值。  
  
### <a name="return-value"></a>傳回值  
 叫用成員函式的 bitset 複本。  
  
### <a name="remarks"></a>備註  
 如果指定的位置大於 bitset 的大小，第二個成員函式會擲回 [out_of_range](../standard-library/out-of-range-class.md) 例外狀況。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_set.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 6 );  
   cout << "The set of bits in bitset<5> b1(6) is: ( "<< b1 << " )"  
        << endl;  
  
   bitset<5> b1s0;  
   b1s0 = b1.set( 0 );  
   cout << "The collecion of bits obtained from setting the\n"  
        << " zeroth bit of bitset b1 is: ( "<< b1s0 << " )"   
        << endl;  
  
   bitset<5> bs1;  
   bs1 = b1.set( );  
   cout << "The collecion of bits obtained from setting all the\n"  
        << " elements of the bitset b1 is: ( "<< bs1 << " )"  
        << endl;  
}  
```  
  
```Output  
The set of bits in bitset<5> b1(6) is: ( 00110 )  
The collecion of bits obtained from setting the  
 zeroth bit of bitset b1 is: ( 00111 )  
The collecion of bits obtained from setting all the  
 elements of the bitset b1 is: ( 11111 )  
```  
  
##  <a name="bitset__size"></a>  bitset::size  
 傳回 bitset 物件中的位元數。  
  
```  
size_t size() const;
```  
  
### <a name="return-value"></a>傳回值  
 bitset\<N> 中的位元數 *N*。  
  
### <a name="example"></a>範例  
  下列範例示範如何使用 bitset::size 成員函式。  
  
```cpp  
// bitset_size.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    bitset<5> b1(6);  
    size_t i;  
  
    cout << "The set of bits in bitset<5> b1( 6 ) is: ( "<< b1 << " )"  
         << endl;  
  
    i = b1.size();  
  
    cout << "The number of bits in bitset b1 is: " << i << "."  
         << endl;  
}  
```  
  
```Output  
The set of bits in bitset<5> b1( 6 ) is: ( 00110 )  
The number of bits in bitset b1 is: 5.  
```  
  
##  <a name="bitset__test"></a>  bitset::test  
 測試位於 bitset 中指定位置的位元是否設為 1。  
  
```  
bool test(size_t _Pos) const;
```  
  
### <a name="parameters"></a>參數  
 `_Pos`  
 bitset 中要測試其值的位元位置。  
  
### <a name="return-value"></a>傳回值  
 若引數位置所指定的位元設為 1，即為 **true**；否則為 **false**。  
  
### <a name="remarks"></a>備註  
 此成員函式會擲回 [out_of_range](../standard-library/out-of-range-class.md)


