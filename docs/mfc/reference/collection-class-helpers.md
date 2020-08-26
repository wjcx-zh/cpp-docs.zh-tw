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
ms.openlocfilehash: 04b142cde12a9795f217559f875eef7fcec3b0f2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841424"
---
# <a name="collection-class-helpers"></a>集合類別 Helper

集合類別 `CMap` 、 `CList` 和會使用樣板 `CArray` 化的全域 helper 函式，以做為比較、複製和序列化元素的目的。 當您根據、和來執行類別的過程中 `CMap` `CList` `CArray` ，您必須視需要覆寫這些函式，以及針對儲存在地圖、清單或陣列中的資料類型量身打造的版本。 如需覆寫 helper 函式（例如）的詳細資訊 `SerializeElements` ，請參閱文章 [集合：如何建立型別安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。 請注意， `ConstructElements` 和 `DestructElements` 已被取代。

MFC 程式庫在 afxtempl.h 中提供下列全域函數，以協助您自訂集合類別：

### <a name="collection-class-helpers"></a>集合類別 Helper

|名稱|描述|
|-|-|
|[CompareElements](#compareelements)|指出元素是否相同。|
|[CopyElements](#copyelements)|將專案從一個陣列複製到另一個陣列。|
|[DumpElements](#dumpelements)|提供資料流程導向的診斷輸出。|
|[HashKey](#hashkey)|計算雜湊索引鍵。|
|[SerializeElements](#serializeelements)|儲存或抓取封存的元素。|

## <a name="compareelements"></a><a name="compareelements"></a> CompareElements

由 [CList：： Find] 直接呼叫 (CList 類別. md # not_found md # clist__find，並 [cmap__lookup](cmap-class.md#lookup) 和 [cmap__operator &#91;&#93;](cmap-class.md#operator_at)間接進行。

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>參數

*TYPE*<br/>
要比較之第一個元素的型別。

*pElement1*<br/>
要比較之第一個元素的指標。

*ARG_TYPE*<br/>
要比較之第二個元素的類型。

*pElement2*<br/>
要比較之第二個元素的指標。

### <a name="return-value"></a>傳回值

如果 *pElement1* 所指向的物件等於 *pElement2*所指向的物件，則為非零。否則為0。

### <a name="remarks"></a>備註

`CMap`呼叫會使用 `CMap` 範本參數索引*鍵*和*ARG_KEY*。

預設的實值會傳回* \* pElement1*和* \* pElement2*的比較結果。 覆寫此函式，使其能以適合您應用程式的方式來比較元素。

C + + 語言會定義簡單類型的比較運算子 ( `==`)  (**`char`** 、 **`int`** 、 **`float`** 等等) 但是不會定義類別和結構的比較運算子。 如果您想要使用 `CompareElements` 或來具現化其中一個使用它的集合類別，您必須使用傳回適當值的版本來定義比較運算子或多載 `CompareElements` 。

### <a name="requirements"></a>規格需求

   **Header:** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a> CopyElements

[CArray：： Append](carray-class.md#append)和[CArray：： Copy](carray-class.md#copy)會直接呼叫這個函式。

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

預設的執行會使用簡單指派運算子 ( **=** ) 來執行複製作業。 如果要複製的類型沒有多載的 operator=，則預設實作會執行位元複製。

如需有關如何執行這項和其他 helper 函式的詳細資訊，請參閱文章 [集合：如何建立型別安全集合](../how-to-make-a-type-safe-collection.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxtempl.h。h

## <a name="dumpelements"></a><a name="dumpelements"></a> DumpElements

當覆寫時，為集合的元素提供文字形式的資料流程導向診斷輸出。

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>參數

*直流*<br/>
傾印元素的轉儲內容。

*TYPE*<br/>
範本參數，指定元素的類型。

*pElements*<br/>
要傾印之元素的指標。

*nCount*<br/>
要傾印的元素數目。

### <a name="remarks"></a>備註

如果傾印的 `CArray::Dump` 深度大於0，則、和函式 `CList::Dump` `CMap::Dump` 會呼叫此函數。

預設實作不做任何動作。 如果集合的專案衍生自 `CObject` ，您的覆寫通常會逐一查看集合的元素，然後再呼叫 `Dump` 每個元素。

### <a name="requirements"></a>規格需求

  **標頭** afxtempl.h。h

## <a name="hashkey"></a><a name="hashkey"></a> HashKey

計算指定索引鍵的雜湊值。

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

這個函式會直接由 [CMap：： RemoveKey](cmap-class.md#removekey) 呼叫，並由 [CMap：： Lookup](cmap-class.md#lookup) 和 [CMap：： Operator &#91;&#93;](cmap-class.md#operator_at)間接呼叫。

預設的執行方式是將索引 *鍵* 右移四個位置，以建立雜湊值。 覆寫此函式，使其傳回適用于您應用程式的雜湊值。

### <a name="example"></a>範例

```cpp
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
```

### <a name="requirements"></a>規格需求

  **標頭** afxtempl.h。h

## <a name="serializeelements"></a><a name="serializeelements"></a> SerializeElements

[CArray](carray-class.md)、 [CList](clist-class.md)和 [CMap](cmap-class.md) 會呼叫這個函式來序列化元素。

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>參數

*TYPE*<br/>
範本參數，指定元素的類型。

*Ar*<br/>
要封存至或從中封存的封存物件。

*pElements*<br/>
要封存之元素的指標。

*nCount*<br/>
要封存的元素數目

### <a name="remarks"></a>備註

預設的執行會進行位讀取或寫入。

如需有關如何執行這項和其他 helper 函式的詳細資訊，請參閱文章 [集合：如何建立型別安全集合](../how-to-make-a-type-safe-collection.md)。

### <a name="example"></a>範例

請參閱文章 [集合：如何建立型別安全集合](../how-to-make-a-type-safe-collection.md)中的範例。

### <a name="requirements"></a>規格需求

  **標頭** afxtempl.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CMap 類別](cmap-class.md)<br/>
[CList 類別](clist-class.md)<br/>
[CArray 類別](carray-class.md)
