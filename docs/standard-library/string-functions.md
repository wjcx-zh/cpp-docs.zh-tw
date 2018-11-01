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
ms.openlocfilehash: 7707f1239bb8612b1c454997a98d134165f09b75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544280"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt; 函式

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a>  getline

從輸入資料流一行一行地擷取字串。

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delim);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& is,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delim);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& is,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>參數

*is*<br/>
要擷取字串的輸入資料流。

*str*<br/>
要從輸入資料流讀取字元的字串。

*Delim*<br/>
行的分隔符號。

### <a name="return-value"></a>傳回值

輸入資料流*是*。

### <a name="remarks"></a>備註

一對函式簽章標示`(1)`擷取其字元*是*直到*delim*找到，則將它們儲存在*str*。

一對函式簽章標示`(2)`新行字元做為預設的行分隔符號，並表現**getline**(`is`， `str`， `is`。 `widen`(' `\n`'))。

每對的第二個函式是第一個函式的類比，以支援 [rvalue 參考](../cpp/lvalues-and-rvalues-visual-cpp.md)。

當發生下列其中一項時，會停止擷取：

- 在檔案結尾，在此情況下的內部狀態旗標*已*設定為`ios_base::eofbit`。

- 此函式擷取到與 `delim` 比較為相等的元素之後；在此情況下，不會將此元素放回或附加至受控制的序列。

- 在函式擷取`str.` [max_size](../standard-library/basic-string-class.md#max_size)項目，在其中案例的內部狀態旗標*會*設為`ios_base::failbit`。

- 以外的一些其他錯誤先前已列出，在此情況下的內部狀態旗標*是*設為 `ios_base::badbit`

如需內部狀態旗標相關的資訊，請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)。

如果函式未不擷取任何項目，內部狀態旗標*已*設定為`ios_base::failbit`。 在任何情況下，`getline`會傳回*是*。

如果擲回例外狀況，*已*並*str*處於有效狀態。

### <a name="example"></a>範例

下列程式碼示範兩種模式的 `getline()`：第一個使用預設的分隔符號 (新行)，第二個使用空白做為分隔符號。 檔案結尾字元 (鍵盤上的 Ctrl-Z 鍵) 用來控制 while 迴圈的終止。 這會將 `cin` 的內部狀態旗標設為 `eofbit`，必須先使用 [basic_ios::clear()](../standard-library/basic-ios-class.md#clear) 加以清除，第二個 while 迴圈才能正常運作。

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

## <a name="stod"></a>  stod

將字元序列**double**。

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

|參數|描述|
|---------------|-----------------|
|*str*|要轉換的字元序列。|
|*idx*|第一個未轉換的字元的索引值。|

### <a name="return-value"></a>傳回值

**Double**值。

### <a name="remarks"></a>備註

函式會轉換中的元素序列*str*的值`val`型別的**double**如同呼叫`strtod( str.c_str(), _Eptr)`，其中`_Eptr`是內部函式的物件。 如果 ` str.c_str() == *_Eptr`，其會擲回 `invalid_argument` 類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會`*_Eptr -  str.c_str()`中`*idx`，並傳回`val`。

## <a name="stof"></a>  stof

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

|參數|描述|
|---------------|-----------------|
|*str*|要轉換的字元序列。|
|*idx*|第一個未轉換的字元的索引值。|

### <a name="return-value"></a>傳回值

浮點值。

### <a name="remarks"></a>備註

函式會轉換中的元素序列*str*的值`val`型別的**float**如同呼叫`strtof( str.c_str(), _Eptr)`，其中`_Eptr`是內部函式的物件。 如果 ` str.c_str() == *_Eptr`，其會擲回 `invalid_argument` 類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會`*_Eptr -  str.c_str()`中`*idx`，並傳回`val`。

## <a name="stoi"></a>  stoi

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

|參數|描述|
|---------------|-----------------|
|*str*|要轉換的字元序列。|
|*idx*|傳回時包含第一個未轉換字元的索引。|
|*base*|要使用的數字基底。|

### <a name="remarks"></a>備註

函式`stoi`中的字元序列轉換*str*類型的值**int** ，並傳回值。 例如，若傳遞字元序列 "10"，則 `stoi` 的傳回值是整數 10。

以 `stoi` 呼叫時， `strtol` 運作起來就像單一位元組字元的 `strtol( str.c_str(), _Eptr, idx)` 函式，其中 `_Eptr` 是函式內部的物件；但以類似的方式 `wcstol` 呼叫時，則類似寬字元的 `wcstol(Str.c_str(), _Eptr, idx)` 函式。 如需詳細資訊，請參閱[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)。

如果`str.c_str() == *_Eptr`，`stoi`類型的物件就會擲回`invalid_argument`。 如果這類呼叫會設定`errno`，則傳回的值無法表示為型別的物件**int**，就會擲回的型別物件`out_of_range`。 否則，如果*idx*不是 null 指標，此函式會`*_Eptr - str.c_str()`在`*idx`。

## <a name="stol"></a>  stol

將字元序列**長**。

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

|參數|描述|
|---------------|-----------------|
|*str*|要轉換的字元序列。|
|*idx*|第一個未轉換的字元的索引值。|
|*base*|要使用的數字基底。|

### <a name="return-value"></a>傳回值

長整數值。

### <a name="remarks"></a>備註

函式會轉換中的元素序列*str*的值`val`型別的**long**如同呼叫`strtol( str.c_str(), _Eptr, idx)`，其中`_Eptr`是內部函式的物件。 如果 ` str.c_str() == *_Eptr`，其會擲回 `invalid_argument` 類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會`*_Eptr -  str.c_str()`中`*idx`，並傳回`val`。

## <a name="stold"></a>  stold

將字元序列**長雙精度**。

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*str*|要轉換的字元序列。|
|*idx*|第一個未轉換的字元的索引值。|

### <a name="return-value"></a>傳回值

**長雙精度**值。

### <a name="remarks"></a>備註

函式會轉換中的元素序列*str*的值`val`型別的**長雙精度**如同呼叫`strtold( str.c_str(), _Eptr)`，其中`_Eptr`是內部函式的物件。 如果 ` str.c_str() == *_Eptr`，其會擲回 `invalid_argument` 類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會`*_Eptr -  str.c_str()`中`*idx`，並傳回`val`。

## <a name="stoll"></a>  stoll

將字元序列**long long**。

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

|參數|描述|
|---------------|-----------------|
|*str*|要轉換的字元序列。|
|*idx*|第一個未轉換的字元的索引值。|
|*base*|要使用的數字基底。|

### <a name="return-value"></a>傳回值

**Long long**值。

### <a name="remarks"></a>備註

函式會轉換中的元素序列*str*的值`val`型別的**long long**如同呼叫`strtoll( str.c_str(), _Eptr, idx)`，其中`_Eptr`是內部函式的物件。 如果 ` str.c_str() == *_Eptr`，其會擲回 `invalid_argument` 類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會`*_Eptr -  str.c_str()`中`*idx`，並傳回`val`。

## <a name="stoul"></a>  stoul

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

|參數|描述|
|---------------|-----------------|
|*str*|要轉換的字元序列。|
|*idx*|第一個未轉換的字元的索引值。|
|*base*|要使用的數字基底。|

### <a name="return-value"></a>傳回值

不帶正負號的 long 整數值。

### <a name="remarks"></a>備註

函式會轉換中的元素序列*str*的值`val`型別的**unsigned long**如同呼叫`strtoul( str.c_str(), _Eptr, idx)`，其中`_Eptr`是內部函式的物件. 如果 ` str.c_str() == *_Eptr`，其會擲回 `invalid_argument` 類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會`*_Eptr -  str.c_str()`中`*idx`，並傳回`val`。

## <a name="stoull"></a>  stoull

將字元序列**unsigned long long**。

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

|參數|描述|
|---------------|-----------------|
|*str*|要轉換的字元序列。|
|*idx*|第一個未轉換的字元的索引值。|
|*base*|要使用的數字基底。|

### <a name="return-value"></a>傳回值

**Unsigned long long**值。

### <a name="remarks"></a>備註

函式會轉換中的元素序列*str*的值`val`型別的**unsigned long long**如同呼叫`strtoull( str.c_str(), _Eptr, idx)`，其中`_Eptr`是內部物件函式。 如果 ` str.c_str() == *_Eptr`，其會擲回 `invalid_argument` 類型的物件。 如果這類呼叫會設定 `errno`，其會擲回 `out_of_range` 類型的物件。 否則，如果*idx*不是 null 指標，此函式會`*_Eptr -  str.c_str()`中`*idx`，並傳回`val`。

## <a name="swap"></a>  swap

交換兩個字串的字元陣列。

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
一個字串，其元素要與另一個字串的元素進行交換。

*right*<br/>
另一個字串，其元素要與第一個字串交換。

### <a name="remarks"></a>備註

範本函式會執行特殊的成員函式*左*。[交換](../standard-library/basic-string-class.md#swap)(*右*) 針對字串，可保證常數的複雜性。

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

## <a name="to_string"></a>  to_string

將值轉換成 `string`。

```cpp
string to_string(int Val);
string to_string(unsigned int Val);
string to_string(long Val);
string to_string(unsigned long Val);
string to_string(long long Val);
string to_string(unsigned long long Val);
string to_string(float Val);
string to_string(double Val);
string to_string(long double Val);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*val*|要轉換的值。|

### <a name="return-value"></a>傳回值

表示值的 `string`。

### <a name="remarks"></a>備註

函式會轉換*Val*陣列物件中儲存的項目序列`Buf`函式內部如同呼叫`sprintf(Buf, Fmt, Val)`，其中`Fmt`是

- `"%d"` 如果`Val`具有類型**int**

- `"%u"` 如果`Val`具有類型**不帶正負號的 int**

- `"%ld"` 如果`Val`具有類型**長**

- `"%lu"` 如果`Val`具有類型**不帶正負號長時間**

- `"%lld"` 如果`Val`具有類型**long long**

- `"%llu"` 如果`Val`具有類型**unsigned long long**

- `"%f"` 如果`Val`具有類型**浮點數**或**double**

- `"%Lf"` 如果`Val`具有類型**長雙精度**

函式會傳回 `string(Buf)`。

## <a name="to_wstring"></a>  to_wstring

將值轉換成寬字串。

```cpp
wstring to_wstring(int Val);
wstring to_wstring(unsigned int Val);
wstring to_wstring(long Val);
wstring to_wstring(unsigned long Val);
wstring to_wstring(long long Val);
wstring to_wstring(unsigned long long Val);
wstring to_wstring(float Val);
wstring to_wstring(double Val);
wstring to_wstring(long double Val);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`Val`|要轉換的值。|

### <a name="return-value"></a>傳回值

表示值的寬字串。

### <a name="remarks"></a>備註

函式會將 `Val` 轉換為函式內部的 `Buf` 陣列物件所儲存的項目序列，就像呼叫 `swprintf(Buf, Len, Fmt, Val)` 一樣，其中 `Fmt` 為

- `L"%d"` 如果`Val`具有類型**int**

- `L"%u"` 如果`Val`具有類型**不帶正負號的 int**

- `L"%ld"` 如果`Val`具有類型**長**

- `L"%lu"` 如果`Val`具有類型**不帶正負號長時間**

- `L"%lld"` 如果`Val`具有類型**long long**

- `L"%llu"` 如果`Val`具有類型**unsigned long long**

- `L"%f"` 如果`Val`具有類型**浮點數**或**double**

- `L"%Lf"` 如果`Val`具有類型**長雙精度**

函式會傳回 `wstring(Buf)`。

## <a name="see-also"></a>另請參閱

[\<string>](../standard-library/string.md)<br/>
