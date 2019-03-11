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
ms.openlocfilehash: 02b5e15a816ec057bfb0a8201b7591e628c3ea2c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745293"
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

*E*<br/>
指定二元述詞，以測試是否與 `T`型別的值相等。 預設值為 `std::equal_to<T>`。

### <a name="remarks"></a>備註

`VectorView`類別會實作[2&gt;{3&gt;windows::foundation::collections::ivectorview&lt;t&lt;3}&lt;2}\<T >](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)介面，也支援標準樣板程式庫迭代器。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[VectorView::VectorView](#ctor)|初始化 VectorView 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[VectorView::First](#first)|傳回迭代器，指定 VectorView 中的第一個項目。|
|[VectorView::GetAt](#getat)|擷取由指定之索引所表示的目前 VectorView 項目。|
|[VectorView::GetMany](#getmany)|由指定的索引處開始，從目前 VectorView 擷取一連串項目。|
|[VectorView::IndexOf](#indexof)|在目前 VectorView 中搜尋指定的項目，如果找到，則傳回項目的索引。|
|[VectorView::Size](#size)|傳回目前 VectorView 物件中的項目數。|

## <a name="inheritance-hierarchy"></a>繼承階層

`VectorView`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="first"></a>  Vectorview:: First 方法

傳回迭代器，指定 VectorView 中的第一個項目。

### <a name="syntax"></a>語法

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>傳回值

指定 VectorView 中第一個項目的迭代器。

### <a name="remarks"></a>備註

若要保留 first （） 所傳回的迭代器的方便作法是將傳回的值指派給宣告的變數**自動**類型推斷關鍵字。 例如， `auto x = myVectorView->First();` 。

## <a name="getat"></a>  Vectorview:: Getat 方法

擷取由指定之索引所表示的目前 VectorView 項目。

### <a name="syntax"></a>語法

```

T GetAt(
   UInt32 index
);
```

### <a name="parameters"></a>參數

*index*<br/>
以零起始、不帶正負號的整數，在 VectorView 物件中指定特別項目。

### <a name="return-value"></a>傳回值


  `index` 參數指定的項目。 VectorView 範本參數所指定的項目類型*T*。

## <a name="getmany"></a>  Vectorview:: Getmany 方法

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

## <a name="indexof"></a>  Vectorview:: Indexof 方法

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

*index*<br/>
如果找到參數 `value`，則為項目以零起始的索引，否則為 0。

*Index*參數為 0，如果任一項目是第一個項目`VectorView`或找不到項目。 如果傳回的值是 **，則為 true**，找不到項目，而且它的第一個元素; 否則項目找不到。

### <a name="return-value"></a>傳回值

**真**找到則為指定的項目是否**false**。

## <a name="size"></a>  Vectorview:: Size 方法

傳回目前 VectorView 物件中的項目數。

### <a name="syntax"></a>語法

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

目前 VectorView 中的項目數。

## <a name="ctor"></a>  Vectorview:: Vectorview 建構函式

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

*InIt*<br/>
用來初始化目前 VectorView 的物件集合類型。

*il*<br/>
A [std:: initializer_list](../standard-library/initializer-list-class.md)其項目會用來初始化 VectorView。

*N*<br/>
用來初始化目前 VectorView 之物件集合中的項目數。

*size*<br/>
VectorView 中的項目數。

*value*<br/>
用來初始化目前 VectorView 中各個項目的值。

*v*<br/>
[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)要[std:: vector](../standard-library/vector-class.md)用來初始化目前 VectorView。

*ptr*<br/>
用來初始化目前 VectorView 之 `std::vector` 的指標。

*arr*<br/>
A [platform:: array](../cppcx/platform-array-class.md)用來初始化目前 VectorView 的物件。

*a*<br/>
A [std:: array](../standard-library/array-class-stl.md)用來初始化目前 VectorView 的物件。

*first*<br/>
用來初始化目前 VectorView 之物件序列中的第一個項目。 型別`first`藉由傳遞*完美地轉送*。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*last*<br/>
用來初始化目前 VectorView 之物件序列中的最後一個項目。 型別`last`藉由傳遞*完美地轉送*。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)<br/>
[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
