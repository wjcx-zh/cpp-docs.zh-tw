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
ms.openlocfilehash: 5a35efb3ca1590931ce1db5fd12d7c930b258286
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218399"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector 類別

表示可依索引來個別存取的物件序列集合。 實行[Windows：： Foundation：： collection：： IObservableVector](/uwp/api/windows.foundation.collections.iobservablevector-1)以協助進行 XAML[資料](/windows/uwp/data-binding/data-binding-in-depth)系結。

## <a name="syntax"></a>語法

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>參數

*T*<br/>
Vector 物件中包含的元素型別。

*版*<br/>
指定一個二元述詞，以測試是否相等於類型*T*的值。預設值是 `std::equal_to<T>` 。

### <a name="remarks"></a>備註

允許的類型為：

1. integers

1. 介面類別別 ^

1. 公用 ref 類別^

1. value struct

1. 公用列舉類別

**Vector**類別是[Windows：： Foundation：： Collection：： IVector](/uwp/api/windows.foundation.collections.ivector-1)介面的 c + + 具體執行。

如果您嘗試在公用傳回值或參數中使用**向量**類型，則會引發編譯器錯誤則 c3986。 您可以將參數或傳回值類型變更為 [Windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1)來修正錯誤。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[Vector：： Vector](#ctor)|初始化 Vector 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[Vector::Append](#append)|在目前 Vector 的最後一個項目之後插入指定的項目。|
|[Vector：： Clear](#clear)|刪除目前 Vector 的所有項目。|
|[Vector：： First](#first)|傳回迭代器，指定 Vector 中的第一個項目。|
|[Vector：： GetAt](#getat)|擷取由指定之索引所識別的目前 Vector 項目。|
|[Vector：： GetMany](#getmany)|從目前 Vector 中，由指定的索引處開始，擷取一連串項目。|
|[Vector：： GetView](#getview)|傳回 Vector 的唯讀檢視，也就是 [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)。|
|[Vector：： IndexOf](#indexof)|在目前 Vector 中搜尋指定的項目，如果找到，則傳回項目的索引。|
|[Vector::InsertAt](#insertat)|將指定的專案插入目前向量的指定索引所識別的元素。|
|[Vector::ReplaceAll](#replaceall)|刪除目前 Vector 中的元素，然後從指定的陣列插入元素。|
|[Vector::RemoveAt](#removeat)|從目前向量中刪除指定索引所識別的元素。|
|[Vector::RemoveAtEnd](#removeatend)|刪除目前 Vector 結尾處的項目。|
|[Vector::SetAt](#setat)|在目前 Vector 中，將指定的值指派給由指定的索引所識別的元素。|
|[Vector：： Size](#size)|傳回目前 Vector 物件中的項目數。|

### <a name="events"></a>事件

|||
|-|-|
|名稱|說明|
|事件[Windows：： Foundation：： Collection：： VectorChangedEventHandler \<T> ^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1)|Vector 變更時發生。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Vector`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="vectorappend-method"></a><a name="append"></a>Vector：： Append 方法

在目前 Vector 的最後一個項目之後插入指定的項目。

### <a name="syntax"></a>語法

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>參數

*指數*<br/>
要插入 Vector 中的項目。 *專案*的類型是由*T* typename 所定義。

## <a name="vectorclear-method"></a><a name="clear"></a>Vector：： Clear 方法

刪除目前 Vector 的所有項目。

### <a name="syntax"></a>語法

```cpp
virtual void Clear();
```

## <a name="vectorfirst-method"></a><a name="first"></a>Vector：： First 方法

傳回指向 Vector 中第一項元素的迭代器。

### <a name="syntax"></a>語法

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>傳回值

指向 Vector 中第一項元素的迭代器。

### <a name="remarks"></a>備註

若要保留 First （）所傳回的反覆運算器，有一個方便的方式，就是將傳回值指派給使用類型推算關鍵字所宣告的變數 **`auto`** 。 例如： `auto x = myVector->First();` 。 此迭代器知道集合的長度。

當您需要一組要傳遞至 STL 函式的反覆運算器時，請使用[Windows：： Foundation：： collection：： begin](../cppcx/begin-function.md)和[Windows：： foundation：： collection：： end](../cppcx/end-function.md)函數的 free 函式。

## <a name="vectorgetat-method"></a><a name="getat"></a>Vector：： GetAt 方法

擷取由指定之索引所識別的目前 Vector 項目。

### <a name="syntax"></a>語法

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>參數

*指數*<br/>
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

### <a name="return-value"></a>傳回值

*索引*參數所指定的元素。 元素類型是由*T* typename 所定義。

## <a name="vectorgetmany-method"></a><a name="getmany"></a>Vector：： GetMany 方法

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
呼叫端配置的專案陣列，從*startIndex*指定的元素開始，並在向量的最後一個元素結束。

### <a name="return-value"></a>傳回值

擷取的項目數目。

### <a name="remarks"></a>備註

此函式並非直接供用戶端程式碼使用。 它會在[to_vector](../cppcx/to-vector-function.md)函式內部使用，以有效率地將 Platform：： vector 實例轉換為 std：： vector 實例。

## <a name="vectorgetview-method"></a><a name="getview"></a>Vector：： GetView 方法

傳回 Vector 的唯讀檢視，也就是 IVectorView。

### <a name="syntax"></a>語法

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>傳回值

IVectorView 物件。

## <a name="vectorindexof-method"></a><a name="indexof"></a>Vector：： IndexOf 方法

在目前 Vector 中搜尋指定的項目，如果找到，則傳回項目的索引。

### <a name="syntax"></a>語法

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>參數

*value*<br/>
要尋找的項目。

*指數*<br/>
如果找到參數*值*，則為專案以零為基底的索引;否則為0。

如果專案是向量的第一個元素，或找不到專案，則*索引*參數為0。 如果傳回值為 **`true`** ，則會找到專案，而且它是第一個元素; 否則，找不到專案。

### <a name="return-value"></a>傳回值

**`true`** 如果找到指定的專案，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

IndexOf 使用 std::find_if 尋找項目。 因此，自訂元素類型應多載 == 和 != 運算子，以啟用 find_if 所需的等號比較。

## <a name="vectorinsertat-method"></a><a name="insertat"></a>Vector：： InsertAt 方法

將指定的專案插入目前向量的指定索引所識別的元素。

### <a name="syntax"></a>語法

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>參數

*指數*<br/>
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

*item*<br/>
要插入向量的專案，該元素是由*index*所指定。 *專案*的類型是由*T* typename 所定義。

## <a name="vectorremoveat-method"></a><a name="removeat"></a>Vector：： RemoveAt 方法

從目前向量中刪除指定索引所識別的元素。

### <a name="syntax"></a>語法

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>參數

*指數*<br/>
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

## <a name="vectorremoveatend-method"></a><a name="removeatend"></a>Vector：： RemoveAtEnd 方法

刪除目前 Vector 結尾處的項目。

### <a name="syntax"></a>語法

```cpp
virtual void RemoveAtEnd();
```

## <a name="vectorreplaceall-method"></a><a name="replaceall"></a>Vector：：型全部型方法

刪除目前 Vector 中的元素，然後從指定的陣列插入元素。

### <a name="syntax"></a>語法

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>參數

*arr*<br/>
物件的陣列，其類型是由*T* typename 所定義。

## <a name="vectorsetat-method"></a><a name="setat"></a>Vector：： SetAt 方法

在目前 Vector 中，將指定的值指派給由指定的索引所識別的元素。

### <a name="syntax"></a>語法

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>參數

*指數*<br/>
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

*item*<br/>
要指派給指定項目的值。 *專案*的類型是由*T* typename 所定義。

## <a name="vectorsize-method"></a><a name="size"></a>Vector：： Size 方法

傳回目前 Vector 物件中的項目數。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

目前 Vector 中的項目數。

## <a name="vectorvector-constructor"></a><a name="ctor"></a>Vector：： Vector 函數

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

*為*<br/>
將用來初始化 Vector 的[std：： array](../standard-library/array-class-stl.md) 。

*arr*<br/>
將用來初始化 Vector 的[Platform：： Array](../cppcx/platform-array-class.md) 。

*初始*<br/>
用來初始化目前 Vector 的物件集合類型。

*il*<br/>
將用來初始化向量之*T*類型物件的[std：： initializer_list](../standard-library/initializer-list-class.md) 。

*N*<br/>
用來初始化目前 Vector 之物件集合中的項目數。

*size*<br/>
Vector 中的項目數。

*value*<br/>
用來初始化目前 Vector 中各個項目的值。

*&*<br/>
用來初始化目前 Vector 之[std：： vector](../standard-library/vector-class.md)的[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)。

*ptr*<br/>
用來初始化目前 Vector 之 `std::vector` 的指標。

*first*<br/>
用來初始化目前 Vector 之物件序列中的第一個項目。 *第一個*類型是透過*完美轉送*的方式傳遞。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*last*<br/>
用來初始化目前 Vector 之物件序列中的最後一個項目。 *最後一*種方式是透過*完美轉送*來傳遞。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另請參閱

[集合（c + +/CX）](collections-c-cx.md)<br/>
[Platform 命名空間](platform-namespace-c-cx.md)<br/>
[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
