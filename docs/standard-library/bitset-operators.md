---
title: "&lt;bitset&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84fe6a13-6f6e-4cdc-bf8f-6f65ab1134d4
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 2a1f1c21cdcd42e7e8d33eb6405297fc88635d87
ms.lasthandoff: 02/24/2017

---
# <a name="ltbitsetgt-operators"></a>&lt;bitset&gt; 運算子
||||  
|-|-|-|  
|[operator&amp;](#operator_amp_)|[operator&gt;&gt;](#operator_gt__gt_)|[operator&lt;&lt;](#operator_lt__lt_)|  
|[operator_xor](#operator_xor)|[operator_or](#operator_or)|  
  
##  <a name="a-nameoperatorampa--operatoramp"></a><a name="operator_amp_"></a>  operator&amp;  
 在兩個 bitset 之間執行位元 `AND`。  
  
```  
template <size_t size>  
bitset<size>  
operator&(
    const bitset<size>& left,  
    const bitset<size>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 兩個 bitset 的第一個 bitset，其相關元素會使用位元 `AND` 結合。  
  
 ` right`  
 兩個 valarray 的第二個 valarray，其相關元素會使用位元 `AND` 結合。  
  
### <a name="return-value"></a>傳回值  
 bitset，其元素是在 ` left` 和 ` right` 的對應元素上執行 `AND` 運算的結果。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_and.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
#include <string>  
  
using namespace std;  
  
int main()  
{  
   bitset<4> b1 ( string("0101") );  
   bitset<4> b2 ( string("0011") );  
   bitset<4> b3 = b1 & b2;  
   cout << "bitset 1: " << b1 << endl;  
   cout << "bitset 2: " << b2 << endl;  
   cout << "bitset 3: " << b3 << endl;  
}  
```  
  
```Output  
bitset 1: 0101  
bitset 2: 0011  
bitset 3: 0001  
```  
  
##  <a name="a-nameoperatorltlta--operatorltlt"></a><a name="operator_lt__lt_"></a>  operator&lt;&lt;  
 將位元序列的文字表示插入輸出資料流。  
  
```  
 
template <class CharType, class Traits, size_t N>  
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,  
    const bitset<N>& 
    right);
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 要當做字串插入輸出資料流之 **bitset\<N>** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 **ostr** 中位元序列的文字表示。  
  
### <a name="remarks"></a>備註  
 此樣板函式會多載 **operator<<**，允許寫出 bitset，而不先將它轉換為字串。 樣板函式有效地執行：  
  
 **ostr** << _ *Right*. [to_string](https://msdn.microsoft.com/library/2f93c55z.aspx) < **CharType**, **Traits**, **allocator**\< **CharType**> > ( )  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_op_insert.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 9 );  
  
   // bitset inserted into output stream directly  
   cout << "The ordered set of bits in the bitset<5> b1(9)"  
        << "\n can be output with the overloaded << as: ( "  
        << b1 << " )" << endl;  
  
   // Compare converting bitset to a string before  
   // inserting it into the output steam  
   string s1;  
   s1 =  b1.template to_string<char,   
      char_traits<char>, allocator<char> >( );  
   cout << "The string returned from the bitset b1"  
        << "\n by the member function to_string( ) is: "  
        << s1 << "." << endl;  
}  
```  
  
##  <a name="a-nameoperatorgtgta--operatorgtgt"></a><a name="operator_gt__gt_"></a>  operator&gt;&gt;  
 將位元字元的字串讀入 bitset。  
  
```  
 
template <class CharType, class Traits, size_t Bits>  
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>& 
_Istr,  
    bitset<N>& 
    right);
```  
  
### <a name="parameters"></a>參數  
 `_Istr`  
 在輸入資料流中輸入以插入 bitset 的字串。  
  
 ` right`  
 要從輸入資料流接收位元的 bitset。  
  
### <a name="return-value"></a>傳回值  
 此樣板函式會傳回字串 `_Istr`。  
  
### <a name="remarks"></a>備註  
 此樣板函式會多載 **operator>>** 將值 bitset( `str`) 儲存在 bitset _ *Right* 中，其中 `str` 是從 `_Istr` 中擷取之 [basic_string](https://msdn.microsoft.com/library/syxtdd4f.aspx) < **CharType**, **Traits**, **allocator**\< **CharType**> > **&** 類型的物件。  
  
 此樣板函式會從 `_Istr` 中擷取元素，並將其插入 bitset，直到：  
  
-   已從輸入資料流中擷取所有位元元素並將其儲存在 bitset 中。  
  
-   已使用輸入資料流中的位元填滿 bitset。  
  
-   遇到不是 0 或 1 的輸入元素。  
  
### <a name="example"></a>範例  
  
```cpp  
#include <bitset>  
#include <iostream>  
#include <string>  
  
using namespace std;  
int main()  
{  
  
   bitset<5> b1;  
   cout << "Enter string of (0 or 1) bits for input into bitset<5>.\n"  
        << "Try bit string of length less than or equal to 5,\n"  
        << " (for example: 10110): ";  
   cin >>  b1;  
  
   cout << "The ordered set of bits entered from the "  
        << "keyboard\n has been input into bitset<5> b1 as: ( "  
        << b1 << " )" << endl;  
  
   // Truncation due to longer string of bits than length of bitset  
   bitset<2> b3;  
   cout << "Enter string of bits (0 or 1) for input into bitset<2>.\n"  
        << " Try bit string of length greater than 2,\n"  
        << " (for example: 1011): ";  
   cin >>  b3;  
  
   cout << "The ordered set of bits entered from the "  
        << "keyboard\n has been input into bitset<2> b3 as: ( "  
        << b3 << " )" << endl;  
  
   // Flushing the input stream  
   char buf[100];  
   cin.getline(&buf[0], 99);  
  
   // Truncation with non-bit value  
   bitset<5> b2;  
   cout << "Enter a string for input into  bitset<5>.\n"  
        << " that contains a character than is NOT a 0 or a 1,\n "  
        << " (for example: 10k01): ";  
   cin >>  b2;  
  
   cout << "The string entered from the keyboard\n"  
        << " has been input into bitset<5> b2 as: ( "  
        << b2 << " )" << endl;  
}  
```  
  
##  <a name="a-nameoperatorxora--operatorxor"></a><a name="operator_xor"></a>  operator_xor  
 在兩個 bitset 之間執行位元 `EXCLUSIVE-OR`。  
  
```  
template <size_t size>  
bitset<size>  
operator^(
    const bitset<size>& left,  
    const bitset<size>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 兩個 bitset 的第一個 bitset，其相關元素會使用位元 `EXCLUSIVE-OR` 結合。  
  
 ` right`  
 兩個 valarray 的第二個 valarray，其相關元素會使用位元 `EXCLUSIVE-OR` 結合。  
  
### <a name="return-value"></a>傳回值  
 bitset，其元素是在 ` left` 和 ` right` 的對應元素上執行 `EXCLUSIVE-OR` 運算的結果。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_xor.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
#include <string>  
  
using namespace std;  
  
int main()  
{  
   bitset<4> b1 ( string("0101") );  
   bitset<4> b2 ( string("0011") );  
   bitset<4> b3 = b1 ^ b2;  
   cout << "bitset 1: " << b1 << endl;  
   cout << "bitset 2: " << b2 << endl;  
   cout << "bitset 3: " << b3 << endl;  
}  
```  
  
```Output  
bitset 1: 0101  
bitset 2: 0011  
bitset 3: 0110  
```  
  
##  <a name="a-nameoperatorora--operatoror"></a><a name="operator_or"></a>  operator_or  
 在兩個 bitset 之間執行位元 `OR`。  
  
```  
template <size_t size>  
bitset<size>  
operator|(
    const bitset<size>& left,  
    const bitset<size>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 兩個 bitset 的第一個 bitset，其相關元素會使用位元 `OR` 結合。  
  
 ` right`  
 兩個 valarray 的第二個 valarray，其相關元素會使用位元 `OR` 結合。  
  
### <a name="return-value"></a>傳回值  
 bitset，其元素是在 ` left` 和 ` right` 的對應元素上執行 `OR` 運算的結果。  
  
### <a name="example"></a>範例  
  
```cpp  
// bitset_or.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
#include <string>  
  
using namespace std;  
  
int main()  
{  
   bitset<4> b1 ( string("0101") );  
   bitset<4> b2 ( string("0011") );  
   bitset<4> b3 = b1 | b2;  
   cout << "bitset 1: " << b1 << endl;  
   cout << "bitset 2: " << b2 << endl;  
   cout << "bitset 3: " << b3 << endl;  
}  
```  
  
```Output  
bitset 1: 0101  
bitset 2: 0011  
bitset 3: 0111  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<bitset>](../standard-library/bitset.md)


