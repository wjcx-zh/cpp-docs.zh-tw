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
ms.openlocfilehash: 7f12c7b926cd8d3d8fc892cff6f2245e7c216219
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032222"
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
指定二元述詞，以測試是否與 `T`型別的值相等。 預設值是 `std::equal_to<T>`。

### <a name="remarks"></a>備註

該`VectorView`類實現[Windows:基礎::集合::iVectorView\<T>](/uwp/api/windows.foundation.collections.ivectorview-1)介面,並支援標準範本庫反覆運算器。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[向量檢視:向量檢視](#ctor)|初始化 VectorView 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[向量檢視:第一](#first)|傳回迭代器，指定 VectorView 中的第一個項目。|
|[向量檢視:抓取](#getat)|擷取由指定之索引所表示的目前 VectorView 項目。|
|[向量檢視:抓取許多](#getmany)|由指定的索引處開始，從目前 VectorView 擷取一連串項目。|
|[向量檢視:索引](#indexof)|在目前 VectorView 中搜尋指定的項目，如果找到，則傳回項目的索引。|
|[VectorView::Size](#size)|傳回目前 VectorView 物件中的項目數。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`VectorView`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="vectorviewfirst-method"></a><a name="first"></a>向量檢視:第一種方法

傳回迭代器，指定 VectorView 中的第一個項目。

### <a name="syntax"></a>語法

```

virtual Windows::Foundation::Collections::IIterator<T>^
   First();
```

### <a name="return-value"></a>傳回值

指定 VectorView 中第一個項目的迭代器。

### <a name="remarks"></a>備註

保存 First() 傳回的反覆運算器的一個方便方法是將返回值分配給使用**自動**類型扣減關鍵字聲明的變數。 例如： `auto x = myVectorView->First();` 。

## <a name="vectorviewgetat-method"></a><a name="getat"></a>向量檢視:GetAt 方法

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

`index` 參數指定的項目。 元素類型由 VectorView 範本參數*T*指定。

## <a name="vectorviewgetmany-method"></a><a name="getmany"></a>向量檢視:抓取許多方法

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

## <a name="vectorviewindexof-method"></a><a name="indexof"></a>向量檢視:方法索引

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

如果項是 的第一個`VectorView`元素 ,或者未找到項,*則索引*參數為 0。 如果返回值為**true,** 則找到項,它是第一個元素;否則,未找到該專案。

### <a name="return-value"></a>傳回值

如果找到指定的項,為 true;如果找到指定的項,則**為 true。** 否則,**假**。

## <a name="vectorviewsize-method"></a><a name="size"></a>向量檢視:大小方法

傳回目前 VectorView 物件中的項目數。

### <a name="syntax"></a>語法

```

virtual property unsigned int Size;
```

### <a name="return-value"></a>傳回值

目前 VectorView 中的項目數。

## <a name="vectorviewvectorview-constructor"></a><a name="ctor"></a>向量檢視:向量檢視構造函數

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

*Init*<br/>
用來初始化目前 VectorView 的物件集合類型。

*I l*<br/>
[std::initializer_list](../standard-library/initializer-list-class.md)其元素將用於初始化 VectorView。

*N*<br/>
用來初始化目前 VectorView 之物件集合中的項目數。

*size*<br/>
VectorView 中的項目數。

*value*<br/>
用來初始化目前 VectorView 中各個項目的值。

*五*<br/>
初始化目前的 VectorView 的 l[值與 R 值](../cpp/lvalues-and-rvalues-visual-cpp.md)到[std::向量](../standard-library/vector-class.md)。

*Ptr*<br/>
用來初始化目前 VectorView 之 `std::vector` 的指標。

*阿爾爾*<br/>
平臺[:用於](../cppcx/platform-array-class.md)初始化當前 VectorView 的陣列物件。

*a*<br/>
用於初始化當前 VectorView 的[std::陣列](../standard-library/array-class-stl.md)物件。

*第一*<br/>
用來初始化目前 VectorView 之物件序列中的第一個項目。 的類型`first`是通過*完美的轉發*傳遞的。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

*最後*<br/>
用來初始化目前 VectorView 之物件序列中的最後一個項目。 的類型`last`是通過*完美的轉發*傳遞的。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="see-also"></a>另請參閱

[平台命名空間](platform-namespace-c-cx.md)<br/>
[在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
