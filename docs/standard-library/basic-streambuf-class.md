---
title: basic_streambuf 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 0cf7b61bde86a4643836346dafd36680fb8cf302
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376735"
---
# <a name="basic_streambuf-class"></a>basic_streambuf 類別

描述抽象的基底類別，用以衍生資料流緩衝區，其控制項目如何傳入或傳出資料流的特定表示。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>參數

*埃萊姆*\
[char_type](#char_type)。

*Tr*\
字元 [traits_type](#traits_type)。

## <a name="remarks"></a>備註

類範本描述用於派生流緩衝區的抽象基類,該類控制元素在流的特定表示形式中傳輸或從流的特定表示形式傳輸。 類別`basic_streambuf`的物件有助於控制具有*Tr*類型(也稱為[char_type)](#char_type)元素的流,其字元特徵由類[char_traits(](../standard-library/char-traits-struct.md)也稱為[traits_type)](#traits_type)決定。

每個資料流緩衝區在概念上會控制兩個獨立的資料流：一個用於擷取 (輸入)，一個用於插入 (輸出)。 不過，特定的表示法可能使這些資料流之一或兩者無法存取。 它通常會維護兩個資料流之間的某種關聯性。 例如,插入到[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`的輸出流中,>`Tr`物件,是以後從其輸入流中提取的內容。 當您將[basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`的一個流`Tr`定位時 ,>对象,將另一個流串聯放置。

類範本`basic_streambuf`的公共介面提供所有流緩衝區共有的操作,無論這些操作是專用的。 受保護的介面會提供資料流的特定表示法以執行其工作所需的作業。 受保護的虛擬成員函式可讓您針對資料流的特定表示法量身訂做衍生之資料流緩衝區的行為。 此程式庫中每個衍生的資料流緩衝區會描述其特製化受保護之虛擬成員函式行為的方式。 本主題描述基底類別的預設行為，這通常是不執行任何動作。

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

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[eback](#eback)|受保護的函式，會傳回輸入緩衝區開頭的指標。|
|[egptr](#egptr)|受保護的函式，會傳回剛好超過輸入緩衝區結尾的指標。|
|[epptr](#epptr)|受保護的函式，會傳回剛好超過輸出緩衝區結尾的指標。|
|[gbump](#gbump)|受保護的函式，會對輸入緩衝區的下個指標加上 `count`。|
|[貝洛克](#getloc)|取得 `basic_streambuf` 物件的地區設定。|
|[gptr](#gptr)|受保護的函式，會傳回輸入緩衝區下個項目的指標。|
|[imbue](#imbue)|由[pubimbue](#pubimbue)調用的受保護虛擬函數。|
|[in_avail](#in_avail)|傳回可以從緩衝區讀取的項目數。|
|[溢出](#overflow)|受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。|
|[pbackfail](#pbackfail)|受保護的虛擬成員函式，會嘗試將項目放回輸入資料流，然後將其設成目前的項目 (由下一個指標指向)。|
|[pbase](#pbase)|受保護的函式，會傳回輸出緩衝區開頭的指標。|
|[pbump](#pbump)|受保護的函式，會對輸出緩衝區的下個指標加上 `count`。|
|[pptr](#pptr)|受保護的函式，會傳回輸出緩衝區下個項目的指標。|
|[pubimbue](#pubimbue)|設定 `basic_streambuf` 物件的地區設定。|
|[pubseekoff](#pubseekoff)|呼叫 [seekoff](#seekoff)，這是在衍生類別中遭覆寫的受保護虛擬函式。|
|[pubseekpos](#pubseekpos)|呼叫[seekpos,](#seekpos)在派生類別中重寫並重置目前指標位置的受保護虛擬函數。|
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
|[交換](#swap)|用這個物件中的值，交換所提供之 `basic_streambuf` 物件參數中的值。|
|[sync](#sync)|受保護的虛擬函式，會嘗試與任何相關聯的外部資料流同步處理控制資料流。|
|[uflow](#uflow)|受保護的虛擬函式，會從輸入資料流擷取目前的項目。|
|[underflow](#underflow)|受保護的虛擬函式，會從輸入資料流擷取目前的項目。|
|[xsgetn](#xsgetn)|受保護的虛擬函式，會從輸入資料流擷取項目。|
|[xsputn](#xsputn)|受保護的虛擬函式，會將項目插入輸出資料流。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子*](#op_eq)|從另一個 `basic_streambuf` 物件指派這個物件的值。|

## <a name="requirements"></a>需求

**標頭：** \<streambuf>

**命名空間：** std

## <a name="basic_streambufbasic_streambuf"></a><a name="basic_streambuf"></a>basic_streambuf::basic_streambuf

建構類型 `basic_streambuf` 的物件。

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>參數

*對*\
`basic_streambuf` 物件的左值參考，用來設定這個 `basic_streambuf` 物件的值。

### <a name="remarks"></a>備註

第一個受保護的建構函式會在控制輸入緩衝區和輸出緩衝區的所有指標中儲存一個 null 指標。 它也會在地區設定物件中儲存 `locale::classic`。 如需詳細資訊，請參閱 [locale::classic](../standard-library/locale-class.md#classic)。

第二個受保護的構造函數從*右側*複製指標和區域設置。

## <a name="basic_streambufchar_type"></a><a name="char_type"></a>basic_streambuf:char_type

將類型名稱與 **Elem** 範本參數建立關聯。

```cpp
typedef Elem char_type;
```

## <a name="basic_streambufeback"></a><a name="eback"></a>basic_streambuf:返回

受保護的函式，會傳回輸入緩衝區開頭的指標。

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>傳回值

輸入緩衝區開頭的指標。

## <a name="basic_streambufegptr"></a><a name="egptr"></a>basic_streambuf:egptr

受保護的函式，會傳回剛好超過輸入緩衝區結尾的指標。

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>傳回值

剛好超過輸入緩衝區結尾的指標。

## <a name="basic_streambufepptr"></a><a name="epptr"></a>basic_streambuf:埃普特爾

受保護的函式，會傳回剛好超過輸出緩衝區結尾的指標。

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>傳回值

剛好超過輸出緩衝區結尾的指標。

## <a name="basic_streambufgbump"></a><a name="gbump"></a>basic_streambuf:凹凸

將*計數*添加到輸入緩衝區的下一個指標的受保護函數。

```cpp
void gbump(int count);
```

### <a name="parameters"></a>參數

*計數*\
用來將指標向前移的數量。

## <a name="basic_streambufgetloc"></a><a name="getloc"></a>basic_streambuf:getloc

取得 basic_streambuf 物件的地區設定。

```cpp
locale getloc() const;
```

### <a name="return-value"></a>傳回值

已儲存的地區設定物件。

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

## <a name="basic_streambufgptr"></a><a name="gptr"></a>basic_streambuf:gptr

受保護的函式，會傳回輸入緩衝區下個項目的指標。

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>傳回值

輸入緩衝區中下一個元素的指標。

## <a name="basic_streambufimbue"></a><a name="imbue"></a>basic_streambuf:英布

受保護的虛擬函式，由 [pubimbue](#pubimbue) 呼叫。

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>參數

*_Loc*\
地區設定的參考。

### <a name="remarks"></a>備註

預設行為是不執行任何動作。

## <a name="basic_streambufin_avail"></a><a name="in_avail"></a>basic_streambuf:in_avail

傳回可以從緩衝區讀取的項目數。

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>傳回值

準備從緩衝區讀取的元素數目。

### <a name="remarks"></a>備註

如果[讀取位置](../standard-library/basic-streambuf-class.md)可用,則成員函數傳回[egptr](#egptr) - [gptr](#gptr)。 否則會傳回 [showmanyc](#showmanyc)。

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

## <a name="basic_streambufint_type"></a><a name="int_type"></a>basic_streambuf:int_type

將 basic_streambuf 範圍內的類型名稱與樣板參數中的其中一個類型產生關聯。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_streambufoff_type"></a><a name="off_type"></a>basic_streambuf:off_type

將 basic_streambuf 範圍內的類型名稱與樣板參數中的其中一個類型產生關聯。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_streambufoperator"></a><a name="op_eq"></a>basic_streambuf::操作員*

從另一個 `basic_streambuf` 物件指派這個物件的值。

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>參數

*對*\
用來指派值給此物件的 `basic_streambuf` 左值參考物件。

### <a name="remarks"></a>備註

受保護的成員運算符從*右側*複製控制輸入緩衝區和輸出緩衝區的指標。 它也會在 `locale object` 中儲存 `right.`[getloc()](#getloc)。 它會傳回 `*this`。

## <a name="basic_streambufoverflow"></a><a name="overflow"></a>basic_streambuf:溢出

受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>參數

*_Meta*\
要插入到緩衝區中的字元,或**traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。

### <a name="return-value"></a>傳回值

如果函式不成功，則傳回 **traits_type::eof** 或擲回例外狀況。 否則會傳回 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)。 預設行為是傳回 **traits_type::eof**。

### <a name="remarks"></a>備註

如果*\_Meta*不比較等於**traits_type::eof,** 則受保護的虛擬成員函數會嘗試將元素*\_***traits_type::to_char_type**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)( 元 ) 插入到輸出流中。 它可以透過下列各種方式來執行：

- 如果有`write position`可供使用，它可以將元素儲存在寫入位置，並遞增輸出緩衝區的下一個指標。

- 為輸出緩衝區配置新的或額外的儲存空間，即可提供寫入位置。

- 藉由將輸出緩衝區的開頭指標和下一個指標之間的部分或所有元素寫出至特定外部目的地，即可提供寫入位置。

此虛擬 overflow 函式可搭配 [sync](#sync) 和 [underflow](#underflow) 函式，定義 streambuf 衍生類別的特性。 每個衍生類別可能會以不同的方式來實作 overflow，但呼叫資料流類別的介面則相同。

`overflow` 函式最常在 put 區域已滿的情況下，由公開 `streambuf` 函式 (例如 `sputc` 和 `sputn`) 呼叫，但其他類別 (包括資料流類別) 也可以隨時呼叫 `overflow`。

此函式會取用 put 區域中介於 `pbase` 和 `pptr` 指標之間的字元，然後將 put 區域重新初始化。 `overflow` 函式也必須取用 `nCh` (如果 `nCh` 不是 `EOF`)；或者，它可能會選擇將該字元放在新的 put 區域，以供下一個呼叫取用。

取用的定義會因衍生類別而異。 例如，`filebuf` 類別會將其字元寫入至檔案，而 `strstreambuf` 類別會將這些字元保留在其緩衝區中 (如果緩衝區已指定為動態)，並擴充緩衝區以回應溢位呼叫。 此擴充可透過釋放舊緩衝區並取代為較大的新緩衝區來達成。 這些指標會視需要進行調整。

## <a name="basic_streambufpbackfail"></a><a name="pbackfail"></a>basic_streambuf::p倒失敗

受保護的虛擬成員函式，會嘗試將項目放回輸入資料流，然後將其設成目前的項目 (由下一個指標指向)。

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>參數

*_Meta*\
要插入到緩衝區中的字元,或**traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。

### <a name="return-value"></a>傳回值

如果函式不成功，則傳回 **traits_type::eof** 或擲回例外狀況。 否則，它會傳回其他值。 預設行為是傳回 **traits_type::eof**。

### <a name="remarks"></a>備註

如果*\_Meta*比較等於**traits_type::eof,** 則要回滾的元素實際上是當前元素之前流中已有的元素。 否則會以 **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*) 取代該元素。 函式可透過下列各種方式來放回項目：

- 如果有放回位置可供使用，它可以將元素儲存在放回位置，並遞減輸入緩衝區的下一個指標。

- 藉由為輸入緩衝區配置新的或額外的儲存體，即可提供放回位置。

- 針對具有通用輸入和輸出資料流的資料流緩衝區，藉由將輸出緩衝區的開頭指標和下一個指標之間的部分或所有元素寫出至特定外部目的地，即可提供放回位置。

## <a name="basic_streambufpbase"></a><a name="pbase"></a>basic_streambuf::p基地

受保護的函式，會傳回輸出緩衝區開頭的指標。

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>傳回值

輸出緩衝區開頭的指標。

## <a name="basic_streambufpbump"></a><a name="pbump"></a>basic_streambuf::p顛簸

將*計數*添加到輸出緩衝區的下一個指標的受保護函數。

```cpp
void pbump(int count);
```

### <a name="parameters"></a>參數

*計數*\
用來將寫入位置向前移動的字元數。

## <a name="basic_streambufpos_type"></a><a name="pos_type"></a>basic_streambuf::pos_類型

將 basic_streambuf 範圍內的類型名稱與樣板參數中的其中一個類型產生關聯。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_streambufpptr"></a><a name="pptr"></a>basic_streambuf::p分

受保護的函式，會傳回輸出緩衝區下個項目的指標。

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>傳回值

輸出緩衝區中下一個元素的指標。

## <a name="basic_streambufpubimbue"></a><a name="pubimbue"></a>basic_streambuf::p烏比姆布埃

設定 basic_streambuf 物件的地區設定。

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>參數

*_Loc*\
地區設定的參考。

### <a name="return-value"></a>傳回值

先前儲存在地區設定物件中的值。

### <a name="remarks"></a>備註

此成員函式會在地區設定物件中儲存 _ *Loc*，並呼叫 [imbue](#imbue)。

### <a name="example"></a>範例

如需使用 `pubimbue` 的範例，請參閱 [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue)。

## <a name="basic_streambufpubseekoff"></a><a name="pubseekoff"></a>basic_streambuf::pubseekoff

呼叫 [seekoff](#seekoff)，這是在衍生類別中遭覆寫的受保護虛擬函式。

```cpp
pos_type pubseekoff(off_type _Off,
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

返回新位置或無效的流位置([尋找](#seekoff)(=*關閉*,))。 `_Way` `_Which`

### <a name="remarks"></a>備註

相對於 *_Way*移動指標。

## <a name="basic_streambufpubseekpos"></a><a name="pubseekpos"></a>basic_streambuf::p烏布斯圖波斯

呼叫 [seekpos](#seekpos)，這是在衍生類別中遭覆寫的受保護虛擬函式，並且重設目前的指標位置。

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Sp*\
要搜尋的位置。

*_Which*\
指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

新位置或無效的資料流位置。 若要判斷資料流位置是否無效，請比較傳回值與 `pos_type(off_type(-1))`。

### <a name="remarks"></a>備註

此成員函式會傳回 [seekpos](#seekpos)(_ *Sp*, `_Which`)。

## <a name="basic_streambufpubsetbuf"></a><a name="pubsetbuf"></a>basic_streambuf::p烏布塞特布夫

呼叫 [setbuf](#setbuf)，這是在衍生類別中遭覆寫的受保護虛擬函式。

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>參數

*_Buffer*\
此具現化的 `char_type` 指標。

*計數*\
緩衝區的大小。

### <a name="return-value"></a>傳回值

傳[回 setbuf](#setbuf) `count`(, `_Buffer`。

## <a name="basic_streambufpubsync"></a><a name="pubsync"></a>basic_streambuf::p

調用[同步](#sync),派生類中重寫的受保護虛擬函數,並更新與此緩衝區關聯的外部流。

```cpp
int pubsync();
```

### <a name="return-value"></a>傳回值

如果發生故障,傳回[同步](#sync)或 -1。

## <a name="basic_streambufsbumpc"></a><a name="sbumpc"></a>basic_streambuf:斯坎奇

讀取並傳回目前項目，同時移動資料流指標。

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>傳回值

目前的元素。

### <a name="remarks"></a>備註

如果有讀取位置可供使用，此成員函式會傳回 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( <strong>\*</strong>[gptr](#gptr))，並遞增輸入緩衝區的下一個指標。 否則會傳回 [uflow](#uflow)。

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

```Input
3
```

```Output
33
51
```

## <a name="basic_streambufseekoff"></a><a name="seekoff"></a>basic_streambuf:尋求

受保護虛擬成員函式嘗試改變受控制資料流目前的位置。

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

傳回新位置或不合法的流位置`seekoff``_Way``_Which`(( =*關閉*, ) 。

### <a name="remarks"></a>備註

新位置的判斷如下：

- 如果 `_Way` == `ios_base::beg`，新位置是資料流開頭加上 _ *Off*。

- 如果 `_Way` == `ios_base::cur`，新位置是目前的資料流位置加上 _ *Off*。

- 如果 `_Way` == `ios_base::end`，新位置是資料流結尾加上 _ *Off*。

一般而言，如果 **which & ios_base::in** 為非零值，則會影響輸入資料流；如果 **which & ios_base::out** 為非零值，則會影響輸出資料流。 不過，此參數的實際用法會因衍生的資料流緩衝區而異。

如果此函式成功改變一或多個資料流位置，則會傳回產生的資料流位置或其中一個產生的資料流位置。 否則會傳回無效的資料流位置。 預設行為是傳回無效的資料流位置。

## <a name="basic_streambufseekpos"></a><a name="seekpos"></a>basic_streambuf::尋求者

受保護虛擬成員函式嘗試改變受控制資料流目前的位置。

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Sp*\
要搜尋的位置。

*_Which*\
指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

新位置或無效的資料流位置。 若要判斷資料流位置是否無效，請比較傳回值與 `pos_type(off_type(-1))`。

### <a name="remarks"></a>備註

新位置為 _ *Sp*。

一般而言，如果 **which & ios_base::in** 為非零值，則會影響輸入資料流；如果 **which & ios_base::out** 為非零值，則會影響輸出資料流。 不過，此參數的實際用法會因衍生的資料流緩衝區而異。

如果此函式成功改變一或多個資料流位置，則會傳回產生的資料流位置或其中一個產生的資料流位置。 否則會傳回無效的資料流位置 (-1)。 預設行為是傳回無效的資料流位置。

## <a name="basic_streambufsetbuf"></a><a name="setbuf"></a>basic_streambuf:塞特布夫

受保護的虛擬成員函式，會執行每個衍生資料流緩衝區的特定作業。

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>參數

*_Buffer*\
緩衝區的指標。

*計數*\
緩衝區的大小。

### <a name="return-value"></a>傳回值

預設行為是傳回 **this**。

### <a name="remarks"></a>備註

請參閱 [basic_filebuf](../standard-library/basic-filebuf-class.md)。 `setbuf` 會提供一個記憶體區域給 `streambuf` 物件使用。 緩衝區的使用方式會定義於衍生類別中。

## <a name="basic_streambufsetg"></a><a name="setg"></a>basic_streambuf:setg

受保護的函式，會在輸入緩衝區的開頭指標儲存 _ *Gbeg*，在下一個指標儲存 `_Gnext`，以及在結尾指標儲存 `_Gend`。

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>參數

*_Gbeg*\
緩衝區開頭的指標。

*_Gnext*\
緩衝區中間某個位置的指標。

*_Gend*\
緩衝區結尾的指標。

## <a name="basic_streambufsetp"></a><a name="setp"></a>basic_streambuf:setp

存儲 *_Pbeg*在輸出緩衝區的末尾指標中的*受保護*函數,_Pend。

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>參數

*_Pbeg*\
緩衝區開頭的指標。

*_Pend*\
緩衝區結尾的指標。

## <a name="basic_streambufsgetc"></a><a name="sgetc"></a>basic_streambuf:斯格拉茨

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

## <a name="basic_streambufsgetn"></a><a name="sgetn"></a>basic_streambuf:斯根

從輸入緩衝區中提取最多*計數*字元,並將它們存儲在提供的緩衝區*ptr*中。

此方法有賴於呼叫者檢查傳遞的值是否正確，因此可能不安全。

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>參數

*Ptr*\
要包含所擷取字元的緩衝區。

*計數*\
要讀取的元素數目。

### <a name="return-value"></a>傳回值

所讀取的元素數目。 如需詳細資訊，請參閱 [streamsize](../standard-library/ios-typedefs.md#streamsize)。

### <a name="remarks"></a>備註

成員函數返回[xsgetn](#xsgetn) `ptr` `count`(, 。

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

## <a name="basic_streambufshowmanyc"></a><a name="showmanyc"></a>basic_streambuf::秀多

受保護的虛擬成員函式，會傳回可從輸入資料流擷取的字元數計數，並確保程式不會無限地等候。

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>傳回值

預設行為是傳回零。

## <a name="basic_streambufsnextc"></a><a name="snextc"></a>basic_streambuf:下一頁

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

```Input
aa
```

```Output
aa97
```

## <a name="basic_streambufsputbackc"></a><a name="sputbackc"></a>basic_streambuf:斯普特貝克

將 char_type 放入資料流。

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>參數

*_Ch*\
字元。

### <a name="return-value"></a>傳回值

傳回字元或失敗。

### <a name="remarks"></a>備註

如果回退位置可用,並且 *_Ch*與存儲在該位置的字元進行比較,則成員函數將下一個指標用於輸入緩衝區,並返回**traits_type::to_int_type**[to_int_type](../standard-library/char-traits-struct.md#to_int_type) `_Ch` ()。 否則,它將返回[pbackfail](#pbackfail)()。 `_Ch`

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

## <a name="basic_streambufsputc"></a><a name="sputc"></a>basic_streambuf:斯普特

將字元放入資料流。

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>參數

*_Ch*\
字元。

### <a name="return-value"></a>傳回值

如果成功，則傳回字元。

### <a name="remarks"></a>備註

如果`write position`可用,則成員函數將 *_Ch*儲存在寫入位置,為輸出緩衝區增加下一個指標,並返回**traits_type::to_int_type**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)()。 `_Ch` 否則,它將返回[溢出](#overflow)()。 `_Ch`

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

## <a name="basic_streambufsputn"></a><a name="sputn"></a>basic_streambuf:斯普滕

將字元字串放入資料流。

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>參數

*Ptr*\
字元字串。

*計數*\
字元計數。

### <a name="return-value"></a>傳回值

實際插入資料流的字元數。

### <a name="remarks"></a>備註

成員函數傳[回 xsputn](#xsputn) `ptr`(, `count`。 如需詳細資訊，請參閱此成員的＜備註＞一節。

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

## <a name="basic_streambufstossc"></a><a name="stossc"></a>basic_streambuf:斯托斯科

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

## <a name="basic_streambufsungetc"></a><a name="sungetc"></a>basic_streambuf:桑奇

從資料流取得字元。

```cpp
int_type sungetc();
```

### <a name="return-value"></a>傳回值

傳回字元或失敗。

### <a name="remarks"></a>備註

如果回退位置可用,則成員函數將下一個指標用於輸入緩衝區`traits_type::`並返回[to_int_type](../standard-library/char-traits-struct.md#to_int_type) `*` [(gptr](#gptr))。 不過，不一定能夠判斷所讀取的最後一個字元，以便在目前緩衝區的狀態中擷取此字元。 如果是此情況，則函式會傳回 [pbackfail](#pbackfail)。 若要避免發生這種情況，請追蹤要放回的字元並呼叫 `sputbackc(ch)`；只要您不是在資料流開頭呼叫，而且未嘗試放回一個以上的字元，此作業就不會失敗。

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

## <a name="basic_streambufswap"></a><a name="swap"></a>basic_streambuf::交換

用此物件的值交換所提供的 `basic_streambuf` 物件中的值。

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*對*|用來交換值的 `basic_streambuf` 左值參考物件。|

### <a name="remarks"></a>備註

受保護的成員函數與*右側*`input buffer`控制與的所有指標交換`output buffer`。 它也會將 `right.`[getloc()](#getloc) 與 `locale` 物件交換。

## <a name="basic_streambufsync"></a><a name="sync"></a>basic_streambuf:同步

受保護的虛擬函式，會嘗試與任何相關聯的外部資料流同步處理控制資料流。

```cpp
virtual int sync();
```

### <a name="return-value"></a>傳回值

如果函式不成功，則傳回 -1。 預設行為是傳回零。

### <a name="remarks"></a>備註

`sync` 需要將輸出緩衝區的開頭指標和下一個指標之間的任何元素寫出。 它不需要將輸入緩衝區的下一個指標和結尾指標之間的任何元素放回。

## <a name="basic_streambuftraits_type"></a><a name="traits_type"></a>basic_streambuf:traits_type

將類型名稱與 **Tr** 範本參數建立關聯。

```cpp
typedef Tr traits_type;
```

## <a name="basic_streambufuflow"></a><a name="uflow"></a>basic_streambuf::流

受保護的虛擬函式，會從輸入資料流擷取目前的項目。

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>傳回值

目前的元素。

### <a name="remarks"></a>備註

此受保護的虛擬成員函式會嘗試從輸入資料流擷取目前的元素 **ch**，然後從目前的資料流位置前移，並傳回此元素作為 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**)。 它可以透過下列各種方式來執行：

- 如果有讀取位置可供使用，它會接受 **ch** 作為儲存在讀取位置中的元素，並前進到輸入緩衝區的下一個指標。

- 它可以直接從特定外部來源讀取元素，並提供此元素作為 **ch** 值。

- 針對具有通用輸入和輸出資料流的資料流緩衝區，藉由將輸出緩衝區的開頭指標和下一個指標之間的部分或所有元素寫出至特定外部目的地，即可提供讀取位置。 或者，它可以為輸入緩衝區配置新的或額外的儲存體。 此函式接著會從特定外部來源讀入一或多個元素。

如果函數無法成功,它將返回**traits_type:eof**[eof](../standard-library/char-traits-struct.md#eof),或引發異常。 否則，它會傳回輸入資料流中目前的元素 `ch` (已如上所述進行轉換)，並前進到輸入緩衝區的下一個指標。 預設行為是呼叫 [underflow](#underflow)；如果該函式傳回 **traits_type::eof**，則傳回 **traits_type::eof**。 否則，此函式會傳回輸入資料流中目前的元素 **ch** (已如上所述進行轉換)，並前進到輸入緩衝區的下一個指標。

## <a name="basic_streambufunderflow"></a><a name="underflow"></a>basic _ streambuf :

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

如果函數無法成功,它將返回`traits_type::` [eof](../standard-library/char-traits-struct.md#eof)`()`或引發異常。 否則會傳回輸入資料流中目前的元素 (已如上所述進行轉換)。 預設行為是傳回 `traits_type::eof()`。

此虛擬 `underflow` 函式可搭配 [sync](#sync) 和 [overflow](#overflow) 函式，定義 `streambuf` 衍生類別的特性。 每個衍生類別可能會以不同的方式來實作 `underflow`，但呼叫資料流類別的介面則相同。

`underflow` 函式最常在 get 區域為空白的情況下，由公開 `streambuf` 函式 (例如 [sgetc](#sgetc) 和 [sgetn](#sgetn)) 呼叫，但其他類別 (包括資料流類別) 也可以隨時呼叫 `underflow`。

`underflow` 函式會將來自輸入來源的字元提供給 get 區域。 如果 get 區域包含字元，`underflow` 會傳回第一個字元。 如果 get 區域為空白，則會填滿 get 區域，並傳回留在 get 區域中的下一個字元。 如果沒有更多字元可供使用，則 `underflow` 會傳回 `EOF`，並將 get 區域保留空白。

在 `strstreambuf` 類別中，`underflow` 會調整 [egptr](#egptr) 指標，以存取藉由呼叫 `overflow` 所動態配置的儲存體。

## <a name="basic_streambufxsgetn"></a><a name="xsgetn"></a>basic_streambuf:xsgetn

要從輸入資料流擷取元素的受保護虛擬函式。

此方法有賴於呼叫者檢查傳遞的值是否正確，因此可能不安全。

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>參數

*Ptr*\
要包含所擷取字元的緩衝區。

*計數*\
要擷取的元素數目。

### <a name="return-value"></a>傳回值

所擷取的元素數目。

### <a name="remarks"></a>備註

受保護的虛擬成員函數提取起來從輸入流*中計算*元素,就像重複調用[sbumpc](#sbumpc)一樣,並將它們存儲在從*ptr*開始的陣列中。 它會傳回實際擷取的元素數目。

## <a name="basic_streambufxsputn"></a><a name="xsputn"></a>basic_streambuf:xsputn

要將元素插入輸出資料流的受保護虛擬函式。

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>參數

*Ptr*\
要插入的元素指標。

*計數*\
要插入的元素數目。

### <a name="return-value"></a>傳回值

實際插入資料流的元素數目。

### <a name="remarks"></a>備註

受保護的虛擬成員函數向上插入*以將元素計數*到輸出流中,就像從*ptr*開始的陣列中重複呼叫[sputc](#sputc)一樣。 寫入所有*計數*字元後,或`sputc( count)`調用`traits::eof()`將返回 后,將字元插入輸出流將停止。 它會傳回實際插入的元素數目。

## <a name="see-also"></a>另請參閱

[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
