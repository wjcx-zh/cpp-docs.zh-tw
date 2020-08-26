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
ms.openlocfilehash: 350a66481c7061322f08a768ec1628598f4af68e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843179"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt; 函式

[getline](#getline)\
[stod](#stod)\
[stof](#stof)\
[stoi](#stoi)\
[stol](#stol)\
[stold](#stold)\
[stoll](#stoll)\
[stoul](#stoul)\
[stoull](#stoull)\
[交換](#swap)\
[to_string](#to_string)\
[to_wstring](#to_wstring)

## <a name="getline"></a><a name="getline"></a> getline

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

*str*\
要從輸入資料流讀取字元的字串。

*delimiter*\
行的分隔符號。

### <a name="return-value"></a>傳回值

輸入資料流程 *in_stream*。

### <a name="remarks"></a>備註

在找到分隔符號之前，會將一組函式簽章標示為 `(1)` 從*in_stream*中解壓縮字元，並將它們儲存在*str*中。 *delimiter*

標記為使用換行的函式簽章對 `(2)` 預設的行分隔符號，其行為就像 `getline(in_stream, str, in_stream. widen('\n'))` 。

每對的第二個函式是第一個函式的類比，以支援 [rvalue 參考](../cpp/lvalues-and-rvalues-visual-cpp.md)。

當發生下列其中一項時，會停止擷取：

- 在檔案結尾， *in_stream* 的內部狀態旗標設定為 `ios_base::eofbit` 。

- 在函式中，將比較等於 *分隔符號*的元素解壓縮之後。 元素不會被放回或附加至受控制的序列。

- 函式解壓縮 `str.` [max_size](../standard-library/basic-string-class.md#max_size)專案之後。 *In_stream*的內部狀態旗標設定為 `ios_base::failbit` 。

- 先前所列的其他錯誤; *in_stream* 的內部狀態旗標設定為 `ios_base::badbit` 。

如需內部狀態旗標相關的資訊，請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)。

如果函式未解壓縮任何元素， *in_stream* 的內部狀態旗標會設為 `ios_base::failbit` 。 在任何情況下，都會傳回 `getline` *in_stream*。

如果擲回例外狀況， *in_stream* 和 *str* 會保持為有效的狀態。

### <a name="example"></a>範例

下列程式碼示範兩種模式的 `getline()`：第一個使用預設的分隔符號 (新行)，第二個使用空白做為分隔符號。 檔案結尾字元 (鍵盤上的 Ctrl-Z 鍵) 用來控制 while 迴圈的終止。 這個值會將的內部狀態旗標設定 `cin` 為 `eofbit` ，在第二個 while 迴圈正常運作之前，必須先使用 [basic_ios：： Clear ( # B1 ](../standard-library/basic-ios-class.md#clear) 來清除此旗標。

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

## <a name="stod"></a><a name="stod"></a> stod

將字元序列轉換成 **`double`** 。

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

*str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

### <a name="return-value"></a>傳回值

**`double`** 值。

### <a name="remarks"></a>備註

函式會將 *str* 中的元素序列轉換為類型的值 **`double`** ，如同藉由呼叫 `strtod( str.c_str(), _Eptr)` ，其中 `_Eptr` 是函式內部的物件。 如果為 `str.c_str() == *_Eptr` ，則會擲回類型的物件 `invalid_argument` 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果 *idx* 不是 null 指標，函式會儲存 `*_Eptr -  str.c_str()` 在中， `*idx` 並傳回值。

## <a name="stof"></a><a name="stof"></a> stof

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

*str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

### <a name="return-value"></a>傳回值

**`float`** 值。

### <a name="remarks"></a>備註

函式會將 *str* 中的元素序列轉換為類型的值 **`float`** ，如同藉由呼叫 `strtof( str.c_str(), _Eptr)` ，其中 `_Eptr` 是函式內部的物件。 如果為 `str.c_str() == *_Eptr` ，則會擲回類型的物件 `invalid_argument` 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果 *idx* 不是 null 指標，函式會儲存 `*_Eptr -  str.c_str()` 在中， `*idx` 並傳回值。

## <a name="stoi"></a><a name="stoi"></a> stoi

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

*str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

*基地*\
要使用的數字基底。

### <a name="remarks"></a>備註

函數會 `stoi` 將 *str* 中的字元序列轉換為類型的值 **`int`** ，並傳回值。 例如，若傳遞字元序列 "10"，則 `stoi` 的傳回值是整數 10。

`stoi``strtol`在使用時，其行為類似于單一位元組字元的函式 `strtol( str.c_str(), _Eptr, idx)` ，其中 `_Eptr` 是函式內部的物件; `wcstol` 如果是寬字元，則會以類似的方式呼叫 `wcstol(Str.c_str(), _Eptr, idx)` 。 如需詳細資訊，請參閱[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)。

如果 `str.c_str() == *_Eptr` 為，則會擲回 `stoi` 類型的物件 `invalid_argument` 。 如果這類呼叫會設定 `errno` ，或者如果傳回的值無法表示為類型的物件 **`int`** ，則會擲回類型的物件 `out_of_range` 。 否則，如果 *idx* 不是 null 指標，函式就會儲存 `*_Eptr - str.c_str()` 在中 `*idx` 。

## <a name="stol"></a><a name="stol"></a> stol

將字元序列轉換成 **`long`** 。

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

*str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

*基地*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

長整數值。

### <a name="remarks"></a>備註

函式會將 *str* 中的元素序列轉換為類型的值 **`long`** ，如同藉由呼叫 `strtol( str.c_str(), _Eptr, idx)` ，其中 `_Eptr` 是函式內部的物件。 如果為 `str.c_str() == *_Eptr` ，則會擲回類型的物件 `invalid_argument` 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果 *idx* 不是 null 指標，函式會儲存 `*_Eptr -  str.c_str()` 在中， `*idx` 並傳回值。

## <a name="stold"></a><a name="stold"></a> stold

將字元序列轉換成 **`long double`** 。

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>參數

*str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

### <a name="return-value"></a>傳回值

**`long double`** 值。

### <a name="remarks"></a>備註

函式會將 *str* 中的元素序列轉換為類型的值 **`long double`** ，如同藉由呼叫 `strtold( str.c_str(), _Eptr)` ，其中 `_Eptr` 是函式內部的物件。 如果為 `str.c_str() == *_Eptr` ，則會擲回類型的物件 `invalid_argument` 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果 *idx* 不是 null 指標，函式會儲存 `*_Eptr -  str.c_str()` 在中， `*idx` 並傳回值。

## <a name="stoll"></a><a name="stoll"></a> stoll

將字元序列轉換成 **`long long`** 。

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

*str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

*基地*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

**`long long`** 值。

### <a name="remarks"></a>備註

函式會將 *str* 中的元素序列轉換為類型的值 **`long long`** ，如同藉由呼叫 `strtoll( str.c_str(), _Eptr, idx)` ，其中 `_Eptr` 是函式內部的物件。 如果為 `str.c_str() == *_Eptr` ，則會擲回類型的物件 `invalid_argument` 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果 *idx* 不是 null 指標，函式會儲存 `*_Eptr -  str.c_str()` 在中， `*idx` 並傳回值。

## <a name="stoul"></a><a name="stoul"></a> stoul

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

*str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

*基地*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

不帶正負號的 long 整數值。

### <a name="remarks"></a>備註

函式會將 *str* 中的元素序列轉換為類型的值 **`unsigned long`** ，如同藉由呼叫 `strtoul( str.c_str(), _Eptr, idx)` ，其中 `_Eptr` 是函式內部的物件。 如果為 `str.c_str() == *_Eptr` ，則會擲回類型的物件 `invalid_argument` 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果 *idx* 不是 null 指標，函式會儲存 `*_Eptr -  str.c_str()` 在中， `*idx` 並傳回值。

## <a name="stoull"></a><a name="stoull"></a> stoull

將字元序列轉換成 **`unsigned long long`** 。

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

*str*\
要轉換的字元序列。

*idx*\
第一個未轉換的字元的索引值。

*基地*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

**`unsigned long long`** 值。

### <a name="remarks"></a>備註

函式會將 *str* 中的元素序列轉換為類型的值 **`unsigned long long`** ，如同藉由呼叫 `strtoull( str.c_str(), _Eptr, idx)` ，其中 `_Eptr` 是函式內部的物件。 如果為 `str.c_str() == *_Eptr` ，則會擲回類型的物件 `invalid_argument` 。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果 *idx* 不是 null 指標，函式會儲存 `*_Eptr -  str.c_str()` 在中， `*idx` 並傳回值。

## <a name="swap"></a><a name="swap"></a> 交換

交換兩個字串的字元陣列。

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*離開*\
一個字串，其元素要與另一個字串的元素交換。

*對*\
另一個字串，其元素要與第一個字串交換。

### <a name="remarks"></a>備註

範本函式會執行左方的特殊成員函 *式*。針對字串[交換](../standard-library/basic-string-class.md#swap) (*右*) ，以確保常數的複雜度。

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

## <a name="to_string"></a><a name="to_string"></a> to_string

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

*value*\
要轉換的值。

### <a name="return-value"></a>傳回值

表示值的 `string`。

### <a name="remarks"></a>備註

函式會將 *值* 轉換為函式內部陣列物件中所儲存的專案序列 `Buf` ，如同藉由 `sprintf(Buf, Fmt, value)` 呼叫，其中 `Fmt` 是

- `"%d"` 如果 *值* 的類型為 **`int`**

- `"%u"` 如果 *值* 的類型為 **`unsigned int`**

- `"%ld"` 如果 *值* 的類型為 **`long`**

- `"%lu"` 如果 *值* 的類型為 **`unsigned long`**

- `"%lld"` 如果 *值* 的類型為 **`long long`**

- `"%llu"` 如果 *值* 的類型為 **`unsigned long long`**

- `"%f"` 如果 *值* 是類型 **`float`** 或 **`double`**

- `"%Lf"` 如果 *值* 的類型為 **`long double`**

函式會傳回 `string(Buf)`。

## <a name="to_wstring"></a><a name="to_wstring"></a> to_wstring

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

*value*\
要轉換的值。

### <a name="return-value"></a>傳回值

表示值的寬字串。

### <a name="remarks"></a>備註

函式會將 *值* 轉換為函式內部陣列物件中所儲存的專案序列 `Buf` ，如同藉由 `swprintf(Buf, Len, Fmt, value)` 呼叫，其中 `Fmt` 是

- `L"%d"` 如果 *值* 的類型為 **`int`**

- `L"%u"` 如果 *值* 的類型為 **`unsigned int`**

- `L"%ld"` 如果 *值* 的類型為 **`long`**

- `L"%lu"` 如果 *值* 的類型為 **`unsigned long`**

- `L"%lld"` 如果 *值* 的類型為 **`long long`**

- `L"%llu"` 如果 *值* 的類型為 **`unsigned long long`**

- `L"%f"` 如果 *值* 是類型 **`float`** 或 **`double`**

- `L"%Lf"` 如果 *值* 的類型為 **`long double`**

函式會傳回 `wstring(Buf)`。

## <a name="see-also"></a>另請參閱

[\<string>](../standard-library/string.md)
