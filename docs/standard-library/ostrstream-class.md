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
ms.openlocfilehash: b52ba70607a5214a6aa28f04cdded0b19a56b2f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373536"
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

|建構函式|描述|
|-|-|
|[ostrstream](#ostrstream)|建構類型 `ostrstream` 的物件。|

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

## <a name="ostrstreamfreeze"></a><a name="freeze"></a>奧斯特流::凍結

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

有關使用`freeze`的範例,請參閱[strstream::凍結](../standard-library/strstreambuf-class.md#freeze)。

## <a name="ostrstreamostrstream"></a><a name="ostrstream"></a>奧斯特流::奧斯特流

建構類型 `ostrstream` 的物件。

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>參數

*Ptr*\
緩衝區。

*計數*\
以位元組為單位的緩衝區大小。

*_Mode*\
緩衝區的輸入和輸出模式。 如需詳細資訊，請參閱 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

### <a name="remarks"></a>備註

兩個構造函數都通過調用[ostream](../standard-library/ostream-typedefs.md#ostream)**(sb**) 初始`sb`化基類,其中是類[strstreambuf](../standard-library/strstreambuf-class.md)的存儲物件。 第一個構造函數也`sb`通過調`strstreambuf`用 初始化。 第二個建構函式使用下列其中一種方法初始化基底類別：

- 如果`_Mode` & **ios_base::app**=`ptr`0,`count`則必須指定 元素陣列的第一個元素,並且構`strstreambuf`造函數調用`count``ptr``ptr`(,,)。

- 否則,`ptr`必須指定計數元素陣列的第一個元素,該元素包含其第一個元素`ptr`由 指定的 C 字串,建構函`strstreambuf``ptr`式`count``ptr` + `strlen`呼`ptr`叫 ( 、 ( ) 。

## <a name="ostrstreampcount"></a><a name="pcount"></a>奧斯特斯裡::p計數

傳回寫入至受控制序列的元素計數。

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>傳回值

寫入受控制序列的項目數。

### <a name="remarks"></a>備註

成員函數傳回[rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount)。

### <a name="example"></a>範例

如需使用 `pcount` 的範例，請參閱 [strstream::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="ostrstreamrdbuf"></a><a name="rdbuf"></a>奧斯特裡::rdbuf

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

## <a name="ostrstreamstr"></a><a name="str"></a>奧斯特裡:斯特

呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後將指標傳回受控制序列的開頭。

```cpp
char *str();
```

### <a name="return-value"></a>傳回值

指向受控制序列開頭的指標。

### <a name="remarks"></a>備註

成員函數傳回[rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)。

### <a name="example"></a>範例

有關`str`使用的示例,請參閱[strstream::str。](../standard-library/strstreambuf-class.md#str)

## <a name="see-also"></a>另請參閱

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
