---
title: Collections 類別 |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- Vector Class (C++/Cx)
ms.assetid: aee8c076-9700-47c3-99b6-799fd3edb0ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aeaed487db1063efd14dddbca28480a169b13522
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686650"
---
# <a name="platformcollectionsvector-class"></a>Platform::Collections::Vector 類別

表示可依索引來個別存取的物件序列集合。

## <a name="syntax"></a>語法

```
template <typename T, typename E>
   ref class Vector sealed;
```

### <a name="parameters"></a>參數

*T*  
Vector 物件中包含的元素型別。

*E*  
指定二元述詞，來測試是否與類型的值相等*T*。預設值是 `std::equal_to<T>`。

### <a name="remarks"></a>備註

可使用的型別如下：

1. 整數

1. 介面類別 ^

1. 公用 ref 類別^

1. value struct

1. 公用列舉類別

**向量**類別是 c + + 具象實作[ivector&lt](/uwp/api/Windows.Foundation.Collections.IVector_T_)介面。

如果您嘗試使用**向量**類型在公用傳回值或參數，編譯器會引發的錯誤 C3986。 您可以修正錯誤，變更參數或傳回實值型別[ivector&lt](/uwp/api/Windows.Foundation.Collections.IVector_T_)。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Vector::Vector](#ctor)|初始化 Vector 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Vector::Append](#append)|在目前 Vector 的最後一個項目之後插入指定的項目。|
|[Vector::Clear](#clear)|刪除目前 Vector 的所有項目。|
|[Vector::First](#first)|傳回迭代器，指定 Vector 中的第一個項目。|
|[Vector::GetAt](#getat)|擷取由指定之索引所識別的目前 Vector 項目。|
|[Vector::GetMany](#getmany)|從目前 Vector 中，由指定的索引處開始，擷取一連串項目。|
|[Vector::GetView](#getview)|傳回 Vector 的唯讀檢視，也就是 [Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)。|
|[Vector::IndexOf](#indexof)|在目前 Vector 中搜尋指定的項目，如果找到，則傳回項目的索引。|
|[Vector::InsertAt](#insertat)|將指定的項目插入至目前 Vector 中，指定之索引所識別項目的後面。|
|[Vector::ReplaceAll](#replaceall)|刪除目前 Vector 中的元素，然後從指定的陣列插入元素。|
|[Vector::RemoveAt](#removeat)|從目前向量中刪除指定索引所識別的元素。|
|[Vector::RemoveAtEnd](#removeatend)|刪除目前 Vector 結尾處的項目。|
|[Vector::SetAt](#setat)|在目前 Vector 中，將指定的值指派給由指定的索引所識別的元素。|
|[Vector::Size](#size)|傳回目前 Vector 物件中的項目數。|

### <a name="events"></a>事件

|||
|-|-|
|名稱|描述|
|事件[Windows::Foundation::Collection::VectorChangedEventHandler\<T > ^ VectorChanged](/uwp/api/windows.foundation.collections.vectorchangedeventhandler)|Vector 變更時發生。|

## <a name="inheritance-hierarchy"></a>繼承階層

`Vector`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="append"></a>  Vector:: append 方法

在目前 Vector 的最後一個項目之後插入指定的項目。

### <a name="syntax"></a>語法

```cpp
virtual void Append(T item);
```

### <a name="parameters"></a>參數

*index*  
要插入 Vector 中的項目。 型別*項目*由此*T*類型名稱。

## <a name="clear"></a>  Vector:: clear 方法

刪除目前 Vector 的所有項目。

### <a name="syntax"></a>語法

```cpp
virtual void Clear();
```

## <a name="first"></a>  Vector:: first 方法

傳回指向 Vector 中第一項元素的迭代器。

### <a name="syntax"></a>語法

```cpp
virtual Windows::Foundation::Collections::IIterator <T>^ First();
```

### <a name="return-value"></a>傳回值

指向 Vector 中第一項元素的迭代器。

### <a name="remarks"></a>備註

若要保留 first （） 所傳回的迭代器的方便作法是將傳回的值指派給宣告的變數**自動**類型推斷關鍵字。 例如，`auto x = myVector->First();`。 此迭代器知道集合的長度。

當您需要一對迭代器，要傳遞至 STL 函式時，使用免費的函式[collections:: begin](../cppcx/begin-function.md)和[不](../cppcx/end-function.md)

## <a name="getat"></a>  Vector:: getat 方法

擷取由指定之索引所識別的目前 Vector 項目。

### <a name="syntax"></a>語法

```cpp
virtual T GetAt(unsigned int index);
```

### <a name="parameters"></a>參數

*index*  
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

### <a name="return-value"></a>傳回值

指定的項目*index*參數。 項目類型定義所*T*類型名稱。

## <a name="getmany"></a>  Vector:: getmany 方法

從目前的 Vector 中，從指定的索引處開始，擷取一連串的項目，並將其複製到呼叫端配置的陣列中。

### <a name="syntax"></a>語法

```cpp
virtual unsigned int GetMany(
    unsigned int startIndex,
    Platform::WriteOnlyArray<T>^ dest);
```

### <a name="parameters"></a>參數

*startIndex*  
要擷取之開始項目以零為起始的索引。

*dest*  
呼叫端配置的陣列所指定的項目開始的項目*startIndex*並在向量中最後一個項目結束。

### <a name="return-value"></a>傳回值

擷取的項目數目。

### <a name="remarks"></a>備註

此函式並非直接供用戶端程式碼使用。 它用於在內部[to_vector 函式](../cppcx/to-vector-function.md)以便有效率地轉換成 std:: vector 執行個體地將 platform。

## <a name="getview"></a>  Vector:: getview 方法

傳回 Vector 的唯讀檢視，也就是 IVectorView。

### <a name="syntax"></a>語法

```cpp
Windows::Foundation::Collections::IVectorView<T>^ GetView();
```

### <a name="return-value"></a>傳回值

IVectorView 物件。

## <a name="indexof"></a>  Vector:: indexof 方法

在目前 Vector 中搜尋指定的項目，如果找到，則傳回項目的索引。

### <a name="syntax"></a>語法

```cpp
virtual bool IndexOf(T value, unsigned int* index);
```

### <a name="parameters"></a>參數

*值*  
要尋找的項目。

*index*  
項目的以零為起始的索引若參數*值*找到; 否則即為 0。

*Index*參數為 0，如果項目是第一個向量的元素，或找不到項目。 如果傳回值為 `true`，表示找到符合項目，並且是第一個項目，否則表示找不到項目。

### <a name="return-value"></a>傳回值

如果找到指定的項目則為 `true`，否則為 `false`。

### <a name="remarks"></a>備註

IndexOf 使用 std::find_if 尋找項目。 因此，自訂元素類型應多載 == 和 != 運算子，以啟用 find_if 所需的等號比較。

##  <a name="insertat"></a>  Vector:: insertat 方法

將指定的項目插入至目前 Vector 中，指定之索引所識別項目的後面。

### <a name="syntax"></a>語法

```cpp
virtual void InsertAt(unsigned int index, T item)
```

### <a name="parameters"></a>參數

*index*  
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

*項目*  
要在指定的項目之後插入向量的項目*index*。 型別*項目*由此*T*類型名稱。

## <a name="removeat"></a>  Vector:: removeat 方法

從目前向量中刪除指定索引所識別的元素。

### <a name="syntax"></a>語法

```cpp
virtual void RemoveAt(unsigned int index);
```

### <a name="parameters"></a>參數

*index*  
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

## <a name="removeatend"></a>  Vector:: removeatend 方法

刪除目前 Vector 結尾處的項目。

### <a name="syntax"></a>語法

```cpp
virtual void RemoveAtEnd();
```

## <a name="replaceall"></a>  Vector:: replaceall 方法

刪除目前 Vector 中的元素，然後從指定的陣列插入元素。

### <a name="syntax"></a>語法

```cpp
virtual void ReplaceAll(const ::Platform::Array<T>^ arr);
```

### <a name="parameters"></a>參數

*arr*  
型別定義的物件陣列*T*類型名稱。

## <a name="setat"></a>  Vector:: setat 方法

在目前 Vector 中，將指定的值指派給由指定的索引所識別的元素。

### <a name="syntax"></a>語法

```cpp
virtual void SetAt(unsigned int index, T item);
```

### <a name="parameters"></a>參數

*index*  
以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。

*項目*  
要指派給指定項目的值。 型別*項目*由此*T*類型名稱。

## <a name="size"></a>  Vector:: size 方法

傳回目前 Vector 物件中的項目數。

### <a name="syntax"></a>語法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

目前 Vector 中的項目數。

## <a name="ctor"></a>  Vector:: vector 建構函式

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

*a*  
A [std:: array](../standard-library/array-class-stl.md) ，將會用來初始化 Vector。

*arr*  
A [platform:: array](../cppcx/platform-array-class.md) ，將會用來初始化 Vector。

*InIt*  
用來初始化目前 Vector 的物件集合類型。

*il*  
A [std:: initializer_list](../standard-library/initializer-list-class.md)之物件的型別*T* ，將會用來初始化 Vector。

*N*  
用來初始化目前 Vector 之物件集合中的項目數。

*size*  
Vector 中的項目數。

*值*  
用來初始化目前 Vector 中各個項目的值。

*v*  
[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)要[std:: vector](../standard-library/vector-class.md)用來初始化目前 Vector。

*ptr*  
用來初始化目前 Vector 之 `std::vector` 的指標。

*first*  
用來初始化目前 Vector 之物件序列中的第一個項目。 型別*第一*藉由傳遞*完美地轉送*。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*最後一個*  
用來初始化目前 Vector 之物件序列中的最後一個項目。 型別*上次*藉由傳遞*完美地轉送*。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)  
[在 c + + 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)  