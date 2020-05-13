---
title: numpunct 類別
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct
- xlocnum/std::numpunct::char_type
- xlocnum/std::numpunct::string_type
- xlocnum/std::numpunct::decimal_point
- xlocnum/std::numpunct::do_decimal_point
- xlocnum/std::numpunct::do_falsename
- xlocnum/std::numpunct::do_grouping
- xlocnum/std::numpunct::do_thousands_sep
- xlocnum/std::numpunct::do_truename
- xlocnum/std::numpunct::falsename
- xlocnum/std::numpunct::grouping
- xlocnum/std::numpunct::thousands_sep
- xlocnum/std::numpunct::truename
helpviewer_keywords:
- std::numpunct [C++]
- std::numpunct [C++], char_type
- std::numpunct [C++], string_type
- std::numpunct [C++], decimal_point
- std::numpunct [C++], do_decimal_point
- std::numpunct [C++], do_falsename
- std::numpunct [C++], do_grouping
- std::numpunct [C++], do_thousands_sep
- std::numpunct [C++], do_truename
- std::numpunct [C++], falsename
- std::numpunct [C++], grouping
- std::numpunct [C++], thousands_sep
- std::numpunct [C++], truename
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
ms.openlocfilehash: 0bdd6556df892e5e231919dbc4ae95d14a6f95fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373621"
---
# <a name="numpunct-class"></a>numpunct 類別

一個類範本,用於描述可用作局部面的物件,用於描述有關數位和布爾表達式的格式和`CharType`標點的資訊的類型序列。

## <a name="syntax"></a>語法

```cpp
template <class CharType>
class numpunct : public locale::facet;
```

### <a name="parameters"></a>參數

*字元類型*\
程式內用於編碼地區設定字元的類型。

## <a name="remarks"></a>備註

如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[numpunct](#numpunct)|`numpunct` 類型物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|
|[string_type](#string_type)|類型，描述包含 `CharType` 類型字元的字串。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[decimal_point](#decimal_point)|傳回地區設定特定項目以做為小數點。|
|[do_decimal_point](#do_decimal_point)|受保護的虛擬成員函式，呼叫以傳回要做為小數點的地區設定特定項目。|
|[do_falsename](#do_falsename)|被呼叫以返回字串以用作值**false**的文本表示形式的保護虛擬成員函數。|
|[do_grouping](#do_grouping)|受保護的虛擬成員函式，呼叫以傳回決定如何將數字群組在小數點左側的地區設定特定規則。|
|[do_thousands_sep](#do_thousands_sep)|受保護的虛擬成員函式，呼叫以傳回要做為千位分隔符號的地區設定特定項目。|
|[do_truename](#do_truename)|受保護的虛擬成員函式，呼叫以傳回要當做 **true** 值的文字表示的字串。|
|[falsename](#falsename)|傳回字串，做為 **false** 值的文字表示。|
|[群組](#grouping)|傳回決定如何將數字群組在任何小數點左側的地區設定特定規則。|
|[thousands_sep](#thousands_sep)|傳回地區設定特定項目以做為千位分隔符號。|
|[truename](#truename)|傳回字串，做為 **true** 值的文字表示。|

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="numpunctchar_type"></a><a name="char_type"></a>數位::char_type

類型，用來描述由地區設定使用的字元。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

類型是範本參數**CharType**的同義詞。

## <a name="numpunctdecimal_point"></a><a name="decimal_point"></a>數位::d次]點

傳回地區設定特定項目以做為小數點。

```cpp
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

## <a name="numpunctdo_decimal_point"></a><a name="do_decimal_point"></a>數位::d奧多數點

受保護的虛擬成員函式，呼叫以傳回要做為小數點的地區設定特定項目。

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>傳回值

要做為小數點的地區設定特定項目。

### <a name="example"></a>範例

請參閱 [decimal_point](#decimal_point) 的範例，其中會由 `decimal_point` 呼叫此虛擬成員函式。

## <a name="numpunctdo_falsename"></a><a name="do_falsename"></a>numpunct::do_假名

受保護的虛擬成員函式，傳回當作 **false** 值的文字表示的序列。

```cpp
virtual string_type do_falsename() const;
```

### <a name="return-value"></a>傳回值

字串，包含當作 **false** 值的文字表示的序列。

### <a name="remarks"></a>備註

成員函式會傳回字串 "false" 來表示所有地區設定中的 **false** 值。

### <a name="example"></a>範例

請參閱 [falsename](#falsename) 的範例，其中 `falsename` 會呼叫虛擬成員函式。

## <a name="numpunctdo_grouping"></a><a name="do_grouping"></a>數位::do_分組

受保護的虛擬成員函式，呼叫以傳回決定如何將數字群組在小數點左側的地區設定特定規則。

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>傳回值

地區設定特定規則，用來決定任何小數點左邊數字分組的方式。

### <a name="remarks"></a>備註

受保護的虛擬成員函式傳回決定如何將數字群組在小數點左側的地區設定特定規則。 編碼和 **lconv::grouping** 相同。

### <a name="example"></a>範例

請參閱[分組的示例](#grouping),其中虛擬成員函`grouping`數由 調用。

## <a name="numpunctdo_thousands_sep"></a><a name="do_thousands_sep"></a>數位::do_千_sep

受保護的虛擬成員函式，呼叫以傳回要做為千位分隔符號的地區設定特定項目。

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>傳回值

傳回地區設定特定項目以做為千位分隔符號。

### <a name="remarks"></a>備註

受保護的虛擬成員函數返回特定於區域設置的類型`CharType`元素,以用作任何小數點左側的組分隔符。

### <a name="example"></a>範例

請參閱 [thousands_sep](#thousands_sep) 的範例，其中會由 `thousands_sep` 呼叫此虛擬成員函式。

## <a name="numpunctdo_truename"></a><a name="do_truename"></a>numpunct::do_truename

受保護的虛擬成員函式，呼叫以傳回要當做 **true** 值的文字表示的字串。

```cpp
virtual string_type do_truename() const;
```

### <a name="remarks"></a>備註

字串，做為 **true** 值的文字表示。

所有的地區設定會傳回字串 "true" 來表示 **true** 值。

### <a name="example"></a>範例

請參閱 [truename](#truename) 的範例，其中 `truename` 會呼叫虛擬成員函式。

## <a name="numpunctfalsename"></a><a name="falsename"></a>數位::假名

傳回字串，做為 **false** 值的文字表示。

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>傳回值

包含用於用作值`CharType`**false**的文本表示表示的序列的字串。

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

## <a name="numpunctgrouping"></a><a name="grouping"></a>數字::群組

傳回決定如何將數字群組在任何小數點左側的地區設定特定規則。

```cpp
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

## <a name="numpunctnumpunct"></a><a name="numpunct"></a>數字::numpunct

`numpunct` 類型物件的建構函式。

```cpp
explicit numpunct(size_t _Refs = 0);
```

### <a name="parameters"></a>參數

*_Refs*\
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

*_Refs*參數的可能值及其顯著性為:

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- \>1: 未定義這些值。

無法提供任何直接範例，因為解構函式受到保護。

建構函式用區域設定初始化其基本物件 **::**[分面](../standard-library/locale-class.md#facet_class)(`_Refs`。

## <a name="numpunctstring_type"></a><a name="string_type"></a>數位::string_type

類型，描述包含 **CharType** 類型字元的字串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>備註

該類型描述了類範本的專門化[basic_string](../standard-library/basic-string-class.md)其物件可以存儲標點序列的副本。

## <a name="numpunctthousands_sep"></a><a name="thousands_sep"></a>數位::thousands_sep

傳回地區設定特定項目以做為千位分隔符號。

```cpp
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

## <a name="numpuncttruename"></a><a name="truename"></a>數位::真名

傳回字串，做為 **true** 值的文字表示。

```cpp
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

[\<區域設定>](../standard-library/locale.md)\
[分面類](../standard-library/locale-class.md#facet_class)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
