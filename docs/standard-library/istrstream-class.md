---
title: istrstream 類別
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: 70e71ac5a6fd523f0b7589625f4e88fdb41ee0e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581931"
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

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[rdbuf](#rdbuf)|將指標傳回至資料流的相關 `strstreambuf` 物件。|
|[str](#str)|呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後傳回指向受控制序列開頭的指標。|

## <a name="requirements"></a>需求

**標頭：**\<strstream>

**命名空間：** std

## <a name="istrstream"></a>  istrstream::istrstream

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

*count*<br/>
緩衝區的長度 (*ptr*)。

*ptr*<br/>
用來將緩衝區初始化的內容。

### <a name="remarks"></a>備註

所有建構函式初始化基底類別，藉由呼叫[istream](../standard-library/istream-typedefs.md#istream)(**sb**)，其中`sb`是類別的預存的物件[strstreambuf](../standard-library/strstreambuf-class.md)。 前兩個建構函式也會初始化`sb`藉由呼叫`strstreambuf`(( **const** `char` \*) `ptr`，0)。 其餘兩個建構函式會改為呼叫 `strstreambuf`( ( **const**`char` *) `ptr`, `count` )。

## <a name="rdbuf"></a>  istrstream::rdbuf

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

## <a name="str"></a>  istrstream::str

呼叫 [freeze](../standard-library/strstreambuf-class.md#freeze)，然後傳回指向受控制序列開頭的指標。

```cpp
char *str();
```

### <a name="return-value"></a>傳回值

指向受控制序列開頭的指標。

### <a name="remarks"></a>備註

成員函式會傳回 [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str)。

### <a name="example"></a>範例

請參閱[strstream:: str](../standard-library/strstreambuf-class.md#str)如需範例，會使用`str`。

## <a name="see-also"></a>另請參閱

[istream](../standard-library/istream-typedefs.md#istream)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
