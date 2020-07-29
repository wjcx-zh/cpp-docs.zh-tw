---
title: ostrstream 類別
ms.date: 11/04/2016
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
ms.openlocfilehash: f17d8006aea6c5467f8de270318386bb12df264a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222221"
---
# <a name="ostrstream-class"></a>ostrstream 類別

描述一個物件，該物件可控制將項目和編碼物件插入 [strstreambuf](../standard-library/strstreambuf-class.md) 類別的資料流緩衝區中。

## <a name="syntax"></a>語法

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>備註

此物件會儲存類別 `strstreambuf` 的物件。

> [!NOTE]
> 這個類別已被取代。 請考慮改用 [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) 或 [wostringstream](../standard-library/sstream-typedefs.md#wostringstream)。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[ostrstream](#ostrstream)|建構類型 `ostrstream` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[暫時](#freeze)|導致資料流緩衝區無法在資料流緩衝區作業中使用。|
|[pcount](#pcount)|傳回寫入至受控制序列的元素計數。|
|[rdbuf](#rdbuf)|將指標傳回至資料流的相關 `strstreambuf` 物件。|
|[字串](#str)|呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後將指標傳回受控制序列的開頭。|

## <a name="requirements"></a>需求

**標頭：**\<strstream>

**命名空間：** std

## <a name="ostrstreamfreeze"></a><a name="freeze"></a>ostrstream：：凍結

導致資料流緩衝區無法在資料流緩衝區作業中使用。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>參數

*_Freezeit*\
**`bool`**，指出您是否要凍結資料流程。

### <a name="remarks"></a>備註

此成員函式會呼叫[rdbuf](#rdbuf)  ->  [凍結](../standard-library/strstreambuf-class.md#freeze)（_ *Freezeit*）。

### <a name="example"></a>範例

如需使用的範例，請參閱[strstream：：凍結](../standard-library/strstreambuf-class.md#freeze) `freeze` 。

## <a name="ostrstreamostrstream"></a><a name="ostrstream"></a>ostrstream：： ostrstream

建構類型 `ostrstream` 的物件。

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>參數

*指標*\
緩衝區。

*計數*\
以位元組為單位的緩衝區大小。

*_Mode*\
緩衝區的輸入和輸出模式。 如需詳細資訊，請參閱 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

### <a name="remarks"></a>備註

這兩個函式都會呼叫[ostream](../standard-library/ostream-typedefs.md#ostream)（**sb**）來初始化基類，其中 `sb` 是[strstreambuf](../standard-library/strstreambuf-class.md)類別的預存物件。 第一個函式也會藉 `sb` 由呼叫來初始化 `strstreambuf` 。 第二個建構函式使用下列其中一種方法初始化基底類別：

- 如果 `_Mode`  &  **ios_base：： app**= = 0，則 `ptr` 必須指定元素陣列的第一個元素 `count` ，而此函式會呼叫 `strstreambuf` （ `ptr` ， `count` ， `ptr` ）。

- 否則， `ptr` 必須指定 count 元素陣列的第一個元素，其中包含 C 字串，其第一個專案是由所指定 `ptr` ，而此函式會呼叫 `strstreambuf` （ `ptr` 、 `count` 、 `ptr`  +  `strlen` （ `ptr` ））。

## <a name="ostrstreampcount"></a><a name="pcount"></a>ostrstream：:p 計數

傳回寫入至受控制序列的元素計數。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>傳回值

寫入受控制序列的項目數。

### <a name="remarks"></a>備註

此成員函式會傳回[rdbuf](#rdbuf)  ->  [pcount](../standard-library/strstreambuf-class.md#pcount)。

### <a name="example"></a>範例

如需使用 `pcount` 的範例，請參閱 [strstream::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="ostrstreamrdbuf"></a><a name="rdbuf"></a>ostrstream：： rdbuf

傳回指向資料流相關 strstreambuf 物件的指標。

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>傳回值

指向資料流相關 strstreambuf 物件的指標。

### <a name="remarks"></a>備註

此成員函式會將類型之儲存資料流程緩衝區的位址傳回 `pointer` 至[strstreambuf](../standard-library/strstreambuf-class.md)。

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="ostrstreamstr"></a><a name="str"></a>ostrstream：： str

呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後將指標傳回受控制序列的開頭。

```cpp
char *str();
```

### <a name="return-value"></a>傳回值

指向受控制序列開頭的指標。

### <a name="remarks"></a>備註

此成員函式會傳回[rdbuf](#rdbuf)  ->  [str](../standard-library/strstreambuf-class.md#str)。

### <a name="example"></a>範例

如需使用的範例，請參閱[strstream：： str](../standard-library/strstreambuf-class.md#str) `str` 。

## <a name="see-also"></a>另請參閱

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
