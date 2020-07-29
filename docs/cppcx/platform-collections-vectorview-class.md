---
title: Platform::Collections::VectorView 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
helpviewer_keywords:
- VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
ms.openlocfilehash: 207f5d517eaae475af1c65a284a3d1ebe50621af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218386"
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections::VectorView 類別

代表物件之循序集合的唯讀檢視，這些物件可透過索引加以個別存取。 集合中每個物件的類型，由樣板參數指定。

## <a name="syntax"></a>語法

```
template <typename T, typename E>
   ref class VectorView sealed;
```

#### <a name="parameters"></a>參數

*T*<br/>
`VectorView` 物件中包含的元素類型。

*版*<br/>
指定二元述詞，以測試是否與 `T`型別的值相等。 預設值是 `std::equal_to<T>`。

### <a name="remarks"></a>備註

類別會實 `VectorView` 作為[Windows：： Foundation：： collection：： IVectorView \<T> ](/uwp/api/windows.foundation.collections.ivectorview-1)介面，並支援標準範本程式庫反覆運算器。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[VectorView：： VectorView](#ctor)|初始化 VectorView 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[VectorView：： First](#first)|傳回迭代器，指定 VectorView 中的第一個項目。|
|[VectorView：： GetAt](#getat)|擷取由指定之索引所表示的目前 VectorView 項目。|
|[VectorView：： GetMany](#getmany)|由指定的索引處開始，從目前 VectorView 擷取一連串項目。|
|[VectorView：： IndexOf](#indexof)|在目前 VectorView 中搜尋指定的項目，如果找到，則傳回項目的索引。|
|[VectorView::Size](#size)|傳回目前 VectorView 物件中的項目數。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`VectorView`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="vectorviewfirst-method"></a><a name="first"></a>VectorView：： First 方法

傳回迭代器，指定 VectorView 中的第一個項目。

### <a name="syntax"></a>語法

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>傳回值

指定 VectorView 中第一個項目的迭代器。

### <a name="remarks"></a>備註

若要保留 First （）所傳回的反覆運算器，有一個方便的方式，就是將傳回值指派給使用類型推算關鍵字所宣告的變數 **`auto`** 。 例如： `auto x = myVectorView->First();` 。

## <a name="vectorviewgetat-method"></a><a name="getat"></a>VectorView：： GetAt 方法

擷取由指定之索引所表示的目前 VectorView 項目。

### <a name="syntax"></a>語法

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>參數

*指數*<br/>
以零起始、不帶正負號的整數，在 VectorView 物件中指定特別項目。

### <a name="return-value"></a>傳回值

`index` 參數指定的項目。 元素類型是由 VectorView 範本參數*T*所指定。

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a>VectorView：： GetMany 方法

由指定的索引處開始，從目前 VectorView 擷取一連串項目。

### <a name="syntax"></a>語法

```

virtual unsigned int GetMany(
   unsigned int startIndex,
   ::Platform::WriteOnlyArray<T>^ dest
);
```

### <a name="parameters"></a>參數

*startIndex*<br/>
要擷取之開始項目以零為起始的索引。

*dest*<br/>
當這項作業完成後，是項目陣列，從 `startIndex` 指定的項目開始，到 VectorView 的最後一個項目結束。

### <a name="return-value"></a>傳回值

擷取的項目數目。

## <a name="vectorviewindexof-method"></a><a name="indexof"></a>VectorView：： IndexOf 方法

在目前 VectorView 中搜尋指定的項目，如果找到，則傳回項目的索引。

### <a name="syntax"></a>語法

```

virtual bool IndexOf(
   T value,
   unsigned int* index
);
```

### <a name="parameters"></a>參數

*value*<br/>
要尋找的項目。

*指數*<br/>
如果找到參數 `value`，則為項目以零起始的索引，否則為 0。

如果*index*專案是的第一個元素， `VectorView` 或找不到專案，則索引參數為0。 如果傳回值為 **`true`** ，則會找到專案，而且它是第一個元素; 否則，找不到專案。

### <a name="return-value"></a>傳回值

**`true`** 如果找到指定的專案，則為，否則為 **`false`** 。

## <a name="vectorviewsize-method"></a><a name="size"></a>VectorView：： Size 方法

傳回目前 VectorView 物件中的項目數。

### <a name="syntax"></a>語法

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

目前 VectorView 中的項目數。

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a>VectorView：： VectorView 函式

初始化 VectorView 類別的新執行個體。

### <a name="syntax"></a>語法

```
VectorView();
explicit VectorView(
   UInt32 size
);
VectorView(
   UInt32 size,
   T value
);
explicit VectorView(
   const ::std::vector<T>& v
);
explicit VectorView(
   ::std::vector<T>&& v
);
VectorView(
   const T * ptr,
   UInt32 size
);

template <
   size_t N
>
explicit VectorView(
   const T (&arr)[N]
);

template <
   size_t N
>
explicit VectorView(
   const ::std::array<T,
   N>& a
);

explicit VectorView(
   const ::Platform::Array<T>^ arr
);

template <
   typename InIt
>
VectorView(
   InItfirst,
   InItlast
);

VectorView(
   std::initializer_list<T> il
);
```

### <a name="parameters"></a>參數

*初始*<br/>
用來初始化目前 VectorView 的物件集合類型。

*il*<br/>
[Std：： initializer_list](../standard-library/initializer-list-class.md)其元素將用來初始化 VectorView。

*N*<br/>
用來初始化目前 VectorView 之物件集合中的項目數。

*size*<br/>
VectorView 中的項目數。

*value*<br/>
用來初始化目前 VectorView 中各個項目的值。

*&*<br/>
用來初始化目前 VectorView 之[std：： vector](../standard-library/vector-class.md)的[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)。

*ptr*<br/>
用來初始化目前 VectorView 之 `std::vector` 的指標。

*arr*<br/>
用來初始化目前 VectorView 的[Platform：： Array](../cppcx/platform-array-class.md)物件。

*為*<br/>
用來初始化目前 VectorView 的[std：： array](../standard-library/array-class-stl.md)物件。

*first*<br/>
用來初始化目前 VectorView 之物件序列中的第一個項目。 的類型 `first` 是透過*完美轉送*的方式來傳遞。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*last*<br/>
用來初始化目前 VectorView 之物件序列中的最後一個項目。 的類型 `last` 是透過*完美轉送*的方式來傳遞。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)<br/>
[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
