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
ms.openlocfilehash: 7dc244cde3d77ad99add1c35716779a55eac9263
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219309"
---
# <a name="basic_filebuf-class"></a>basic_filebuf 類別

描述資料流程緩衝區，其控制類型*Char_T*的元素傳輸，其字元特性是由類別*Tr*和儲存在外部檔案中的專案序列所決定。

## <a name="syntax"></a>語法

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_filebuf : public basic_streambuf<Char_T, Tr>
```

### <a name="parameters"></a>參數

*Char_T*\
檔案緩衝區的基本項目。

*Tr*\
檔案緩衝區的基本元素特性（通常是 `char_traits<Char_T>` ）。

## <a name="remarks"></a>備註

類別樣板描述的資料流程緩衝區，可控制類型*Char_T*的元素傳輸，其字元特性是由類別*Tr*和儲存在外部檔案中的元素序列所決定。

> [!NOTE]
> 類型的物件 `basic_filebuf` 會使用類型為__char \* __的內部緩衝區來建立，而不論 `char_type` 類型參數所指定的*Char_T*。 這表示在將 Unicode 字串（包含 **`wchar_t`** 字元）寫入內部緩衝區之前，會將它轉換成 ANSI 字串（包含 **`char`** 字元）。 若要在緩衝區中儲存 Unicode 字串，請建立類型的新緩衝區， **`wchar_t`** 並使用方法加以設定 [`basic_streambuf::pubsetbuf`](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` 。 若要查看示範此行為的範例，請參閱以下範例。

類別的物件會 `basic_filebuf<Char_T, Tr>` 儲存檔案指標，它 `FILE` 會指定物件，以控制與開啟的檔案相關聯的資料流程。 它也會將指標儲存至兩個檔案轉換 Facet，以供受保護成員函式 [overflow](#overflow) 和 [underflow](#underflow) 使用。 如需詳細資訊，請參閱 [`basic_filebuf::open`](#open)。

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

|建構函式|說明|
|-|-|
|[basic_filebuf](#basic_filebuf)|建構類型 `basic_filebuf` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
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
|[調換](#swap)|針對提供之 `basic_filebuf` 參數的內容，交換此 `basic_filebuf` 的內容。|
|[保持](#sync)|受保護的虛擬函式會嘗試與任何相關聯的外部資料流同步處理控制資料流。|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|用於從輸入資料流擷取目前項目之受保護的虛擬函式。|
|[underflow](#underflow)|用於從輸入資料流擷取目前項目之受保護的虛擬函式。|

## <a name="requirements"></a>需求

**標頭：**\<fstream>

**命名空間：** std

## <a name="basic_filebufbasic_filebuf"></a><a name="basic_filebuf"></a>basic_filebuf：： basic_filebuf

建構類型 `basic_filebuf` 的物件。

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>備註

第一個建構函式會在控制輸入緩衝區和輸出緩衝區的所有指標中儲存 Null 指標。 它也會將 Null 指標儲存在檔案指標中。

第二個函式會使用*right*的內容初始化物件，並將其視為右值參考。

## <a name="basic_filebufchar_type"></a><a name="char_type"></a>basic_filebuf：： char_type

將類型名稱與 `Char_T` 樣板參數產生關聯。

```cpp
typedef Char_T char_type;
```

## <a name="basic_filebufclose"></a><a name="close"></a>basic_filebuf：： close

關閉檔案。

```cpp
basic_filebuf<Char_T, Tr> *close();
```

### <a name="return-value"></a>傳回值

如果檔案指標為 Null 指標，則成員函式會傳回 Null 指標。

### <a name="remarks"></a>備註

`close` 會呼叫 `fclose(fp)`。 如果該函式傳回非零值，則函式會傳回 Null 指標。 否則，它會傳回 **`this`** 以表示已成功關閉檔案。

針對寬資料流程，如果在開啟資料流程之後，或自上次呼叫之後發生任何插入，則函式會 `streampos` 呼叫 [`overflow`](#overflow) 。 它也會插入還原初始轉換狀態所需的任何順序，方法是使用 [檔案轉換] facet `fac` `fac.unshift` 視需要呼叫。 類型的每個產生專案 `byte` **`char`** 都會寫入至檔案指標所指定的相關聯資料流程， `fp` 就像後續呼叫表單一樣 `fputc(byte, fp)` 。 如果對 `fac.unshift` 或任何寫入的呼叫失敗，函數不會成功。

### <a name="example"></a>範例

下列範例假設目前目錄中有兩個檔案： *basic_filebuf_close.txt* （內容為「測試」）並*iotest.txt* （內容為 "ssss"）。

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

## <a name="basic_filebufint_type"></a><a name="int_type"></a>basic_filebuf：： int_type

使此類型在 `basic_filebuf` 範圍內等同于範圍中相同名稱的類型 `Tr` 。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_filebufis_open"></a><a name="is_open"></a>basic_filebuf：： is_open

指出檔案是否為開啟。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果檔案指標不是 null。

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

## <a name="basic_filebufoff_type"></a><a name="off_type"></a>basic_filebuf：： off_type

使此類型在 `basic_filebuf` 範圍內等同于範圍中相同名稱的類型 `Tr` 。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_filebufopen"></a><a name="open"></a>basic_filebuf：： open

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

*名稱*\
要開啟之檔案的名稱。

*下*\
其中一個列舉 [`ios_base::openmode`](../standard-library/ios-base-class.md#openmode) 。

*保護*\
預設檔案開啟保護，相當於 _fsopen 中的*shflag*參數[，_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)。

### <a name="return-value"></a>傳回值

如果緩衝區已開啟，或如果檔案指標為 null 指標，則函式會傳回 null 指標。 否則，它會傳回 **`this`** 。

### <a name="remarks"></a>備註

此函式 `FILE *` 會使用來傳回， `basic_filebuf` 如同您已呼叫 [`fopen/wfopen`](../c-runtime-library/reference/fopen-wfopen.md) `(filename, strmode)` 。 `strmode`取決於 `mode & ~(` [`ate`](../standard-library/ios-base-class.md#openmode) `|` [`binary`](../standard-library/ios-base-class.md#openmode) `)` ：

- `ios_base::in`變成 `"r"` （開啟現有檔案以供讀取）。
- [ios_base：： out](../standard-library/ios-base-class.md#fmtflags)或 `ios_base::out | ios_base::trunc` 會變成 `"w"` （截斷現有檔案或建立以進行寫入）。
- `ios_base::out | app`會變成 `"a"` （開啟現有檔案以附加所有寫入）。
- `ios_base::in | ios_base::out`會變成 `"r+"` （開啟現有檔案以供讀取和寫入）。
- `ios_base::in | ios_base::out | ios_base::trunc`會變成 `"w+"` （截斷現有檔案或建立以進行讀取和寫入）。
- `ios_base::in | ios_base::out | ios_base::app`會變成 `"a+"` （開啟現有的檔案以供讀取及附加所有寫入）。

如果 `mode & ios_base::binary` 為非零值，函式會將附加 `b` 至 `strmode` 以開啟二進位資料流程，而不是文字資料流程。
如果 `mode & ios_base::ate` 為非零值，而且檔案已成功開啟，則資料流程中的目前位置會放在檔案結尾。 如果失敗，則表示檔案已關閉。

如果上述作業順利完成，則會決定檔案轉換 facet： `use_facet<codecvt<Char_T, char, traits_type::` [`state_type`](../standard-library/char-traits-struct.md#state_type) `> >(` [`getloc`](../standard-library/basic-streambuf-class.md#getloc) `)` ，供[下溢](#underflow)和[溢位](#overflow)使用。

如果無法成功開啟檔案，則會傳回 null。

### <a name="example"></a>範例

[`basic_filebuf::close`](#close)如需使用的範例，請參閱 `open` 。

## <a name="basic_filebufoperator"></a><a name="op_eq"></a>basic_filebuf：： operator =

指派此資料流緩衝區物件的內容。 這是一個移動指派，涉及不會留下複本的右值。

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>參數

*再*\
[basic_filebuf](../standard-library/basic-filebuf-class.md) 物件的右值參考。

### <a name="return-value"></a>傳回值

傳回 __* this__。

### <a name="remarks"></a>備註

成員運算子會使用*right*的內容來取代物件的內容，並將其視為右值參考。 如需詳細資訊，請參閱右值參考宣告子[：  &&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="basic_filebufoverflow"></a><a name="overflow"></a>basic_filebuf：：溢位

將新字元插入已滿的緩衝區時呼叫。

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>參數

*_Meta*\
要插入緩衝區或的字元 `traits_type::eof` 。

### <a name="return-value"></a>傳回值

如果函式不成功，則會傳回 `traits_type::eof` 。 否則，它會傳回 `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)` 。

### <a name="remarks"></a>備註

如果為 `_Meta != traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) ，則受保護的虛擬成員函式會嘗試將元素插入 `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)` 輸出緩衝區。 它可以透過下列各種方式來執行：

- 如果有寫入位置可供使用，它可以將項目儲存至寫入位置，並遞增輸出緩衝區的下一個指標。

- 為輸出緩衝區配置新的或額外的儲存空間，即可提供寫入位置。

- 它可以在輸出緩衝區中轉換任何暫止的輸出，接著 `ch` 使用 [檔案轉換] facet `fac` `fac.out` 視需要呼叫。 `ch` *Char*類型的每個產生專案都會寫入至檔案指標所指定的相關聯資料流程， `fp` 就像後續呼叫表單一樣 `fputc(ch, fp)` 。 如果任何轉換或寫入失敗，則函式會失敗。

## <a name="basic_filebufpbackfail"></a><a name="pbackfail"></a>basic_filebuf：:p backfail

嘗試將元素放回輸入資料流，然後將其設成目前元素 (透過下一個指標所指向)。

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>參數

*_Meta*\
要插入緩衝區的字元，或 `traits_type::eof`。

### <a name="return-value"></a>傳回值

如果函式不成功，則會傳回 `traits_type::eof` 。 否則，它會傳回 `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)` 。

### <a name="remarks"></a>備註

受保護虛擬成員函式會將元素放回輸入緩衝區，然後將其設成目前元素 (透過下一個指標所指向)。 如果 `_Meta == traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 是，要推回的元素實際上是目前專案之前在資料流程中的專案。 否則，就會取代該元素 `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)` 。 函式可透過下列各種方式來放回項目：

- 如果有 `putback` 位置可供使用，而且儲存在其中的專案比較等於 `ch` ，它可以遞減輸入緩衝區的下一個指標。

- 如果函式可以讓 `putback` 位置可供使用，它可以執行這項操作，將下一個指標設定為指向該位置，並儲存 `ch` 在該位置。

- 如果函式可以將專案推送回輸入資料流程，它可以執行這項操作，例如呼叫 `ungetc` 類型的元素 **`char`** 。

## <a name="basic_filebufpos_type"></a><a name="pos_type"></a>basic_filebuf：:p os_type

使此類型在 `basic_filebuf` 範圍內等同于範圍中相同名稱的類型 `Tr` 。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_filebufseekoff"></a><a name="seekoff"></a>basic_filebuf：： seekoff

嘗試改變受控制資料流的目前位置。

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Off*\
要搜尋的相對於 *_Way*的位置。

*_Way*\
位移作業的起點。 如需可能的值，請參閱 [seekdir](../standard-library/ios-base-class.md#seekdir)。

*_Which*\
指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

傳回新位置或無效的資料流位置。

### <a name="remarks"></a>備註

受保護的虛擬成員函式會嘗試改變受控制資料流程的目前位置。 針對類別的物件 [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>` ，資料流程位置可以由類型的物件表示 `fpos_t` ，其中儲存了剖析寬資料流程所需的位移和任何狀態資訊。 Offset 零指的是資料流程的第一個元素。 （類型的物件 [`pos_type`](../standard-library/basic-streambuf-class.md#pos_type) 至少會儲存一個 `fpos_t` 物件）。

針對開啟進行讀取和寫入的檔案，輸入和輸出資料流會一前一後地放置在一起。 若要在插入和解壓縮之間切換，您必須呼叫 [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) 或 [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) 。 `pubseekoff` `seekoff` 對於[文字資料流程](../c-runtime-library/text-and-binary-streams.md)、[二進位資料流程](../c-runtime-library/text-and-binary-streams.md)和[寬資料流程](../c-runtime-library/byte-and-wide-streams.md)的呼叫（並因此）有各種限制。

如果檔案指標 `fp` 為 null 指標，則函式會失敗。 否則，它會嘗試藉由呼叫來改變數據流位置 `fseek(fp, _Off, _Way)` 。 如果該函式成功，且產生的位置 `fposn` 可以藉由呼叫來判斷，則函式會 `fgetpos(fp, &fposn)` 成功。 如果函式成功，它會傳回包含之類型的值 `pos_type` `fposn` 。 否則會傳回無效的資料流位置。

## <a name="basic_filebufseekpos"></a><a name="seekpos"></a>basic_filebuf：： seekpos

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

如果檔案指標 `fp` 為 null 指標，則函式會失敗。 否則，它會嘗試藉由呼叫來改變數據流位置 `fsetpos(fp, &fposn)` ，其中 `fposn` 是 `fpos_t` 儲存在中的物件 `pos` 。 如果該函式成功，則函式會傳回 `pos`。 否則會傳回無效的資料流位置。 若要判斷資料流位置是否無效，請比較傳回值與 `pos_type(off_type(-1))`。

### <a name="remarks"></a>備註

受保護的虛擬成員函式會嘗試改變受控制資料流程的目前位置。 針對類別的物件 [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>` ，資料流程位置可以由類型的物件表示 `fpos_t` ，其中儲存了剖析寬資料流程所需的位移和任何狀態資訊。 Offset 零指的是資料流程的第一個元素。 (`pos_type` 類型的物件會儲存至少一個 `fpos_t` 物件)。

針對開啟進行讀取和寫入的檔案，輸入和輸出資料流會一前一後地放置在一起。 若要在插入和解壓縮之間切換，您必須呼叫 [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) 或 [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) 。 對 `pubseekoff` （和）的呼叫 `seekoff` 具有文字資料流程、二進位資料流程和寬資料流程的各種限制。

針對寬資料流，如果在開啟資料流之後或最後一次呼叫 `streampos` 之後進行過任何插入，則函式會呼叫 [overflow](#overflow)。 它也會插入還原初始轉換狀態所需的任何順序，方法是使用 [檔案轉換] facet `fac` `fac.unshift` 視需要呼叫。 類型的每個產生專案 `byte` **`char`** 都會寫入至檔案指標所指定的相關聯資料流程， `fp` 就像後續呼叫表單一樣 `fputc(byte, fp)` 。 如果對 `fac.unshift` 或任何寫入的呼叫失敗，函數不會成功。

## <a name="basic_filebufsetbuf"></a><a name="setbuf"></a>basic_filebuf：： setbuf

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

`setbuf`呼叫 `setvbuf( fp, (char*) _Buffer, _IOFBF, count * sizeof( Char_T))` 以提供 `count` 從 *_Buffer*開始的元素陣列，做為資料流程的緩衝區。 如果該函式傳回非零值，則函式會傳回 Null 指標。 否則，它會傳回 **`this`** 以表示成功。

## <a name="basic_filebufswap"></a><a name="swap"></a>basic_filebuf：： swap

將這個 `basic_filebuf` 的內容和提供的 `basic_filebuf` 內容交換。

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>參數

*再*\
另一個的左值參考 `basic_filebuf` 。

## <a name="basic_filebufsync"></a><a name="sync"></a>basic_filebuf：： sync

嘗試與任何相關聯外部資料流同步處理受控制資料流。

```cpp
virtual int sync();
```

### <a name="return-value"></a>傳回值

如果檔案指標 `fp` 為 null 指標，則會傳回零。 否則，只有在呼叫[溢](#overflow)位並 `fflush(fp)` 成功清除任何暫止的輸出到資料流程時，它才會傳回零。

## <a name="basic_filebuftraits_type"></a><a name="traits_type"></a>basic_filebuf：： traits_type

將類型名稱與 `Tr` 樣板參數產生關聯。

```cpp
typedef Tr traits_type;
```

## <a name="basic_filebufunderflow"></a><a name="underflow"></a>basic_filebuf：：下溢

從輸入資料流擷取目前元素。

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>傳回值

如果函式不成功，則會傳回 `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 。 否則，它會傳回 `ch` ，如「備註」一節所述進行轉換。

### <a name="remarks"></a>備註

受保護的虛擬成員函式會嘗試從輸入資料流程解壓縮目前的專案 `ch` ，並將專案傳回為 `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(ch)` 。 它可以透過下列各種方式來執行：

- 如果有讀取位置可供使用，它會將專案當做 `ch` 儲存在讀取位置中的元素，並前進到輸入緩衝區的下一個指標。

- 它可以讀取類型的一或多個專案 **`char`** ，如同後續呼叫表單一樣， `fgetc(fp)` 然後 `ch` `Char_T` 使用 [檔案轉換] facet `fac` `fac.in` 視需要呼叫，將它們轉換成類型的元素。 如果任何讀取或轉換失敗，則函式會失敗。

## <a name="see-also"></a>另請參閱

[\<fstream>](../standard-library/fstream.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
