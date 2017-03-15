---
title: "numpunct 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xlocnum/std::numpunct"
  - "std::numpunct"
  - "numpunct"
  - "std.numpunct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "numpunct 類別"
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# numpunct 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存的值儲存在唯一的正值 **識別碼。**  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[numpunct](#numpunct__numpunct)|`numpunct` 類型物件的建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#numpunct__char_type)|類型，用來描述由地區設定使用的字元。|  
|[string_type](#numpunct__string_type)|類型，描述包含 `CharType` 類型字元的字串。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[decimal_point](#numpunct__decimal_point)|傳回地區設定特定項目以做為小數點。|  
|[do_decimal_point](#numpunct__do_decimal_point)|受保護的虛擬成員函式，呼叫以傳回要做為小數點的地區設定特定項目。|  
|[do_falsename](#numpunct__do_falsename)|受保護的虛擬成員函式，呼叫以傳回要當做 `false` 值的文字表示的字串。|  
|[do_grouping](#numpunct__do_grouping)|受保護的虛擬成員函式，呼叫以傳回決定如何將數字群組在小數點左側的地區設定特定規則。|  
|[do_thousands_sep](#numpunct__do_thousands_sep)|受保護的虛擬成員函式，呼叫以傳回要做為千位分隔符號的地區設定特定項目。|  
|[do_truename](#numpunct__do_truename)|受保護的虛擬成員函式，呼叫以傳回要當做 `true` 值的文字表示的字串。|  
|[falsename](#numpunct__falsename)|傳回字串，做為 `false` 值的文字表示。|  
|[群組](#numpunct__grouping)|傳回決定如何將數字群組在任何小數點左側的地區設定特定規則。|  
|[thousands_sep](#numpunct__thousands_sep)|傳回地區設定特定項目以做為千位分隔符號。|  
|[truename](#numpunct__truename)|傳回字串，做為 `true` 值的文字表示。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 地區設定>  
  
 **命名空間：** std  
  
##  <a name="a-namenumpunctchartypea-numpunctchartype"></a><a name="numpunct__char_type"></a>  numpunct:: char_type  
 類型，用來描述由地區設定使用的字元。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **CharType。**  
  
##  <a name="a-namenumpunctdecimalpointa-numpunctdecimalpoint"></a><a name="numpunct__decimal_point"></a>  numpunct:: decimal_point  
 傳回地區設定特定項目以做為小數點。  
  
```  
CharType decimal_point() const;
```  
  
### <a name="return-value"></a>傳回值  
 要做為小數點的地區設定特定項目。  
  
### <a name="remarks"></a>備註  
 成員函式傳回 [do_decimal_point](#numpunct__do_decimal_point)。  
  
### <a name="example"></a>範例  
  
```  
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
  
##  <a name="a-namenumpunctdodecimalpointa-numpunctdodecimalpoint"></a><a name="numpunct__do_decimal_point"></a>  numpunct:: do_decimal_point  
 受保護的虛擬成員函式，呼叫以傳回要做為小數點的地區設定特定項目。  
  
```  
virtual CharType do_decimal_point() const;
```  
  
### <a name="return-value"></a>傳回值  
 要做為小數點的地區設定特定項目。  
  
### <a name="example"></a>範例  
  請參閱範例 [decimal_point](#numpunct__decimal_point), ，其中的虛擬成員函式會呼叫 `decimal_point`。  
  
##  <a name="a-namenumpunctdofalsenamea-numpunctdofalsename"></a><a name="numpunct__do_falsename"></a>  numpunct:: do_falsename  
 受保護的虛擬成員函式會傳回要做為值的文字表示序列 **false**。  
  
```  
virtual string_type do_falsename() const;
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含要做為值的文字表示的序列 **false**。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回字串"false"來代表值 **false** 所有地區設定。  
  
### <a name="example"></a>範例  
  請參閱範例 [falsename](#numpunct__falsename), ，其中的虛擬成員函式會呼叫 `falsename`。  
  
##  <a name="a-namenumpunctdogroupinga-numpunctdogrouping"></a><a name="numpunct__do_grouping"></a>  numpunct:: do_grouping  
 受保護的虛擬成員函式，呼叫以傳回決定如何將數字群組在小數點左側的地區設定特定規則。  
  
```  
virtual string do_grouping() const;
```  
  
### <a name="return-value"></a>傳回值  
 決定如何將數字群組的任何小數點左側的地區設定特定規則。  
  
### <a name="remarks"></a>備註  
 受保護的虛擬成員函式傳回決定如何將數字群組在小數點左側的地區設定特定規則。 編碼是相同 **lconv::grouping**。  
  
### <a name="example"></a>範例  
  請參閱範例 [分組](#numpunct__grouping), ，其中的虛擬成員函式會呼叫 **分組**。  
  
##  <a name="a-namenumpunctdothousandssepa-numpunctdothousandssep"></a><a name="numpunct__do_thousands_sep"></a>  numpunct:: do_thousands_sep  
 受保護的虛擬成員函式，呼叫以傳回要做為千位分隔符號的地區設定特定項目。  
  
```  
virtual CharType do_thousands_sep() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回地區設定特定項目以做為千位分隔符號。  
  
### <a name="remarks"></a>備註  
 受保護的虛擬成員函式傳回地區設定特定項目型別的 **CharType** 要做為群組分隔符號的小數點左邊。  
  
### <a name="example"></a>範例  
  請參閱範例 [thousands_sep](#numpunct__thousands_sep), ，其中的虛擬成員函式會呼叫 `thousands_sep`。  
  
##  <a name="a-namenumpunctdotruenamea-numpunctdotruename"></a><a name="numpunct__do_truename"></a>  numpunct:: do_truename  
 受保護的虛擬成員函式，呼叫以傳回要做為值的文字表示的字串 **true**。  
  
```  
virtual string_type do_truename() const;
```  
  
### <a name="remarks"></a>備註  
 若要使用之值的文字表示為字串 **true**。  
  
 所有地區設定會傳回字串"true"來代表值 **true**。  
  
### <a name="example"></a>範例  
  請參閱範例 [truename](#numpunct__truename), ，其中的虛擬成員函式會呼叫 `truename`。  
  
##  <a name="a-namenumpunctfalsenamea-numpunctfalsename"></a><a name="numpunct__falsename"></a>  numpunct:: falsename  
 傳回字串，做為值的文字表示 **false**。  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含一系列 **CharType**s 来做為值的文字表示 **false**。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回字串"false"來代表值 **false** 所有地區設定。  
  
 成員函式傳回 [do_falsename](#numpunct__do_falsename)。  
  
### <a name="example"></a>範例  
  
```  
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
  
##  <a name="a-namenumpunctgroupinga-numpunctgrouping"></a><a name="numpunct__grouping"></a>  numpunct:: grouping  
 傳回決定如何將數字群組在任何小數點左側的地區設定特定規則。  
  
```  
string grouping() const;
```  
  
### <a name="return-value"></a>傳回值  
 決定如何將數字群組的任何小數點左側的地區設定特定規則。  
  
### <a name="remarks"></a>備註  
 成員函式傳回 [do_grouping](#numpunct__do_grouping)。  
  
### <a name="example"></a>範例  
  
```  
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
  
##  <a name="a-namenumpunctnumpuncta-numpunctnumpunct"></a><a name="numpunct__numpunct"></a>  numpunct:: numpunct  
 `numpunct` 類型物件的建構函式。  
  
```  
explicit numpunct(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>參數  
 `_Refs`  
 用來指定物件的記憶體管理類型的整數值。  
  
### <a name="remarks"></a>備註  
 可能值 `_Refs` 參數和其重要性為︰  
  
-   0︰ 物件存留期由包含它的地區設定。  
  
-   1︰ 必須以手動方式管理物件存留期。  
  
-   \> 0︰ 未定義這些值。  
  
 因為解構函式會受到保護，是可行的沒有直接的範例。  
  
 建構函式初始化具有其基底物件 **地區設定::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`)。  
  
##  <a name="a-namenumpunctstringtypea-numpunctstringtype"></a><a name="numpunct__string_type"></a>  numpunct:: string_type  
 類型，描述包含型別字元的字串 **CharType**。  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述範本類別的特製化 [basic_string](../standard-library/basic-string-class.md) 其物件可以儲存複本的標點符號序列。  
  
##  <a name="a-namenumpunctthousandssepa-numpunctthousandssep"></a><a name="numpunct__thousands_sep"></a>  numpunct:: thousands_sep  
 傳回地區設定特定項目以做為千位分隔符號。  
  
```  
CharType thousands_sep() const;
```  
  
### <a name="return-value"></a>傳回值  
 將地區設定特定項目做為千位分隔符號。  
  
### <a name="remarks"></a>備註  
 成員函式傳回 [do_thousands_sep](#numpunct__do_thousands_sep)。  
  
### <a name="example"></a>範例  
  
```  
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
  
##  <a name="a-namenumpuncttruenamea-numpuncttruename"></a><a name="numpunct__truename"></a>  numpunct:: truename  
 傳回字串，做為值的文字表示 **true**。  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>傳回值  
 若要使用之值的文字表示為字串 **true**。  
  
### <a name="remarks"></a>備註  
 成員函式傳回 [do_truename](#numpunct__do_truename)。  
  
 所有地區設定會傳回字串"true"來代表值 **true**。  
  
### <a name="example"></a>範例  
  
```  
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
 [\< 地區設定>](../standard-library/locale.md)   
 [facet 類別](../standard-library/locale-class.md#facet_class)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

