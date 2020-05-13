---
title: istrstream 類別
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: d548a8c2c47a5a345be725afdedb47524344f720
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337531"
---
# <a name="istrstream-class"></a>istrstream 類別

描述一個物件，此物件可控制如何從 [strstreambuf](../standard-library/strstreambuf-class.md) 類別的資料流緩衝區中擷取元素和編碼物件。

## <a name="syntax"></a>語法

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>備註

此物件會儲存類別 `strstreambuf` 的物件。

> [!NOTE]
> 這個類別已被取代。 請考慮改用 [istringstream](../standard-library/sstream-typedefs.md#istringstream) 或 [wistringstream](../standard-library/sstream-typedefs.md#wistringstream)。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[istrstream](#istrstream)|建構類型 `istrstream` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[rdbuf](#rdbuf)|將指標傳回至資料流的相關 `strstreambuf` 物件。|
|[Str](#str)|呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後將指標傳回受控制序列的開頭。|

## <a name="requirements"></a>需求

**標頭：** \<strstream>

**命名空間：** std

## <a name="istrstreamistrstream"></a><a name="istrstream"></a>分流:istrstream

建構類型 `istrstream` 的物件。

```cpp
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```

### <a name="parameters"></a>參數

*計數*\
緩衝區的長度 (*ptr*)。

*Ptr*\
用來將緩衝區初始化的內容。

### <a name="remarks"></a>備註

所有構造函數通過調用[istream](../standard-library/istream-typedefs.md#istream)**(sb**)`sb`初始化基類 ,其中是類[strstreambuf](../standard-library/strstreambuf-class.md)的存儲物件。 前兩個`sb`建構函數也通過調用`strstreambuf`((const) **const** `char` \* `ptr`0 來初始化。 其餘兩個建構`strstreambuf`函數改為呼**const**`char`叫 ((const `count` `ptr`+) 。

## <a name="istrstreamrdbuf"></a><a name="rdbuf"></a>是斯特朗::rdbuf

傳回指向資料流相關 strstreambuf 物件的指標。

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>傳回值

指向資料流相關 strstreambuf 物件的指標。

### <a name="remarks"></a>備註

成員函式會傳回預存資料流緩衝區 (屬於 [strstreambuf](../standard-library/strstreambuf-class.md) 的 pointer 類型) 的位址。

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)。

## <a name="istrstreamstr"></a><a name="str"></a>是斯特朗:斯特

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

[伊流](../standard-library/istream-typedefs.md#istream)\
[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
