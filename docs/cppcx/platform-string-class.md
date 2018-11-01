---
title: Platform::String 類別
ms.date: 12/30/2016
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
ms.openlocfilehash: ef9838fa8a6a34eac1d2d3531ff93fb124c81d4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607034"
---
# <a name="platformstring-class"></a>Platform::String 類別

用來代表文字之 Unicode 字元的循序集合。 如需詳細資訊和範例，請參閱 <<c0> [ 字串](../cppcx/strings-c-cx.md)。

## <a name="syntax"></a>語法

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>迭代器

有兩個 Iterator 函式 (不是字串類別的成員) 可與 `std::for_each` 樣板搭配使用，以列舉 String 物件中的字元。

|成員|描述|
|------------|-----------------|
|`const char16* begin(String^ s)`|讓指標回到指定 String 物件的開頭。|
|`const char16* end(String^ s)`|讓指標回到指定 String 物件的結尾之後。|

### <a name="members"></a>成員

字串類別繼承自 Object 以及 IDisposable、IEquatable 與 IPrintable 介面。

字串類別也有下列幾種型别的成員。

**建構函式**

|成員|描述|
|------------|-----------------|
|[String::String](#ctor)|初始化字串類別的新執行個體。|

**方法**

字串類別會從 [Platform::Object Class](../cppcx/platform-object-class.md)繼承 Equals()、Finalize()、GetHashCode()、GetType()、MemberwiseClose() 與 ToString() 等方法。 字串也有下列方法。

|方法|描述|
|------------|-----------------|
|[String::Begin](#begin)|讓指標回到目前字串的開頭。|
|[String::CompareOrdinal](#compareordinal)|評估物件所代表之兩個字串值中的對應字元數值，藉以比較兩個 `String` 物件。|
|[String::Concat](#concat)|串連兩個 String 物件的值。|
|[String::Data](#data)|讓指標回到目前字串的開頭。|
|[String::Dispose](#dispose)|釋放或釋出資源。|
|[String::End](#end)|讓指標回到目前字串的結尾之後。|
|[String:: equals](#equals)|指出指定的物件是否等同於目前的物件。|
|[String::GetHashCode](#gethashcode)|傳回這個執行個體的雜湊碼。|
|[String::IsEmpty](#isempty)|指出目前 String 物件是否為空。|
|[String::IsFastPass](#isfastpass)|指出目前 String 物件會參與*快速傳遞*作業。 在快速傳遞作業時，參考計數會暫停。|
|[String::Length](#length)|擷取目前 String 物件的長度。|
|[String::ToString](#tostring)|傳回值與目前字串相同的 String 物件。|

**運算子**

字串類別具有下列運算子。

|成員|描述|
|------------|-----------------|
|[String:: operator = = 運算子](#operator-equality)|指出兩個指定的 String 物件是否具有相同的值。|
|[operator+ 運算子](#operator-plus)|將兩個 String 物件串連成新的 String 物件。|
|[String:: operator > 運算子](#operator-greater-than)|指出其中一個 String 物件的值是否大於另一個 String 物件的值。|
|[String:: operator > = 運算子](#operator-greater-than-or-equals)|指出其中一個 String 物件的值是否大於或等於另一個 String 物件的值。|
|[String:: operator ！ = 運算子](#operator-inequality)|指出兩個指定的 String 物件是否具有不同的值。|
|[String:: operator < 運算子](#operator-less-than)|指出其中一個 String 物件的值是否小於另一個 String 物件的值。|

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**標頭** ：vccorlib.h (預設包含)

## <a name="begin"></a>  String:: begin 方法

讓指標回到目前字串的開頭。

### <a name="syntax"></a>語法

```cpp
char16* Begin();
```

### <a name="return-value"></a>傳回值

位於目前字串開頭處的指標。

## <a name="compareordinal"></a>  String:: compareordinal 方法

評估物件所代表之兩個字串值中的對應字元數值，藉以比較兩個 `String` 物件。

### <a name="syntax"></a>語法

```cpp
int CompareOrdinal( String^ str1, String^ str2 );
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

## <a name="concat"></a>  String:: concat 方法

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

## <a name="data"></a>  String:: data 方法

傳回物件資料緩衝區開頭的指標當做 `char16` (`wchar_t`) 元素的 C-style 陣列。

### <a name="syntax"></a>語法

```
const char16* Data();
```

### <a name="return-value"></a>傳回值

開頭的指標`const char16`Unicode 字元陣列 (`char16`是 typedef `wchar_t`)。

### <a name="remarks"></a>備註

使用這個方法可從 `Platform::String^` 轉換為 `wchar_t*`。 當 `String` 物件超出範圍時，資料指標不再保證有效。 若要儲存對資料執行非原始的存留期`String`物件，請使用[wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)將陣列複製到您自行配置的記憶體。

## <a name="dispose"></a>  String:: dispose 方法

釋放或釋出資源。

### <a name="syntax"></a>語法

```cpp
virtual override void Dispose();
```

## <a name="end"></a>  String:: end 方法

讓指標回到目前字串的結尾之後。

### <a name="syntax"></a>語法

```cpp
char16* End();
```

### <a name="return-value"></a>傳回值

超過目前字串結尾的指標。

### <a name="remarks"></a>備註

End （） 傳回 begin （） + Length。

## <a name="equals"></a>  String:: equals 方法

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

**真**如果`str`等於目前的物件，否則**false**。

### <a name="remarks"></a>備註

這個方法相當於[string:: compareordinal](#compareordinal)。 在第一個多載中，`str` 參數應該可以轉換成 String^ 物件。

## <a name="gethashcode"></a>  String:: gethashcode 方法

傳回這個執行個體的雜湊碼。

### <a name="syntax"></a>語法

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>傳回值

這個執行個體的雜湊碼。

## <a name="isempty"></a>  String:: isempty 方法

指出目前 String 物件是否為空。

### <a name="syntax"></a>語法

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>傳回值

**true**如果目前`String`物件**null**或空字串 (L"")，否則**false**。

## <a name="isfastpass"></a>  String:: isfastpass 方法

指出目前 String 物件會參與*快速傳遞*作業。 在快速傳遞作業時，參考計數會暫停。

### <a name="syntax"></a>語法

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>傳回值

**真**如果目前`String`物件是快速傳遞; 否則為**false**。

### <a name="remarks"></a>備註

在呼叫函式時如果參考計數的物件是參數，而被呼叫的函式只讀取該物件，則編譯器可以安全地暫停參考計數，改善呼叫效能。 您的程式碼不需要處理這個屬性， 系統會處理所有的細節。

## <a name="length"></a>  String:: length 方法

擷取在目前的字元數目`String`物件。

### <a name="syntax"></a>語法

```cpp
unsigned int Length();
```

### <a name="return-value"></a>傳回值

在目前的字元數`String`物件。

### <a name="remarks"></a>備註

String 的長度，其中沒有字元為零。 以下字串的長度為 5：

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

所傳回的字元陣列[string:: data](#data)有一個額外的字元，也就是終止的 NULL 或 '\0'。 這個字元的長度也是兩個位元組。

## <a name="operator-plus"></a>  String:: operator + 運算子

串連兩個[字串](../cppcx/platform-string-class.md)至新的物件[字串](../cppcx/platform-string-class.md)物件。

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

**真**如果*str1*等於*str2*，否則**false**。

### <a name="remarks"></a>備註

這個運算子會建立 `String^` 物件，其中包含這兩個運算元的資料。 當極端的效能不重要時，可基於方便的理由使用它。 在函式中呼叫 "`+`" 幾次可能不會被注意到，但是，如果您在緊密迴圈中操作大型物件或文字資料，請使用標準 C++ 機制和類型。

##  <a name="operator-equality"></a> String:: operator = = 運算子

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

**true**如果的內容`str1`相等`str2`; 否則**false**。

### <a name="remarks"></a>備註

此運算子相當於[string:: compareordinal](#compareordinal)。

##  <a name="operator-greater-than"></a>  String::operator&gt;

指出是否其中一個值`String`物件是否大於第二個值`String`物件。

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

**true**如果的值`str1`的值大於`str2`; 否則**false**。

### <a name="remarks"></a>備註

這個運算子等於明確呼叫[string:: compareordinal](#compareordinal)並取得結果小於或等於零。

## <a name="operator-greater-than-or-equals"></a> String::operator&gt;=

指出是否其中一個值`String`物件是否大於或等於第二個值`String`物件。

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

**true**如果的值`str1`大於或等於值`str2`; 否則**false**。

## <a name="operator-inequality"></a> String:: operator ！ =

指出兩個指定`String`物件有不同的值。

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

**真**如果`str1`不等於`str2`，否則**false**。

## <a name="operator-less-than"></a> String:: operator&lt;

指出是否其中一個值`String`物件是否小於第二個值`String`物件。

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

**true**如果的值*str1*的值少於*str2*; 否則**false**。

## <a name="ctor"></a> String:: string 建構函式

初始化的新執行個體`String`複本的輸入的字串資料的類別。

### <a name="syntax"></a>語法

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>參數

*s*<br/>
初始設定字串的一系列寬字元。 char16

*n*<br/>
用以指定字串長度的數值。

### <a name="remarks"></a>備註

如果效能至關重要，而您控制在來源字串的存留期，您可以使用[platform:: stringreference](../cppcx/platform-stringreference-class.md)取代字串。
### <a name="example"></a>範例

```cpp
String^ s = L"Hello!";
```

## <a name="tostring"></a> String::ToString

傳回`String`物件，其值為與目前字串相同。

### <a name="syntax"></a>語法

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>傳回值

A`String`物件，其值為與目前字串相同。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](../cppcx/platform-namespace-c-cx.md)