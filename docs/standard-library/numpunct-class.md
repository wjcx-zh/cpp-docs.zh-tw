---
title: "numpunct 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocnum/std::numpunct
- numpunct
- locale/std::numpunct::char_type
- locale/std::numpunct::string_type
- locale/std::numpunct::decimal_point
- locale/std::numpunct::do_decimal_point
- locale/std::numpunct::do_falsename
- locale/std::numpunct::do_grouping
- locale/std::numpunct::do_thousands_sep
- locale/std::numpunct::do_truename
- locale/std::numpunct::falsename
- locale/std::numpunct::grouping
- locale/std::numpunct::thousands_sep
- locale/std::numpunct::truename
dev_langs:
- C++
helpviewer_keywords:
- numpunct class
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 56dbd3ed6e655ec5f431d383864f949925baaf5c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="numpunct-class"></a>numpunct 類別
樣板類別，描述可以做為區域 facet 的物件，以描述用來表示數值和布林運算式格式和標點符號資訊之 `CharType` 類型的序列。  
  
## <a name="syntax"></a>語法  
  
```  
template <class CharType>  
class numpunct : public locale::facet;  
```  
  
#### <a name="parameters"></a>參數  
 `CharType`  
 程式內用於編碼地區設定字元的類型。  
  
## <a name="remarks"></a>備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[numpunct](#numpunct)|`numpunct` 類型物件的建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|  
|[string_type](#string_type)|類型，描述包含 `CharType` 類型字元的字串。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[decimal_point](#decimal_point)|傳回地區設定特定項目以做為小數點。|  
|[do_decimal_point](#do_decimal_point)|受保護的虛擬成員函式，呼叫以傳回要做為小數點的地區設定特定項目。|  
|[do_falsename](#do_falsename)|受保護的虛擬成員函式，呼叫以傳回要當做 `false` 值的文字表示的字串。|  
|[do_grouping](#do_grouping)|受保護的虛擬成員函式，呼叫以傳回決定如何將數字群組在小數點左側的地區設定特定規則。|  
|[do_thousands_sep](#do_thousands_sep)|受保護的虛擬成員函式，呼叫以傳回要做為千位分隔符號的地區設定特定項目。|  
|[do_truename](#do_truename)|受保護的虛擬成員函式，呼叫以傳回要當做 `true` 值的文字表示的字串。|  
|[falsename](#falsename)|傳回字串，做為 `false` 值的文字表示。|  
|[grouping](#grouping)|傳回決定如何將數字群組在任何小數點左側的地區設定特定規則。|  
|[thousands_sep](#thousands_sep)|傳回地區設定特定項目以做為千位分隔符號。|  
|[truename](#truename)|傳回字串，做為 `true` 值的文字表示。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
##  <a name="char_type"></a>  numpunct::char_type  
 類型，用來描述由地區設定使用的字元。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型與範本參數 **CharType** 同義。  
  
##  <a name="decimal_point"></a>  numpunct::decimal_point  
 傳回地區設定特定項目以做為小數點。  
  
```  
CharType decimal_point() const;
```  
  
### <a name="return-value"></a>傳回值  
 要做為小數點的地區設定特定項目。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回 [do_decimal_point](#do_decimal_point)。  
  
### <a name="example"></a>範例  
  
```cpp  
// numpunct_decimal_point.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const numpunct <char> &npunct =   
   use_facet <numpunct <char> >( loc);  
   cout << loc.name( ) << " decimal point "<<   
   npunct.decimal_point( ) << endl;  
   cout << loc.name( ) << " thousands separator "   
   << npunct.thousands_sep( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 decimal point ,  
German_Germany.1252 thousands separator .  
```  
  
##  <a name="do_decimal_point"></a>  numpunct::do_decimal_point  
 受保護的虛擬成員函式，呼叫以傳回要做為小數點的地區設定特定項目。  
  
```  
virtual CharType do_decimal_point() const;
```  
  
### <a name="return-value"></a>傳回值  
 要做為小數點的地區設定特定項目。  
  
### <a name="example"></a>範例  
  請參閱 [decimal_point](#decimal_point) 的範例，其中 `decimal_point` 會呼叫虛擬成員函式。  
  
##  <a name="do_falsename"></a>  numpunct::do_falsename  
 受保護的虛擬成員函式，傳回當作 **false** 值的文字表示的序列。  
  
```  
virtual string_type do_falsename() const;
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含當作 **false** 值的文字表示的序列。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回字串 "false" 來表示所有地區設定中的 **false** 值。  
  
### <a name="example"></a>範例  
  請參閱 [falsename](#falsename) 的範例，其中 `falsename` 會呼叫虛擬成員函式。  
  
##  <a name="do_grouping"></a>  numpunct::do_grouping  
 受保護的虛擬成員函式，呼叫以傳回決定如何將數字群組在小數點左側的地區設定特定規則。  
  
```  
virtual string do_grouping() const;
```  
  
### <a name="return-value"></a>傳回值  
 地區設定特定規則，用來決定任何小數點左邊數字分組的方式。  
  
### <a name="remarks"></a>備註  
 受保護的虛擬成員函式傳回決定如何將數字群組在小數點左側的地區設定特定規則。 編碼和 **lconv::grouping** 相同。  
  
### <a name="example"></a>範例  
  請參閱 [grouping](#grouping) 的範例，其中 **grouping** 會呼叫虛擬成員函式。  
  
##  <a name="do_thousands_sep"></a>  numpunct::do_thousands_sep  
 受保護的虛擬成員函式，呼叫以傳回要做為千位分隔符號的地區設定特定項目。  
  
```  
virtual CharType do_thousands_sep() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回地區設定特定項目以做為千位分隔符號。  
  
### <a name="remarks"></a>備註  
 受保護的虛擬成員函式會傳回類型 **CharType** 的地區設定特定項目，當作任何小數點左側的群組分隔符號。  
  
### <a name="example"></a>範例  
  請參閱 [thousands_sep](#thousands_sep) 的範例，其中 `thousands_sep` 會呼叫虛擬成員函式。  
  
##  <a name="do_truename"></a>  numpunct::do_truename  
 受保護的虛擬成員函式，呼叫以傳回要當做 **true** 值的文字表示的字串。  
  
```  
virtual string_type do_truename() const;
```  
  
### <a name="remarks"></a>備註  
 字串，做為 **true** 值的文字表示。  
  
 所有的地區設定會傳回字串 "true" 來表示 **true** 值。  
  
### <a name="example"></a>範例  
  請參閱 [truename](#truename) 的範例，其中 `truename` 會呼叫虛擬成員函式。  
  
##  <a name="falsename"></a>  numpunct::falsename  
 傳回字串，做為 **false** 值的文字表示。  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含當作 **false** 值的文字表示的 **CharType** 序列。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回字串 "false" 來表示所有地區設定中的 **false** 值。  
  
 成員函式會傳回 [do_falsename](#do_falsename)。  
  
### <a name="example"></a>範例  
  
```cpp  
// numpunct_falsename.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "English" );  
  
   const numpunct <char> &npunct = use_facet <numpunct <char> >( loc );  
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;  
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;  
  
   locale loc2( "French" );  
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >(loc2);  
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;  
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;  
}  
```  
  
```Output  
English_United States.1252 truename true  
English_United States.1252 falsename false  
French_France.1252 truename true  
French_France.1252 falsename false  
```  
  
##  <a name="grouping"></a>  numpunct::grouping  
 傳回決定如何將數字群組在任何小數點左側的地區設定特定規則。  
  
```  
string grouping() const;
```  
  
### <a name="return-value"></a>傳回值  
 地區設定特定規則，用來決定任何小數點左邊數字分組的方式。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回 [do_grouping](#do_grouping)。  
  
### <a name="example"></a>範例  
  
```cpp  
// numpunct_grouping.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany");  
  
   const numpunct <char> &npunct =   
       use_facet < numpunct <char> >( loc );  
   for (unsigned int i = 0; i < npunct.grouping( ).length( ); i++)  
   {  
      cout << loc.name( ) << " international grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(npunct.grouping ( )[i])   
           << endl;  
   }  
}  
```  
  
```Output  
German_Germany.1252 international grouping:  
 the 0th group to the left of the radix character is of size 3  
```  
  
##  <a name="numpunct"></a>  numpunct::numpunct  
 `numpunct` 類型物件的建構函式。  
  
```  
explicit numpunct(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>參數  
 `_Refs`  
 整數值，用來指定物件的記憶體管理類型。  
  
### <a name="remarks"></a>備註  
 `_Refs` 參數的可能值和其意義如下：  
  
-   0：物件的存留期由包含該物件的地區設定來管理。  
  
-   1：物件的存留期必須以手動方式管理。  
  
-   \>1︰ 未定義這些值。  
  
 無法提供任何直接範例，因為解構函式受到保護。  
  
 建構函式會以 **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`) 初始化其基底物件。  
  
##  <a name="string_type"></a>  numpunct::string_type  
 類型，描述包含 **CharType** 類型字元的字串。  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 [basic_string](../standard-library/basic-string-class.md) 樣板類別的特製化，其物件可儲存標點符號序列的複本。  
  
##  <a name="thousands_sep"></a>  numpunct::thousands_sep  
 傳回地區設定特定項目以做為千位分隔符號。  
  
```  
CharType thousands_sep() const;
```  
  
### <a name="return-value"></a>傳回值  
 要做為千位分隔符號的地區設定特定項目。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回 [do_thousands_sep](#do_thousands_sep)。  
  
### <a name="example"></a>範例  
  
```cpp  
// numpunct_thou_sep.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const numpunct <char> &npunct =   
   use_facet < numpunct < char > >( loc );  
   cout << loc.name( ) << " decimal point "<<   
   npunct.decimal_point( ) << endl;  
   cout << loc.name( ) << " thousands separator "   
   << npunct.thousands_sep( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 decimal point ,  
German_Germany.1252 thousands separator .  
```  
  
##  <a name="truename"></a>  numpunct::truename  
 傳回字串，做為 **true** 值的文字表示。  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>傳回值  
 字串，做為 **true** 值的文字表示。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 [do_truename](#do_truename)。  
  
 所有的地區設定會傳回字串 "true" 來表示 **true** 值。  
  
### <a name="example"></a>範例  
  
```cpp  
// numpunct_truename.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "English" );  
  
   const numpunct < char> &npunct = use_facet <numpunct <char> >( loc );  
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;  
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;  
  
   locale loc2("French");  
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >( loc2 );  
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;  
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;  
}  
```  
  
```Output  
English_United States.1252 truename true  
English_United States.1252 falsename false  
French_France.1252 truename true  
French_France.1252 falsename false  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<locale>](../standard-library/locale.md)   
 [facet 類別](../standard-library/locale-class.md#facet_class)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


