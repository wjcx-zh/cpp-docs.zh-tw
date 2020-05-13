---
title: basic_filebuf 類別
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
ms.openlocfilehash: 35bed08f2495c971df7f79f62e32b3ff68dfb3d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376887"
---
# <a name="basic_filebuf-class"></a>basic_filebuf 類別

描述控制*類型Char_T*元素的流緩衝區,該元素的字元特徵由類*Tr*決定,並且從存儲在外部檔中的元素序列進行。

## <a name="syntax"></a>語法

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_filebuf : public basic_streambuf<Char_T, Tr>
```

### <a name="parameters"></a>參數

*Char_T*\
檔案緩衝區的基本項目。

*Tr*\
檔緩衝區的基本元素(通常`char_traits<Char_T>`)的特性。

## <a name="remarks"></a>備註

類範本描述一個流緩衝區,它控制類型*Char_T*的元素的傳輸,其字元特徵由類*Tr*決定,並且從存儲在外部檔中的元素序列進行。

> [!NOTE]
> 類型`basic_filebuf`的物件使用__字元\*__ 的內部緩衝區建立`char_type`, 而不考慮類型參數*Char_T*指定的物件。 這意味著 Unicode 字串(包含**wchar_t**字元)在寫入內部緩衝區之前將轉換為 ANSI 字串(包含**字元**)。 要將 Unicode 字串儲存在緩衝區中,請建立**類型wchar_t**的新緩衝區,[`basic_streambuf::pubsetbuf`](../standard-library/basic-streambuf-class.md#pubsetbuf)`()`並使用方法設定它。 若要查看示範此行為的範例，請參閱以下範例。

類`basic_filebuf<Char_T, Tr>`的物件存儲檔指標,該指標指定控制與打開文件`FILE`關聯的流的物件。 它也會將指標儲存至兩個檔案轉換 Facet，以供受保護成員函式 [overflow](#overflow) 和 [underflow](#underflow) 使用。 有關詳細資訊,請參閱[`basic_filebuf::open`](#open)。

## <a name="example"></a>範例

下列範例示範如何強制類型 `basic_filebuf<wchar_t>` 的物件，以藉由呼叫 `pubsetbuf()` 方法，在其內部緩衝區中儲存 Unicode 字元。

```cpp
// unicode_basic_filebuf.cpp
// compile with: /EHsc

#include <iostream>
#include <string>
#include <fstream>
#include <iomanip>
#include <memory.h>
#include <string.h>

#define IBUFSIZE 16

using namespace std;

void hexdump(const string& filename);

int main()
{
    wchar_t* wszHello = L"Hello World";
    wchar_t wBuffer[128];

    basic_filebuf<wchar_t> wOutFile;

    // Open a file, wcHello.txt, then write to it, then dump the
    // file's contents in hex
    wOutFile.open("wcHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wcHello.txt\n";
        return -1;
    }
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";
    hexdump(string("wcHello.txt"));

    // Open a file, wwHello.txt, then set the internal buffer of
    // the basic_filebuf object to be of type wchar_t, then write
    // to the file and dump the file's contents in hex
    wOutFile.open("wwHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wwHello.txt\n";
        return -1;
    }
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";
    hexdump(string("wwHello.txt"));

    return 0;
}

// dump contents of filename to stdout in hex
void hexdump(const string& filename)
{
    fstream ifile(filename.c_str(),
        ios_base::in | ios_base::binary);
    char *ibuff = new char[IBUFSIZE];
    char *obuff = new char[(IBUFSIZE*2)+1];
    int i;

    if(!ifile.is_open())
    {
        cout << "Cannot Open " << filename.c_str()
             << " for reading\n";
        return;
    }
    if(!ibuff || !obuff)
    {
        cout << "Cannot Allocate buffers\n";
        ifile.close();
        return;
    }

    while(!ifile.eof())
    {
        memset(obuff,0,(IBUFSIZE*2)+1);
        memset(ibuff,0,IBUFSIZE);
        ifile.read(ibuff,IBUFSIZE);

        // corner case where file is exactly a multiple of
        // 16 bytes in length
        if(ibuff[0] == 0 && ifile.eof())
            break;

        for(i = 0; i < IBUFSIZE; i++)
        {
            if(ibuff[i] >= ' ')
                obuff[i] = ibuff[i];
            else
                obuff[i] = '.';

            cout << setfill('0') << setw(2) << hex
                 << (int)ibuff[i] << ' ';
        }
        cout << "  " << obuff << endl;
    }
    ifile.close();
}
```

```Output
Hex Dump of wcHello.txt - note that output is ANSI chars:
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....

Hex Dump of wwHello.txt - note that output is wchar_t chars:
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........
```

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_filebuf](#basic_filebuf)|建構類型 `basic_filebuf` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|將類型名稱與 `Char_T` 樣板參數產生關聯。|
|[int_type](#int_type)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|
|[off_type](#off_type)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|
|[pos_type](#pos_type)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|
|[traits_type](#traits_type)|將類型名稱與 `Tr` 樣板參數產生關聯。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[關閉](#close)|關閉檔案。|
|[is_open](#is_open)|指出檔案是否為開啟。|
|[open](#open)|開啟檔案。|
|[溢出](#overflow)|受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。|
|[pbackfail](#pbackfail)|受保護的虛擬成員函式會嘗試將項目放回輸入資料流，然後將其設成目前的項目 (由下一個指標指向)。|
|[seekoff](#seekoff)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|
|[seekpos](#seekpos)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|
|[setbuf](#setbuf)|受保護的虛擬成員函式會執行每個衍生資料流緩衝區的特定作業。|
|[交換](#swap)|針對提供之 `basic_filebuf` 參數的內容，交換此 `basic_filebuf` 的內容。|
|[sync](#sync)|受保護的虛擬函式會嘗試與任何相關聯的外部資料流同步處理控制資料流。|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|用於從輸入資料流擷取目前項目之受保護的虛擬函式。|
|[underflow](#underflow)|用於從輸入資料流擷取目前項目之受保護的虛擬函式。|

## <a name="requirements"></a>需求

**標頭：** \<fstream>

**命名空間：** std

## <a name="basic_filebufbasic_filebuf"></a><a name="basic_filebuf"></a>basic_filebuf:basic_filebuf

建構類型 `basic_filebuf` 的物件。

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>備註

第一個建構函式會在控制輸入緩衝區和輸出緩衝區的所有指標中儲存 Null 指標。 它也會將 Null 指標儲存在檔案指標中。

第二個構造函數用*右側*的內容初始化物件,作為rvalue引用處理。

## <a name="basic_filebufchar_type"></a><a name="char_type"></a>basic_filebuf:char_type

將類型名稱與 `Char_T` 樣板參數產生關聯。

```cpp
typedef Char_T char_type;
```

## <a name="basic_filebufclose"></a><a name="close"></a>basic_filebuf:關閉

關閉檔案。

```cpp
basic_filebuf<Char_T, Tr> *close();
```

### <a name="return-value"></a>傳回值

如果檔案指標為 Null 指標，則成員函式會傳回 Null 指標。

### <a name="remarks"></a>備註

`close` 會呼叫 `fclose(fp)`。 如果該函式傳回非零值，則函式會傳回 Null 指標。 否則，它會傳回 **this**，表示已成功關閉檔案。

對於寬流,如果自打開流或自上次調用 後發生任何`streampos`插入 ,則函數[`overflow`](#overflow)呼叫 。 它還通過根據需要使用檔轉換面`fac`來呼`fac.unshift`叫,插入還原初始轉換狀態所需的任何序列。 **類型 char**的每個生成`fp``fputc(byte, fp)``byte`的元素 都寫入檔指標指定的關聯流,就像窗體的連續調用一樣。 如果對的`fac.unshift`調用或任何寫入失敗,則函數不會成功。

### <a name="example"></a>範例

以下範例假定目前的目錄中有兩個檔案 *:basic_filebuf_close.txt(* 內容為"測試")和*iotest.txt(* 內容為"ssss")。

```cpp
// basic_filebuf_close.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main() {
   using namespace std;
   ifstream file;
   basic_ifstream <wchar_t> wfile;
   char c;
   // Open and close with a basic_filebuf
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );
   file >> c;
   cout << c << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "iotest.txt" );
   file >> c;
   cout << c << endl;
   file.close( );

   // open a file with a wide character name
   wfile.open( L"iotest.txt" );

   // Open and close a nonexistent with a basic_filebuf
   file.rdbuf()->open( "ziotest.txt", ios::in );
   cout << file.fail() << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "ziotest.txt" );
   cout << file.fail() << endl;
   file.close( );
}
```

```Output
t
s
0
1
```

## <a name="basic_filebufint_type"></a><a name="int_type"></a>basic_filebuf::int_type

使此類型在`basic_filebuf`作用域中等效於`Tr`作用域中的相同名稱的類型。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_filebufis_open"></a><a name="is_open"></a>basic_filebuf:is_open

指出檔案是否為開啟。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>傳回值

如果檔案指標不為空,**則為 true。**

### <a name="example"></a>範例

```cpp
// basic_filebuf_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;

   file.open( "basic_filebuf_is_open.cpp" );
   cout << file.rdbuf( )->is_open( ) << endl;
}
```

```Output
false
true
```

## <a name="basic_filebufoff_type"></a><a name="off_type"></a>basic_filebuf:off_type

使此類型在`basic_filebuf`作用域中等效於`Tr`作用域中的相同名稱的類型。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_filebufopen"></a><a name="open"></a>basic_filebuf::打開

開啟檔案。

```cpp
basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode);
```

### <a name="parameters"></a>參數

*檔案名稱*\
要開啟之檔案的名稱。

*模式*\
中的[`ios_base::openmode`](../standard-library/ios-base-class.md#openmode)枚舉之一。

*保護*\
預設檔案開啟保護,等效於 _fsopen 中的*shflag*參數[,_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)。

### <a name="return-value"></a>傳回值

如果緩衝區已打開,或者如果檔指標是空指標,則函數返回一個空指標。 否則，它會傳回 **this**。

### <a name="remarks"></a>備註

成員函數通過調用[`fopen`](../c-runtime-library/reference/fopen-wfopen.md)`(filename, strmode)`打開具有名稱*檔名*的檔。 `strmode``mode & ~(`[`binary`](../standard-library/ios-base-class.md#openmode)確定`)`:[`ate`](../standard-library/ios-base-class.md#openmode)`|`

- `ios_base::in`變為`"r"`(打開現有文件進行讀取)。

- [ios_base::退出](../standard-library/ios-base-class.md#fmtflags)`ios_base::out | ios_base::trunc`或`"w"`變為 (截截現有檔或創建以進行寫入)。

- `ios_base::out | app`變為`"a"`(打開用於追加所有寫入的現有檔案)。

- `ios_base::in | ios_base::out`成為`"r+"`(打開用於讀取和寫入的現有檔)。

- `ios_base::in | ios_base::out | ios_base::trunc`成為`"w+"`(截截現有檔或創建用於讀取和寫入)。

- `ios_base::in | ios_base::out | ios_base::app`成為`"a+"`(打開用於讀取和追加所有寫入的現有檔)。

如果`mode & ios_base::binary`為非零,則函數將追加`b``strmode`以 打開二進位流而不是文本流。 然後,它將返回的值存儲在檔`fopen`指標`fp`中。 如果`mode & ios_base::ate`為非零,並且檔指標不是空指標,則函數將調用`fseek(fp, 0, SEEK_END)`以將流定位到檔末尾。 如果定位操作失敗,函數將調用[`close`](#close)`(fp)`並在檔指標中存儲空指標。

如果檔指標不是空指標,則函數確定檔`use_facet<codecvt<Char_T, char, traits_type::`[`state_type`](../standard-library/char-traits-struct.md#state_type)`> >(`[`getloc`](../standard-library/basic-streambuf-class.md#getloc)`)`轉換面: ,供[下溢](#underflow)和[溢出](#overflow)使用。

如果檔案指標為 Null 指標，則函式會傳回 Null 指標。 否則，它會傳回 **this**。

### <a name="example"></a>範例

有關[`basic_filebuf::close`](#close)`open`使用的示例,請參閱。

## <a name="basic_filebufoperator"></a><a name="op_eq"></a>basic_filebuf::操作員*

指派此資料流緩衝區物件的內容。 這是一個移動分配,涉及不會留下副本的 rvalue。

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>參數

*對*\
[basic_filebuf](../standard-library/basic-filebuf-class.md) 物件的右值參考。

### <a name="return-value"></a>傳回值

返回 ___this__。

### <a name="remarks"></a>備註

成員運算符使用*權利*的內容替換物件的內容,該內容被視為rvalue引用。 有關詳細資訊,請參閱[Rvalue 引用聲明符: &&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="basic_filebufoverflow"></a><a name="overflow"></a>basic_filebuf:溢出

將新字元插入已滿的緩衝區時呼叫。

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>參數

*_Meta*\
要插入到緩衝區或`traits_type::eof`的字元。

### <a name="return-value"></a>傳回值

如果函數無法成功,它將傳`traits_type::eof`回 。 否則,它將返回`traits_type::`[`not_eof`](../standard-library/char-traits-struct.md#not_eof)`(_Meta)`。

### <a name="remarks"></a>備註

如果`_Meta != traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof),受保護的虛擬成員函數將嘗試將`ch = traits_type::`[`to_char_type`](../standard-library/char-traits-struct.md#to_char_type)`(_Meta)`元素 插入到輸出緩衝區中。 它可以透過下列各種方式來執行：

- 如果有寫入位置可供使用，它可以將項目儲存至寫入位置，並遞增輸出緩衝區的下一個指標。

- 為輸出緩衝區配置新的或額外的儲存空間，即可提供寫入位置。

- 它可以轉換輸出緩衝區中的任何掛起的輸出,然後轉換`ch`,使用檔轉換`fac`面 根據需要調`fac.out`用。 *類型 char*的每個生成`fp``fputc(ch, fp)``ch`的元素 都寫入檔指標指定的關聯流,就像窗體的連續調用一樣。 如果任何轉換或寫入失敗，則函式會失敗。

## <a name="basic_filebufpbackfail"></a><a name="pbackfail"></a>basic_filebuf::p回擊失敗

嘗試將元素放回輸入資料流，然後將其設成目前元素 (透過下一個指標所指向)。

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>參數

*_Meta*\
要插入緩衝區的字元，或 `traits_type::eof`。

### <a name="return-value"></a>傳回值

如果函數無法成功,它將傳`traits_type::eof`回 。 否則,它將返回`traits_type::`[`not_eof`](../standard-library/char-traits-struct.md#not_eof)`(_Meta)`。

### <a name="remarks"></a>備註

受保護虛擬成員函式會將元素放回輸入緩衝區，然後將其設成目前元素 (透過下一個指標所指向)。 如果`_Meta == traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof),要回滾的元素實際上是當前元素之前流中的元素。 否則,此元素會取代為`ch = traits_type::`[`to_char_type`](../standard-library/char-traits-struct.md#to_char_type)`(_Meta)`。 函式可透過下列各種方式來放回項目：

- 如果位置`putback`可用,並且存儲在那裡的元素比較等`ch`於 ,它可以遞減輸入緩衝區的下一個指標。

- 如果函數可以使位置`putback`可用,則可以這樣做,將下一個指標設置為指向該位置,並存儲在`ch`該位置。

- 如果函數可以將元素推回輸入流,則可以這樣做,例如調用`ungetc`類型**char**的元素。

## <a name="basic_filebufpos_type"></a><a name="pos_type"></a>basic_filebuf::pos_類型

使此類型在`basic_filebuf`作用域中等效於`Tr`作用域中的相同名稱的類型。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_filebufseekoff"></a><a name="seekoff"></a>basic_filebuf:尋求

嘗試改變受控制資料流的目前位置。

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Off*\
相對於 *_Way*尋求的位置。

*_Way*\
位移作業的起點。 如需可能的值，請參閱 [seekdir](../standard-library/ios-base-class.md#seekdir)。

*_Which*\
指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

傳回新位置或無效的資料流位置。

### <a name="remarks"></a>備註

受保護的虛擬成員函數嘗試更改受控流的當前位置。 對於類[`basic_filebuf`](../standard-library/basic-filebuf-class.md)`<Char_T, Tr>`的物件,流位置可以由類型`fpos_t`物件表示,該物件存儲偏移量以及解析寬流所需的任何狀態資訊。 偏移零是指流的第一個元素。 (類型[`pos_type`](../standard-library/basic-streambuf-class.md#pos_type)的物件至少存儲一`fpos_t`個 物件。

針對開啟進行讀取和寫入的檔案，輸入和輸出資料流會一前一後地放置在一起。 若要在插入與擷取之間切換,必須呼叫[`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff)[`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)或 。 `pubseekoff`對(因此)的`seekoff`調用對[文本流](../c-runtime-library/text-and-binary-streams.md)、[二進位流](../c-runtime-library/text-and-binary-streams.md)和[寬流](../c-runtime-library/byte-and-wide-streams.md)有各種限制。

如果檔指標`fp`為空指標,則函數將失敗。 否則,它嘗試通過調用`fseek(fp, _Off, _Way)`來更改流位置。 如果該函數成功,並且生成的位置`fposn`可以通過`fgetpos(fp, &fposn)`調用 確定,則函數將成功。 如果函數成功,它將返回包含`pos_type``fposn`的類型值。 否則會傳回無效的資料流位置。

## <a name="basic_filebufseekpos"></a><a name="seekpos"></a>basic_filebuf:seekpos

嘗試改變受控制資料流的目前位置。

```cpp
virtual pos_type seekpos(
    pos_type _Sp,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Sp*\
要搜尋的位置。

*_Which*\
指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

如果檔指標`fp`為空指標,則函數將失敗。 否則,它`fsetpos(fp, &fposn)`嘗試通過調用 來更改流位置`fposn``fpos_t`, 物件`pos`存儲在 中的位置。 如果該函式成功，則函式會傳回 `pos`。 否則會傳回無效的資料流位置。 若要判斷資料流位置是否無效，請比較傳回值與 `pos_type(off_type(-1))`。

### <a name="remarks"></a>備註

受保護的虛擬成員函數嘗試更改受控流的當前位置。 對於類[`basic_filebuf`](../standard-library/basic-filebuf-class.md)`<Char_T, Tr>`的物件,流位置可以由類型`fpos_t`物件表示,該物件存儲偏移量以及解析寬流所需的任何狀態資訊。 偏移零是指流的第一個元素。 (`pos_type` 類型的物件會儲存至少一個 `fpos_t` 物件)。

針對開啟進行讀取和寫入的檔案，輸入和輸出資料流會一前一後地放置在一起。 若要在插入與擷取之間切換,必須呼叫[`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff)[`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)或 。 對`pubseekoff`(`seekoff`和 ) 的調用對文本流、二進位流和寬流具有各種限制。

針對寬資料流，如果在開啟資料流之後或最後一次呼叫 `streampos` 之後進行過任何插入，則函式會呼叫 [overflow](#overflow)。 它還通過根據需要使用檔轉換面`fac`來呼`fac.unshift`叫,插入還原初始轉換狀態所需的任何序列。 **類型 char**的每個生成`fp``fputc(byte, fp)``byte`的元素 都寫入檔指標指定的關聯流,就像窗體的連續調用一樣。 如果對的`fac.unshift`調用或任何寫入失敗,則函數不會成功。

## <a name="basic_filebufsetbuf"></a><a name="setbuf"></a>basic_filebuf:塞特布夫

執行每個衍生資料流緩衝區的特定作業。

```cpp
virtual basic_streambuf<Char_T, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>參數

*_Buffer*\
緩衝區的指標。

*計數*\
緩衝區的大小。

### <a name="return-value"></a>傳回值

如果檔案指標 `fp` 為 Null 指標，則受保護成員函式會傳回零。

### <a name="remarks"></a>備註

`setbuf`提供`setvbuf( fp, (char*) _Buffer, _IOFBF, count * sizeof( Char_T))`從`count`*_Buffer*開始的元素陣列作為流的緩衝區。 如果該函式傳回非零值，則函式會傳回 Null 指標。 否則，它會傳回 **this** 以發出成功訊號。

## <a name="basic_filebufswap"></a><a name="swap"></a>basic_filebuf::交換

將這個 `basic_filebuf` 的內容和提供的 `basic_filebuf` 內容交換。

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>參數

*對*\
對另一個`basic_filebuf`的lvalue引用。

## <a name="basic_filebufsync"></a><a name="sync"></a>basic_filebuf:同步

嘗試與任何相關聯外部資料流同步處理受控制資料流。

```cpp
virtual int sync();
```

### <a name="return-value"></a>傳回值

如果檔指標`fp`為空指標,則返回零。 否則,僅當[對溢出的](#overflow)調用並`fflush(fp)`成功刷新到流的任何掛起的輸出時,它才會返回零。

## <a name="basic_filebuftraits_type"></a><a name="traits_type"></a>basic_filebuf::traits_type

將類型名稱與 `Tr` 樣板參數產生關聯。

```cpp
typedef Tr traits_type;
```

## <a name="basic_filebufunderflow"></a><a name="underflow"></a>basic _ filebuf :

從輸入資料流擷取目前元素。

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>傳回值

如果函數無法成功,它將傳`traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof)回 。 否則,它將返回`ch`,轉換,如註釋部分所述。

### <a name="remarks"></a>備註

受保護的虛擬成員函數試著從輸入串流擷取`ch`目前元素 ,並將該`traits_type::`[`to_int_type`](../standard-library/char-traits-struct.md#to_int_type)`(ch)`元素傳回為 。 它可以透過下列各種方式來執行：

- 如果讀取位置可用,則它用作`ch`存儲在讀取位置的元素,並推進輸入緩衝區的下一個指標。

- 它可以讀取**字元**類型的一個或多個元素,`fgetc(fp)`就像通過 窗體的連續調用一樣,並通過使用`ch``Char_T``fac`檔案轉換面`fac.in`根據需要調用 它們轉換為類型元素。 如果任何讀取或轉換失敗，則函式會失敗。

## <a name="see-also"></a>另請參閱

[\<>](../standard-library/fstream.md)\
[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
