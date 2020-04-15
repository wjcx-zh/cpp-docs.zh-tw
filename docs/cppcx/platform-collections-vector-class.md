---
title: Platform::Collections::Vector 類別
ms.date: 12/04/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Vector::Vector
- COLLECTION/Platform::Collections::Vector::Append
- COLLECTION/Platform::Collections::Vector::Clear
- COLLECTION/Platform::Collections::Vector::First
- COLLECTION/Platform::Collections::Vector::GetAt
- COLLECTION/Platform::Collections::Vector::GetMany
- COLLECTION/Platform::Collections::Vector::GetView
- COLLECTION/Platform::Collections::Vector::IndexOf
- COLLECTION/Platform::Collections::Vector::InsertAt
- COLLECTION/Platform::Collections::Vector::ReplaceAll
- COLLECTION/Platform::Collections::Vector::RemoveAt
- COLLECTION/Platform::Collections::Vector::RemoveAtEnd
- COLLECTION/Platform::Collections::Vector::SetAt
- COLLECTION/Platform::Collections::Vector::Size
- COLLECTION/Platform::Collections::Vector::VectorChanged
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
ms.openlocfilehash: b2d08461b4ab57ed8479549c18c35c872d0eb9f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354378"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector 類別

表示可依索引來個別存取的物件序列集合。 實[作 Windows:基礎:集合::I 可觀察Vector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_)以幫助進行 XAML[資料繫結](/windows/uwp/data-binding/data-binding-in-depth)。

## <a name="syntax"></a>語法

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>參數

*T*<br/>
Vector 物件中包含的元素型別。

*E*<br/>
指定二進位謂詞,用於使用*類型T*的值測試相等性。預設值為`std::equal_to<T>`。

### <a name="remarks"></a>備註

允許的類型為：

1. 整數

1. 介面類*

1. 公用 ref 類別^

1. value struct

1. 公用列舉類別

**Vector**類是[Windows::基礎:集合::iVector](/uwp/api/Windows.Foundation.Collections.IVector_T_)介面C++具體實現。

如果嘗試在公共返回值或參數中使用**Vector**類型,則引發編譯器錯誤 C3986。 您可以將參數或傳回值類型變更為 [Windows::Foundation::Collections::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_)來修正錯誤。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[向量:向量](#ctor)|初始化 Vector 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Vector::Append](#append)|在目前 Vector 的最後一個項目之後插入指定的項目。|
|[向量:清除](#clear)|刪除目前 Vector 的所有項目。|
|[向量:第一](#first)|傳回迭代器，指定 Vector 中的第一個項目。|
|[向量:getAt](#getat)|擷取由指定之索引所識別的目前 Vector 項目。|
|[向量:取得許多](#getmany)|從目前 Vector 中，由指定的索引處開始，擷取一連串項目。|
|[向量:取得檢視](#getview)|傳回 Vector 的唯讀檢視，也就是 [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)。|
|[向量:索引](#indexof)|在目前 Vector 中搜尋指定的項目，如果找到，則傳回項目的索引。|
|[Vector::InsertAt](#insertat)|在指定索引標識的元素處將指定項插入到當前向量中。|
|[Vector::ReplaceAll](#replaceall)|刪除目前 Vector 中的元素，然後從指定的陣列插入元素。|
|[Vector::RemoveAt](#removeat)|從目前向量中刪除指定索引所識別的元素。|
|[Vector::RemoveAtEnd](#removeatend)|刪除目前 Vector 結尾處的項目。|
|[Vector::SetAt](#setat)|在目前 Vector 中，將指定的值指派給由指定的索引所識別的元素。|
|[向量:大小](#size)|傳回目前 Vector 物件中的項目數。|

### <a name="events"></a>事件

|||
|-|-|
|名稱|描述|
|事件[視窗::基礎:集合:::向量更改\<事件 處理程式 T>= 向量更改](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|Vector 變更時發生。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Vector`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="vectorappend-method"></a><a name="append"></a>向量::追加方法

在目前 Vector 的最後一個項目之後插入指定的項目。

### <a name="syntax"></a>語法

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>參數

*指數*<br/>
要插入 Vector 中的項目。 *項的*類型由*T*類型名稱定義。

## <a name="vectorclear-method"></a><a name="clear"></a>向量:清除方法

刪除目前 Vector 的所有項目。

### <a name="syntax"></a>語法

```cpp
virtual void Clear();
```

## <a name="vectorfirst-method"></a><a name="first"></a>向量:第一種方法

傳回指向 Vector 中第一項元素的迭代器。

### <a name="syntax"></a>語法

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>傳回值

指向 Vector 中第一項元素的迭代器。

### <a name="remarks"></a>備註

保存 First() 傳回的反覆運算器的一個方便方法是將返回值分配給使用**自動**類型扣減關鍵字聲明的變數。 例如： `auto x = myVector->First();` 。 此迭代器知道集合的長度。

When you need a pair of iterators to pass to an STL function, use the free functions [Windows::Foundation::Collections::begin](../cppcx/begin-function.md) and [Windows::Foundation::Collections::end](../cppcx/end-function.md)

## <a name="vectorgetat-method"></a><a name="getat"></a>向量:GetAt 方法

擷取由指定之索引所識別的目前 Vector 項目。

### <a name="syntax"></a>語法

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>參數

*指數*<br/>
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

### <a name="return-value"></a>傳回值

*索引*參數指定的元素。 元素類型由*T*類型名稱定義。

## <a name="vectorgetmany-method"></a><a name="getmany"></a>向量:取得多種方法

從目前的 Vector 中，從指定的索引處開始，擷取一連串的項目，並將其複製到呼叫端配置的陣列中。

### <a name="syntax"></a>語法

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>參數

*startIndex*<br/>
要擷取之開始項目以零為起始的索引。

*dest*<br/>
調用方分配的項陣列,從*startIndex*指定的元素開始,到 Vector 中的最後一個元素結束。

### <a name="return-value"></a>傳回值

擷取的項目數目。

### <a name="remarks"></a>備註

此函式並非直接供用戶端程式碼使用。 它在[to_vector函數](../cppcx/to-vector-function.md)中內部使用,以便有效地轉換平臺::向量內量到std::vector 實例。

## <a name="vectorgetview-method"></a><a name="getview"></a>向量:取得檢視方法

傳回 Vector 的唯讀檢視，也就是 IVectorView。

### <a name="syntax"></a>語法

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>傳回值

IVectorView 物件。

## <a name="vectorindexof-method"></a><a name="indexof"></a>向量:方法索引

在目前 Vector 中搜尋指定的項目，如果找到，則傳回項目的索引。

### <a name="syntax"></a>語法

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>參數

*值*<br/>
要尋找的項目。

*指數*<br/>
如果找到參數*值*,則項的零基索引;否則,0。

如果項是 Vector 的第一個元素,或者未找到該項,*則索引*參數為 0。 如果返回值為**true,** 則找到項,它是第一個元素;否則,未找到該專案。

### <a name="return-value"></a>傳回值

如果找到指定的項,為 true;如果找到指定的項,則**為 true。** 否則,**假**。

### <a name="remarks"></a>備註

IndexOf 使用 std::find_if 尋找項目。 因此，自訂元素類型應多載 == 和 != 運算子，以啟用 find_if 所需的等號比較。

## <a name="vectorinsertat-method"></a><a name="insertat"></a>向量:插入方法

在指定索引標識的元素處將指定項插入到當前向量中。

### <a name="syntax"></a>語法

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>參數

*指數*<br/>
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

*項目*<br/>
要在*索引*指定的元素處插入到向量中的項。 *項的*類型由*T*類型名稱定義。

## <a name="vectorremoveat-method"></a><a name="removeat"></a>向量:刪除方法

從目前向量中刪除指定索引所識別的元素。

### <a name="syntax"></a>語法

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>參數

*指數*<br/>
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

## <a name="vectorremoveatend-method"></a><a name="removeatend"></a>向量::刪除 Atend 方法

刪除目前 Vector 結尾處的項目。

### <a name="syntax"></a>語法

```cpp
virtual void RemoveAtEnd();
```

## <a name="vectorreplaceall-method"></a><a name="replaceall"></a>向量::替換所有方法

刪除目前 Vector 中的元素，然後從指定的陣列插入元素。

### <a name="syntax"></a>語法

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>參數

*阿爾爾*<br/>
其類型由*T*類型名稱定義的物件的陣列。

## <a name="vectorsetat-method"></a><a name="setat"></a>向量:setat 方法

在目前 Vector 中，將指定的值指派給由指定的索引所識別的元素。

### <a name="syntax"></a>語法

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>參數

*指數*<br/>
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

*項目*<br/>
要指派給指定項目的值。 *項的*類型由*T*類型名稱定義。

## <a name="vectorsize-method"></a><a name="size"></a>向量:大小方法

傳回目前 Vector 物件中的項目數。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

目前 Vector 中的項目數。

## <a name="vectorvector-constructor"></a><a name="ctor"></a>向量:向量建構函數

初始化 Vector 類別的新執行個體。

### <a name="syntax"></a>語法

```cpp
Vector();

explicit Vector(unsigned int size);
Vector( unsigned int size, T value);
template <typename U> explicit Vector( const ::std::vector<U>& v);
template <typename U> explicit Vector( std::vector<U>&& v);

Vector( const T * ptr, unsigned int size);
template <size_t N> explicit Vector(const T(&arr)[N]);
template <size_t N> explicit Vector(const std::array<T, N>& a);
explicit Vector(const Array<T>^ arr);

template <typename InIt> Vector(InIt first, InIt last);
Vector(std::initializer_list<T> il);
```

### <a name="parameters"></a>參數

*a*<br/>
初始化向量的[std::陣列](../standard-library/array-class-stl.md)。

*阿爾爾*<br/>
[平臺:](../cppcx/platform-array-class.md)將用於初始化向量的陣列。

*Init*<br/>
用來初始化目前 Vector 的物件集合類型。

*I l*<br/>
用於初始化向量的*T*型物件的[std::initializer_list。](../standard-library/initializer-list-class.md)

*N*<br/>
用來初始化目前 Vector 之物件集合中的項目數。

*大小*<br/>
Vector 中的項目數。

*值*<br/>
用來初始化目前 Vector 中各個項目的值。

*五*<br/>
初始化目前向量的 l[值與 r 值](../cpp/lvalues-and-rvalues-visual-cpp.md)到[std::向量](../standard-library/vector-class.md)。

*Ptr*<br/>
用來初始化目前 Vector 之 `std::vector` 的指標。

*第一*<br/>
用來初始化目前 Vector 之物件序列中的第一個項目。 *第一*種是通過*完美的轉發*傳遞的。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*最後*<br/>
用來初始化目前 Vector 之物件序列中的最後一個項目。 *最後*一種是通過*完美的轉發*傳遞的。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另請參閱

[集合(C++/CX)](collections-c-cx.md)<br/>
[平台命名空間](platform-namespace-c-cx.md)<br/>
[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
