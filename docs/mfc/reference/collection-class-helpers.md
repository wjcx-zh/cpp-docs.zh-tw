---
title: 集合類別 Helper
ms.date: 11/04/2016
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 02bc5c5a7c1766c97d9a834c8b6b4dfb2a26ae82
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231789"
---
# <a name="collection-class-helpers"></a>集合類別 Helper

集合類別 `CMap` 、 `CList` 和會使用樣板 `CArray` 化的全域 helper 函式，以進行比較、複製和序列化專案的目的。 根據 `CMap` 、 `CList` 和 `CArray` ，您必須根據對應、清單或陣列中所儲存之資料類型量身打造的版本，視需要覆寫這些函式。 如需覆寫 helper 函式（例如）的相關資訊 `SerializeElements` ，請參閱文章[集合：如何建立型別安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。 請注意， `ConstructElements` 和已 `DestructElements` 被取代。

MFC 程式庫在 afxtempl.h 中提供下列全域函式，以協助您自訂集合類別：

### <a name="collection-class-helpers"></a>集合類別 Helper

|||
|-|-|
|[CompareElements](#compareelements)|指出元素是否相同。|
|[CopyElements](#copyelements)|將元素從一個陣列複製到另一個。|
|[DumpElements](#dumpelements)|提供串流導向的診斷輸出。|
|[HashKey](#hashkey)|計算雜湊索引鍵。|
|[SerializeElements](#serializeelements)|儲存或抓取封存的元素。|

## <a name="compareelements"></a><a name="compareelements"></a>CompareElements

會由 [CList：： Find] （CList not_found）直接呼叫，並由[cmap__lookup](cmap-class.md#lookup)和[cmap__operator &#91;&#93;](cmap-class.md#operator_at)間接地 clist__find。

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>參數

*TYPE*<br/>
要比較之第一個元素的類型。

*pElement1*<br/>
要比較之第一個元素的指標。

*ARG_TYPE*<br/>
要比較之第二個元素的類型。

*pElement2*<br/>
要比較之第二個元素的指標。

### <a name="return-value"></a>傳回值

如果*pElement1*所指向的物件等於*pElement2*所指向的物件，則為非零。否則為0。

### <a name="remarks"></a>備註

`CMap`呼叫會使用 `CMap` 範本參數索引*鍵*和*ARG_KEY*。

預設的實值會傳回* \* pElement1*和* \* pElement2*比較的結果。 覆寫此函式，使其能以適合您應用程式的方式來比較元素。

C + + 語言 `==` 會定義簡單類型（、、等）的比較運算子（）， **`char`** 但不 **`int`** **`float`** 會定義類別和結構的比較運算子。 如果您想要使用 `CompareElements` 或來具現化其中一個使用它的集合類別，您必須使用傳回適當值的版本來定義比較運算子或多載 `CompareElements` 。

### <a name="requirements"></a>需求

   **Header:** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a>CopyElements

此函式是由[CArray：： Append](carray-class.md#append)和[CArray：： Copy](carray-class.md#copy)直接呼叫。

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>參數

*TYPE*<br/>
指定要複製之項目的類型的樣板參數。

*pDest*<br/>
指向項目複製目的地的指標。

*.Psrc*<br/>
指向要複製項目之來源的指標。

*nCount*<br/>
要複製項目的數目。

### <a name="remarks"></a>備註

預設的實作為使用簡單指派運算子（ **=** ）來執行複製作業。 如果要複製的類型沒有多載的 operator=，則預設實作會執行位元複製。

如需有關如何執行這個和其他 helper 函式的詳細資訊，請參閱文章[集合：如何建立型別安全集合](../how-to-make-a-type-safe-collection.md)。

### <a name="requirements"></a>需求

  **標頭**afxtempl.h。h

## <a name="dumpelements"></a><a name="dumpelements"></a>DumpElements

當覆寫時，針對集合的元素提供以文字形式呈現的資料流程導向診斷輸出。

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>參數

*dc*<br/>
傾印元素的傾印內容。

*TYPE*<br/>
指定元素類型的範本參數。

*pElements*<br/>
要傾印之元素的指標。

*nCount*<br/>
要傾印的元素數目。

### <a name="remarks"></a>備註

如果傾印的 `CArray::Dump` 深度大於0，則、和函式 `CList::Dump` `CMap::Dump` 會呼叫此項。

預設實作不做任何動作。 如果集合的專案衍生自，則您的覆 `CObject` 寫通常會逐一查看集合的元素，然後 `Dump` 再針對每個專案呼叫。

### <a name="requirements"></a>需求

  **標頭**afxtempl.h。h

## <a name="hashkey"></a><a name="hashkey"></a>HashKey

計算給定索引鍵的雜湊值。

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>參數

*ARG_KEY*<br/>
範本參數，指定用來存取對應索引鍵的資料類型。

*key*<br/>
要計算其雜湊值的索引鍵。

### <a name="return-value"></a>傳回值

索引鍵的雜湊值。

### <a name="remarks"></a>備註

此函式是由[CMap：： RemoveKey](cmap-class.md#removekey)直接呼叫，並間接由[CMap：： Lookup](cmap-class.md#lookup)和[CMap：： Operator &#91;&#93;](cmap-class.md#operator_at)。

預設的執行會將索引*鍵*右移四個位置，以建立雜湊值。 覆寫此函式，使其傳回適用于您應用程式的雜湊值。

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

  **標頭**afxtempl.h。h

## <a name="serializeelements"></a><a name="serializeelements"></a>SerializeElements

[CArray](carray-class.md)、 [CList](clist-class.md)和[CMap](cmap-class.md)會呼叫這個函式來序列化元素。

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>參數

*TYPE*<br/>
指定元素類型的範本參數。

*ar*<br/>
要封存到或從中封存的封存物件。

*pElements*<br/>
要封存之元素的指標。

*nCount*<br/>
要封存的元素數目

### <a name="remarks"></a>備註

預設的執行會執行位讀取或寫入。

如需有關如何執行這個和其他 helper 函式的詳細資訊，請參閱文章[集合：如何建立型別安全集合](../how-to-make-a-type-safe-collection.md)。

### <a name="example"></a>範例

請參閱文章[集合：如何建立型別安全集合](../how-to-make-a-type-safe-collection.md)中的範例。

### <a name="requirements"></a>需求

  **標頭**afxtempl.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CMap 類別](cmap-class.md)<br/>
[CList 類別](clist-class.md)<br/>
[CArray 類別](carray-class.md)
