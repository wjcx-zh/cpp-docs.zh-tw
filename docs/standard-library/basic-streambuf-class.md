---
title: basic_streambuf 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- streambuf/std::basic_streambuf
- streambuf/std::basic_streambuf::char_type
- streambuf/std::basic_streambuf::int_type
- streambuf/std::basic_streambuf::off_type
- streambuf/std::basic_streambuf::pos_type
- streambuf/std::basic_streambuf::traits_type
- streambuf/std::basic_streambuf::eback
- streambuf/std::basic_streambuf::egptr
- streambuf/std::basic_streambuf::epptr
- streambuf/std::basic_streambuf::gbump
- streambuf/std::basic_streambuf::getloc
- streambuf/std::basic_streambuf::gptr
- streambuf/std::basic_streambuf::imbue
- streambuf/std::basic_streambuf::in_avail
- streambuf/std::basic_streambuf::overflow
- streambuf/std::basic_streambuf::pbackfail
- streambuf/std::basic_streambuf::pbase
- streambuf/std::basic_streambuf::pbump
- streambuf/std::basic_streambuf::pptr
- streambuf/std::basic_streambuf::pubimbue
- streambuf/std::basic_streambuf::pubseekoff
- streambuf/std::basic_streambuf::pubseekpos
- streambuf/std::basic_streambuf::pubsetbuf
- streambuf/std::basic_streambuf::pubsync
- streambuf/std::basic_streambuf::sbumpc
- streambuf/std::basic_streambuf::seekoff
- streambuf/std::basic_streambuf::seekpos
- streambuf/std::basic_streambuf::setbuf
- streambuf/std::basic_streambuf::setg
- streambuf/std::basic_streambuf::setp
- streambuf/std::basic_streambuf::sgetc
- streambuf/std::basic_streambuf::sgetn
- streambuf/std::basic_streambuf::showmanyc
- streambuf/std::basic_streambuf::snextc
- streambuf/std::basic_streambuf::sputbackc
- streambuf/std::basic_streambuf::sputc
- streambuf/std::basic_streambuf::sputn
- streambuf/std::basic_streambuf::stossc
- streambuf/std::basic_streambuf::sungetc
- streambuf/std::basic_streambuf::swap
- streambuf/std::basic_streambuf::sync
- streambuf/std::basic_streambuf::uflow
- streambuf/std::basic_streambuf::underflow
- streambuf/std::basic_streambuf::xsgetn
- streambuf/std::basic_streambuf::xsputn
dev_langs:
- C++
helpviewer_keywords:
- std::basic_streambuf [C++]
- std::basic_streambuf [C++], char_type
- std::basic_streambuf [C++], int_type
- std::basic_streambuf [C++], off_type
- std::basic_streambuf [C++], pos_type
- std::basic_streambuf [C++], traits_type
- std::basic_streambuf [C++], eback
- std::basic_streambuf [C++], egptr
- std::basic_streambuf [C++], epptr
- std::basic_streambuf [C++], gbump
- std::basic_streambuf [C++], getloc
- std::basic_streambuf [C++], gptr
- std::basic_streambuf [C++], imbue
- std::basic_streambuf [C++], in_avail
- std::basic_streambuf [C++], overflow
- std::basic_streambuf [C++], pbackfail
- std::basic_streambuf [C++], pbase
- std::basic_streambuf [C++], pbump
- std::basic_streambuf [C++], pptr
- std::basic_streambuf [C++], pubimbue
- std::basic_streambuf [C++], pubseekoff
- std::basic_streambuf [C++], pubseekpos
- std::basic_streambuf [C++], pubsetbuf
- std::basic_streambuf [C++], pubsync
- std::basic_streambuf [C++], sbumpc
- std::basic_streambuf [C++], seekoff
- std::basic_streambuf [C++], seekpos
- std::basic_streambuf [C++], setbuf
- std::basic_streambuf [C++], setg
- std::basic_streambuf [C++], setp
- std::basic_streambuf [C++], sgetc
- std::basic_streambuf [C++], sgetn
- std::basic_streambuf [C++], showmanyc
- std::basic_streambuf [C++], snextc
- std::basic_streambuf [C++], sputbackc
- std::basic_streambuf [C++], sputc
- std::basic_streambuf [C++], sputn
- std::basic_streambuf [C++], stossc
- std::basic_streambuf [C++], sungetc
- std::basic_streambuf [C++], swap
- std::basic_streambuf [C++], sync
- std::basic_streambuf [C++], uflow
- std::basic_streambuf [C++], underflow
- std::basic_streambuf [C++], xsgetn
- std::basic_streambuf [C++], xsputn
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ab94a9aadc40b4313995a71171d6712657e7ff0
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964947"
---
# <a name="basicstreambuf-class"></a>basic_streambuf 類別

描述抽象的基底類別，用以衍生資料流緩衝區，其控制項目如何傳入或傳出資料流的特定表示。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>參數

*Elem* A [char_type](#char_type)。

*Tr*字元[traits_type](#traits_type)。

## <a name="remarks"></a>備註

此範本類別描述抽象的基底類別，用以衍生資料流緩衝區，其控制項目如何傳入或傳出資料流的特定表示。 類別的物件`basic_streambuf`有助於控制資料流類型的項目*Tr*，也稱為[char_type](#char_type)，其字元特性由類別[char_traits](../standard-library/char-traits-struct.md)也稱為[traits_type](#traits_type)。

每個資料流緩衝區在概念上會控制兩個獨立的資料流：一個用於擷取 (輸入)，一個用於插入 (輸出)。 不過，特定的表示法可能使這些資料流之一或兩者無法存取。 它通常會維護兩個資料流之間的某種關聯性。 例如，您插入 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> 物件輸出資料流的內容，即是您稍後從其輸入資料流擷取的內容。 當您定位 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> 物件的一個資料流時，您會串聯地定位其他資料流。

範本類別 `basic_streambuf` 的公用介面提供通用於所有資料流緩衝區的作業，不過是經過特製化。 受保護的介面會提供資料流的特定表示法以執行其工作所需的作業。 受保護的虛擬成員函式可讓您針對資料流的特定表示法量身訂做衍生之資料流緩衝區的行為。 此程式庫中每個衍生的資料流緩衝區會描述其特製化受保護之虛擬成員函式行為的方式。 本主題描述基底類別的預設行為，這通常是不執行任何動作。

剩餘的受保護成員函式會控制要提供給資料流往返傳輸之任何儲存體之間的複製。 例如，輸入緩衝區的特性有：

- [eback](#eback)，緩衝區開頭的指標。

- [gptr](#gptr)，下個待讀取元素的指標。

- [egptr](#egptr)，剛好超過緩衝區結尾的指標。

同樣地，輸出緩衝區的特性有：

- [pbase](#pbase)，緩衝區開頭的指標。

- [pptr](#pptr)，下個待寫入元素的指標。

- [epptr](#epptr)，剛好超過緩衝區結尾的指標。

針對任何緩衝區，會使用下列通訊協定：

- 如果下一個指標為 null，則沒有緩衝區存在。 否則，所有三個指標都指向相同的順序。 它們可以安全地比較順序。

- 針對輸出緩衝區，如果下一個指標比較起來會小於結尾指標，您可以將項目儲存在下個指標所指定的寫入位置。

- 針對輸入緩衝區，如果下一個指標比較起來會小於結尾指標，您可以在下個指標所指定的讀取位置讀取項目。

- 針對輸入緩衝區，如果開始指標比較起來會小於下個指標，您可以將項目放回遞減過之下個指標所指定的放回位置。

您針對衍生自 `basic_streambuf`< `Elem`, `Tr`> 的類別所撰寫的任何受保護虛擬成員函式，都必須相互合作以維護這個通訊協定。

類別 `basic_streambuf`< `Elem`, `Tr`> 的物件會儲存先前所述的六個指標。 它也會在 [locale](../standard-library/locale-class.md) 類型的物件中儲存地區設定物件，以供衍生的資料流緩衝區使用。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_streambuf](#basic_streambuf)|建構類型 `basic_streambuf` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|將類型名稱與 `Elem` 樣板參數產生關聯。|
|[int_type](#int_type)|將  `basic_streambuf` 範圍內的類型名稱與 `Elem` 範本參數產生關聯。|
|[off_type](#off_type)|將  `basic_streambuf` 範圍內的類型名稱與 `Elem` 範本參數產生關聯。|
|[pos_type](#pos_type)|將  `basic_streambuf` 範圍內的類型名稱與 `Elem` 範本參數產生關聯。|
|[traits_type](#traits_type)|將類型名稱與 `Tr` 樣板參數產生關聯。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[eback](#eback)|受保護的函式，會傳回輸入緩衝區開頭的指標。|
|[egptr](#egptr)|受保護的函式，會傳回剛好超過輸入緩衝區結尾的指標。|
|[epptr](#epptr)|受保護的函式，會傳回剛好超過輸出緩衝區結尾的指標。|
|[gbump](#gbump)|受保護的函式，會對輸入緩衝區的下個指標加上 `count`。|
|[getloc](#getloc)|取得 `basic_streambuf` 物件的地區設定。|
|[gptr](#gptr)|受保護的函式，會傳回輸入緩衝區下個項目的指標。|
|[imbue](#imbue)|受保護的虛擬函式，由 [pubimbue](#pubimbue) 呼叫。|
|[in_avail](#in_avail)|傳回可以從緩衝區讀取的項目數。|
|[overflow](#overflow)|受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。|
|[pbackfail](#pbackfail)|受保護的虛擬成員函式，會嘗試將項目放回輸入資料流，然後將其設成目前的項目 (由下一個指標指向)。|
|[pbase](#pbase)|受保護的函式，會傳回輸出緩衝區開頭的指標。|
|[pbump](#pbump)|受保護的函式，會對輸出緩衝區的下個指標加上 `count`。|
|[pptr](#pptr)|受保護的函式，會傳回輸出緩衝區下個項目的指標。|
|[pubimbue](#pubimbue)|設定 `basic_streambuf` 物件的地區設定。|
|[pubseekoff](#pubseekoff)|呼叫 [seekoff](#seekoff)，這是在衍生類別中遭覆寫的受保護虛擬函式。|
|[pubseekpos](#pubseekpos)|呼叫 [seekpos](#seekpos)，這是在衍生類別中遭覆寫的受保護虛擬函式，並且重設目前的指標位置。|
|[pubsetbuf](#pubsetbuf)|呼叫 [setbuf](#setbuf)，這是在衍生類別中遭覆寫的受保護虛擬函式。|
|[pubsync](#pubsync)|呼叫 [sync](#sync)，這是在衍生類別中遭覆寫的受保護虛擬函式，並且更新這個緩衝區相關聯的外部資料流。|
|[sbumpc](#sbumpc)|讀取並傳回目前項目，同時移動資料流指標。|
|[seekoff](#seekoff)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|
|[seekpos](#seekpos)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|
|[setbuf](#setbuf)|受保護的虛擬成員函式會執行每個衍生資料流緩衝區的特定作業。|
|[setg](#setg)|受保護的函式，會在開頭指標儲存 `_Gbeg`，在下個指標儲存 `_Gnext`，以及在輸入緩衝區的結尾指標儲存 `_Gend`。|
|[setp](#setp)|受保護的函式，會在開頭指標儲存 `_Pbeg`，以及在輸出緩衝區的結尾指標儲存 `_Pend`。|
|[sgetc](#sgetc)|傳回目前的項目而不變更資料流中的位置。|
|[sgetn](#sgetn)|傳回讀取的項目數目。|
|[showmanyc](#showmanyc)|受保護的虛擬成員函式，會傳回可從輸入資料流擷取的字元數計數，並確保程式不會無限地等候。|
|[snextc](#snextc)|讀取目前項目並傳回下個項目。|
|[sputbackc](#sputbackc)|將 `char_type` 放入資料流。|
|[sputc](#sputc)|將字元放入資料流。|
|[sputn](#sputn)|將字元字串放入資料流。|
|[stossc](#stossc)|移動超過資料流中目前的項目。|
|[sungetc](#sungetc)|從資料流取得字元。|
|[swap](#swap)|用這個物件中的值，交換所提供之 `basic_streambuf` 物件參數中的值。|
|[sync](#sync)|受保護的虛擬函式，會嘗試與任何相關聯的外部資料流同步處理控制資料流。|
|[uflow](#uflow)|受保護的虛擬函式，會從輸入資料流擷取目前的項目。|
|[underflow](#underflow)|受保護的虛擬函式，會從輸入資料流擷取目前的項目。|
|[xsgetn](#xsgetn)|受保護的虛擬函式，會從輸入資料流擷取項目。|
|[xsputn](#xsputn)|受保護的虛擬函式，會將項目插入輸出資料流。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_eq)|從另一個 `basic_streambuf` 物件指派這個物件的值。|

## <a name="requirements"></a>需求

**標頭：**\<streambuf>

**命名空間：** std

## <a name="basic_streambuf"></a>  basic_streambuf::basic_streambuf

建構類型 `basic_streambuf` 的物件。

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>參數

*右*左值參考`basic_streambuf`用來設定值，這個物件`basic_streambuf`物件。

### <a name="remarks"></a>備註

第一個受保護的建構函式會在控制輸入緩衝區和輸出緩衝區的所有指標中儲存一個 null 指標。 它也會在地區設定物件中儲存 `locale::classic`。 如需詳細資訊，請參閱 [locale::classic](../standard-library/locale-class.md#classic)。

第二個受保護的建構函式複製指標和地區設定，從*右*。

## <a name="char_type"></a>  basic_streambuf::char_type

將類型名稱與 **Elem** 範本參數建立關聯。

```cpp
typedef Elem char_type;
```

## <a name="eback"></a>  basic_streambuf::eback

受保護的函式，會傳回輸入緩衝區開頭的指標。

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>傳回值

輸入緩衝區開頭的指標。

## <a name="egptr"></a>  basic_streambuf::egptr

受保護的函式，會傳回剛好超過輸入緩衝區結尾的指標。

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>傳回值

剛好超過輸入緩衝區結尾的指標。

## <a name="epptr"></a>  basic_streambuf::epptr

受保護的函式，會傳回剛好超過輸出緩衝區結尾的指標。

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>傳回值

剛好超過輸出緩衝區結尾的指標。

## <a name="gbump"></a>  basic_streambuf::gbump

受保護的函式，將它新增*計數*到輸入緩衝區的下一個指標。

```cpp
void gbump(int count);
```

### <a name="parameters"></a>參數

*計數*指標前進的數量。

## <a name="getloc"></a>  basic_streambuf::getloc

取得 basic_streambuf 物件的地區設定。

```cpp
locale getloc() const;
```

### <a name="return-value"></a>傳回值

預存的地區設定物件。

### <a name="remarks"></a>備註

如需相關資訊，請參閱 [ios_base::getloc](../standard-library/ios-base-class.md#getloc)。

### <a name="example"></a>範例

```cpp
// basic_streambuf_getloc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << cout.rdbuf( )->getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="gptr"></a>  basic_streambuf::gptr

受保護的函式，會傳回輸入緩衝區下個項目的指標。

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>傳回值

輸入緩衝區中下一個元素的指標。

## <a name="imbue"></a>  basic_streambuf::imbue

受保護的虛擬函式，由 [pubimbue](#pubimbue) 呼叫。

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>參數

*_Loc*地區設定的參考。

### <a name="remarks"></a>備註

預設行為是不執行任何動作。

## <a name="in_avail"></a>  basic_streambuf::in_avail

傳回可以從緩衝區讀取的項目數。

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>傳回值

準備從緩衝區讀取的元素數目。

### <a name="remarks"></a>備註

如果[讀取位置](../standard-library/basic-streambuf-class.md)可供使用，此成員函式會傳回[egptr](#egptr) - [gptr](#gptr)。 否則會傳回 [showmanyc](#showmanyc)。

### <a name="example"></a>範例

```cpp
// basic_streambuf_in_avail.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   char c;
   // cin's buffer is empty, in_avail will return 0
   cout << cin.rdbuf( )->in_avail( ) << endl;
   cin >> c;
   cout << cin.rdbuf( )->in_avail( ) << endl;
}
```

## <a name="int_type"></a>  basic_streambuf::int_type

將 basic_streambuf 範圍內的類型名稱與樣板參數中的其中一個類型產生關聯。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_streambuf::off_type

將 basic_streambuf 範圍內的類型名稱與樣板參數中的其中一個類型產生關聯。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_eq"></a>  basic_streambuf::operator=

從另一個 `basic_streambuf` 物件指派這個物件的值。

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>參數

*右*左值參考`basic_streambuf`用來將值指派給這個物件的物件。

### <a name="remarks"></a>備註

受保護的成員運算子會從複製*右*控制輸入的緩衝區和輸出緩衝區的指標。 它也會在 `locale object` 中儲存 `right.`[getloc()](#getloc)。 它會傳回 `*this`。

## <a name="overflow"></a>  basic_streambuf::overflow

受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>參數

*_Meta*要插入緩衝區的字元或**traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。

### <a name="return-value"></a>傳回值

如果函式不成功，則傳回 **traits_type::eof** 或擲回例外狀況。 否則會傳回 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)。 預設行為是傳回 **traits_type::eof**。

### <a name="remarks"></a>備註

如果 _ *Meta* 與 **traits_type::eof** 比較的結果不相等，此受保護的虛擬成員函式會嘗試將元素 **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) 插入輸出資料流。 它可以透過下列各種方式來執行：

- 如果有`write position`可供使用，它可以將元素儲存在寫入位置，並遞增輸出緩衝區的下一個指標。

- 為輸出緩衝區配置新的或額外的儲存空間，即可提供寫入位置。

- 藉由將輸出緩衝區的開頭指標和下一個指標之間的部分或所有元素寫出至特定外部目的地，即可提供寫入位置。

此虛擬 overflow 函式可搭配 [sync](#sync) 和 [underflow](#underflow) 函式，定義 streambuf 衍生類別的特性。 每個衍生類別可能會以不同的方式來實作 overflow，但呼叫資料流類別的介面則相同。

`overflow` 函式最常在 put 區域已滿的情況下，由公開 `streambuf` 函式 (例如 `sputc` 和 `sputn`) 呼叫，但其他類別 (包括資料流類別) 也可以隨時呼叫 `overflow`。

此函式會取用 put 區域中介於 `pbase` 和 `pptr` 指標之間的字元，然後將 put 區域重新初始化。 `overflow` 函式也必須取用 `nCh` (如果 `nCh` 不是 `EOF`)；或者，它可能會選擇將該字元放在新的 put 區域，以供下一個呼叫取用。

取用的定義會因衍生類別而異。 例如，`filebuf` 類別會將其字元寫入至檔案，而 `strstreambuf` 類別會將這些字元保留在其緩衝區中 (如果緩衝區已指定為動態)，並擴充緩衝區以回應溢位呼叫。 此擴充可透過釋放舊緩衝區並取代為較大的新緩衝區來達成。 這些指標會視需要進行調整。

## <a name="pbackfail"></a>  basic_streambuf::pbackfail

受保護的虛擬成員函式，會嘗試將項目放回輸入資料流，然後將其設成目前的項目 (由下一個指標指向)。

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>參數

*_Meta*要插入緩衝區的字元或**traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。

### <a name="return-value"></a>傳回值

如果函式不成功，則傳回 **traits_type::eof** 或擲回例外狀況。 否則，它會傳回其他值。 預設行為是傳回 **traits_type::eof**。

### <a name="remarks"></a>備註

如果 _ *Meta* 與 **traits_type::eof** 比較的結果相等，要推回的元素實際上是一個已在資料流中目前元素之前的元素。 否則會以 **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) 取代該元素。 函式可透過下列各種方式來放回項目：

- 如果有放回位置可供使用，它可以將元素儲存在放回位置，並遞減輸入緩衝區的下一個指標。

- 藉由為輸入緩衝區配置新的或額外的儲存體，即可提供放回位置。

- 針對具有通用輸入和輸出資料流的資料流緩衝區，藉由將輸出緩衝區的開頭指標和下一個指標之間的部分或所有元素寫出至特定外部目的地，即可提供放回位置。

## <a name="pbase"></a>  basic_streambuf::pbase

受保護的函式，會傳回輸出緩衝區開頭的指標。

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>傳回值

輸出緩衝區開頭的指標。

## <a name="pbump"></a>  basic_streambuf::pbump

受保護的函式，將它新增*計數*至輸出緩衝區的下一個指標。

```cpp
void pbump(int count);
```

### <a name="parameters"></a>參數

*計數*用以移動寫入的字元數的位置往前。

## <a name="pos_type"></a>  basic_streambuf::pos_type

將 basic_streambuf 範圍內的類型名稱與樣板參數中的其中一個類型產生關聯。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="pptr"></a>  basic_streambuf::pptr

受保護的函式，會傳回輸出緩衝區下個項目的指標。

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>傳回值

輸出緩衝區中下一個元素的指標。

## <a name="pubimbue"></a>  basic_streambuf::pubimbue

設定 basic_streambuf 物件的地區設定。

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>參數

*_Loc*地區設定的參考。

### <a name="return-value"></a>傳回值

先前儲存在地區設定物件中的值。

### <a name="remarks"></a>備註

此成員函式會在地區設定物件中儲存 _ *Loc*，並呼叫 [imbue](#imbue)。

### <a name="example"></a>範例

如需使用 `pubimbue` 的範例，請參閱 [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue)。

## <a name="pubseekoff"></a>  basic_streambuf::pubseekoff

呼叫 [seekoff](#seekoff)，這是在衍生類別中遭覆寫的受保護虛擬函式。

```cpp
pos_type pubseekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Off*要搜尋的相對位置 *_Way*。

*_Way*位移作業的起點。 如需可能的值，請參閱 [seekdir](../standard-library/ios-base-class.md#seekdir)。

*_Which*指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

傳回新位置或無效的資料流位置 ( [seekoff](#seekoff)(_ *Off*, `_Way`, `_Which`) )。

### <a name="remarks"></a>備註

移動指標相對於 *_Way*。

## <a name="pubseekpos"></a>  basic_streambuf::pubseekpos

呼叫 [seekpos](#seekpos)，這是在衍生類別中遭覆寫的受保護虛擬函式，並且重設目前的指標位置。

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Sp*来搜尋的位置。

*_Which*指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

新位置或無效的資料流位置。 若要判斷資料流位置是否無效，請比較傳回值與 `pos_type(off_type(-1))`。

### <a name="remarks"></a>備註

此成員函式會傳回 [seekpos](#seekpos)(_ *Sp*, `_Which`)。

## <a name="pubsetbuf"></a>  basic_streambuf::pubsetbuf

呼叫 [setbuf](#setbuf)，這是在衍生類別中遭覆寫的受保護虛擬函式。

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>參數

*_Buffer*指向的`char_type`此具現化。

*計數*緩衝區的大小。

### <a name="return-value"></a>傳回值

傳回 [setbuf](#setbuf)( `_Buffer`, `count`)。

## <a name="pubsync"></a>  basic_streambuf::pubsync

呼叫 [sync](#sync)，這是在衍生類別中遭覆寫的受保護虛擬函式，並且更新這個緩衝區相關聯的外部資料流。

```cpp
int pubsync();
```

### <a name="return-value"></a>傳回值

傳回[同步](#sync)或-1 表示失敗。

## <a name="sbumpc"></a>  basic_streambuf::sbumpc

讀取並傳回目前項目，同時移動資料流指標。

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>傳回值

目前的元素。

### <a name="remarks"></a>備註

如果有讀取位置可供使用，此成員函式會傳回 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **\***[gptr](#gptr))，並遞增輸入緩衝區的下一個指標。 否則會傳回 [uflow](#uflow)。

### <a name="example"></a>範例

```cpp
// basic_streambuf_sbumpc.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->sbumpc( );
   cout << i << endl;
}
```

```Output

3

```

```Output

      33
51
```

## <a name="seekoff"></a>  basic_streambuf::seekoff

受保護虛擬成員函式嘗試改變受控制資料流目前的位置。

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Off*要搜尋的相對位置 *_Way*。

*_Way*位移作業的起點。 如需可能的值，請參閱 [seekdir](../standard-library/ios-base-class.md#seekdir)。

*_Which*指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

傳回新位置或無效的資料流位置 ( `seekoff` (_ *Off*, `_Way`, `_Which`) )。

### <a name="remarks"></a>備註

新位置的判斷方式如下：

- 如果 `_Way` == `ios_base::beg`，新位置是資料流開頭加上 _ *Off*。

- 如果 `_Way` == `ios_base::cur`，新位置是目前的資料流位置加上 _ *Off*。

- 如果 `_Way` == `ios_base::end`，新位置是資料流結尾加上 _ *Off*。

一般而言，如果 **which & ios_base::in** 為非零值，則會影響輸入資料流；如果 **which & ios_base::out** 為非零值，則會影響輸出資料流。 不過，此參數的實際用法會因衍生的資料流緩衝區而異。

如果此函式成功改變一或多個資料流位置，則會傳回產生的資料流位置或其中一個產生的資料流位置。 否則會傳回無效的資料流位置。 預設行為是傳回無效的資料流位置。

## <a name="seekpos"></a>  basic_streambuf::seekpos

受保護虛擬成員函式嘗試改變受控制資料流目前的位置。

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Sp*来搜尋的位置。

*_Which*指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

新位置或無效的資料流位置。 若要判斷資料流位置是否無效，請比較傳回值與 `pos_type(off_type(-1))`。

### <a name="remarks"></a>備註

新位置為 _ *Sp*。

一般而言，如果 **which & ios_base::in** 為非零值，則會影響輸入資料流；如果 **which & ios_base::out** 為非零值，則會影響輸出資料流。 不過，此參數的實際用法會因衍生的資料流緩衝區而異。

如果此函式成功改變一或多個資料流位置，則會傳回產生的資料流位置或其中一個產生的資料流位置。 否則會傳回無效的資料流位置 (-1)。 預設行為是傳回無效的資料流位置。

## <a name="setbuf"></a>  basic_streambuf::setbuf

受保護的虛擬成員函式，會執行每個衍生資料流緩衝區的特定作業。

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>參數

*_Buffer*緩衝區的指標。

*計數*緩衝區的大小。

### <a name="return-value"></a>傳回值

預設行為是傳回 **this**。

### <a name="remarks"></a>備註

請參閱 [basic_filebuf](../standard-library/basic-filebuf-class.md)。 `setbuf` 會提供一個記憶體區域給 `streambuf` 物件使用。 緩衝區的使用方式會定義於衍生類別中。

## <a name="setg"></a>  basic_streambuf::setg

受保護的函式，會在輸入緩衝區的開頭指標儲存 _ *Gbeg*，在下一個指標儲存 `_Gnext`，以及在結尾指標儲存 `_Gend`。

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>參數

*_Gbeg*緩衝區開頭的指標。

*_Gnext*某個位置的指標緩衝區中間。

*_Gend*緩衝區結尾的指標。

## <a name="setp"></a>  basic_streambuf::setp

受保護的函數，可儲存 *_Pbeg*在開頭指標和 *_Pend*輸出緩衝區的結尾指標。

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>參數

*_Pbeg*緩衝區開頭的指標。

*_Pend*緩衝區結尾的指標。

## <a name="sgetc"></a>  basic_streambuf::sgetc

傳回目前的項目而不變更資料流中的位置。

```cpp
int_type sgetc();
```

### <a name="return-value"></a>傳回值

目前的元素。

### <a name="remarks"></a>備註

如果有讀取位置可供使用，此成員函式會傳回 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*`[gptr](#gptr))。 否則會傳回 [underflow](#underflow)。

### <a name="example"></a>範例

```cpp
// basic_streambuf_sgetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_sgetc.txt", ios::in );

   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
   i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sgetn"></a>  basic_streambuf::sgetn

最多會擷取*計數*從輸入緩衝區的字元，並將它們儲存在提供的緩衝區*ptr*。

此方法有賴於呼叫者檢查傳遞的值是否正確，因此可能不安全。

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>參數

*ptr*包含所擷取的字元的緩衝區。

*計數*讀取的項目數。

### <a name="return-value"></a>傳回值

所讀取的元素數目。 如需詳細資訊，請參閱 [streamsize](../standard-library/ios-typedefs.md#streamsize)。

### <a name="remarks"></a>備註

此成員函式會傳回 [xsgetn](#xsgetn)( `ptr`, `count`)。

### <a name="example"></a>範例

```cpp
// basic_streambuf_sgetn.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    ifstream myfile("basic_streambuf_sgetn.txt", ios::in);
    char a[10];

    // Extract 3 characters from myfile and store them in a.
    streamsize i = myfile.rdbuf()->sgetn(&a[0], 3);  // C4996
    a[i] = myfile.widen('\0');

    // Display the size and contents of the buffer passed to sgetn.
    cout << i << " " << a << endl;

    // Display the contents of the original input buffer.
    cout << myfile.rdbuf() << endl;
}
```

## <a name="showmanyc"></a>  basic_streambuf::showmanyc

受保護的虛擬成員函式，會傳回可從輸入資料流擷取的字元數計數，並確保程式不會無限地等候。

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>傳回值

預設行為是傳回零。

## <a name="snextc"></a>  basic_streambuf::snextc

讀取目前項目並傳回下個項目。

```cpp
int_type snextc();
```

### <a name="return-value"></a>傳回值

資料流中的下一個元素。

### <a name="remarks"></a>備註

此成員函式會呼叫 [sbumpc](#sbumpc)；如果該函式傳回 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)，則傳回 **traits_type::eof**。 否則會傳回 [sgetc](#sgetc)。

### <a name="example"></a>範例

```cpp
// basic_streambuf_snextc.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   int i = 0;
   i = cin.rdbuf( )->snextc( );
   // cout << ( int )char_traits<char>::eof << endl;
   cout << i << endl;
}
```

```Output

aa

```

```Output

aa97
```

## <a name="sputbackc"></a>  basic_streambuf::sputbackc

將 char_type 放入資料流。

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>參數

*_Ch*字元。

### <a name="return-value"></a>傳回值

傳回字元或失敗。

### <a name="remarks"></a>備註

如果有 putback 位置可供使用並 *_Ch*字元儲存在該位置中，成員函式會遞減輸入的緩衝區和傳回的下一個指標比較結果相等**traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`)。 否則會傳回 [pbackfail](#pbackfail)( `_Ch`)。

### <a name="example"></a>範例

```cpp
// basic_streambuf_sputbackc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;

    ifstream myfile("basic_streambuf_sputbackc.txt",
        ios::in);

    int i = myfile.rdbuf()->sbumpc();
    cout << (char)i << endl;
    int j = myfile.rdbuf()->sputbackc('z');
    if (j == 'z')
    {
        cout << "it worked" << endl;
    }
    i = myfile.rdbuf()->sgetc();
    cout << (char)i << endl;
}
```

## <a name="sputc"></a>  basic_streambuf::sputc

將字元放入資料流。

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>參數

*_Ch*字元。

### <a name="return-value"></a>傳回值

如果成功，則傳回字元。

### <a name="remarks"></a>備註

如果`write position`可供使用，此成員函式會 *_Ch*在寫入位置，遞增輸出緩衝區的下一個指標，並傳回**traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`). 否則會傳回 [overflow](#overflow)( `_Ch`)。

### <a name="example"></a>範例

```cpp
// basic_streambuf_sputc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   int i = cout.rdbuf( )->sputc( 'a' );
   cout << endl << ( char )i << endl;
}
```

```Output
a
a
```

## <a name="sputn"></a>  basic_streambuf::sputn

將字元字串放入資料流。

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>參數

*ptr*字元字串。

*計數*的字元計數。

### <a name="return-value"></a>傳回值

實際插入資料流的字元數。

### <a name="remarks"></a>備註

此成員函式會傳回 [xsputn](#xsputn)( `ptr`, `count`)。 如需詳細資訊，請參閱此成員的＜備註＞一節。

### <a name="example"></a>範例

```cpp
// basic_streambuf_sputn.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;

    streamsize i = cout.rdbuf()->sputn("test", 4);
    cout << endl << i << endl;
}
```

```Output
test
4
```

## <a name="stossc"></a>  basic_streambuf::stossc

移動超過資料流中目前的項目。

```cpp
void stossc();
```

### <a name="remarks"></a>備註

此成員函式會呼叫 [sbumpc](#sbumpc)。 請注意，不需要實作就能提供此成員函式。

### <a name="example"></a>範例

```cpp
// basic_streambuf_stossc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   ifstream myfile( "basic_streambuf_stossc.txt", ios::in );

   myfile.rdbuf( )->stossc( );
   char i = myfile.rdbuf( )->sgetc( );
   cout << i << endl;
}
```

## <a name="sungetc"></a>  basic_streambuf::sungetc

從資料流取得字元。

```cpp
int_type sungetc();
```

### <a name="return-value"></a>傳回值

傳回字元或失敗。

### <a name="remarks"></a>備註

如果有放回位置可供使用，此成員函式會遞減輸入緩衝區的下一個指標，並傳回 `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*`[gptr](#gptr))。 不過，不一定能夠判斷所讀取的最後一個字元，以便在目前緩衝區的狀態中擷取此字元。 如果是此情況，則函式會傳回 [pbackfail](#pbackfail)。 若要避免發生這種情況，請追蹤要放回的字元並呼叫 `sputbackc(ch)`；只要您不是在資料流開頭呼叫，而且未嘗試放回一個以上的字元，此作業就不會失敗。

### <a name="example"></a>範例

```cpp
// basic_streambuf_sungetc.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ifstream myfile( "basic_streambuf_sungetc.txt", ios::in );

   // Read and increment
   int i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Read and increment
   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;

   // Decrement, read, and do not increment
   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sungetc( );
   cout << ( char )i << endl;

   i = myfile.rdbuf( )->sbumpc( );
   cout << ( char )i << endl;
}
```

## <a name="swap"></a>  basic_streambuf::swap

用此物件的值交換所提供的 `basic_streambuf` 物件中的值。

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*right*|用來交換值的 `basic_streambuf` 左值參考物件。|

### <a name="remarks"></a>備註

受保護的成員函式交換*右*控制的所有指標`input buffer`而`output buffer`。 它也會將 `right.`[getloc()](#getloc) 與 `locale` 物件交換。

## <a name="sync"></a>  basic_streambuf::sync

受保護的虛擬函式，會嘗試與任何相關聯的外部資料流同步處理控制資料流。

```cpp
virtual int sync();
```

### <a name="return-value"></a>傳回值

如果函式不成功，則傳回 -1。 預設行為是傳回零。

### <a name="remarks"></a>備註

`sync` 需要將輸出緩衝區的開頭指標和下一個指標之間的任何元素寫出。 它不需要將輸入緩衝區的下一個指標和結尾指標之間的任何元素放回。

## <a name="traits_type"></a>  basic_streambuf::traits_type

將類型名稱與 **Tr** 樣板參數產生關聯。

```cpp
typedef Tr traits_type;
```

## <a name="uflow"></a>  basic_streambuf::uflow

受保護的虛擬函式，會從輸入資料流擷取目前的項目。

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>傳回值

目前的元素。

### <a name="remarks"></a>備註

此受保護的虛擬成員函式會嘗試從輸入資料流擷取目前的元素 **ch**，然後從目前的資料流位置前移，並傳回此元素作為 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**)。 它可以透過下列各種方式來執行：

- 如果有讀取位置可供使用，它會採用 **ch** 作為儲存在讀取位置中的元素，並前進到輸入緩衝區的下一個指標。

- 它可以直接從特定外部來源讀取元素，並提供此元素作為 **ch** 值。

- 針對具有通用輸入和輸出資料流的資料流緩衝區，藉由將輸出緩衝區的開頭指標和下一個指標之間的部分或所有元素寫出至特定外部目的地，即可提供讀取位置。 或者，它可以為輸入緩衝區配置新的或額外的儲存體。 此函式接著會從特定外部來源讀入一或多個元素。

如果函式不成功，則傳回 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof) 或擲回例外狀況。 否則，它會傳回輸入資料流中目前的元素 `ch` (已如上所述進行轉換)，並前進到輸入緩衝區的下一個指標。 預設行為是呼叫 [underflow](#underflow)；如果該函式傳回 **traits_type::eof**，則傳回 **traits_type::eof**。 否則，此函式會傳回輸入資料流中目前的元素 **ch** (已如上所述進行轉換)，並前進到輸入緩衝區的下一個指標。

## <a name="underflow"></a>  basic_streambuf::underflow

用於從輸入資料流擷取目前項目之受保護的虛擬函式。

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>傳回值

目前的元素。

### <a name="remarks"></a>備註

此受保護的虛擬成員函式會嘗試從輸入資料流擷取目前的元素 **ch**，而不需要從目前的資料流位置前移，並傳回此元素作為 `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**)。 它可以透過下列各種方式來執行：

- 如果有讀取位置可供使用，**ch** 會是儲存在讀取位置的元素。 如需詳細資訊，請參閱 [basic_streambuf 類別](../standard-library/basic-streambuf-class.md)的＜備註＞一節。

- 藉由為輸入緩衝區配置新的或額外的儲存體，然後從特定外部來源讀入一或多個元素，即可提供讀取位置。 如需詳細資訊，請參閱 [basic_streambuf 類別](../standard-library/basic-streambuf-class.md)的＜備註＞一節。

如果函式不成功，則傳回 `traits_type::`[eof](../standard-library/char-traits-struct.md#eof)`()` 或擲回例外狀況。 否則會傳回輸入資料流中目前的元素 (已如上所述進行轉換)。 預設行為是傳回 `traits_type::eof()`。

此虛擬 `underflow` 函式可搭配 [sync](#sync) 和 [overflow](#overflow) 函式，定義 `streambuf` 衍生類別的特性。 每個衍生類別可能會以不同的方式來實作 `underflow`，但呼叫資料流類別的介面則相同。

`underflow` 函式最常在 get 區域為空白的情況下，由公開 `streambuf` 函式 (例如 [sgetc](#sgetc) 和 [sgetn](#sgetn)) 呼叫，但其他類別 (包括資料流類別) 也可以隨時呼叫 `underflow`。

`underflow` 函式會將來自輸入來源的字元提供給 get 區域。 如果 get 區域包含字元，`underflow` 會傳回第一個字元。 如果 get 區域為空白，則會填滿 get 區域，並傳回留在 get 區域中的下一個字元。 如果沒有更多字元可供使用，則 `underflow` 會傳回 `EOF`，並將 get 區域保留空白。

在 `strstreambuf` 類別中，`underflow` 會調整 [egptr](#egptr) 指標，以存取藉由呼叫 `overflow` 所動態配置的儲存體。

## <a name="xsgetn"></a>  basic_streambuf::xsgetn

要從輸入資料流擷取元素的受保護虛擬函式。

此方法有賴於呼叫者檢查傳遞的值是否正確，因此可能不安全。

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>參數

*ptr*包含所擷取的字元的緩衝區。

*計數*擷取的項目數。

### <a name="return-value"></a>傳回值

所擷取的元素數目。

### <a name="remarks"></a>備註

受保護虛擬成員函式最多會擷取*計數*項目，從輸入資料流中，像重複呼叫[sbumpc](#sbumpc)，並將它們儲存在開頭的陣列中*ptr*. 它會傳回實際擷取的元素數目。

## <a name="xsputn"></a>  basic_streambuf::xsputn

要將元素插入輸出資料流的受保護虛擬函式。

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>參數

*ptr*插入元素的指標。

*計數*要插入的元素數目。

### <a name="return-value"></a>傳回值

實際插入資料流的元素數目。

### <a name="remarks"></a>備註

受保護虛擬成員函式會插入最多*計數*元素插入輸出串流，一樣重複呼叫[sputc](#sputc)，從陣列開頭*ptr*。 將插入的字元輸出資料流一次停止所有*計數*已寫入的字元，或如果呼叫`sputc( count)`會傳回`traits::eof()`。 它會傳回實際插入的元素數目。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
