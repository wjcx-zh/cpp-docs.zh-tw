---
title: "char_traits 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iosfwd/std::char_traits
- char_traits
- string/std::char_traits::char_type
- string/std::char_traits::int_type
- string/std::char_traits::off_type
- string/std::char_traits::pos_type
- string/std::char_traits::state_type
- string/std::char_traits::assign
- string/std::char_traits::compare
- string/std::char_traits::copy
- string/std::char_traits::_Copy_s
- string/std::char_traits::eof
- string/std::char_traits::eq
- string/std::char_traits::eq_int_type
- string/std::char_traits::find
- string/std::char_traits::length
- string/std::char_traits::lt
- string/std::char_traits::move
- string/std::char_traits::_Move_s
- string/std::char_traits::not_eof
- string/std::char_traits::to_char_type
- string/std::char_traits::to_int_type
dev_langs:
- C++
helpviewer_keywords:
- char_traits struct
- char_traits class
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
caps.latest.revision: 20
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
ms.openlocfilehash: 558234b6411d3f2d10e84e3befda99084c7ca6d2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="chartraits-struct"></a>char_traits 結構
Char_traits 結構會描述與字元相關聯的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
template <class CharType>  
struct char_traits;  
```  
  
#### <a name="parameters"></a>參數  
 `CharType`  
 項目資料類型。  
  
## <a name="remarks"></a>備註  
 此樣板結構描述 **CharType** 類型的不同字元特性。 樣板類別 [basic_string](../standard-library/basic-string-class.md) 以及數個 iostream 樣板類別 (包含 [basic_ios](../standard-library/basic-ios-class.md)) 會使用此資訊來管理 **CharType** 類型的元素。 這類項目類型不得要求明確建構或解構。 它必須將預設建構函式、複製建構函式和指派運算子提供給預期的語意。 位元複製必須具有和指派相同的效果。 結構 char_traits 的成員函式都無法擲回例外狀況。  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|字元的類型。|  
|[int_type](#int_type)|整數類型，可以代表 `char_type` 類型的字元或檔案結尾 (EOF) 字元。|  
|[off_type](#off_type)|整數類型，可以代表資料流中位置之間的位移。|  
|[pos_type](#pos_type)|整數類型，可以代表資料流中的位置。|  
|[state_type](#state_type)|類型，代表資料流中多位元組字元的轉換狀態。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[assign](#assign)|將一個字元的值指派給另一個。|  
|[compare](#compare)|比較多達兩個字串中字元的指定數目。|  
|[copy](#copy)|將指定的字元數從一個字串複製到另一個。 已取代。 請改用 [char_traits::_Copy_s](#copy_s)。|  
|[_Copy_s](#copy_s)|將指定的字元數從一個字串複製到另一個。|  
|[eof](#eof)|傳回檔案結尾 (EOF) 字元。|  
|[eq](#eq)|測試兩個 `char_type` 字元是否相等。|  
|[eq_int_type](#eq_int_type)|測試兩個表示為 `int_type` 的字元是否相等。|  
|[find](#find)|在字元範圍中搜尋指定字元第一次出現處。|  
|[length](#length)|傳回字串的長度。|  
|[lt](#lt)|測試一個字元是否小於另一個。|  
|[move](#move)|將序列中指定的字元數複製到可能重疊的另一個序列。 已取代。 請改用 [char_traits::_Move_s](#move_s)。|  
|[_Move_s](#move_s)|將序列中指定的字元數複製到可能重疊的另一個序列。|  
|[not_eof](#not_eof)|測試字元是否為檔案結尾 (EOF) 字元。|  
|[to_char_type](#to_char_type)|將 `int_type` 字元轉換為對應的 `char_type` 字元，並傳回結果。|  
|[to_int_type](#to_int_type)|將 `char_type` 字元轉換為對應的 `int_type` 字元，並傳回結果。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<string>  
  
 **命名空間：** std  
  
##  <a name="assign"></a>  char_traits::assign  
 將一個字元值指派給字串中的另一個元素或一定範圍的元素。  
  
```  
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```  
  
### <a name="parameters"></a>參數  
 **_** *CharFrom*  
 要指派其值的字元。  
  
 *_CharTo*  
 要指派字元值的元素。  
  
 * strTo*  
 要將字元值指派給其初始元素的字串或字元陣列。  
  
 `_Num`  
 要指派值之元素的數目。  
  
### <a name="return-value"></a>傳回值  
 第二個成員函式會傳回其第一個 `_Num` 元素已指派 *_CharFrom* 值的字串指標。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_assign.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   // The first member function assigning   
   // one character value to another character  
   char ChTo = 't';  
   const char ChFrom = 'f';  
   cout << "The initial characters ( ChTo , ChFrom ) are: ( "  
        << ChTo << " , " << ChFrom << " )." << endl;  
   char_traits<char>::assign ( ChTo , ChFrom );  
   cout << "After assigning, the characters ( ChTo , ChFrom ) are: ( "  
        << ChTo << " , " << ChFrom << " )." << endl << endl;  
  
   // The second member function assigning   
   // character values to initial part of a string  
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";  
   char_traits<char>::char_type* result1;  
   cout << "The target string s1 is: " << s1 << endl;  
   result1 = char_traits<char>::assign ( s1 , 4 , 'f' );  
   cout << "The result1 = assign ( s1 , 4 , 'f' ) is: "  
        << result1 << endl;  
}  
```  
  
```Output  
The initial characters ( ChTo , ChFrom ) are: ( t , f ).  
After assigning, the characters ( ChTo , ChFrom ) are: ( f , f ).  
  
The target string s1 is: abcd-1234-abcd  
The result1 = assign ( s1 , 4 , 'f' ) is: ffff-1234-abcd  
```  
  
##  <a name="char_type"></a>  char_traits::char_type  
 字元的類型。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型與範本參數 **CharType** 同義。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `char_type` 的範例，請參閱 [copy](#copy) 的範例。  
  
##  <a name="compare"></a>  char_traits::compare  
 比較多達兩個字串中字元的指定數目。  
  
```  
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```  
  
### <a name="parameters"></a>參數  
 * str1*  
 要互相比較之兩個字串的第一個字串。  
  
 * str2*  
 要互相比較之兩個字串的第二個字串。  
  
 `_Num`  
 要比較之字串中的元素數目。  
  
### <a name="return-value"></a>傳回值  
 如果第一個字串小於第二個字串，則為負值；如果兩個字串相等，則為 0；如果第一個字串大於第二個字串，則為正值。  
  
### <a name="remarks"></a>備註  
 字串之間會逐元素進行比較，先測試是否相等，如果序列測試中有任何一對元素不相等，則會接著測試何者較小。  
  
 如果兩個字串比較結果為在一定範圍內相等，但其中一個字串比另一個字串長，則兩者中較短的字串會小於較長的字串。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_compare.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main() {  
   using namespace std;  
  
   char_traits<char>::char_type* s1 = "CAB";  
   char_traits<char>::char_type* s2 = "ABC";  
   char_traits<char>::char_type* s3 = "ABC";  
   char_traits<char>::char_type* s4 = "ABCD";  
  
   cout << "The string s1 is: " << s1 << endl;  
   cout << "The string s2 is: " << s2 << endl;  
   cout << "The string s3 is: " << s3 << endl;  
   cout << "The string s4 is: " << s4 << endl;  
  
   int comp1, comp2, comp3, comp4;  
   comp1 = char_traits<char>::compare ( s1 , s2 , 2 );  
   comp2 = char_traits<char>::compare ( s2 , s3 , 3 );  
   comp3 = char_traits<char>::compare ( s3 , s4 , 4 );  
   comp4 = char_traits<char>::compare ( s4 , s3 , 4 );  
   cout << "compare ( s1 , s2 , 2 ) = " << comp1 << endl;  
   cout << "compare ( s2 , s3 , 3 ) = " << comp2 << endl;  
   cout << "compare ( s3 , s4 , 4 ) = " << comp3 << endl;  
   cout << "compare ( s4 , s3 , 4 ) = " << comp4 << endl;  
}  
```  
  
##  <a name="copy"></a>  char_traits::copy  
 將指定的字元數從一個字串複製到另一個。  
  
 此方法有賴於呼叫者檢查傳遞的值是否正確，因此可能不安全。 請考慮改用 [char_traits::_Copy_s](#copy_s)。  
  
```  
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```  
  
### <a name="parameters"></a>參數  
 `_To`  
 要接收已複製字元序列之目標字串或字元陣列開頭的元素。  
  
 `_From`  
 要複製之來源字串或字元陣列開頭的元素。  
  
 `_Num`  
 要複製之元素的數目。  
  
### <a name="return-value"></a>傳回值  
 複製到要接收已複製字元序列之目標字串或字元陣列的第一個元素。  
  
### <a name="remarks"></a>備註  
 來源和目的字元序列不得重疊。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_copy.cpp  
// compile with: /EHsc /W3  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";  
   char_traits<char>::char_type s2[] = "ABCD-1234";  
   char_traits<char>::char_type* result1;  
   cout << "The source string is: " << s1 << endl;  
   cout << "The destination string is: " << s2 << endl;  
   // Note: char_traits::copy is potentially unsafe, consider  
   // using char_traits::_Copy_s instead.  
   result1 = char_traits<char>::copy ( s1 , s2 , 4 );  // C4996  
   cout << "The result1 = copy ( s1 , s2 , 4 ) is: "  
        << result1 << endl;  
}  
```  
  
```Output  
The source string is: abcd-1234-abcd  
The destination string is: ABCD-1234  
The result1 = copy ( s1 , s2 , 4 ) is: ABCD-1234-abcd  
```  
  
##  <a name="copy_s"></a>  char_traits::_Copy_s  
 將指定的字元數從一個字串複製到另一個。  
  
```  
static char_type *_Copy_s(
    char_type* dest,  
    size_t dest_size,  
    const char_type* _From,  
    size_t count);
```  
  
### <a name="parameters"></a>參數  
 `dest`  
 要接收已複製字元序列的目標字串或字元陣列。  
  
 `dest_size`  
 `dest` 的大小。 如果 `char_type` 是 `char`，則此大小是以位元組為單位。 如果 `char_type` 是 `wchar_t`，則此大小是以字組為單位。  
  
 `_From`  
 要複製的來源字串或字元陣列。  
  
 `count`  
 要複製之元素的數目。  
  
### <a name="return-value"></a>傳回值  
 要接收已複製字元序列的目標字串或字元陣列。  
  
### <a name="remarks"></a>備註  
 來源和目的字元序列不得重疊。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits__Copy_s.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
  
    char_traits<char>::char_type s1[] = "abcd-1234-abcd";  
    char_traits<char>::char_type s2[] = "ABCD-1234";  
    char_traits<char>::char_type* result1;  
    cout << "The source string is: " << s1 << endl;  
    cout << "The destination string is: " << s2 << endl;  
    result1 = char_traits<char>::_Copy_s(s1,  
        char_traits<char>::length(s1), s2, 4);  
    cout << "The result1 = _Copy_s(s1, "  
         << "char_traits<char>::length(s1), s2, 4) is: "  
         << result1 << endl;  
}  
```  
  
```Output  
The source string is: abcd-1234-abcd  
The destination string is: ABCD-1234  
The result1 = _Copy_s(s1, char_traits<char>::length(s1), s2, 4) is: ABCD-1234-abcd  
```  
  
##  <a name="eof"></a>  char_traits::eof  
 傳回檔案結尾 (EOF) 字元。  
  
```  
static int_type eof();
```  
  
### <a name="return-value"></a>傳回值  
 EOF 字元。  
  
### <a name="remarks"></a>備註  
 代表檔案結尾的值 (例如 `EOF` 或 `WEOF`)。  
  
 C++ 標準指出此值不得對應至有效的 `char_type` 值。 Visual C++ 編譯器會對 `char` 類型強制執行這項條件約束，但不會對 `wchar_t` 類型強制執行。 以下範例即為示範。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_eof.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    char_traits<char>::char_type ch1 = 'x';  
    char_traits<char>::int_type int1;  
    int1 = char_traits<char>::to_int_type(ch1);  
    cout << "char_type ch1 is '" << ch1 << "' and corresponds to int_type "  
         << int1 << "." << endl << endl;  
  
    char_traits<char>::int_type int2 = char_traits<char>::eof();  
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;  
  
    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();  
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;  
}  
```  
  
```Output  
char_type ch1 is 'x' and corresponds to int_type 120.  
  
The eof marker for char_traits<char> is: -1  
The eof marker for char_traits<wchar_t> is: 65535  
```  
  
##  <a name="eq"></a>  char_traits::eq  
 測試兩個 `char_type` 字元是否相等。  
  
```  
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```  
  
### <a name="parameters"></a>參數  
 `_Ch1`  
 要測試是否相等之兩個字元的第一個字元。  
  
 `_Ch2`  
 要測試是否相等之兩個字元的第二個字元。  
  
### <a name="return-value"></a>傳回值  
 若第一個字元等於第二個字元，即為 **true**；否則為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_eq.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::char_type ch2 =  'y';  
   char_traits<char>::char_type ch3 =  'x';  
  
   // Testing for equality  
   bool b1 = char_traits<char>::eq ( ch1 , ch2 );  
   if ( b1 )  
      cout << "The character ch1 is equal "  
           << "to the character ch2." << endl;  
   else  
      cout << "The character ch1 is not equal "  
           << "to the character ch2." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( ch1 == ch3 )  
      cout << "The character ch1 is equal "  
           << "to the character ch3." << endl;  
   else  
      cout << "The character ch1 is not equal "  
           << "to the character ch3." << endl;  
}  
```  
  
```Output  
The character ch1 is not equal to the character ch2.  
The character ch1 is equal to the character ch3.  
```  
  
##  <a name="eq_int_type"></a>  char_traits::eq_int_type  
 測試以 `int_type` 表示的兩個字元是否相等。  
  
```  
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```  
  
### <a name="parameters"></a>參數  
 `_Ch1`  
 要測試是否相等之兩個字元的第一個字元 (以 **int_type** 表示)。  
  
 `_Ch2`  
 要測試是否相等之兩個字元的第二個字元 (以 `int_type` 表示)。  
  
### <a name="return-value"></a>傳回值  
 若第一個字元等於第二個字元，即為 **true**；否則為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_eq_int_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::char_type ch2 =  'y';  
   char_traits<char>::char_type ch3 =  'x';  
  
   // Converting from char_type to int_type  
   char_traits<char>::int_type int1, int2 , int3;  
   int1 =char_traits<char>:: to_int_type ( ch1 );  
   int2 =char_traits<char>:: to_int_type ( ch2 );  
   int3 =char_traits<char>:: to_int_type ( ch3 );  
  
   cout << "The char_types and corresponding int_types are:"  
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "  
        << int1 << "."  
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "  
        << int2 << "."  
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "  
        << int3 << "." << endl << endl;  
  
   // Testing for equality of int_type representations  
   bool b1 = char_traits<char>::eq_int_type ( int1 , int2 );  
   if ( b1 )  
      cout << "The int_type representation of character ch1\n "  
           << "is equal to the int_type representation of ch2."  
           << endl;  
   else  
      cout << "The int_type representation of character ch1\n is "  
           << "not equal to the int_type representation of ch2."  
           << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( int1 == int3 )  
      cout << "The int_type representation of character ch1\n "  
           << "is equal to the int_type representation of ch3."  
           << endl;  
   else  
      cout << "The int_type representation of character ch1\n is "  
           << "not equal to the int_type representation of ch3."  
           << endl;  
}  
```  
  
```Output  
The char_types and corresponding int_types are:  
    ch1 = x corresponding to int1 = 120.  
    ch2 = y corresponding to int1 = 121.  
    ch3 = x corresponding to int1 = 120.  
  
The int_type representation of character ch1  
 is not equal to the int_type representation of ch2.  
The int_type representation of character ch1  
 is equal to the int_type representation of ch3.  
```  
  
##  <a name="find"></a>  char_traits::find  
 在字元範圍中搜尋指定字元第一次出現處。  
  
```  
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 要在字串中搜尋的第一個字元。  
  
 `_Num`  
 要在範圍中搜尋的位置數值 (從第一個字元算起)。  
  
 `_Ch`  
 要在範圍中搜尋的字元。  
  
### <a name="return-value"></a>傳回值  
 如果找到相符項，則為範圍中第一個出現的指定字元指標；否則為 null 指標。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_find.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   const char* s1 = "f2d-1234-abcd";  
   const char* result1;  
   cout << "The string to be searched is: " << s1 << endl;  
  
   // Searching for a 'd' in the first 6 positions of string s1  
   result1 = char_traits<char>::find ( s1 , 6 , 'd');  
   cout << "The character searched for in s1 is: "  
        << *result1 << endl;  
   cout << "The string beginning with the first occurrence\n "  
        << "of the character 'd' is: " << result1 << endl;  
  
   // When no match is found the NULL value is returned  
   const char* result2;  
   result2 = char_traits<char>::find ( s1 , 3 , 'a');  
   if ( result2 == NULL )  
      cout << "The result2 of the search is NULL." << endl;  
   else  
      cout << "The result2 of the search  is: " << result1  
           << endl;  
}  
```  
  
```Output  
The string to be searched is: f2d-1234-abcd  
The character searched for in s1 is: d  
The string beginning with the first occurrence  
 of the character 'd' is: d-1234-abcd  
The result2 of the search is NULL.  
```  
  
##  <a name="int_type"></a>  char_traits::int_type  
 整數類型，可以代表 `char_type` 類型的字元或檔案結尾 (EOF) 字元。  
  
```  
typedef long int_type;  
```  
  
### <a name="remarks"></a>備註  
 它必須能夠將 **CharType** 類型值的類型轉換為 `int_type`，再轉換回 **CharType**，而不需要改變原始值。  
  
### <a name="example"></a>範例  
  如需如何宣告及使用 `int_type` 的範例，請參閱 [eq_int_type](#eq_int_type) 的範例。  
  
##  <a name="length"></a>  char_traits::length  
 傳回字串的長度。  
  
```  
static size_t length(const char_type* str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 要測量其長度的 C 字串。  
  
### <a name="return-value"></a>傳回值  
 序列中所要測量的元素數目，不包括 Null 結束字元。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_length.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   const char* str1= "Hello";  
   cout << "The C-string str1 is: " << str1 << endl;  
  
   size_t lenStr1;  
   lenStr1 = char_traits<char>::length ( str1 );  
   cout << "The length of C-string str1 is: "   
        << lenStr1 << "." << endl;  
}  
```  
  
```Output  
The C-string str1 is: Hello  
The length of C-string str1 is: 5.  
```  
  
##  <a name="lt"></a>  char_traits::lt  
 測試一個字元是否小於另一個。  
  
```  
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```  
  
### <a name="parameters"></a>參數  
 `_Ch1`  
 要測試何者較小之兩個字元的第一個字元。  
  
 `_Ch2`  
 要測試何者較小之兩個字元的第二個字元。  
  
### <a name="return-value"></a>傳回值  
 若第一個字元小於第二個字元，即為 **true**；否則為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_lt.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::char_type ch2 =  'y';  
   char_traits<char>::char_type ch3 =  'z';  
  
   // Testing for less than  
   bool b1 = char_traits<char>::lt ( ch1 , ch2 );  
   if ( b1 )  
      cout << "The character ch1 is less than "  
           << "the character ch2." << endl;  
   else  
      cout << "The character ch1 is not less "  
           << "than the character ch2." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( ch3 <  ch2 )  
      cout << "The character ch3 is less than "  
           << "the character ch2." << endl;  
   else  
      cout << "The character ch3 is not less "  
           << "than the character ch2." << endl;  
}  
```  
  
```Output  
The character ch1 is less than the character ch2.  
The character ch3 is not less than the character ch2.  
```  
  
##  <a name="move"></a>  char_traits::move  
 將序列中指定的字元數複製到可能重疊的另一個序列。  
  
 此方法有賴於呼叫者檢查傳遞的值是否正確，因此可能不安全。 請考慮改用 [char_traits::_Move_s](#move_s)。  
  
```  
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```  
  
### <a name="parameters"></a>參數  
 `_To`  
 要接收已複製字元序列之目標字串或字元陣列開頭的元素。  
  
 `_From`  
 要複製之來源字串或字元陣列開頭的元素。  
  
 `_Num`  
 要從來源字串中複製的元素數目。  
  
### <a name="return-value"></a>傳回值  
 複製到要接收已複製字元序列之目標字串或字元陣列的第一個元素 `_To`。  
  
### <a name="remarks"></a>備註  
 來源和目的地可能會重疊。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_move.cpp  
// compile with: /EHsc /W3  
#include <string>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";  
   char_traits<char>::char_type sTo1[] =  "ABCD-1234";  
   char_traits<char>::char_type* result1;  
   cout << "The source string sFrom1 is: " << sFrom1 << endl;  
   cout << "The destination stringsTo1 is: " << sTo1 << endl;  
   // Note: char_traits::move is potentially unsafe, consider  
   // using char_traits::_Move_s instead.  
   result1 = char_traits<char>::move ( sTo1 ,  sFrom1 , 4 );  // C4996  
   cout << "The result1 = move ( sTo1 , sFrom1 , 4 ) is: "  
        << result1 << endl << endl;  
  
   // When source and destination overlap  
   char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";  
   char_traits<char>::char_type* result2;  
   cout << "The source/destination string sToFrom2 is: "  
        << sToFrom2 << endl;  
   const char* findc = char_traits<char>::find ( sToFrom2 , 4 , 'c' );  
   // Note: char_traits::move is potentially unsafe, consider  
   // using char_traits::_Move_s instead.  
   result2 = char_traits<char>::move ( sToFrom2 , findc , 8 );  // C4996  
   cout << "The result2 = move ( sToFrom2 , findc , 8 ) is: "  
        << result2 << endl;  
}  
```  
  
```Output  
The source string sFrom1 is: abcd-1234-abcd  
The destination stringsTo1 is: ABCD-1234  
The result1 = move ( sTo1 , sFrom1 , 4 ) is: abcd-1234  
  
The source/destination string sToFrom2 is: abcd-1234-ABCD  
The result2 = move ( sToFrom2 , findc , 8 ) is: cd-1234-4-ABCD  
```  
  
##  <a name="move_s"></a>  char_traits::_Move_s  
 將序列中指定的字元數複製到可能重疊的另一個序列。  
  
```  
static char_type *_Move_s(
    char_type* dest,  
    size_t dest_size,  
    const char_type* _From,  
    size_t count);
```  
  
### <a name="parameters"></a>參數  
 `dest`  
 要接收已複製字元序列之目標字串或字元陣列開頭的元素。  
  
 `dest_size`  
 `dest` 的大小。 如果 `char_type` 是 `char`，則以位元組為單位。 如果 `char_type` 是 `wchar_t`，則以字組為單位。  
  
 `_From`  
 要複製之來源字串或字元陣列開頭的元素。  
  
 `count`  
 要從來源字串中複製的元素數目。  
  
### <a name="return-value"></a>傳回值  
 複製到要接收已複製字元序列之目標字串或字元陣列的第一個元素 `dest`。  
  
### <a name="remarks"></a>備註  
 來源和目的地可能會重疊。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits__Move_s.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
  
    char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";  
    char_traits<char>::char_type sTo1[] =  "ABCD-1234";  
    char_traits<char>::char_type* result1;  
    cout << "The source string sFrom1 is: " << sFrom1 << endl;  
    cout << "The destination stringsTo1 is: " << sTo1 << endl;  
    result1 = char_traits<char>::_Move_s(sTo1,  
        char_traits<char>::length(sTo1), sFrom1, 4);  
    cout << "The result1 = _Move_s(sTo1, "  
         << "char_traits<char>::length(sTo1), sFrom1, 4) is: "  
         << result1 << endl << endl;  
  
    // When source and destination overlap  
    char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";  
    char_traits<char>::char_type* result2;  
    cout << "The source/destination string sToFrom2 is: "  
         << sToFrom2 << endl;  
    const char* findc = char_traits<char>::find(sToFrom2, 4, 'c');  
    result2 = char_traits<char>::_Move_s(sToFrom2,  
        char_traits<char>::length(sToFrom2), findc, 8);  
    cout << "The result2 = _Move_s(sToFrom2, "  
        << "char_traits<char>::length(sToFrom2), findc, 8) is: "  
         << result2 << endl;  
}  
```  
  
```Output  
The source string sFrom1 is: abcd-1234-abcd  
The destination stringsTo1 is: ABCD-1234  
The result1 = _Move_s(sTo1, char_traits<char>::length(sTo1), sFrom1, 4) is: abcd-1234  
  
The source/destination string sToFrom2 is: abcd-1234-ABCD  
The result2 = _Move_s(sToFrom2, char_traits<char>::length(sToFrom2), findc, 8) is: cd-1234-4-ABCD  
```  
  
##  <a name="not_eof"></a>  char_traits::not_eof  
 測試字元是否為檔案結尾 (EOF) 字元。  
  
```  
static int_type not_eof(const int_type& _Ch);
```  
  
### <a name="parameters"></a>參數  
 `_Ch`  
 要測試其是否為 EOF 字元的字元 (以 `int_type` 表示)。  
  
### <a name="return-value"></a>傳回值  
 如果所測試之字元的 **int_type** 與 EOF 字元的類型不相等，則以 `int_type` 表示該字元。  
  
 若字元的 `int_type` 值等於 EOF 的 `int_type` 值，即為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_not_eof.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( ) {  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'x';  
   char_traits<char>::int_type int1;  
   int1 = char_traits<char>:: to_int_type ( ch1 );  
   cout << "The char_type ch1 is " << ch1  
        << " corresponding to int_type: "   
        << int1 << "." << endl;  
  
   // EOF member function  
   char_traits <char>::int_type int2 = char_traits<char>::eof ( );  
   cout << "The eofReturn is: " << int2 << endl;  
  
   // Testing for EOF or another character  
   char_traits <char>::int_type eofTest1, eofTest2;  
   eofTest1 = char_traits<char>::not_eof ( int1 );  
   if ( !eofTest1 )  
      cout << "The eofTest1 indicates ch1 is an EOF character."  
              << endl;  
   else  
      cout << "The eofTest1 returns: " << eofTest1   
           << ", which is the character: "   
           <<  char_traits<char>::to_char_type ( eofTest1 )  
           << "." << endl;  
  
   eofTest2 = char_traits<char>::not_eof ( int2 );  
   if ( !eofTest2 )  
      cout << "The eofTest2 indicates int2 is an EOF character."   
           << endl;  
   else  
      cout << "The eofTest1 returns: " << eofTest2   
           << ", which is the character: "   
           <<  char_traits<char>::to_char_type ( eofTest2 )   
           << "." << endl;  
}  
```  
  
```Output  
The char_type ch1 is x corresponding to int_type: 120.  
The eofReturn is: -1  
The eofTest1 returns: 120, which is the character: x.  
The eofTest2 indicates int2 is an EOF character.  
```  
  
##  <a name="off_type"></a>  char_traits::off_type  
 整數類型，可以代表資料流中位置之間的位移。  
  
```  
typedef streamoff off_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是帶正負號整數，描述可儲存與各種資料流定位作業有關之位元組位移的物件。 它通常與 [streamoff](../standard-library/ios-typedefs.md#streamoff) 同義，但基本上會有與該類型相同的屬性。  
  
##  <a name="pos_type"></a>  char_traits::pos_type  
 整數類型，可以代表資料流中的位置。  
  
```  
typedef streampos pos_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述可儲存對資料流內的任意檔案位置指標進行還原之所有必要資訊的物件。 它通常與 [streamoff](../standard-library/ios-typedefs.md#streampos) 同義，但在任何情況下基本上都會有與該類型相同的屬性。  
  
##  <a name="state_type"></a>  char_traits::state_type  
 代表資料流中多位元組字元之轉換狀態的類型。  
  
```  
typedef implementation-defined state_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述可代表轉換狀態的物件。 它通常與 `mbstate_t` 同義，但在任何情況下基本上都會有與該類型相同的屬性。  
  
##  <a name="to_char_type"></a>  char_traits::to_char_type  
 將 `int_type` 字元轉換為對應的 `char_type` 字元，並傳回結果。  
  
```  
static char_type to_char_type(const int_type& _Ch);
```  
  
### <a name="parameters"></a>參數  
 `_Ch`  
 要以 `char_type` 表示的 `int_type` 字元。  
  
### <a name="return-value"></a>傳回值  
 對應至 `int_type` 的 `char_type` 字元。  
  
 無法以此表示的 `_Ch` 值會產生不明結果。  
  
### <a name="remarks"></a>備註  
 轉換作業 [to_int_type](#to_int_type) 和 `to_char_type` 彼此相反，因此：  
  
 `to_int_type` ( `to_char_type` ( *x* ) ) == *x*  
  
 (針對任何 `int_type` *x*)，且  
  
 `to_char_type` ( `to_int_type` ( *x* ) ) == *x*  
  
 (針對任何 `char_type` *x*)。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_to_char_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   char_traits<char>::char_type ch1 =  'a';  
   char_traits<char>::char_type ch2 =  'b';  
   char_traits<char>::char_type ch3 =  'a';  
  
   // Converting from char_type to int_type  
   char_traits<char>::int_type int1, int2 , int3;  
   int1 =char_traits<char>:: to_int_type ( ch1 );  
   int2 =char_traits<char>:: to_int_type ( ch2 );  
   int3 =char_traits<char>:: to_int_type ( ch3 );  
  
   cout << "The char_types and corresponding int_types are:"  
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "   
        << int1 << "."  
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "   
        << int2 << "."  
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "   
        << int3 << "." << endl << endl;  
  
   // Converting from int_type back to char_type  
   char_traits<char>::char_type rec_ch1;  
   rec_ch1 = char_traits<char>:: to_char_type ( int1);  
   char_traits<char>::char_type rec_ch2;  
   rec_ch2 = char_traits<char>:: to_char_type ( int2);  
  
   cout << "The recovered char_types and corresponding int_types are:"  
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "   
        << int1 << "."  
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "   
        << int2 << "." << endl << endl;  
  
   // Testing that the conversions are inverse operations  
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );  
   if ( b1 )  
      cout << "The recovered char_type of ch1"  
           << " is equal to the original ch1." << endl;  
   else  
      cout << "The recovered char_type of ch1"  
           << " is not equal to the original ch1." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( rec_ch2 == ch2 )  
      cout << "The recovered char_type of ch2"  
           << " is equal to the original ch2." << endl;  
   else  
      cout << "The recovered char_type of ch2"  
           << " is not equal to the original ch2." << endl;  
}  
```  
  
```Output  
The char_types and corresponding int_types are:  
    ch1 = a corresponding to int1 = 97.  
    ch2 = b corresponding to int1 = 98.  
    ch3 = a corresponding to int1 = 97.  
  
The recovered char_types and corresponding int_types are:  
    recovered ch1 = a from int1 = 97.  
    recovered ch2 = b from int2 = 98.  
  
The recovered char_type of ch1 is equal to the original ch1.  
The recovered char_type of ch2 is equal to the original ch2.  
```  
  
##  <a name="to_int_type"></a>  char_traits::to_int_type  
 將 `char_type` 字元轉換為對應的 `int_type` 字元，並傳回結果。  
  
```  
static int_type to_int_type(const char_type& _Ch);
```  
  
### <a name="parameters"></a>參數  
 `_Ch`  
 要以 `int_type` 表示的 `char_type` 字元。  
  
### <a name="return-value"></a>傳回值  
 對應至 `char_type` 的 `int_type` 字元。  
  
### <a name="remarks"></a>備註  
 轉換作業 `to_int_type` 和 [to_char_type](#to_char_type) 彼此相反，因此：  
  
 `to_int_type` ( `to_char_type` ( *x* ) ) == *x*  
  
 (針對任何 `int_type` *x*)，且  
  
 `to_char_type` ( `to_int_type` ( *x* ) ) == *x*  
  
 (針對任何 `char_type` *x*)。  
  
### <a name="example"></a>範例  
  
```cpp  
// char_traits_to_int_type.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   char_traits<char>::char_type ch1 = 'a';  
   char_traits<char>::char_type ch2 = 'b';  
   char_traits<char>::char_type ch3 = 'a';  
  
   // Converting from char_type to int_type  
   char_traits<char>::int_type int1, int2 , int3;  
   int1 =char_traits<char>:: to_int_type ( ch1 );  
   int2 =char_traits<char>:: to_int_type ( ch2 );  
   int3 =char_traits<char>:: to_int_type ( ch3 );  
  
   cout << "The char_types and corresponding int_types are:"  
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "   
        << int1 << "."  
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "   
        << int2 << "."  
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "   
        << int3 << "." << endl << endl;  
  
   // Converting from int_type back to char_type  
   char_traits<char>::char_type rec_ch1;  
   rec_ch1 = char_traits<char>:: to_char_type ( int1);  
   char_traits<char>::char_type rec_ch2;  
   rec_ch2 = char_traits<char>:: to_char_type ( int2);  
  
   cout << "The recovered char_types and corresponding int_types are:"  
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "   
        << int1 << "."  
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "   
        << int2 << "." << endl << endl;  
  
   // Testing that the conversions are inverse operations  
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );  
   if ( b1 )  
      cout << "The recovered char_type of ch1"  
           << " is equal to the original ch1." << endl;  
   else  
      cout << "The recovered char_type of ch1"  
           << " is not equal to the original ch1." << endl;  
  
   // An equivalent and alternatively test procedure  
   if ( rec_ch2 == ch2 )  
      cout << "The recovered char_type of ch2"  
           << " is equal to the original ch2." << endl;  
   else  
      cout << "The recovered char_type of ch2"  
           << " is not equal to the original ch2." << endl;  
}  
```  
  
```Output  
The char_types and corresponding int_types are:  
    ch1 = a corresponding to int1 = 97.  
    ch2 = b corresponding to int1 = 98.  
    ch3 = a corresponding to int1 = 97.  
  
The recovered char_types and corresponding int_types are:  
    recovered ch1 = a from int1 = 97.  
    recovered ch2 = b from int2 = 98.  
  
The recovered char_type of ch1 is equal to the original ch1.  
The recovered char_type of ch2 is equal to the original ch2.  
```  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


