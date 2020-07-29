---
title: time_put 類別
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
ms.openlocfilehash: 4f7b609493e16d3d1c0a9ab6274ed6f5bfd7b033
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212107"
---
# <a name="time_put-class"></a>time_put 類別

類別樣板描述可以做為地區設定 facet 的物件，以控制時間值轉換為類型的序列 `CharType` 。

## <a name="syntax"></a>語法

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>參數

*CharType*\
用於程式內部字元編碼的類型。

*OutputIterator*\
時間 put 函式將其輸出寫入其中的迭代器類型。

## <a name="remarks"></a>備註

如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[time_put](#time_put)|`time_put` 類型物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|
|[iter_type](#iter_type)|描述輸出迭代器的類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[do_put](#do_put)|虛擬函式，會輸出日期和時間資訊做為 `CharType` 的序列。|
|[提出](#put)|輸出日期和時間資訊做為 `CharType` 的序列。|

## <a name="requirements"></a>需求

**標頭：**\<locale>

**命名空間：** std

## <a name="time_putchar_type"></a><a name="char_type"></a>time_put：： char_type

類型，用來描述由地區設定使用的字元。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `CharType` 的同義字。

## <a name="time_putdo_put"></a><a name="do_put"></a>time_put：:d o_put

虛擬函式，會輸出日期和時間資訊做為 `CharType` 的序列。

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>參數

*下一個*\
輸出迭代器，其中的字元序列代表插入的日期與時間。

*_Iosbase*\
未使用的。

*_Pt*\
輸出的日期和時間資訊。

*_Fmt*\
輸出的格式。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

*_Mod*\
格式修飾詞。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

### <a name="return-value"></a>傳回值

插入最後一個元素之後第一個位置的迭代器。

### <a name="remarks"></a>備註

虛擬受保護的成員函式會 `next` 從類型的物件中儲存的時間值開始產生順序元素 \* `_Pt` `tm` 。 此函式會傳回迭代器，此迭代器指定在所產生的輸出後下一個要插入元素的位置。

輸出是由所使用的相同規則所產生 `strftime` ，以及 *_Pt*的最後一個引數，以便將一系列的 **`char`** 元素產生到陣列中。 每個這類 **`char`** 元素都會被假設為對應至類型的對等元素 `CharType` ，方法是使用簡單的一對一對應。 如果 *_Mod*等於零，有效的格式為 "% F"，其中的 F 是由 *_Fmt*所取代。 否則，有效的格式為 "% MF"，其中 M 會取代為 *_Mod*。

### <a name="example"></a>範例

請參閱 [put](#put) 的範例，其會呼叫 `do_put`。

## <a name="time_putiter_type"></a><a name="iter_type"></a>time_put：： iter_type

描述輸出迭代器的類型。

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `OutputIterator` 的同義字。

## <a name="time_putput"></a><a name="put"></a>time_put：:p 的

輸出日期和時間資訊做為 `CharType` 的序列。

```cpp
iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;

iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>參數

*下一個*\
輸出迭代器，其中的字元序列代表插入的日期與時間。

*_Iosbase*\
未使用的。

*_Fill*\
用於間距的類型字元 `CharType` 。

*_Pt*\
輸出的日期和時間資訊。

*_Fmt*\
輸出的格式。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

*_Mod*\
格式修飾詞。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

*頭*\
輸出的格化式字串開頭。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

*次*\
輸出的格化式字串結尾。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

### <a name="return-value"></a>傳回值

插入最後一個元素之後第一個位置的迭代器。

### <a name="remarks"></a>備註

第一個成員函式會傳回[do_put](#do_put)（ `next` 、 `_Iosbase` 、 `_Fill` 、 `_Pt` 、 `_Fmt` 、 `_Mod` ）。 第二個成員函式會複製到 \* `next` + + 間隔 [，）中的任何元素， `first` `last` 而不是百分比（%）。 若為百分比，後面接著間隔 [，）中的字元*C* ，則函式會 `first` 改為 `last` 評估 `next`  =  `do_put` （ `next` 、 `_Iosbase` 、 `_Fill` 、 `_Pt` 、 *C*、0）並略過*C*。不過，如果*C*是來自 set EOQ # 的限定詞字元，後面接著 `C2` 間隔 [，）中的字元，則函式會 `first` `last` 改為評估 `next`  =  `do_put` （ `next` 、 `_Iosbase` 、 `_Fill` 、 `_Pt` 、 `C2` 、 *C*）並略過 `C2` 。

### <a name="example"></a>範例

```cpp
// time_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   t.tm_hour = 5;
   t.tm_min = 30;
   t.tm_sec = 40;
   t.tm_year = 00;
   t.tm_mday = 4;
   t.tm_mon = 6;

   pszPutI.imbue( loc );
   char *pattern = "x: %X %x";
   use_facet <time_put <char> >
   (loc).put(basic_ostream<char>::_Iter(pszPutI.rdbuf( )),
          pszPutI, ' ', &t, pattern, pattern+strlen(pattern));

      cout << "num_put( ) = " << pszPutI.rdbuf( )->str( ) << endl;

      char strftimebuf[255];
      strftime(&strftimebuf[0], 255, pattern, &t);
      cout << "strftime( ) = " << &strftimebuf[0] << endl;
}
```

```Output
num_put( ) = x: 05:30:40 07/04/00
strftime( ) = x: 05:30:40 07/04/00
```

## <a name="time_puttime_put"></a><a name="time_put"></a>time_put：： time_put

`time_put` 類型物件的建構函式。

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>參數

*_Refs*\
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

*_Refs*參數和其重要性的可能值為：

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- \>1：未定義這些值。

此函式會使用[locale：： facet](../standard-library/locale-class.md#facet_class)（*_Refs*）初始化其基底物件。

## <a name="see-also"></a>另請參閱

[\<locale>](../standard-library/locale.md)\
[time_base 類別](../standard-library/time-base-class.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
