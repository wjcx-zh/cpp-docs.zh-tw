---
title: '&lt;string&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- string/std::getline
- string/std::stod
- string/std::stof
- string/std::stoi
- string/std::stol
- string/std::stold
- string/std::stoll
- string/std::stoul
- string/std::stoull
- string/std::swap
- string/std::to_string
- string/std::to_wstring
ms.assetid: 1a4ffd11-dce5-4cc6-a043-b95de034c7c4
helpviewer_keywords:
- std::getline [C++]
- std::stod [C++]
- std::stof [C++]
- std::stoi [C++]
- std::stol [C++]
- std::stold [C++]
- std::stoll [C++]
- std::stoul [C++]
- std::stoull [C++]
- std::swap [C++]
- std::to_string [C++]
- std::to_wstring [C++]
ms.openlocfilehash: 3f1dca71a6bb9d5461150378191b9373f907ecd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376666"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt; 函式

||||
|-|-|-|
|[getline](#getline)|[斯托德](#stod)|[斯特下](#stof)|
|[斯托伊](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[斯圖爾](#stoul)|[斯圖爾](#stoull)|
|[交換](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a><a name="getline"></a>getline

從輸入資料流一行一行地擷取字串。

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delimiter);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delimiter);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& in_stream,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>參數

*in_stream*\
要擷取字串的輸入資料流。

*Str*\
要從輸入資料流讀取字元的字串。

*分隔符*\
行的分隔符號。

### <a name="return-value"></a>傳回值

輸入流*in_stream*。

### <a name="remarks"></a>備註

標記`(1)`從*in_stream*中提取字元的函數簽名對,直到找到*分隔元*,將它們存儲在*str*中。

標記`(2)`的函數簽署對使用 newline 為預設行分隔符,`getline(in_stream, str, in_stream. widen('\n'))`並且行為為 。

每對的第二個函式是第一個函式的類比，以支援 [rvalue 參考](../cpp/lvalues-and-rvalues-visual-cpp.md)。

當發生下列其中一項時，會停止擷取：

- 在檔案末尾,在這種情況下 *,in_stream*的內部狀態旗`ios_base::eofbit`標設定為 。

- 函數提取一個與*分隔符*相等的元素。 元素不會放回或追加到受控序列中。

- 函數提取`str.`[max_size](../standard-library/basic-string-class.md#max_size)元素後。 *in_stream*的內部狀態旗標`ios_base::failbit`設定為 。

- 除了之前列出的錯誤之外,其他一些錯誤;*in_stream*的內部狀態旗標`ios_base::badbit`設定為 。

如需內部狀態旗標相關的資訊，請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)。

如果函數不提取任何元素,則*in_stream*的內部狀態旗標`ios_base::failbit`設定為 。 在任何情況下,`getline`傳回*in_stream*。

如果引發異常,*則in_stream*和*str*處於有效狀態。

### <a name="example"></a>範例

下列程式碼示範兩種模式的 `getline()`：第一個使用預設的分隔符號 (新行)，第二個使用空白做為分隔符號。 檔案結尾字元 (鍵盤上的 Ctrl-Z 鍵) 用來控制 while 迴圈的終止。 此值設置`cin``eofbit`到的內部狀態標誌,在第二個迴圈正常工作之前,必須用[basic_ios::clear()](../standard-library/basic-ios-class.md#clear)清除該標誌。

```cpp
// compile with: /EHsc /W4
#include <string>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    string str;
    vector<string> v1;
    cout << "Enter a sentence, press ENTER between sentences. (Ctrl-Z to stop): " << endl;
    // Loop until end-of-file (Ctrl-Z) is input, store each sentence in a vector.
    // Default delimiter is the newline character.
    while (getline(cin, str)) {
        v1.push_back(str);
    }

    cout << "The following input was stored with newline delimiter:" << endl;
    for (const auto& p : v1) {
        cout << p << endl;
    }

    cin.clear();

    vector<string> v2;
    // Now try it with a whitespace delimiter
    while (getline(cin, str, ' ')) {
        v2.push_back(str);
    }

    cout << "The following input was stored with whitespace as delimiter:" << endl;
    for (const auto& p : v2) {
        cout << p << endl;
    }
}
```

## <a name="stod"></a><a name="stod"></a>斯托德

將字元序列轉換為**`double`**。

```cpp
double stod(
    const string& str,
    size_t* idx = 0);

double stod(
    const wstring& str,
    size_t* idx = 0
;
```

### <a name="parameters"></a>參數

*Str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

### <a name="return-value"></a>傳回值

數**`double`** 值 。

### <a name="remarks"></a>備註

函數將*str*中的元素序列轉換**`double`** 為類型 值,就像`strtod( str.c_str(), _Eptr)`通過調`_Eptr`用 ,其中 是函數內部的物件。 如果`str.c_str() == *_Eptr`,它將引發類型的`invalid_argument`物件 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則,如果*idx*不是空指標,則函數將`*_Eptr -  str.c_str()`儲存`*idx`並返回該值。

## <a name="stof"></a><a name="stof"></a>斯特下

將字元序列轉換為 float。

```cpp
float stof(
    const string& str,
    size_t* idx = 0);

float stof(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>參數

*Str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

### <a name="return-value"></a>傳回值

數**`float`** 值 。

### <a name="remarks"></a>備註

函數將*str*中的元素序列轉換**`float`** 為類型 值,就像`strtof( str.c_str(), _Eptr)`通過調`_Eptr`用 ,其中 是函數內部的物件。 如果`str.c_str() == *_Eptr`,它將引發類型的`invalid_argument`物件 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則,如果*idx*不是空指標,則函數將`*_Eptr -  str.c_str()`儲存`*idx`並返回該值。

## <a name="stoi"></a><a name="stoi"></a>斯托伊

將字元序列轉換為整數。

```cpp
int stoi(
    const string& str,
    size_t* idx = 0,
    int base = 10);

int stoi(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="return-value"></a>傳回值

整數值。

### <a name="parameters"></a>參數

*Str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

*基地*\
要使用的數字基底。

### <a name="remarks"></a>備註

函數`stoi`將*str*中的字元序列轉換**`int`** 為類型的 值並返回該值。 例如，若傳遞字元序列 "10"，則 `stoi` 的傳回值是整數 10。

`stoi`當以單位元元的方式調用`strtol`時`strtol( str.c_str(), _Eptr, idx)`,其行為類似於該函數,`_Eptr`其中 是函數內部的物件;或`wcstol`對於寬字元,當它以類似的方式呼叫時`wcstol(Str.c_str(), _Eptr, idx)`, 。 如需詳細資訊，請參閱[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)。

如果`str.c_str() == *_Eptr``stoi`可`invalid_argument`用型態的物件 。 如果這樣的調用將設置`errno`,或者如果返回的值不能表示為**`int`** 類型的物件,則它將引發`out_of_range`類型的物件。 否則,如果*idx*不是空指標,則函數將存儲`*_Eptr - str.c_str()``*idx`在中。

## <a name="stol"></a><a name="stol"></a>斯托爾

將字元序列轉換為**`long`**。

```cpp
long stol(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long stol(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>參數

*Str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

*基地*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

長整數值。

### <a name="remarks"></a>備註

函數將*str*中的元素序列轉換**`long`** 為類型 值,就像`strtol( str.c_str(), _Eptr, idx)`通過調`_Eptr`用 ,其中 是函數內部的物件。 如果`str.c_str() == *_Eptr`,它將引發類型的`invalid_argument`物件 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則,如果*idx*不是空指標,則函數將`*_Eptr -  str.c_str()`儲存`*idx`並返回該值。

## <a name="stold"></a><a name="stold"></a>斯代

將字元序列轉換為**`long double`**。

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>參數

*Str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

### <a name="return-value"></a>傳回值

數**`long double`** 值 。

### <a name="remarks"></a>備註

函數將*str*中的元素序列轉換**`long double`** 為類型 值,就像`strtold( str.c_str(), _Eptr)`通過調`_Eptr`用 ,其中 是函數內部的物件。 如果`str.c_str() == *_Eptr`,它將引發類型的`invalid_argument`物件 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則,如果*idx*不是空指標,則函數將`*_Eptr -  str.c_str()`儲存`*idx`並返回該值。

## <a name="stoll"></a><a name="stoll"></a>斯托爾

將字元序列轉換為**`long long`**。

```cpp
long long stoll(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long long stoll(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>參數

*Str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

*基地*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

數**`long long`** 值 。

### <a name="remarks"></a>備註

函數將*str*中的元素序列轉換**`long long`** 為類型 值,就像`strtoll( str.c_str(), _Eptr, idx)`通過調`_Eptr`用 ,其中 是函數內部的物件。 如果`str.c_str() == *_Eptr`,它將引發類型的`invalid_argument`物件 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則,如果*idx*不是空指標,則函數將`*_Eptr -  str.c_str()`儲存`*idx`並返回該值。

## <a name="stoul"></a><a name="stoul"></a>斯圖爾

將字元序列轉換成不帶正負號的 long。

```cpp
unsigned long stoul(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long stoul(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>參數

*Str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

*基地*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

不帶正負號的 long 整數值。

### <a name="remarks"></a>備註

函數將*str*中的元素序列轉換**`unsigned long`** 為類型 值,就像`strtoul( str.c_str(), _Eptr, idx)`通過調`_Eptr`用 ,其中 是函數內部的物件。 如果`str.c_str() == *_Eptr`,它將引發類型的`invalid_argument`物件 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則,如果*idx*不是空指標,則函數將`*_Eptr -  str.c_str()`儲存`*idx`並返回該值。

## <a name="stoull"></a><a name="stoull"></a>斯圖爾

將字元序列轉換為**`unsigned long long`**。

```cpp
unsigned long long stoull(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long long stoull(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>參數

*Str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

*基地*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

數**`unsigned long long`** 值 。

### <a name="remarks"></a>備註

函數將*str*中的元素序列轉換**`unsigned long long`** 為類型 值,就像`strtoull( str.c_str(), _Eptr, idx)`通過調`_Eptr`用 ,其中 是函數內部的物件。 如果`str.c_str() == *_Eptr`,它將引發類型的`invalid_argument`物件 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則,如果*idx*不是空指標,則函數將`*_Eptr -  str.c_str()`儲存`*idx`並返回該值。

## <a name="swap"></a><a name="swap"></a>交換

交換兩個字串的字元陣列。

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*離開*\
其元素要與另一個字串的元素交換的字串。

*對*\
另一個字串，其元素要與第一個字串交換。

### <a name="remarks"></a>備註

範本函數執行*左側*的專用成員函數。[交換](../standard-library/basic-string-class.md#swap)字串 (*右*), 保證恆定的複雜性.

### <a name="example"></a>範例

```cpp
// string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   swap ( s1 , s2 );
   cout << "\nAfter swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.

After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="to_string"></a><a name="to_string"></a>to_string

將值轉換成 `string`。

```cpp
string to_string(int value);
string to_string(unsigned int value);
string to_string(long value);
string to_string(unsigned long value);
string to_string(long long value);
string to_string(unsigned long long value);
string to_string(float value);
string to_string(double value);
string to_string(long double value);
```

### <a name="parameters"></a>參數

*價值*\
要轉換的值。

### <a name="return-value"></a>傳回值

表示值的 `string`。

### <a name="remarks"></a>備註

函數將*值*轉換為儲存在函式內部陣列`Buf`的元素序列,就像透過呼`sprintf(Buf, Fmt, value)``Fmt`叫

- `"%d"`沒有*值*為類型**`int`**

- `"%u"`沒有*值*為類型**`unsigned int`**

- `"%ld"`沒有*值*為類型**`long`**

- `"%lu"`沒有*值*為類型**`unsigned long`**

- `"%lld"`沒有*值*為類型**`long long`**

- `"%llu"`沒有*值*為類型**`unsigned long long`**

- `"%f"`如果*值*為類型**`float`** 或**`double`**

- `"%Lf"`沒有*值*為類型**`long double`**

函式會傳回 `string(Buf)`。

## <a name="to_wstring"></a><a name="to_wstring"></a>to_wstring

將值轉換成寬字串。

```cpp
wstring to_wstring(int value);
wstring to_wstring(unsigned int value);
wstring to_wstring(long value);
wstring to_wstring(unsigned long value);
wstring to_wstring(long long value);
wstring to_wstring(unsigned long long value);
wstring to_wstring(float value);
wstring to_wstring(double value);
wstring to_wstring(long double value);
```

### <a name="parameters"></a>參數

*價值*\
要轉換的值。

### <a name="return-value"></a>傳回值

表示值的寬字串。

### <a name="remarks"></a>備註

函數將*值*轉換為儲存在函式內部陣列`Buf`的元素序列,就像透過呼`swprintf(Buf, Len, Fmt, value)``Fmt`叫

- `L"%d"`沒有*值*為類型**`int`**

- `L"%u"`沒有*值*為類型**`unsigned int`**

- `L"%ld"`沒有*值*為類型**`long`**

- `L"%lu"`沒有*值*為類型**`unsigned long`**

- `L"%lld"`沒有*值*為類型**`long long`**

- `L"%llu"`沒有*值*為類型**`unsigned long long`**

- `L"%f"`如果*值*為類型**`float`** 或**`double`**

- `L"%Lf"`沒有*值*為類型**`long double`**

函式會傳回 `wstring(Buf)`。

## <a name="see-also"></a>另請參閱

[\<字串>](../standard-library/string.md)
