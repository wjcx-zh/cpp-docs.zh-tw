---
title: time_get 類別
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get
- locale/std::time_get::char_type
- locale/std::time_get::iter_type
- locale/std::time_get::date_order
- locale/std::time_get::do_date_order
- locale/std::time_get::do_get
- locale/std::time_get::do_get_date
- locale/std::time_get::do_get_monthname
- locale/std::time_get::do_get_time
- locale/std::time_get::do_get_weekday
- locale/std::time_get::do_get_year
- locale/std::time_get::get
- locale/std::time_get::get_date
- locale/std::time_get::get_monthname
- locale/std::time_get::get_time
- locale/std::time_get::get_weekday
- locale/std::time_get::get_year
helpviewer_keywords:
- std::time_get [C++]
- std::time_get [C++], char_type
- std::time_get [C++], iter_type
- std::time_get [C++], date_order
- std::time_get [C++], do_date_order
- std::time_get [C++], do_get
- std::time_get [C++], do_get_date
- std::time_get [C++], do_get_monthname
- std::time_get [C++], do_get_time
- std::time_get [C++], do_get_weekday
- std::time_get [C++], do_get_year
- std::time_get [C++], get
- std::time_get [C++], get_date
- std::time_get [C++], get_monthname
- std::time_get [C++], get_time
- std::time_get [C++], get_weekday
- std::time_get [C++], get_year
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
ms.openlocfilehash: 9aebdaffc8bf3754bdbda08247f72ae08475711f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368043"
---
# <a name="time_get-class"></a>time_get 類別

類範本描述一個物件,該物件可用作區域設置,用於控制類型`CharType`到時間值序列的轉換。

## <a name="syntax"></a>語法

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>參數

*字元類型*\
用於程式內部字元編碼的類型。

*輸入反覆運算器*\
從中讀取時間值的迭代器。

## <a name="remarks"></a>備註

如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[time_get](#time_get)|`time_get` 類型物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|
|[iter_type](#iter_type)|描述輸入迭代器的類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[date_order](#date_order)|傳回 facet 使用的日期順序。|
|[do_date_order](#do_date_order)|受保護的虛擬成員函式，呼叫以傳回 facet 所使用的日期順序。|
|[do_get](#do_get)|讀取和轉換字元資料為時間值。|
|[do_get_date](#do_get_date)|受保護的虛擬成員函式，呼叫以將字串剖析為由 `x` 的 `strftime` 規範所產生的日期。|
|[do_get_monthname](#do_get_monthname)|受保護的虛擬成員函式，呼叫以將字串剖析為月份名稱。|
|[do_get_time](#do_get_time)|受保護的虛擬成員函式，呼叫以將字串剖析為由 `X` 的 `strftime` 規範所產生的日期。|
|[do_get_weekday](#do_get_weekday)|受保護的虛擬成員函式，呼叫以將字串剖析為週間日名稱。|
|[do_get_year](#do_get_year)|受保護的虛擬成員函式，呼叫以將字串剖析為年份名稱。|
|[get](#get)|從字元資料來源讀取，並將該資料轉換為時間結構儲存的時間。|
|[get_date](#get_date)|將字串剖析為 `x` 的 `strftime` 規範所產生的日期。|
|[get_monthname](#get_monthname)|將字串剖析為月份名稱。|
|[get_time](#get_time)|將字串剖析為 `X` 的 `strftime` 規範所產生的日期。|
|[get_weekday](#get_weekday)|將字串剖析為週間日名稱。|
|[get_year](#get_year)|將字串剖析為年份名稱。|

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="time_getchar_type"></a><a name="char_type"></a>time_get::char_type

類型，用來描述由地區設定使用的字元。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 **CharType** 的同義字。

## <a name="time_getdate_order"></a><a name="date_order"></a>time_get::d

傳回 facet 使用的日期順序。

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>傳回值

facet 使用的日期順序。

### <a name="remarks"></a>備註

成員函式傳回 [do_date_order](#do_date_order)。

### <a name="example"></a>範例

```cpp
// time_get_date_order.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
void po( char *p )
{
   locale loc( p );

   time_get <char>::dateorder order = use_facet <time_get <char> >( loc ).date_order ( );
   cout << loc.name( );
   switch (order){
      case time_base::dmy: cout << "(day, month, year)" << endl;
      break;
      case time_base::mdy: cout << "(month, day, year)" << endl;
      break;
      case time_base::ydm: cout << "(year, day, month)" << endl;
      break;
      case time_base::ymd: cout << "(year, month, day)"<< endl;
      break;
      case time_base::no_order: cout << "(no_order)"<< endl;
      break;
   }
}

int main( )
{
   po( "C" );
   po( "german" );
   po( "English_Britain" );
}
```

```Output
C(month, day, year)
German_Germany.1252(day, month, year)
English_United Kingdom.1252(day, month, year)
```

## <a name="time_getdo_date_order"></a><a name="do_date_order"></a>time_get::d日期\訂單

受保護的虛擬成員函式，呼叫以傳回 facet 所使用的日期順序。

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>傳回值

facet 使用的日期順序。

### <a name="remarks"></a>備註

受保護的虛擬成員函式會傳回類型**time_base::dateorder** 的值，用來描述透過 [do_get_date](#do_get_date) 比對的日期元件順序。 在此實作中，該值為 **time_base::mdy**，對應到「12 月 2 日，1979 年」格式的日期。

### <a name="example"></a>範例

請參閱 [date_order](#date_order) 的範例，其會呼叫 `do_date_order`。

## <a name="time_getdo_get"></a><a name="do_get"></a>time_get::do_get

讀取和轉換字元資料為時間值。 接受一個轉換規範和修飾詞。

```cpp
virtual iter_type
    do_get(
iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，表示要轉換的序列開頭。

*最後*\
輸入迭代器，表示序列的結尾。

*約斯基地*\
資料流物件。

*狀態*\
iosbase 中的欄位,其中設置適當的位掩碼元素以指示錯誤。

*ptm*\
要儲存時間之時間結構的指標。

*Fmt*\
轉換規範字元。

*國防部*\
選擇性修飾詞字元。

### <a name="return-value"></a>傳回值

傳回迭代器，該迭代器指定第一個未轉換的項目。 轉換失敗設定`ios_base::failbit``state`並*首先*傳回 。

### <a name="remarks"></a>備註

虛擬成員函數轉換並跳過範圍內的一個或多個輸入元素`first`*`last`, 以確定存儲在的一個或`*pt`多個成員中的值。 轉換失敗設定`ios_base::failbit``state`並*首先*傳回 。 否則，函式會傳回指定第一個未轉換項目的迭代器。

轉換規範包括：

`'a'` 或 `'A'` -- 行為與 [time_get::get_weekday](#get_weekday) 相同。

`'b'`、`'B'` 或 `'h'` -- 行為與 [time_get::get_monthname](#get_monthname) 相同。

`'c'` - 行為與 `"%b %d %H : %M : %S %Y"` 相同。

`'C'` - 將範圍 [0, 99] 中的十進位輸入欄位轉換成值 `val`，並將 `val * 100 - 1900` 儲存在 `pt-&tm_year` 中。

`'d'` 或 `'e'` - 轉換範圍 [1, 31] 中的十進位輸入欄位，並將其值儲存在 `pt-&tm_mday` 中。

`'D'` - 行為與 `"%m / %d / %y"` 相同。

`'H'` - 轉換範圍 [0, 23] 中的十進位輸入欄位，並將其值儲存在 `pt-&tm_hour` 中。

`'I'` - 轉換範圍 [0, 11] 中的十進位輸入欄位，並將其值儲存在 `pt-&tm_hour` 中。

`'j'` - 轉換範圍 [1, 366] 中的十進位輸入欄位，並將其值儲存在 `pt-&tm_yday` 中。

`'m'` - 將範圍 [1, 12] 中的十進位輸入欄位轉換成值 `val`，並將 `val - 1` 及其值儲存在 `pt-&tm_mon` 中。

`'M'` - 轉換範圍 [0, 59] 中的十進位輸入欄位，並將其值儲存在 `pt-&tm_min` 中。

`'n'` 或 `'t'` - 行為與 `" "` 相同。

`'p'` - 將 "AM" 或 "am" 轉換成零、"PM" 或 "PM" 轉換成 12，並將這個值加入 `pt-&tm_hour`。

`'r'` - 行為與 `"%I : %M : %S %p"` 相同。

`'R'` - 行為與 `"%H %M"` 相同。

`'S'` - 轉換範圍 [0, 59] 中的十進位輸入欄位，並將其值儲存在 `pt-&tm_sec` 中。

`'T'` 或 `'X'` - 行為與 `"%H : %M : S"` 相同。

`'U'` - 轉換範圍 [0, 53] 中的十進位輸入欄位，並將其值儲存在 `pt-&tm_yday` 中。

`'w'` - 轉換範圍 [0, 6] 中的十進位輸入欄位，並將其值儲存在 `pt-&tm_wday` 中。

`'W'` - 轉換範圍 [0, 53] 中的十進位輸入欄位，並將其值儲存在 `pt-&tm_yday` 中。

`'x'` - 行為與 `"%d / %m / %y"` 相同。

`'y'` - 將範圍 [0, 99] 中的十進位輸入欄位轉換成值 `val`，並將 `val < 69  val + 100 : val` 儲存在 `pt-&tm_year` 中。

`'Y'` -- 行為與 [time_get::get_year](#get_year) 相同。

其他任何轉換規範會在 `state` 中設定 `ios_base::failbit` 並傳回。 在這個實作中，所有修飾詞都沒有作用。

## <a name="time_getdo_get_date"></a><a name="do_get_date"></a>time_get::d_取日期

受保護的虛擬成員函式，呼叫以將字串剖析為由 `strftime` 的 *x* 規範所產生的日期。

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*約斯基地*\
格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。

*狀態*\
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*ptm*\
指向日期資訊儲存位置的指標。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

虛擬的受保護成員函式會嘗試比對序列 [ `first`, `last`) 中從 first 開始的一系列元素，直到它辨識出完整、非空白的日期輸入欄位為止。 如果成功,它將此字段轉換為其等效值,如元件**\_tm::tm**`ptm->tm_day`mon、tm::tm`ptm->tm_year` ** \_day**和**\_tm::tm 年**,並將結果分別儲存在`ptm->tm_mon`中 。 和 。 它會傳回迭代器，此迭代器指定日期輸入欄位後的第一個元素。 否則,函數將設定`iosbase::failbit`*state*狀態 。 它會傳回迭代器，此迭代器指定有效日期輸入欄位之任何前置詞後的第一個元素。 在這兩種情況下,如果返回值等於最後一*個*,則函`ios_base::eofbit`數 將*設定*狀態 。

日期輸入欄位的格式取決於地區設定。 對於預設地區設定，日期輸入欄位的格式為 MMM DD，YYYY，其中︰

- MMM 是透過呼叫 [get_monthname](#get_monthname) 來比對，可提供月份。

- DD 是一連串十進位數字，其對應數值必須在範圍 [1, 31] 內，提供月份日期。

- YYYY 是透過呼叫 [get_year](#get_year) 來比對，可提供年份。

常值的空格和逗號都必須符合輸入序列中的對應元素。

### <a name="example"></a>範例

請參閱 [get_date](#get_date) 的範例，其會呼叫 `do_get_date`。

## <a name="time_getdo_get_monthname"></a><a name="do_get_monthname"></a>time_get::do_get_月名

受保護的虛擬成員函式，呼叫以將字串剖析為月份名稱。

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*約斯基地*\
未使用的。

*狀態*\
輸出餐參數，會根據作業是否成功，將適當的位元遮罩元素設定為資料流狀態。

*ptm*\
指向月份資訊儲存位置的指標。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

虛擬的受保護成員函式會嘗試比對序列 [ `first`, `last`) 中從 first 開始的一系列元素，直到它辨識出完整、非空白的月份輸入欄位為止。 如果成功,它將此字段轉換為其等效值為元件**tm::tm\_mon,** 並將結果存儲在`ptm->tm_mon`中。 它會傳回迭代器，此迭代器指定月份輸入欄位後的第一個元素。 否則,函數將設定`ios_base::failbit`*state*狀態 。 它會傳回迭代器，此迭代器指定有效月份輸入欄位之任何前置詞後的第一個元素。 在這兩種情況下,如果返回值等於最後一*個*,則函`ios_base::eofbit`數 將*設定*狀態 。

月份輸入欄位是一個序列，符合一組最長的地區設定特定順序，例如 1 月、一月、2 月、二月，依此類推。 轉換值是自一月起的月份數。

### <a name="example"></a>範例

請參閱 [get_monthname](#get_monthname) 的範例，其會呼叫 `do_get_monthname`。

## <a name="time_getdo_get_time"></a><a name="do_get_time"></a>time_get::d

被呼叫以解析字串作為*X*規範器生成的日期`strftime`的 受保護虛擬成員函數。

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*約斯基地*\
未使用的。

*狀態*\
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*ptm*\
指向日期資訊儲存位置的指標。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

虛擬的受保護成員函式會嘗試比對序列 [ `first`, `last`) 中從 first 開始的一系列元素，直到它辨識出完整、非空白的時間輸入欄位為止。 如果成功,它將此欄位轉換為其等效值`tm::tm_hour`,`tm::tm_min`作為元件、和`tm::tm_sec`,並將結果分別儲存在`ptm->tm_hour`中`ptm->tm_min`,`ptm->tm_sec`和中。 它會傳回迭代器，此迭代器指定時間輸入欄位後的第一個元素。 否則,函數將設定`ios_base::failbit`*state*狀態 。 它會傳回迭代器，此迭代器指定有效時間輸入欄位之任何前置詞後的第一個元素。 在這兩種情況下,如果返回值等於最後一*個*,則函`ios_base::eofbit`數 將*設定*狀態 。

在此實作中，時間輸入欄位的格式為 HH:MM:SS，其中︰

- HH 是一連串十進位數字，其對應數值必須在範圍 [0, 24) 內，提供當天的小時數。

- MM 是一連串十進位數字，其對應數值必須在範圍 [0, 60) 內，提供小時內的分鐘數。

- SS 是一連串十進位數字，其對應數值必須在範圍 [0, 60) 內，提供分鐘內的秒數。

常值的冒號必須符合輸入序列中的對應元素。

### <a name="example"></a>範例

請參閱 [get_time](#get_time) 的範例，其會呼叫 `do_get_time`。

## <a name="time_getdo_get_weekday"></a><a name="do_get_weekday"></a>time_get::do_get_工作日

受保護的虛擬成員函式，呼叫以將字串剖析為週間日名稱。

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*約斯基地*\
格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。

*狀態*\
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*ptm*\
指向工作日資訊儲存位置的指標。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

虛擬受保護成員函數嘗試符合序列*first*`first`# 開頭的順序元素`last`, 直到它識別完整的非空工作日輸入欄位。 如果成功,它將此字段轉換為其等效值為元件`ptm->tm_wday`**tm::tm\_wday,** 並將結果存儲在 中。 它會傳回迭代器，此迭代器指定工作日輸入欄位後的第一個元素。 否則,函數將設定`ios_base::failbit`*state*狀態 。 它會傳回迭代器，此迭代器指定有效工作日輸入欄位之任何前置詞後的第一個元素。 在這兩種情況下,如果返回值等於最後一*個*,則函`ios_base::eofbit`數 將*設定*狀態 。

工作日輸入欄位是一個序列，符合一組最長的地區設定特定順序，例如日、星期日、一、星期一，依此類推。 轉換值是自星期日起的天數。

### <a name="example"></a>範例

請參閱 [get_weekday](#get_weekday) 的範例，其會呼叫 `do_get_weekday`。

## <a name="time_getdo_get_year"></a><a name="do_get_year"></a>time_get::d年

受保護的虛擬成員函式，呼叫以將字串剖析為年份名稱。

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*約斯基地*\
格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。

*狀態*\
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*ptm*\
指向年份資訊儲存位置的指標。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

虛擬受保護成員函數嘗試匹配序列開頭的順序元素,*first*`first``last`直到它識別了完整的非空年份輸入欄位。 如果成功,它將此欄位轉換為其等效值為元件**tm::tm\_年**,並將結果存儲在`ptm->tm_year`中。 它會傳回迭代器，此迭代器指定年份輸入欄位後的第一個元素。 否則,函數將設定`ios_base::failbit`*state*狀態 。 它會傳回迭代器，此迭代器指定有效年份輸入欄位之任何前置詞後的第一個元素。 在這兩種情況下,如果返回值等於最後一*個*,則函`ios_base::eofbit`數 將*設定*狀態 。

年份輸入欄位是一連串十進位數字，其對應數值必須在範圍 [1900, 2036) 內。 儲存的值是這個值減去 1900。 在此實作中，範圍內的值 [69, 136) 代表年份範圍 [1969, 2036)。 範圍內的值也允許 [0, 69)，但表示的年份範圍可能是 [1900, 1969) 或 [2000, 2069)，取決於特定轉譯環境。

### <a name="example"></a>範例

請參閱 [get_year](#get_year) 的範例，其會呼叫 `do_get_year`。

## <a name="time_getget"></a><a name="get"></a>time_get:取得

從字元資料來源讀取，並將該資料轉換為時間結構儲存的時間。 第一個函式可接受一個轉換規範和修飾詞，而第二個可接受數個。

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char_type* fmt_first,
    char_type* fmt_last) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，表示要轉換的序列是否開始。

*最後*\
輸入迭代器，表示要轉換之序列的結束。

*約斯基地*\
資料流。

*狀態*\
已針對此資料流狀態設定適當位元遮罩項目，藉此指出錯誤。

*ptm*\
要儲存時間之時間結構的指標。

*Fmt*\
轉換規範字元。

*國防部*\
選擇性修飾詞字元。

*fmt_first*\
格式指示詞開始位置的點。

*fmt_last*\
格式指示詞結尾的點。

### <a name="return-value"></a>傳回值

在指定時間結構的資料之後,將反覆發代器傳回到第一`*ptm`個字元 。

### <a name="remarks"></a>備註

第一個成員函式會傳回 `do_get(first, last, iosbase, state, ptm, fmt, mod)`。

第二個成員函式呼叫 `do_get`，且由 `[fmt_first, fmt_last)` 分隔的格式控制。 它會將格式視為欄位序列，其中每個欄位決定 `[first, last)` 分隔的零或多個輸入項目轉換。 它會傳回迭代器，指定第一個未轉換的項目。 有三種欄位：

百分比(%)在格式中,後面是集 [EOQ] 中的可選修飾器*mod,* 後跟轉換指定器*fmt,**首先*替換為返回`do_get(first, last, iosbase, state, ptm, fmt, mod)`的值。 轉換失敗集`ios_base::failbit`*狀態*並返回。

此格式中空白項目會略過零個或多個空白項目。

此格式中任何其他項目必須符合下一個略過的輸入項目。 匹配失敗設定`ios_base::failbit`*狀態*並返回。

## <a name="time_getget_date"></a><a name="get_date"></a>time_get::get_date

將字串剖析為 `strftime` 的 *x* 規範所產生的日期。

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*約斯基地*\
格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。

*狀態*\
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*ptm*\
指向日期資訊儲存位置的指標。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

成員函數傳[回](#do_get_date)`first`do_get_date `last` `iosbase` `state` `ptm`(、 、 、 、

請注意，月份的計算是從 0 到 11。

### <a name="example"></a>範例

```cpp
// time_get_get_date.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset(&t, 0, sizeof(struct tm));

   pszGetF << "July 4, 2000";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get<char> >
   (loc).get_date(basic_istream<char>::_Iter(pszGetF.rdbuf( ) ),
            basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if ( st & ios_base::failbit )
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(July 4, 2000) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 4
tm_mon: 6
tm_year: 100
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="time_getget_monthname"></a><a name="get_monthname"></a>time_get:get_monthname

將字串剖析為月份名稱。

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*約斯基地*\
未使用的。

*狀態*\
輸出餐參數，會根據作業是否成功，將適當的位元遮罩元素設定為資料流狀態。

*ptm*\
指向月份資訊儲存位置的指標。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

成員函數傳[do_get_monthname](#do_get_monthname)`first`回 do_get_monthname `last` `iosbase` `state` `ptm`(、 、 、 、

### <a name="example"></a>範例

```cpp
// time_get_get_monthname.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "juillet";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get <char> >
   (loc).get_monthname(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
              basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(juillet) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 0
tm_mon: 6
tm_year: 0
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="time_getget_time"></a><a name="get_time"></a>time_get:get_time

將字串解析為 X*規範器*`strftime`生成的日期。

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*約斯基地*\
未使用的。

*狀態*\
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*ptm*\
指向日期資訊儲存位置的指標。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

成員函數傳[do_get_time](#do_get_time)`first`回 do_get_time `last` `iosbase` `state` `ptm`(、 、 、 、

### <a name="example"></a>範例

```cpp
// time_get_get_time.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "11:13:20";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get <char> >
      (loc).get_time(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << endl;
}
```

```Output
time_get::get_time(11:13:20) =
tm_sec: 20
tm_min: 13
tm_hour: 11
```

## <a name="time_getget_weekday"></a><a name="get_weekday"></a>time_get::get_weekday

將字串剖析為週間日名稱。

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*約斯基地*\
格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。

*狀態*\
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*ptm*\
指向工作日資訊儲存位置的指標。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

成員函數傳[do_get_weekday](#do_get_weekday)`first`回 do_get_weekday `last` `iosbase` `state` `ptm`(、 、 、 、

### <a name="example"></a>範例

```cpp
// time_get_get_weekday.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "mercredi";
   pszGetF.imbue(loc);
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_weekday(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_wday: " << t.tm_wday
      << endl;
}
```

```Output
time_get::get_time(mercredi) =
tm_wday: 3
```

## <a name="time_getget_year"></a><a name="get_year"></a>time_get:get_year

將字串剖析為年份名稱。

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*約斯基地*\
格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。

*狀態*\
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*ptm*\
指向年份資訊儲存位置的指標。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

成員函數傳[do_get_year](#do_get_year)`first`回 do_get_year `last` `iosbase` `state` `ptm`(、 、 、 、

### <a name="example"></a>範例

```cpp
// time_get_get_year.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "1928";

   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_year(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_year: " << t.tm_year
      << endl;
}
```

```Output
time_get::get_year(1928) =
tm_year: 28
```

## <a name="time_getiter_type"></a><a name="iter_type"></a>time_get::iter_type

描述輸入迭代器的類型。

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 **InputIterator** 同義。

## <a name="time_gettime_get"></a><a name="time_get"></a>time_get:time_get

`time_get` 類型物件的建構函式。

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>參數

*裁判*\
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

*refs*參數的可能值及其顯著性為:

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- \>1: 未定義這些值。

無法提供任何直接範例，因為解構函式受到保護。

建構函式用區域設定初始化其基本物件 **::**[分面](../standard-library/locale-class.md#facet_class)(`refs`。

## <a name="see-also"></a>另請參閱

[\<區域設定>](../standard-library/locale.md)\
[time_base類](../standard-library/time-base-class.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
