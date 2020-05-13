---
title: messages 類別
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
ms.openlocfilehash: deb9eaedba3c99bb2fcb8399ac412ccedb11545f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375916"
---
# <a name="messages-class"></a>messages 類別

類範本描述一個物件,該物件可用作區域設置,用於從給定區域設置的國際化消息目錄中檢索當地語系化的消息。

目前，雖然實作 messages 類別，但沒有訊息。

## <a name="syntax"></a>語法

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>參數

*字元類型*\
程式內用於編碼地區設定字元的類型。

## <a name="remarks"></a>備註

如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。

這個 facet 基本上會開啟基底類別 messages_base 所定義的訊息目錄，擷取所需的資訊，並關閉目錄。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[訊息](#messages)|訊息 facet 建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|用來顯示訊息的字元類型。|
|[string_type](#string_type)|類型，描述包含 `basic_string` 類型字元的 `CharType` 類型字串。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[關閉](#close)|關閉訊息目錄。|
|[do_close](#do_close)|虛擬函式，呼叫以關閉訊息目錄。|
|[do_get](#do_get)|虛擬函式，呼叫以擷取訊息目錄。|
|[do_open](#do_open)|虛擬函式，呼叫以開啟訊息目錄。|
|[get](#get)|擷取訊息目錄。|
|[open](#open)|開啟訊息目錄。|

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="messageschar_type"></a><a name="char_type"></a>消息::char_type

用來顯示訊息的字元類型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 **CharType** 的同義字。

## <a name="messagesclose"></a><a name="close"></a>訊息:關閉

關閉訊息目錄。

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>參數

*_Catval*\
要關閉的目錄。

### <a name="remarks"></a>備註

此成員函式會呼叫 [do_close](#do_close)(_ *Catval*)。

## <a name="messagesdo_close"></a><a name="do_close"></a>消息::d_close

虛擬函式，呼叫以關閉訊息目錄。

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>參數

*_Catval*\
要關閉的目錄。

### <a name="remarks"></a>備註

受保護的成員函數關閉消息目錄 *_Catval*,該目錄必須通過之前對[do_open](#do_open)調用打開。

*_Catval* 必須是從先前開啟且尚未關閉的目錄取得。

### <a name="example"></a>範例

請參閱 [close](#close) 的範例，它會呼叫 `do_close`。

## <a name="messagesdo_get"></a><a name="do_get"></a>訊息::do_get

虛擬函式，呼叫以擷取訊息目錄。

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>參數

*_Catval*\
識別值，指定所要搜尋的訊息目錄。

*_Set*\
第一個識別的項目，用來找出訊息目錄中的訊息。

*_Message*\
第二個識別的項目，用來找出訊息目錄中的訊息。

*_Dfault*\
失敗時要傳回的字串。

### <a name="return-value"></a>傳回值

它在發生故障時返回 *_Dfault*的副本。 否則，會傳回所指定訊息序列的複本。

### <a name="remarks"></a>備註

受保護的成員函數嘗試從消息目錄 *_Catval*獲取消息序列。 在這樣做時,它可能會 *_Set*利用 *_Set、_Message*和 *_Dfault。*

### <a name="example"></a>範例

請參閱 [get](#get) 的範例，它會呼叫 `do_get`。

## <a name="messagesdo_open"></a><a name="do_open"></a>訊息::do_開啟

虛擬函式，呼叫以開啟訊息目錄。

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>參數

*_Catname*\
所要搜尋之目錄的名稱。

*_Loc*\
要在目錄中搜尋的地區設定。

### <a name="return-value"></a>傳回值

它會在失敗時傳回小於零的值。 否則，傳回的值可用來作為稍後對 [get](#get) 進行呼叫時的第一個引數。

### <a name="remarks"></a>備註

受保護的成員函數嘗試打開名稱*為_Catname*的消息目錄。 在這樣做時,它可以利用區域設置 *_Loc*

傳回值應該用來作為稍後對 [close](#close) 進行呼叫時的引數。

### <a name="example"></a>範例

請參閱 [open](#open) 的範例，它會呼叫 `do_open`。

## <a name="messagesget"></a><a name="get"></a>訊息:抓取

擷取訊息目錄。

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>參數

*_Catval*\
識別值，指定所要搜尋的訊息目錄。

*_Set*\
第一個識別的項目，用來找出訊息目錄中的訊息。

*_Message*\
第二個識別的項目，用來找出訊息目錄中的訊息。

*_Dfault*\
失敗時要傳回的字串。

### <a name="return-value"></a>傳回值

它在發生故障時返回 *_Dfault*的副本。 否則，會傳回所指定訊息序列的複本。

### <a name="remarks"></a>備註

成員函數傳[do_get](#do_get)`_Catval`回 do_get `_Set` `_Message` `_Dfault`(、 、 、

## <a name="messagesmessages"></a><a name="messages"></a>訊息:消息

訊息 facet 建構函式。

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>參數

*_Refs*\
整數值，用來指定物件的記憶體管理類型。

*_Locname*\
地區設定的名稱。

### <a name="remarks"></a>備註

*_Refs*參數的可能值及其顯著性為:

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- \>1: 未定義這些值。

無法提供任何直接範例，因為解構函式受到保護。

建構函式會以 **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`) 初始化其基底物件。

## <a name="messagesopen"></a><a name="open"></a>訊息::開啟

開啟訊息目錄。

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>參數

*_Catname*\
所要搜尋之目錄的名稱。

*_Loc*\
要在目錄中搜尋的地區設定。

### <a name="return-value"></a>傳回值

它會在失敗時傳回小於零的值。 否則，傳回的值可用來作為稍後對 [get](#get) 進行呼叫時的第一個引數。

### <a name="remarks"></a>備註

成員函數返回[do_open](#do_open) `_Catname` `_Loc` (。

## <a name="messagesstring_type"></a><a name="string_type"></a>消息::string_type

類型，描述包含 `basic_string` 類型字元的 `CharType` 類型字串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>備註

該類型描述了類範本的專門化[basic_string](../standard-library/basic-string-class.md)其物件可以存儲消息序列的副本。

## <a name="see-also"></a>另請參閱

[\<區域設定>](../standard-library/locale.md)\
[messages_base類](../standard-library/messages-base-class.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
