---
title: basic_iostream 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
dev_langs:
- C++
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de2f28feb775cd6e37116ea7c27691397d2dfce4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="basiciostream-class"></a>basic_iostream 類別

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

此樣板類別描述透過其基底類別 [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`> 控制插入的物件，和透過其基底類別 [basic_istream](../standard-library/basic-istream-class.md)< `Elem`, `Tr`> 擷取的物件。 兩個物件共用通用的虛擬基底類別 [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, `Tr`>。 它們也會以 `Elem` 類型的項目 (其字元特性由類別 `Tr` 決定) 管理通用的資料流緩衝區。 此建構函式會藉由 `basic_istream`( **strbuf**) 和 `basic_ostream`( **strbuf**) 初始化其基底類別。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_iostream](#basic_iostream)|建立 `basic_iostream` 物件。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[swap](#swap)|將提供之 `basic_iostream` 物件的內容與此物件的內容交換。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_eq)|將指定的 `basic_iostream` 物件值指派給這個物件。 這是一個移動指派，涉及不會留下複本的 `rvalue`。|

## <a name="requirements"></a>需求

**標頭︰**\<istream>

**命名空間：** std

## <a name="basic_iostream"></a>  basic_iostream::basic_iostream

建立 `basic_iostream` 物件。

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>參數

`strbuf` 現有`basic_streambuf`物件。

`right` 現有`basic_iostream`物件，用來建構新`basic_iostream`。

### <a name="remarks"></a>備註

第一個建構函式會藉由 `basic_istream(strbuf)` 和 `basic_ostream(strbuf)` 初始化基底物件。

第二個建構函式呼叫來初始化基底物件`move(right)`。

## <a name="op_eq"></a>  basic_iostream::operator=

將指定的 `basic_iostream` 物件值指派給這個物件。 這是一個移動指派，涉及不會留下複本的右值。

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>參數

`right` `rvalue`參考`basic_iostream`從指派的物件。

### <a name="remarks"></a>備註

此成員運算子會呼叫`swap(right)`。

## <a name="swap"></a>  basic_iostream::swap

將提供之 `basic_iostream` 物件的內容與此物件的內容交換。

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>參數

`right` `basic_iostream`来交換的物件。

### <a name="remarks"></a>備註

成員函式呼叫`swap(right)`。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
