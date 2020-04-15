---
title: strstream 類別
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
ms.openlocfilehash: 047b7e9d7fdece75137980b013d43abf1d5e3ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376623"
---
# <a name="strstream-class"></a>strstream 類別

描述一個物件，該物件可控制如何使用類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區來插入及擷取項目和編碼物件。

## <a name="syntax"></a>語法

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>備註

此物件會儲存類別 `strstreambuf` 的物件。

> [!NOTE]
> 這個類別已被取代。 請考慮改用 [stringstream](../standard-library/sstream-typedefs.md#stringstream) 或 [wstringstream](../standard-library/sstream-typedefs.md#wstringstream)。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[斯特流](#strstream)|建構類型 `strstream` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[凍結](#freeze)|導致資料流緩衝區無法在資料流緩衝區作業中使用。|
|[pcount](#pcount)|傳回寫入至受控制序列的元素計數。|
|[rdbuf](#rdbuf)|將指標傳回至資料流的相關 `strstreambuf` 物件。|
|[Str](#str)|呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後將指標傳回受控制序列的開頭。|

## <a name="requirements"></a>需求

**標頭：** \<strstream>

**命名空間：** std

## <a name="strstreamfreeze"></a><a name="freeze"></a>流::凍結

導致資料流緩衝區無法在資料流緩衝區作業中使用。

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>參數

*_Freezeit*\
指示是否要凍結流的**布林**。

### <a name="remarks"></a>備註

成員函數調用[rdbuf](#rdbuf) -> [凍結](../standard-library/strstreambuf-class.md#freeze)(=*凍結*)。

### <a name="example"></a>範例

有關使用`freeze`的範例,請參閱[strstreambuf::凍結](../standard-library/strstreambuf-class.md#freeze)。

## <a name="strstreampcount"></a><a name="pcount"></a>斯特流::p計數

傳回寫入至受控制序列的元素計數。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>傳回值

寫入受控制序列的項目數。

### <a name="remarks"></a>備註

成員函數傳回[rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount)。

### <a name="example"></a>範例

如需使用 pcount 的範例，請參閱 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="strstreamrdbuf"></a><a name="rdbuf"></a>斯特蘭::rdbuf

傳回指向資料流相關 strstreambuf 物件的指標。

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>傳回值

指向資料流相關 strstreambuf 物件的指標。

### <a name="remarks"></a>備註

成員函數將類型的`pointer`儲存流緩衝區的位址傳回為[strstreambuf](../standard-library/strstreambuf-class.md)。

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="strstreamstr"></a><a name="str"></a>斯特蘭:斯特

呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後將指標傳回受控制序列的開頭。

```cpp
char *str();
```

### <a name="return-value"></a>傳回值

指向受控制序列開頭的指標。

### <a name="remarks"></a>備註

成員函數傳回[rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)。

### <a name="example"></a>範例

有關`str`使用的示例,請參閱[strstreambuf:str。](../standard-library/strstreambuf-class.md#str)

## <a name="strstreamstrstream"></a><a name="strstream"></a>串流::斯特流

建構類型 `strstream` 的物件。

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*計數*\
緩衝區的大小。

*_Mode*\
緩衝區的輸入和輸出模式。 如需詳細資訊，請參閱 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

*Ptr*\
緩衝區。

### <a name="remarks"></a>備註

兩個構造函數都通過調用[streambuf](../standard-library/streambuf-typedefs.md#streambuf) **(sb**) 初始`sb`化基類,其中是類[strstreambuf](../standard-library/strstreambuf-class.md)的存儲物件。 第一個構造函數也`sb`通過調用[strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf)進行初始化。 第二個建構函式使用下列其中一種方法初始化基底類別：

- 如果`_Mode` & **ios_base::app**= 0,則*ptr*必須`count`指定元素陣列的第一個元素,`strstreambuf`建構函數`ptr``count``ptr`呼叫 (,,)

- 否則 *,ptr*必須指定計數元素陣列的第一個元素,該元素包含第一個元素由*ptr*指定的 C 字串`strstreambuf`,建`ptr``count`構`ptr` + `strlen`函數 呼叫 ( `ptr`, ( ) 。

## <a name="see-also"></a>另請參閱

[iostream](../standard-library/istream-typedefs.md#iostream)\
[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
