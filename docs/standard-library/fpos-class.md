---
title: fpos 類別
ms.date: 03/27/2019
f1_keywords:
- iosfwd/std::fpos
- iosfwd/std::fpos::seekpos
- iosfwd/std::fpos::state
- iosfwd/std::fpos::operator streamoff
helpviewer_keywords:
- std::fpos [C++]
- std::fpos [C++], seekpos
- std::fpos [C++], state
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
ms.openlocfilehash: 78b136d72067fa5fff58e8a7acc044fb4e1a409e
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565057"
---
# <a name="fpos-class"></a>fpos 類別

此範本類別說明可儲存對任何資料流內的任意檔案位置指標進行還原之所有必要資訊的物件。 類別 fpos\< **St**> 的物件可有效儲存至少兩個成員物件：

- 位元組位移，屬於 [streamoff](../standard-library/ios-typedefs.md#streamoff) 類型。

- 轉換狀態，以供屬於類別 basic_filebuf 的物件型別的`St`，通常是`mbstate_t`。

它也可以儲存 `fpos_t` 類型的任意檔案位置，以供 [basic_filebuf](../standard-library/basic-filebuf-class.md) 類別的物件使用。 但在大小受限的環境中，`streamoff` 與 `fpos_t` 有時候可以互換使用。 若環境中沒有任何資料流有依存於狀態的編碼，實際上可能不會用到 `mbstate_t`。 因此，儲存的成員物件數目可能會不同。

## <a name="syntax"></a>語法

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>參數

*Statetype*<br/>
狀態資訊。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[fpos](#fpos)|建立一個物件，其中包含與資料流中的位置 (位移) 有關的資訊。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[seekpos](#seekpos)|僅限 C++ 標準程式庫內部使用。 請勿從您的程式碼呼叫此方法。|
|[state](#state)|設定或傳回轉換狀態。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](#op_neq)|測試檔案位置指標是否不相等。|
|[operator+](#op_add)|遞增檔案位置指標|
|[operator+=](#op_add_eq)|遞增檔案位置指標|
|[operator-](#operator-)|減少檔案位置指標。|
|[operator-=](#operator-_eq)|減少檔案位置指標。|
|[operator==](#op_eq_eq)|測試檔案位置指標是否相等。|
|[operator streamoff](#op_streamoff)|將類型 `fpos` 的物件轉換成類型 `streamoff` 的物件。|

## <a name="requirements"></a>需求

**標頭：**\<ios>

**命名空間：** std

## <a name="fpos"></a>  fpos::fpos

建立一個物件，其中包含與資料流中的位置 (位移) 有關的資訊。

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>參數

*_Off*<br/>
資料流中的位移。

*_State*<br/>
`fpos` 物件的開始狀態。

*_Filepos*<br/>
資料流中的位移。

### <a name="remarks"></a>備註

第一個建構函式儲存的位移 *_Off*，相對於檔案開頭和初始轉換狀態 （如果重要的話）。 如果 *_Off*為-1，產生的物件代表無效的資料流位置。

第二個建構函式會儲存一個零位移與物件 *_State*。

## <a name="op_neq"></a>  fpos::operator!=

測試檔案位置指標是否不相等。

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
以比較目標為依據的檔案位置指標。

### <a name="return-value"></a>傳回值

如果檔案位置指標不相等，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

成員函式會傳回 `!(*this == right)`。

### <a name="example"></a>範例

```cpp
// fpos_op_neq.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;

   fpos<int> pos1, pos2;
   ifstream file;
   char c;

   // Compare two fpos object
   if ( pos1 != pos2 )
      cout << "File position pos1 and pos2 are not equal" << endl;
   else
      cout << "File position pos1 and pos2 are equal" << endl;

   file.open( "fpos_op_neq.txt" );
   file.seekg( 0 );   // Goes to a zero-based position in the file
   pos1 = file.tellg( );
   file.get( c);
   cout << c << endl;

   // Increment pos1
   pos1 += 1;
   file.get( c );
   cout << c << endl;

   pos1 = file.tellg( ) - fpos<int>( 2);
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   // Increment pos1
   pos1 = pos1 + fpos<int>( 1 );
   file.get(c);
   cout << c << endl;

   pos1 -= fpos<int>( 2 );
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   file.close( );
}
```

## <a name="op_add"></a>  fpos::operator+

遞增檔案位置指標

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>參數

*_Off*<br/>
遞增檔案位置指標時所要依據的位移。

### <a name="return-value"></a>傳回值

檔案中的位置。

### <a name="remarks"></a>備註

此成員函式會傳回 **fpos(\*this) +=** `_Off`。

### <a name="example"></a>範例

如需 `operator+` 的使用方式範例，請參閱 [operator!=](#op_neq)。

## <a name="op_add_eq"></a>  fpos::operator+=

遞增檔案位置指標

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>參數

*_Off*<br/>
遞增檔案位置指標時所要依據的位移。

### <a name="return-value"></a>傳回值

檔案中的位置。

### <a name="remarks"></a>備註

成員函式會將 *_Off*至預存的位移的成員物件，然後傳回**\*這**。 針對檔案中的定位，通常僅當二進位資料流沒有依存於狀態的編碼時，結果才有效。

### <a name="example"></a>範例

如需 `operator+=` 的使用方式範例，請參閱 [operator!=](#op_neq)。

## <a name="operator-"></a>  fpos::operator-

減少檔案位置指標。

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>參數

*right*<br/>
檔案位置。

*_Off*<br/>
資料流位移。

### <a name="return-value"></a>傳回值

第一個成員函式會傳回 `(streamoff)*this - (streamoff) right`。 第二個成員函式會傳回 `fpos(*this) -= _Off`。

### <a name="example"></a>範例

如需 `operator-` 的使用方式範例，請參閱 [operator!=](#op_neq)。

## <a name="operator-_eq"></a>  fpos::operator-=

減少檔案位置指標。

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>參數

*_Off*<br/>
資料流位移。

### <a name="return-value"></a>傳回值

成員函式會傳回 `fpos(*this) -= _Off`。

### <a name="remarks"></a>備註

針對檔案中的定位，通常僅當二進位資料流沒有依存於狀態的編碼時，結果才有效。

### <a name="example"></a>範例

如需 `operator-=` 的使用方式範例，請參閱 [operator!=](#op_neq)。

## <a name="op_eq_eq"></a>  fpos::operator==

測試檔案位置指標是否相等。

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>參數

*right*<br/>
以比較目標為依據的檔案位置指標。

### <a name="return-value"></a>傳回值

如果檔案位置指標相等，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

成員函式會傳回 `(streamoff)*this == (streamoff)right`。

### <a name="example"></a>範例

如需 `operator+=` 的使用方式範例，請參閱 [operator!=](#op_neq)。

## <a name="op_streamoff"></a>  fpos::operator streamoff

將 `fpos` 類型的物件轉換成 `streamoff` 類型的物件。

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回預存位移物件以及任何其他位移 (儲存為 `fpos_t` 成員物件的一部分)。

### <a name="example"></a>範例

```cpp
// fpos_op_streampos.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   streamoff s;
   ofstream file( "rdbuf.txt");

   fpos<mbstate_t> f = file.tellp( );
   // Is equivalent to ..
   // streampos f = file.tellp( );
   s = f;
   cout << s << endl;
}
```

```Output
0
```

## <a name="seekpos"></a>  fpos::seekpos

此方法僅限 C++ 標準程式庫內部使用。 請勿從您的程式碼呼叫此方法。

```cpp
fpos_t seekpos() const;
```

## <a name="state"></a>  fpos::state

設定或傳回轉換狀態。

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>參數

*_State*<br/>
新的轉換狀態。

### <a name="return-value"></a>傳回值

轉換狀態。

### <a name="remarks"></a>備註

第一個成員函式傳回值儲存在`St`成員物件。 第二個成員函式存放區 *_State*在`St`成員物件。

### <a name="example"></a>範例

```cpp
// fpos_state.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main() {
   using namespace std;
   streamoff s;
   ifstream file( "fpos_state.txt" );

   fpos<mbstate_t> f = file.tellg( );
   char ch;
   while ( !file.eof( ) )
      file.get( ch );
   s = f;
   cout << f.state( ) << endl;
   f.state( 9 );
   cout << f.state( ) << endl;
}
```

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
