---
title: time_put 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
dev_langs:
- C++
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27a200ba94be8c4937342820fadf89e4225ba97d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719949"
---
# <a name="timeput-class"></a>time_put 類別

此樣板類別描述可以做為地區設定 facet 的物件，以控制時間值轉換為類型 `CharType` 的序列。

## <a name="syntax"></a>語法

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>參數

*CharType*<br/>
用於程式內部字元編碼的類型。

*OutputIterator*<br/>
時間 put 函式將其輸出寫入其中的迭代器類型。

## <a name="remarks"></a>備註

如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[time_put](#time_put)|`time_put` 類型物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|
|[iter_type](#iter_type)|描述輸出迭代器的類型。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[do_put](#do_put)|虛擬函式，會輸出日期和時間資訊做為 `CharType` 的序列。|
|[put](#put)|輸出日期和時間資訊做為 `CharType` 的序列。|

## <a name="requirements"></a>需求

**標頭︰**\<locale>

**命名空間：** std

## <a name="char_type"></a>  time_put::char_type

類型，用來描述由地區設定使用的字元。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `CharType`的同義字。

## <a name="do_put"></a>  time_put::do_put

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

*next*<br/>
輸出迭代器，其中的字元序列代表插入的日期與時間。

*_Iosbase*<br/>
未使用。

*_Pt*<br/>
輸出的日期和時間資訊。

*_Fmt*<br/>
輸出的格式。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

*_Mod*<br/>
格式修飾詞。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

### <a name="return-value"></a>傳回值

插入最後一個元素之後第一個位置的迭代器。

### <a name="remarks"></a>備註

受保護的虛擬成員函式會產生開始的循序元素`next`物件中儲存的時間值從\* `_Pt`，型別的`tm`。 此函式會傳回迭代器，此迭代器指定在所產生的輸出後下一個要插入元素的位置。

所使用的相同規則會產生輸出`strftime`，與最後一個引數 *_Pt*，來產生一系列**char**成陣列的項目。 每個這類**char**項目都會被假設為型別之對等項目的`CharType`簡單、 一對一的對應。 如果 *_Mod*等於零，有效的格式為"%f"，其中 F 由取代 *_Fmt*。 否則，有效的格式是"%MF"，其中 M 由取代 *_Mod*。

### <a name="example"></a>範例

請參閱 [put](#put) 的範例，其會呼叫 `do_put`。

## <a name="iter_type"></a>  time_put::iter_type

描述輸出迭代器的類型。

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `OutputIterator`的同義字。

## <a name="put"></a>  time_put::put

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

*next*<br/>
輸出迭代器，其中的字元序列代表插入的日期與時間。

*_Iosbase*<br/>
未使用。

*_Fill*<br/>
類型字元`CharType`空間所使用。

*_Pt*<br/>
輸出的日期和時間資訊。

*_Fmt*<br/>
輸出的格式。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

*_Mod*<br/>
格式修飾詞。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

*first*<br/>
輸出的格化式字串開頭。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

*最後一個*<br/>
輸出的格化式字串結尾。 如需有效值，請參閱 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。

### <a name="return-value"></a>傳回值

插入最後一個元素之後第一個位置的迭代器。

### <a name="remarks"></a>備註

第一個成員函式會傳回[do_put](#do_put)(`next`， `_Iosbase`， `_Fill`， `_Pt`， `_Fmt`， `_Mod`)。 第二個成員函式會將 \* `next` ++ 複製到間隔 [ `first`, `last`) 中的任何元素，而不是百分比 (%)。 對於在間隔 [ `first`, `last`) 後面接著一個字元 *C* 的百分比，函式會改為評估 `next` = `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) 並跳過 *C*。然而，如果 *C* 是來自集合 EOQ# 的限定詞字元，在間隔 [ `first`, `last`) 後面接著一個字元 `C2`，函式會改為評估 `next` = `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, `C2`, *C*) 並跳過 `C2`。

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

## <a name="time_put"></a>  time_put::time_put

`time_put` 類型物件的建構函式。

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>參數

*_Refs*<br/>
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

可能值 *_Refs*參數和其意義如下：

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- \> 1： 未定義這些值。

建構函式會初始化其基底物件[locale:: facet](../standard-library/locale-class.md#facet_class)(*_Refs*)。

## <a name="see-also"></a>另請參閱

[\<locale>](../standard-library/locale.md)<br/>
[time_base 類別](../standard-library/time-base-class.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
