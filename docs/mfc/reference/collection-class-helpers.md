---
title: 集合類別 Helper
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.classes
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 3992e6c0cf25925e01858016e4bac93d5552fe8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373462"
---
# <a name="collection-class-helpers"></a>集合類別 Helper

集合類別`CMap`， `CList`，和`CArray`樣板化的全域 helper 函式用於這些用途，做為比較、 複製和序列化項目。 為您的基礎類別的實作的一部分`CMap`， `CList`，和`CArray`，您必須使用的資料儲存在您的對應、 清單或陣列類型量身打造的版本覆寫視這些函式。 如需覆寫協助程式函式時，這類`SerializeElements`，請參閱文章[集合：如何建立類型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。 請注意，`ConstructElements`和`DestructElements`已被取代。

Microsoft Foundation 類別庫提供 afxtempl.h 來協助您自訂您的集合類別中的下列全域函式：

### <a name="collection-class-helpers"></a>集合類別 Helper

|||
|-|-|
|[CompareElements](#compareelements)|表示項目是否相同。|
|[CopyElements](#copyelements)|複製的項目一個陣列至另一個。|
|[DumpElements](#dumpelements)|提供資料流導向診斷輸出。|
|[HashKey](#hashkey)|計算雜湊索引鍵。|
|[SerializeElements](#serializeelements)|儲存或擷取項目，或從封存。|

##  <a name="compareelements"></a>  CompareElements

直接呼叫 [CList::Find] (clist class.md #not_found.md #clist__find 和間接[cmap__lookup](cmap-class.md#lookup)並[cmap__operator &#91; &#93; ](cmap-class.md#operator_at)。

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>參數

*型別*<br/>
要比較的第一個項目類型。

*pElement1*<br/>
要比較的第一個元素的指標。

*ARG_TYPE*<br/>
要比較的第二個項目類型。

*pElement2*<br/>
要比較的第二個項目指標。

### <a name="return-value"></a>傳回值

如果指向的物件為非零*pElement1*所指向的物件等於*pElement2*，否則為 0。

### <a name="remarks"></a>備註

`CMap`呼叫使用`CMap`範本參數*金鑰*並*ARG_KEY*。

預設實作會傳回比較的結果 *\*pElement1*並 *\*pElement2*。 覆寫這個函式，使它比較適合您的應用程式的方式中的項目。

C++語言定義比較運算子 ( `==`) 的簡單型別 (**char**， **int**， **float**等等)，但沒有定義的比較類別和結構的運算子。 如果您想要使用`CompareElements`若要具現化其中一個使用它的集合類別，您必須定義比較運算子，或者多載或`CompareElements`版本會傳回適當的值。

### <a name="requirements"></a>需求

   **Header:** afxtempl.h

##  <a name="copyelements"></a>  CopyElements

藉由直接呼叫此函式[carray:: Append](carray-class.md#append)並[carray:: Copy](carray-class.md#copy)。

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>參數

*型別*<br/>
指定要複製之項目的類型的樣板參數。

*pDest*<br/>
指向項目複製目的地的指標。

*pSrc*<br/>
指向要複製項目之來源的指標。

*nCount*<br/>
要複製項目的數目。

### <a name="remarks"></a>備註

預設實作會使用簡單指派運算子 ( **=** ) 來執行複製作業。 如果要複製的類型沒有多載的 operator=，則預設實作會執行位元複製。

如需實作這個和其他 helper 函式的資訊，請參閱文章[集合：如何建立類型安全集合](../how-to-make-a-type-safe-collection.md)。

### <a name="requirements"></a>需求

  **標頭**afxtempl.h

##  <a name="dumpelements"></a>  DumpElements

以文字格式的資料流導向診斷輸出的項目提供您的集合時覆寫。

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>參數

*dc*<br/>
傾印內容傾印項目。

*型別*<br/>
指定的項目類型的樣板參數。

*pElements*<br/>
要傾印之項目的指標。

*nCount*<br/>
要傾印的元素數目。

### <a name="remarks"></a>備註

`CArray::Dump`， `CList::Dump`，和`CMap::Dump`函式會呼叫這個傾印的深度是否大於 0。

預設實作不做任何動作。 如果您集合的元素衍生自`CObject`，覆寫會通常逐一查看集合的項目，呼叫`Dump`中開啟每個元素。

### <a name="requirements"></a>需求

  **標頭**afxtempl.h

##  <a name="hashkey"></a>  HashKey

計算指定的索引鍵的雜湊值。

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>參數

*ARG_KEY*<br/>
指定用來存取地圖索引鍵的資料類型的樣板參數。

*key*<br/>
雜湊值會計算索引鍵。

### <a name="return-value"></a>傳回值

索引鍵的雜湊值。

### <a name="remarks"></a>備註

藉由直接呼叫此函式[CMap::RemoveKey](cmap-class.md#removekey)和間接[CMap::Lookup](cmap-class.md#lookup)並[CMap::Operator &#91; &#93; ](cmap-class.md#operator_at)。

預設實作會建立雜湊值移位*金鑰*權限是由四個位置。 覆寫這個函式，使它傳回雜湊值適用於您的應用程式。

### <a name="example"></a>範例

```cpp
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
```

### <a name="requirements"></a>需求

  **標頭**afxtempl.h

##  <a name="serializeelements"></a>  SerializeElements

[CArray](carray-class.md)， [CList](clist-class.md)，以及[CMap](cmap-class.md)呼叫此函式可序列化的項目。

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>參數

*型別*<br/>
指定的項目類型的樣板參數。

*ar*<br/>
若要封存或從封存物件。

*pElements*<br/>
封存項目指標。

*nCount*<br/>
封存項目數目

### <a name="remarks"></a>備註

預設實作會位元讀取或寫入。

如需實作這個和其他 helper 函式的資訊，請參閱文章[集合：如何建立類型安全集合](../how-to-make-a-type-safe-collection.md)。

### <a name="example"></a>範例

請參閱本文的範例[集合：如何建立類型安全集合](../how-to-make-a-type-safe-collection.md)。

### <a name="requirements"></a>需求

  **標頭**afxtempl.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CMap 類別](cmap-class.md)<br/>
[CList 類別](clist-class.md)<br/>
[CArray 類別](carray-class.md)
