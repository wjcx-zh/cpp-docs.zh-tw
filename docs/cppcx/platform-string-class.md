---
title: Platform::String 類別
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
ms.openlocfilehash: 3c8c179c416ca744cace26cff3def0829f425664
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587927"
---
# <a name="platformstring-class"></a>Platform::String 類別

用來代表文字之 Unicode 字元的循序集合。 如需詳細資訊和範例，請參閱[字串](../cppcx/strings-c-cx.md)。

## <a name="syntax"></a>語法

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iterators

有兩個 Iterator 函式 (不是字串類別的成員) 可與 `std::for_each` 樣板搭配使用，以列舉 String 物件中的字元。

|成員|描述|
|------------|-----------------|
|`const char16* begin(String^ s)`|讓指標回到指定 String 物件的開頭。|
|`const char16* end(String^ s)`|讓指標回到指定 String 物件的結尾之後。|

### <a name="members"></a>Members

字串類別繼承自 Object 以及 IDisposable、IEquatable 與 IPrintable 介面。

字串類別也有下列幾種型别的成員。

**建構函式**

|成員|描述|
|------------|-----------------|
|[String：： String](#ctor)|初始化字串類別的新執行個體。|

**方法**

字串類別會從 [Platform::Object Class](../cppcx/platform-object-class.md)繼承 Equals()、Finalize()、GetHashCode()、GetType()、MemberwiseClose() 與 ToString() 等方法。 字串也有下列方法。

|方法|描述|
|------------|-----------------|
|[String：： Begin](#begin)|讓指標回到目前字串的開頭。|
|[String：： CompareOrdinal](#compareordinal)|評估物件所代表之兩個字串值中的對應字元數值，藉以比較兩個 `String` 物件。|
|[String：： Concat](#concat)|串連兩個 String 物件的值。|
|[字串：:D ata](#data)|讓指標回到目前字串的開頭。|
|[字串：:D ispose](#dispose)|釋放或釋出資源。|
|[String：： End](#end)|讓指標回到目前字串的結尾之後。|
|[String：： Equals](#equals)|指出指定的物件是否等同於目前的物件。|
|[String：： GetHashCode](#gethashcode)|傳回這個執行個體的雜湊碼。|
|[String：： IsEmpty](#isempty)|指出目前 String 物件是否為空。|
|[String：： IsFastPass](#isfastpass)|指出目前的字串物件是否參與*快速傳遞*作業。 在快速傳遞作業時，參考計數會暫停。|
|[String：： Length](#length)|擷取目前 String 物件的長度。|
|[String：： ToString](#tostring)|傳回值與目前字串相同的 String 物件。|

**運算子**

String 類別具有下列運算子。

|成員|描述|
|------------|-----------------|
|[String：： operator = = 運算子](#operator-equality)|指出兩個指定的字串物件是否有相同的值。|
|[operator+ 運算子](#operator-plus)|將兩個 String 物件串連成新的 String 物件。|
|[String：： operator > 運算子](#operator-greater-than)|指出其中一個 String 物件的值是否大於另一個 String 物件的值。|
|[String：： operator > = 運算子](#operator-greater-than-or-equals)|指出其中一個 String 物件的值是否大於或等於另一個 String 物件的值。|
|[String：： operator！ = 運算子](#operator-inequality)|指出兩個指定的字串物件是否有不同的值。|
|[String：： operator < 運算子](#operator-less-than)|指出其中一個 String 物件的值是否小於另一個 String 物件的值。|

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**標頭** ：vccorlib.h (預設包含)

## <a name="begin"></a>String：： Begin 方法

讓指標回到目前字串的開頭。

### <a name="syntax"></a>語法

```cpp
char16* Begin();
```

### <a name="return-value"></a>傳回值

位於目前字串開頭處的指標。

## <a name="compareordinal"></a>String：： CompareOrdinal 方法

靜態方法，藉由評估物件所代表之兩個字串值中對應字元的數值，來比較兩個 `String` 的物件。

### <a name="syntax"></a>語法

```cpp
static int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個 String 物件。

*str2*<br/>
第二個 String 物件。

### <a name="return-value"></a>傳回值

整數，表示兩個比較元 (Comparand) 之間的語彙關係。 下表列出可能的傳回值。

|值|條件|
|-----------|---------------|
|-1|`str1` 小於 `str2`。|
|0|`str1` 等於 `str2`。|
|1|`str1` 大於 `str2`。|

## <a name="concat"></a>String：： Concat 方法

串連兩個 String 物件的值。

### <a name="syntax"></a>語法

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個 String 物件，或 `null`。

*str2*<br/>
第二個 String 物件，或 `null`。

### <a name="return-value"></a>傳回值

由 `str1` 與 `str2` 兩者的值串連後得出其值的新 String^ 物件。

如果 `str1` 為 `null` 而 `str2` 不是，則會傳回 `str1`。 如果 `str2` 為 `null` 而 `str1` 不是，則會傳回 `str2`。 如果 `str1` 與 `str2` 都是 `null`，則會傳回空字串 (L"")。

## <a name="data"></a>字串：:D ata 方法

傳回物件資料緩衝區開頭的指標當做 `char16` (`wchar_t`) 元素的 C-style 陣列。

### <a name="syntax"></a>語法

```
const char16* Data();
```

### <a name="return-value"></a>傳回值

Unicode 字元 `const char16` 陣列開頭的指標（`char16` 是 `wchar_t` 的 typedef）。

### <a name="remarks"></a>備註

使用這個方法可從 `Platform::String^` 轉換為 `wchar_t*`。 當 `String` 物件超出範圍時，資料指標不再保證有效。 若要儲存超出原始 `String` 物件存留期的資料，請使用[wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)將陣列複製到您自行配置的記憶體中。

## <a name="dispose"></a>String：:D ispose 方法

釋放或釋出資源。

### <a name="syntax"></a>語法

```cpp
virtual override void Dispose();
```

## <a name="end"></a>String：： End 方法

讓指標回到目前字串的結尾之後。

### <a name="syntax"></a>語法

```cpp
char16* End();
```

### <a name="return-value"></a>傳回值

超過目前字串結尾的指標。

### <a name="remarks"></a>備註

End （）會傳回 Begin （） + Length。

## <a name="equals"></a>String：： Equals 方法

指出指定的字串是否擁有與目前物件相同的值。

### <a name="syntax"></a>語法

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>參數

*str*<br/>
要比較的物件。

### <a name="return-value"></a>傳回值

如果 `str` 等於目前的物件，則**為 true** ，否則為。否則**為 false**。

### <a name="remarks"></a>備註

這個方法相當於靜態[字串：： CompareOrdinal](#compareordinal)。 在第一個多載中，`str` 參數應該可以轉換成 String^ 物件。

## <a name="gethashcode"></a>String：： GetHashCode 方法

傳回這個執行個體的雜湊碼。

### <a name="syntax"></a>語法

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>傳回值

這個執行個體的雜湊碼。

## <a name="isempty"></a>String：： IsEmpty 方法

指出目前 String 物件是否為空。

### <a name="syntax"></a>語法

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>傳回值

如果目前 `String` 物件為**null**或空字串（L ""），則為**true** ;否則**為 false**。

## <a name="isfastpass"></a>String：： IsFastPass 方法

指出目前的字串物件是否參與*快速傳遞*作業。 在快速傳遞作業時，參考計數會暫停。

### <a name="syntax"></a>語法

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>傳回值

如果目前的 `String` 物件是快過去，則為**true** ;否則**為 false**。

### <a name="remarks"></a>備註

在呼叫函式時如果參考計數的物件是參數，而被呼叫的函式只讀取該物件，則編譯器可以安全地暫停參考計數，改善呼叫效能。 您的程式碼不需要處理這個屬性， 系統會處理所有的細節。

## <a name="length"></a>String：： Length 方法

抓取目前 `String` 物件中的字元數。

### <a name="syntax"></a>語法

```cpp
unsigned int Length();
```

### <a name="return-value"></a>傳回值

目前 `String` 物件中的字元數。

### <a name="remarks"></a>備註

String 的長度，其中沒有字元為零。 以下字串的長度為 5：

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

[字串：:D ata](#data)所傳回的字元陣列有一個額外的字元，也就是終止的 Null 或 ' \ 0 '。 這個字元的長度也是兩個位元組。

## <a name="operator-plus"></a>String：： operator + 運算子

將兩個[字串](../cppcx/platform-string-class.md)物件串連成新的[字串](../cppcx/platform-string-class.md)物件。

### <a name="syntax"></a>語法

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個 `String` 物件。

*str2*<br/>
第二個 `String` 物件，其內容將會附加至 `str1`。

### <a name="return-value"></a>傳回值

如果*str1*等於*str2*，則**為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

這個運算子會建立 `String^` 物件，其中包含這兩個運算元的資料。 當極端的效能不重要時，可基於方便的理由使用它。 在函式中呼叫 "`+`" 幾次可能不會被注意到，但是，如果您在緊密迴圈中操作大型物件或文字資料，請使用標準 C++ 機制和類型。

##  <a name="operator-equality"></a>String：： operator = = 運算子

指出兩個指定的 String 物件是否具有相同的文字值。

### <a name="syntax"></a>語法

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>參數

*str1*<br/>
要比較的第一個 `String` 物件。

*str2*<br/>
要比較的第二個 `String` 物件。

### <a name="return-value"></a>傳回值

如果 `str1` 的內容等於 `str2`，則為**true** ;否則**為 false**。

### <a name="remarks"></a>備註

這個運算子相當於[String：： CompareOrdinal](#compareordinal)。

##  <a name="operator-greater-than"></a>String：： operator &gt;

指出某個 `String` 物件的值是否大於第二個 `String` 物件的值。

### <a name="syntax"></a>語法

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個 `String` 物件。

*str2*<br/>
第二個 `String` 物件。

### <a name="return-value"></a>傳回值

如果 `str1` 的值大於 `str2` 的值，則為**true** ;否則**為 false**。

### <a name="remarks"></a>備註

這個運算子相當於明確呼叫[String：： CompareOrdinal](#compareordinal) ，並取得大於零的結果。

## <a name="operator-greater-than-or-equals"></a>String：： operator &gt; =

指出某個 `String` 物件的值是否大於或等於第二個 `String` 物件的值。

### <a name="syntax"></a>語法

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個 `String` 物件。

*str2*<br/>
第二個 `String` 物件。

### <a name="return-value"></a>傳回值

如果 `str1` 的值大於或等於 `str2` 的值，則為**true** ;否則**為 false**。

## <a name="operator-inequality"></a>String：： operator！ =

指出兩個指定的 `String` 物件是否有不同的值。

### <a name="syntax"></a>語法

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>參數

*str1*<br/>
要比較的第一個 `String` 物件。

*str2*<br/>
要比較的第二個 `String` 物件。

### <a name="return-value"></a>傳回值

如果 `str1` 不等於 `str2`，則為**true** ;否則**為 false**。

## <a name="operator-less-than"></a>String：： operator &lt;

指出某個 `String` 物件的值是否小於第二個 `String` 物件的值。

### <a name="syntax"></a>語法

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>參數

*str1*<br/>
第一個 `String` 物件。

*str2*<br/>
第二個 `String` 物件。

### <a name="return-value"></a>傳回值

如果*str1*的值小於*str2*的值，則為**true** ;否則**為 false**。

## <a name="ctor"></a>String：： String 函數

使用輸入字串資料的複本，初始化 `String` 類別的新實例。

### <a name="syntax"></a>語法

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>參數

*秒*<br/>
初始設定字串的一系列寬字元。 char16

*n*<br/>
用以指定字串長度的數值。

### <a name="remarks"></a>備註

如果效能非常重要，而且您控制來源字串的存留期，您可以使用[Platform：： StringReference](../cppcx/platform-stringreference-class.md)取代字串。
### <a name="example"></a>範例

```cpp
String^ s = L"Hello!";
```

## <a name="tostring"></a>String：： ToString

傳回其值與目前字串相同的 `String` 物件。

### <a name="syntax"></a>語法

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>傳回值

@No__t_0 物件，其值與目前的字串相同。

## <a name="see-also"></a>請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)
