---
title: strstreambuf 類別
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
helpviewer_keywords:
- std::strstreambuf [C++], freeze
- std::strstreambuf [C++], overflow
- std::strstreambuf [C++], pbackfail
- std::strstreambuf [C++], pcount
- std::strstreambuf [C++], seekoff
- std::strstreambuf [C++], seekpos
- std::strstreambuf [C++], str
- std::strstreambuf [C++], underflow
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
ms.openlocfilehash: 5a9fa47ab19a5935bf0c7c36dea37b3cfe6180ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512381"
---
# <a name="strstreambuf-class"></a>strstreambuf 類別

描述控制項的項目中儲存之元素的順序來回傳輸的資料流緩衝區**char**陣列物件。

## <a name="syntax"></a>語法

```cpp
class strstreambuf : public streambuf
```

## <a name="remarks"></a>備註

根據物件的建構方式，它可以視需要配置、擴充和釋出，以回應序列中的變更。

`strstreambuf` 類別的物件會將模式的幾個位元資訊儲存為其 `strstreambuf` 模式。 這些位元表示受控制的序列是否：

- 已配置，且最後需要釋放。

- 可修改。

- 可透過重新配置儲存體來擴充。

- 已凍結，因此需要解除凍結再終結物件，或由物件以外的代理程式釋放 (如果已配置)。

不論這些個別模式位元的狀態為何，您都無法修改或擴充凍結的受控制序列。

這個物件也會儲存控制 `strstreambuf` 配置的兩個函式指標。 如果這些指標是 null 指標，則該物件會規劃自己的方法來配置及釋放受控制序列的儲存體。

> [!NOTE]
> 這個類別已被取代。 請考慮改用 [stringbuf](../standard-library/sstream-typedefs.md#stringbuf) 或 [wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[strstreambuf](#strstreambuf)|建構類型 `strstreambuf` 的物件。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[freeze](#freeze)|導致資料流緩衝區無法在資料流緩衝區作業中使用。|
|[overflow](#overflow)|受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。|
|[pbackfail](#pbackfail)|嘗試將項目放回輸入資料流，然後將其設為目前項目 (由下一個指標指向) 的受保護虛擬成員函式。|
|[pcount](#pcount)|傳回寫入至受控制序列的元素計數。|
|[seekoff](#seekoff)|受保護虛擬成員函式嘗試改變受控制資料流目前的位置。|
|[seekpos](#seekpos)|受保護虛擬成員函式嘗試改變受控制資料流目前的位置。|
|[str](#str)|呼叫 [freeze](#freeze)，然後將指標傳回受控制序列的開頭。|
|[underflow](#underflow)|要從輸入資料流擷取目前項目的受保護虛擬函式。|

## <a name="requirements"></a>需求

**標頭：**\<strstream>

**命名空間：** std

## <a name="freeze"></a>  strstreambuf::freeze

導致資料流緩衝區無法在資料流緩衝區作業中使用。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>參數

*_Freezeit*<br/>
A **bool**指出您是否要凍結的資料流。

### <a name="remarks"></a>備註

如果 *_Freezeit*為 true，此函式會改變儲存`strstreambuf`先凍結受控制的序列的模式。 否則，不會凍結受控制的序列。

[str](#str) 表示 `freeze`。

> [!NOTE]
> 凍結的緩衝區將不會在 `strstreambuf` 解構期間釋放。 您必須先取消凍結緩衝區，之後才能釋放它以避免記憶體流失。

### <a name="example"></a>範例

```cpp
// strstreambuf_freeze.cpp
// compile with: /EHsc

#include <iostream>
#include <strstream>

using namespace std;

void report(strstream &x)
{
    if (!x.good())
        cout << "stream bad" << endl;
    else
        cout << "stream good" << endl;
}

int main()
{
    strstream x;

    x << "test1";
    cout << "before freeze: ";
    report(x);

    // Calling str freezes stream.
    cout.write(x.rdbuf()->str(), 5) << endl;
    cout << "after freeze: ";
    report(x);

    // Stream is bad now, wrote on frozen stream
    x << "test1.5";
    cout << "after write to frozen stream: ";
    report(x);

    // Unfreeze stream, but it is still bad
    x.rdbuf()->freeze(false);
    cout << "after unfreezing stream: ";
    report(x);

    // Clear stream
    x.clear();
    cout << "after clearing stream: ";
    report(x);

    x << "test3";
    cout.write(x.rdbuf()->str(), 10) << endl;

    // Clean up.  Failure to unfreeze stream will cause a
    // memory leak.
    x.rdbuf()->freeze(false);
}
```

```Output
before freeze: stream good
test1
after freeze: stream good
after write to frozen stream: stream bad
after unfreezing stream: stream bad
after clearing stream: stream good
test1test3
```

## <a name="overflow"></a>  strstreambuf::overflow

受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。

```cpp
virtual int overflow(int _Meta = EOF);
```

### <a name="parameters"></a>參數

*_Meta*<br/>
要插入緩衝區的字元，或 `EOF`。

### <a name="return-value"></a>傳回值

如果函式不成功，則會傳回 `EOF`。 否則，如果 _ *Meta* == `EOF`，就會傳回 `EOF` 以外的某個值。 否則，會傳回 \_ *Meta*。

### <a name="remarks"></a>備註

如果 _ *Meta* != `EOF`，受保護的虛擬成員函式就會嘗試將項目 ( `char`)\_ *Meta* 插入輸出緩衝區。 它可以透過下列各種方式來執行：

- 如果有寫入位置可供使用，它可以將項目儲存至寫入位置，並遞增輸出緩衝區的下一個指標。

- 如果儲存的 strstreambuf 模式表示受控制的序列是可修改、可擴充且未凍結的，則函式可為輸出緩衝區配置新的指標，藉以使寫入位置可供使用。 以這種方式擴充輸出緩衝區時，也會擴充任何相關的輸入緩衝區。

## <a name="pbackfail"></a>  strstreambuf::pbackfail

受保護的虛擬成員函式，會嘗試將項目放回輸入資料流，然後將其設成目前的項目 (由下一個指標指向)。

```cpp
virtual int pbackfail(int _Meta = EOF);
```

### <a name="parameters"></a>參數

*_Meta*<br/>
要插入緩衝區的字元，或 `EOF`。

### <a name="return-value"></a>傳回值

如果函式不成功，則會傳回 `EOF`。 否則，如果 _ *Meta* == `EOF`，就會傳回 `EOF` 以外的某個值。 否則，會傳回 \_ *Meta*。

### <a name="remarks"></a>備註

受保護的虛擬成員函式會嘗試將元素放回輸入緩衝區，然後將其設成目前的元素 (由下一個指標指向)。

如果 _ *Meta* == `EOF`，要推回的項目實際上是已經在資料流中目前項目之前的項目。 否則，**ch** = ( `char`)\_ *Meta* 會取代該項目。 函式可透過下列各種方式來放回項目：

- 如果有 putback 位置可供使用，而且儲存在該處的項目比較為相等`ch`，則可遞減輸入緩衝區的下一個指標。

- 如果有 putback 位置可供使用，而且 stringbuf 模式表示受控制的序列是可修改，如果函式可以儲存`ch`至 putback 位置，並遞減輸入緩衝區的下一個指標。

## <a name="pcount"></a>  strstreambuf::pcount

傳回寫入至受控制序列的元素計數。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>傳回值

寫入受控制序列的項目計數。

### <a name="remarks"></a>備註

具體來說，如果 [pptr](../standard-library/basic-streambuf-class.md#pptr) 是 null 指標，此函式會傳回零。 否則，它會傳回`pptr`  -  [pbase](../standard-library/basic-streambuf-class.md#pbase)。

### <a name="example"></a>範例

```cpp
// strstreambuf_pcount.cpp
// compile with: /EHsc
#include <iostream>
#include <strstream>
using namespace std;

int main( )
{
   strstream x;
   x << "test1";
   cout << x.rdbuf( )->pcount( ) << endl;
   x << "test2";
   cout << x.rdbuf( )->pcount( ) << endl;
}
```

## <a name="seekoff"></a>  strstreambuf::seekoff

受保護虛擬成員函式嘗試改變受控制資料流目前的位置。

```cpp
virtual streampos seekoff(streamoff _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Off*<br/>
要搜尋的相對位置 *_Way*。

*_Way*<br/>
位移作業的起點。 如需可能的值，請參閱 [seekdir](../standard-library/ios-base-class.md#seekdir)。

*_Which*<br/>
指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

如果函式成功改變一個或兩個資料流位置，則會傳回結果資料流位置。 否則會失敗，並傳回無效的資料流位置。

### <a name="remarks"></a>備註

受保護的虛擬成員函式會致力於改變受控制資料流的目前位置。 針對 strstreambuf 類別的物件，資料流位置完全是由資料流位移所組成。 位移零會指定受控制序列的第一個項目。

新位置的判斷方式如下：

- 如果 `_Way` == `ios_base::beg`，新位置是資料流開頭加上 _ *Off*。

- 如果 `_Way` == `ios_base::cur`，新位置是目前的資料流位置加上 _ *Off*。

- 如果 `_Way` == `ios_base::end`，新位置是資料流結尾加上 _ *Off*。

如果 `_Which` & **ios_base::in** 為非零值，且輸入緩衝區存在，函式就會改變輸入緩衝區中下一個要讀取的位置。 如果 `_Which` & **ios_base::out** 也是非零值、`_Way` != **ios_base::cur**，且輸出緩衝區存在，則函式也會設定下一個要寫入的位置，以符合下一個要讀取的位置。

否則，如果 `_Which` & `ios_base::out` 為非零值，且輸入緩衝區存在，函式就會改變輸出緩衝區中下一個要寫入的位置。 否則，置放作業會失敗。 若要讓置放作業能夠成功，產生的資料流位置必須位於受控制的序列內。

## <a name="seekpos"></a>  strstreambuf::seekpos

受保護虛擬成員函式嘗試改變受控制資料流目前的位置。

```cpp
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Sp*<br/>
要搜尋的位置。

*_Which*<br/>
指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

如果函式成功改變一個或兩個資料流位置，則會傳回結果資料流位置。 否則會失敗，並傳回無效的資料流位置。 若要判斷資料流位置是否無效，請比較傳回值與 `pos_type(off_type(-1))`。

### <a name="remarks"></a>備註

受保護的虛擬成員函式會致力於改變受控制資料流的目前位置。 針對 strstreambuf 類別的物件，資料流位置完全是由資料流位移所組成。 位移零會指定受控制序列的第一個項目。 新位置是由 _ *Sp* 所來判斷。

如果 `_Which` & **ios_base::in** 為非零值，且輸入緩衝區存在，函式就會改變輸入緩衝區中下一個要讀取的位置。 如果 `_Which` & `ios_base::out` 為非零值，且輸出緩衝區存在，則函式也會設定下一個要寫入的位置，以符合下一個要讀取的位置。 否則，如果 `_Which` & `ios_base::out` 為非零值，且輸入緩衝區存在，函式就會改變輸出緩衝區中下一個要寫入的位置。 否則，置放作業會失敗。 若要讓置放作業能夠成功，產生的資料流位置必須位於受控制的序列內。

## <a name="str"></a>  strstreambuf::str

呼叫 [freeze](#freeze)，然後傳回指向受控制序列開頭的指標。

```cpp
char *str();
```

### <a name="return-value"></a>傳回值

指向受控制序列開頭的指標。

### <a name="remarks"></a>備註

除非您明確地插入一個，否則不會有終止的 null 項目存在。

### <a name="example"></a>範例

如需使用 **str** 的範例，請參閱 [strstreambuf::freeze](#freeze)。

## <a name="strstreambuf"></a>  strstreambuf::strstreambuf

建構類型 `strstreambuf` 的物件。

```cpp
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* _Allocfunc)(size_t),
    void (* _Freefunc)(void*));

strstreambuf(char* _Getptr,
    streamsize count,
    char* _Putptr = 0);

strstreambuf(signed char* _Getptr,
    streamsize count,
    signed char* _Putptr = 0);

strstreambuf(unsigned char* _Getptr,
    streamsize count,
    unsigned char* _Putptr = 0);

strstreambuf(const char* _Getptr,
    streamsize count);

strstreambuf(const signed char* _Getptr,
    streamsize count);

strstreambuf(const unsigned char* _Getptr,
    streamsize count);
```

### <a name="parameters"></a>參數

*_Allocfunc*<br/>
用於配置記憶體緩衝區的函式。

*count*<br/>
判斷所指向緩衝區的長度 *_Getptr*。 如果 *_Getptr*不是引數 （第一個建構函式的形式），建議的配置大小的緩衝區。

*_Freefunc*<br/>
用於釋放記憶體緩衝區的函式。

*_Getptr*<br/>
用於輸入的緩衝區。

*_Putptr*<br/>
用於輸出的緩衝區。

### <a name="remarks"></a>備註

第一個建構函式會在控制輸入緩衝區、輸出緩衝區及 strstreambuf 配置的所有指標中儲存一個 null 指標。 它會設定儲存的 strstreambuf 模式，以使受控制的序列成為可修改且可擴充的。 它也會接受*計數*做為建議的初始配置大小。

第二個建構函式的運作方式與第一個類似，但它會儲存 _ *Allocfunc* 做為要呼叫來配置儲存體之函式的指標，以及 \_ *Freefunc* 做為要呼叫來釋放該儲存體之函式的指標。

這三個建構函式：

```cpp
strstreambuf(char *_Getptr,
    streamsize count,
    char *putptr = 0);

strstreambuf(signed char *_Getptr,
    streamsize count,
    signed char *putptr = 0);

strstreambuf(unsigned char *_Getptr,
    streamsize count,
    unsigned char *putptr = 0);
```

運作方式也會與第一個類似，不同之處在於 `_Getptr` 會指定用來保存受控制序列的陣列物件 (因此，它不能是 null 指標)。陣列中的項目數 *N* 的判斷方式如下：

- 如果 (`count` > 0)，然後*N*是`count`。

- 如果 (`count` = = 0)，然後*N*是`strlen`(( **const** `char` *) `_Getptr` )。

- 如果 (`count` < 0)，然後*N*是**INT_MAX**。

如果 `_Putptr` 是 null 指標，函式就會執行下列程式碼，只建立輸入緩衝區：

```cpp
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```

否則，它會執行下列程式碼，來建立輸入和輸出緩衝區：

```cpp
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```

在此情況下，`_Putptr` 必須位於間隔 [ `_Getptr`, `_Getptr` + *N*] 內。

最後，這三個建構函式：

```cpp
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```

全都會以如下的方式運作：

```cpp
streambuf((char *)_Getptr, count);
```

但有個例外是，儲存的模式會使受控制的序列變成不可修改且不可擴充的。

## <a name="underflow"></a>  strstreambuf::underflow

要從輸入資料流擷取目前項目的受保護虛擬函式。

```cpp
virtual int underflow();
```

### <a name="return-value"></a>傳回值

如果函式不成功，則會傳回 `EOF`。 否則會傳回輸入資料流中目前的項目 (已如上所述進行轉換)。

### <a name="remarks"></a>備註

受保護虛擬成員函式會嘗試擷取目前的項目`ch`從輸入緩衝區，然後目前資料流位置前移，並傳回此元素作為 (`int`) (`unsigned char`) **ch**。 它可以這樣做只是一種方式： 如果有讀取的位置可用，它會採用`ch`作為項目儲存在讀取位置，並前進到輸入緩衝區的下一個指標。

## <a name="see-also"></a>另請參閱

[streambuf](../standard-library/streambuf-typedefs.md#streambuf)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
