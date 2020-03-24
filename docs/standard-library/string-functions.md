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
ms.openlocfilehash: dbcc4a86731bba092d8358a046fd3f9eb949f91f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214964"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt; 函式

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a><a name="getline"></a>  getline

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

*分隔符號*\
行的分隔符號。

### <a name="return-value"></a>傳回值

輸入資料流程*in_stream*。

### <a name="remarks"></a>備註

已標記的函式簽章對 `(1)` 從*in_stream*解壓縮字元，直到找到*分隔符號*為止，將它們儲存在*str*中。

標記為 `(2)` 的函式簽章配對會使用分行符號做為預設的行分隔符號，並以 `getline(in_stream, str, in_stream. widen('\n'))`的方式運作。

每對的第二個函式是第一個函式的類比，以支援 [rvalue 參考](../cpp/lvalues-and-rvalues-visual-cpp.md)。

當發生下列其中一項時，會停止擷取：

- 在檔案結尾，在這種情況下， *in_stream*的內部狀態旗標設為 `ios_base::eofbit`。

- 函式之後，會將比較等於*分隔符號*的元素解壓縮。 元素不會被放回或附加至受控制的序列。

- 函式在函式解壓縮 `str.`[max_size](../standard-library/basic-string-class.md#max_size)元素。 *In_stream*的內部狀態旗標設為 `ios_base::failbit`。

- 先前列出的其他錯誤，*in_stream*的內部狀態旗標設為 `ios_base::badbit`。

如需內部狀態旗標相關的資訊，請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)。

如果函式未解壓縮任何元素， *in_stream*的內部狀態旗標會設定為 `ios_base::failbit`。 在任何情況下，`getline` 都會傳回*in_stream*。

如果擲回例外狀況， *in_stream*和*str*會保持有效的狀態。

### <a name="example"></a>範例

下列程式碼示範兩種模式的 `getline()`：第一個使用預設的分隔符號 (新行)，第二個使用空白做為分隔符號。 檔案結尾字元 (鍵盤上的 Ctrl-Z 鍵) 用來控制 while 迴圈的終止。 這個值會將 `cin` 的內部狀態旗標設定為 `eofbit`，這必須使用[basic_ios：： clear （）](../standard-library/basic-ios-class.md#clear)清除，第二個 while 迴圈才能正常運作。

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

## <a name="stod"></a><a name="stod"></a>  stod

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

函式會將*str*中的專案序列轉換成類型的值 **`double`** 如同呼叫 `strtod( str.c_str(), _Eptr)`，其中 `_Eptr` 是函數內部的物件。 如果 `str.c_str() == *_Eptr`，它會擲回 `invalid_argument`類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會將 `*_Eptr -  str.c_str()` 儲存在 `*idx` 中，並傳回值。

## <a name="stof"></a><a name="stof"></a>  stof

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

函式會將*str*中的專案序列轉換成類型的值 **`float`** 如同呼叫 `strtof( str.c_str(), _Eptr)`，其中 `_Eptr` 是函數內部的物件。 如果 `str.c_str() == *_Eptr`，它會擲回 `invalid_argument`類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會將 `*_Eptr -  str.c_str()` 儲存在 `*idx` 中，並傳回值。

## <a name="stoi"></a><a name="stoi"></a>  stoi

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

*base*\
要使用的數字基底。

### <a name="remarks"></a>備註

函式 `stoi` 會將*str*中的字元序列轉換成 **`int`** 類型的值，並傳回值。 例如，若傳遞字元序列 "10"，則 `stoi` 的傳回值是整數 10。

`stoi` 的行為類似于以 `strtol( str.c_str(), _Eptr, idx)`方式呼叫單一位元組字元時的函式 `strtol`，其中 `_Eptr` 是函數內部的物件;或 `wcstol` 寬字元時，以類似的方式呼叫時，`wcstol(Str.c_str(), _Eptr, idx)`。 如需詳細資訊，請參閱[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)。

如果 `str.c_str() == *_Eptr`，`stoi` 會擲回 `invalid_argument`類型的物件。 如果這類呼叫會設定 `errno`，或傳回的值無法表示為 **`int`** 類型的物件，則會擲回 `out_of_range`類型的物件。 否則，如果*idx*不是 null 指標，此函式會將 `*_Eptr - str.c_str()` 儲存在 `*idx`中。

## <a name="stol"></a><a name="stol"></a>  stol

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

*base*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

長整數值。

### <a name="remarks"></a>備註

函式會將*str*中的專案序列轉換成類型的值 **`long`** 如同呼叫 `strtol( str.c_str(), _Eptr, idx)`，其中 `_Eptr` 是函數內部的物件。 如果 `str.c_str() == *_Eptr`，它會擲回 `invalid_argument`類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會將 `*_Eptr -  str.c_str()` 儲存在 `*idx` 中，並傳回值。

## <a name="stold"></a><a name="stold"></a>  stold

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

函式會將*str*中的專案序列轉換成類型的值 **`long double`** 如同呼叫 `strtold( str.c_str(), _Eptr)`，其中 `_Eptr` 是函數內部的物件。 如果 `str.c_str() == *_Eptr`，它會擲回 `invalid_argument`類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會將 `*_Eptr -  str.c_str()` 儲存在 `*idx` 中，並傳回值。

## <a name="stoll"></a><a name="stoll"></a>  stoll

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

*base*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

**`long long`** 值。

### <a name="remarks"></a>備註

函式會將*str*中的專案序列轉換成類型的值 **`long long`** 如同呼叫 `strtoll( str.c_str(), _Eptr, idx)`，其中 `_Eptr` 是函數內部的物件。 如果 `str.c_str() == *_Eptr`，它會擲回 `invalid_argument`類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會將 `*_Eptr -  str.c_str()` 儲存在 `*idx` 中，並傳回值。

## <a name="stoul"></a><a name="stoul"></a>  stoul

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

*base*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

不帶正負號的 long 整數值。

### <a name="remarks"></a>備註

函式會將*str*中的專案序列轉換成類型的值 **`unsigned long`** 如同呼叫 `strtoul( str.c_str(), _Eptr, idx)`，其中 `_Eptr` 是函數內部的物件。 如果 `str.c_str() == *_Eptr`，它會擲回 `invalid_argument`類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會將 `*_Eptr -  str.c_str()` 儲存在 `*idx` 中，並傳回值。

## <a name="stoull"></a><a name="stoull"></a>  stoull

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

*base*\
要使用的數字基底。

### <a name="return-value"></a>傳回值

**`unsigned long long`** 值。

### <a name="remarks"></a>備註

函式會將*str*中的專案序列轉換成類型的值 **`unsigned long long`** 如同呼叫 `strtoull( str.c_str(), _Eptr, idx)`，其中 `_Eptr` 是函數內部的物件。 如果 `str.c_str() == *_Eptr`，它會擲回 `invalid_argument`類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會將 `*_Eptr -  str.c_str()` 儲存在 `*idx` 中，並傳回值。

## <a name="swap"></a><a name="swap"></a> swap

交換兩個字串的字元陣列。

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
一個字串，其元素要與另一個字串的專案交換。

*right*\
另一個字串，其元素要與第一個字串交換。

### <a name="remarks"></a>備註

範本函式會執行 left 的特殊成員函*式*。針對字串的[swap](../standard-library/basic-string-class.md#swap)（*right*），可保證常數的複雜性。

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

## <a name="to_string"></a><a name="to_string"></a>  to_string

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

函式會將*值*轉換成陣列物件中儲存的專案序列，`Buf` 函數的內部，如同藉由呼叫 `sprintf(Buf, Fmt, value)`，其中 `Fmt` 為

- 如果*值*的類型為 **`int`** ，則 `"%d"`

- 如果*值*的類型為 **`unsigned int`** ，則 `"%u"`

- 如果*值*的類型為 **`long`** ，則 `"%ld"`

- 如果*值*的類型為 **`unsigned long`** ，則 `"%lu"`

- 如果*值*的類型為 **`long long`** ，則 `"%lld"`

- 如果*值*的類型為 **`unsigned long long`** ，則 `"%llu"`

- 如果*值*的類型 **`float`** 或 **`double`** ，則 `"%f"`

- 如果*值*的類型為 **`long double`** ，則 `"%Lf"`

此函式會傳回 `string(Buf)`。

## <a name="to_wstring"></a><a name="to_wstring"></a>  to_wstring

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

函式會將*值*轉換成陣列物件中儲存的專案序列，`Buf` 函數的內部，如同藉由呼叫 `swprintf(Buf, Len, Fmt, value)`，其中 `Fmt` 為

- 如果*值*的類型為 **`int`** ，則 `L"%d"`

- 如果*值*的類型為 **`unsigned int`** ，則 `L"%u"`

- 如果*值*的類型為 **`long`** ，則 `L"%ld"`

- 如果*值*的類型為 **`unsigned long`** ，則 `L"%lu"`

- 如果*值*的類型為 **`long long`** ，則 `L"%lld"`

- 如果*值*的類型為 **`unsigned long long`** ，則 `L"%llu"`

- 如果*值*的類型 **`float`** 或 **`double`** ，則 `L"%f"`

- 如果*值*的類型為 **`long double`** ，則 `L"%Lf"`

此函式會傳回 `wstring(Buf)`。

## <a name="see-also"></a>另請參閱

[\<string>](../standard-library/string.md)
