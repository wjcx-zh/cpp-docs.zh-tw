---
title: basic_iostream 類別
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: e2a892525afbbad6d5b42d0b836fee096a70c297
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376811"
---
# <a name="basic_iostream-class"></a>basic_iostream 類別

可執行輸入和輸出的資料流類別。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_iostream : public basic_istream<Elem, Tr>,
    public basic_ostream<Elem, Tr>
{
public:
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};
```

## <a name="remarks"></a>備註

類範本描述通過基類[basic_ostream、>](../standard-library/basic-ostream-class.md)< `Elem``Tr`和提取通過其基類[basic_istream>](../standard-library/basic-istream-class.md)< `Elem``Tr`控制插入的物件。 這兩個物件共用一個公共虛擬基類`Tr`[basic_ios,>。](../standard-library/basic-ios-class.md) <  `Elem` 它們也會以 `Elem` 類型的項目 (其字元特性由類別 `Tr` 決定) 管理通用的資料流緩衝區。 此建構函式會藉由 `basic_istream`( **strbuf**) 和 `basic_ostream`( **strbuf**) 初始化其基底類別。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_iostream](#basic_iostream)|建立 `basic_iostream` 物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[交換](#swap)|將提供之 `basic_iostream` 物件的內容與此物件的內容交換。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子*](#op_eq)|將指定的 `basic_iostream` 物件值指派給這個物件。 這是一個移動指派，涉及不會留下複本的 `rvalue`。|

## <a name="requirements"></a>需求

**標頭︰** \<istream>

**命名空間：** std

## <a name="basic_iostreambasic_iostream"></a><a name="basic_iostream"></a>basic_iostream::basic_iostream

建立 `basic_iostream` 物件。

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>參數

*斯特布夫*\
現有的 `basic_streambuf` 物件。

*對*\
現有的 `basic_iostream` 物件，用來建構新的 `basic_iostream`。

### <a name="remarks"></a>備註

第一個建構函式會藉由 `basic_istream(strbuf)` 和 `basic_ostream(strbuf)` 初始化基底物件。

第二個構造函數通過調用`move(right)`初始化基物件。

## <a name="basic_iostreamoperator"></a><a name="op_eq"></a>basic_iostream::操作員*

將指定的 `basic_iostream` 物件值指派給這個物件。 這是一個移動指派，涉及不會留下複本的右值。

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>參數

*對*\
要指派之來源 `basic_iostream` 物件的 `rvalue` 參考。

### <a name="remarks"></a>備註

成員運算子呼叫`swap(right)`。

## <a name="basic_iostreamswap"></a><a name="swap"></a>basic_iostream:交換

將提供之 `basic_iostream` 物件的內容與此物件的內容交換。

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>參數

*對*\
要交換的 `basic_iostream` 物件。

### <a name="remarks"></a>備註

成員函數呼叫`swap(right)`。

## <a name="see-also"></a>另請參閱

[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
