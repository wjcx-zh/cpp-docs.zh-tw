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
ms.openlocfilehash: 05fe49a4d8e6de92c584d40f3871f3efb906c7c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374819"
---
# <a name="collection-class-helpers"></a>集合類別 Helper

集合類`CMap`、`CList`並`CArray`使用 範本化全域説明器函數,用於比較、複製和序列化元素等目的。 作為基於`CMap`的類實現的一部分`CList`,`CArray`必須根據需要使用根據地圖、清單或陣列中存儲的數據類型定製的版本來覆蓋這些函數。 有關重寫説明器函數的資訊,`SerializeElements`例如 ,請參閱文章[「集合:如何創建類型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)」。 請注意,`ConstructElements`並`DestructElements`已棄用。

Microsoft 基礎類庫在 afxtempl.h 中提供了以下全域函數,以説明您自定義集合類:

### <a name="collection-class-helpers"></a>集合類別 Helper

|||
|-|-|
|[CompareElements](#compareelements)|指示元素是否相同。|
|[CopyElements](#copyelements)|將元素從一個陣列複製到另一個陣列。|
|[DumpElements](#dumpelements)|提供面向流的診斷輸出。|
|[哈希基](#hashkey)|計算哈希鍵。|
|[SerializeElements](#serializeelements)|將元素存儲或檢索到存檔或從存檔中檢索。|

## <a name="compareelements"></a><a name="compareelements"></a>比較元素

直接調用 [CList::Find](clist-class.md.not_found.md_clist__find,由[cmap__lookup](cmap-class.md#lookup)和[cmap__operator &#91;&#93;](cmap-class.md#operator_at)間接調用。

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>參數

*類型*<br/>
要比較的第一個元素的類型。

*p元素1*<br/>
指向要比較的第一個元素的指標。

*ARG_TYPE*<br/>
要比較的第二個元素的類型。

*p元素2*<br/>
指向要比較的第二個元素的指標。

### <a name="return-value"></a>傳回值

如果*pElement1*指向的物件等於*pElement2*指向的物件,則非零;否則 0。

### <a name="remarks"></a>備註

呼叫`CMap``CMap`使用 樣本參數*KEY*和*ARG_KEY*。

默認實現返回*\*pElement1*和*\*pElement2*的比較結果。 重寫此函數,以便以適合應用程式的方式比較元素。

C++語言為簡單類型(**字元****、int、float**等)定義比較**float**運算符`==`(), 但不定義類和結構的比較運算符。 如果要使用`CompareElements`或實體化使用它的集合類之一,則必須定義比較運算元或使用傳回適當值的版本重載`CompareElements`。

### <a name="requirements"></a>需求

   **Header:** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a>複製元素

此函數由[CArray::追加和](carray-class.md#append) [CArray::copy](carray-class.md#copy)直接調用。

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>參數

*類型*<br/>
指定要複製之項目的類型的樣板參數。

*pDest*<br/>
指向項目複製目的地的指標。

*pSrc*<br/>
指向要複製項目之來源的指標。

*n( N) Count*<br/>
要複製項目的數目。

### <a name="remarks"></a>備註

預設實現使用簡單賦值運算符 ( **=** ) 執行複製操作。 如果要複製的類型沒有多載的 operator=，則預設實作會執行位元複製。

有關實現此函數和其他説明器函數的資訊,請參閱文章[「集合:如何創建類型安全集合](../how-to-make-a-type-safe-collection.md)」。

### <a name="requirements"></a>需求

  **頭**afxtempl.h

## <a name="dumpelements"></a><a name="dumpelements"></a>傾印元素

在重寫時,以文本形式為集合元素提供面向流的診斷輸出。

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>參數

*直流*<br/>
轉儲元素的轉儲上下文。

*類型*<br/>
指定元素類型的範本參數。

*p 元素*<br/>
指向要轉儲的元素的指標。

*n( N) Count*<br/>
要轉儲的元素數。

### <a name="remarks"></a>備註

如果轉儲的深度大於`CMap::Dump`0,`CArray::Dump`則調用 和 函數將調`CList::Dump`用此。

預設實作不做任何動作。 如果集合的元素派生自`CObject`,則重寫通常會遍轉集合的元素,依次調`Dump`用 每個元素。

### <a name="requirements"></a>需求

  **頭**afxtempl.h

## <a name="hashkey"></a><a name="hashkey"></a>哈希基

計算給定鍵的哈希值。

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>參數

*ARG_KEY*<br/>
指定用於存取對應鍵的資料類型的範本參數。

*關鍵*<br/>
要計算哈希值的鍵。

### <a name="return-value"></a>傳回值

鍵的哈希值。

### <a name="remarks"></a>備註

此函數由[CMap 直接呼叫::刪除Key,](cmap-class.md#removekey)並間接由[CMap::尋找](cmap-class.md#lookup)與[CMap:::運算子 &#91;&#93;](cmap-class.md#operator_at)。

預設實現通過將*鍵*向右移動四個位置來創建哈希值。 重寫此函數,以便返回適合應用程式的哈希值。

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

  **頭**afxtempl.h

## <a name="serializeelements"></a><a name="serializeelements"></a>序列化元素

[CArray、CList](carray-class.md)和[CMap](cmap-class.md)呼叫此函式來序列[CList](clist-class.md)化元素。

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>參數

*類型*<br/>
指定元素類型的範本參數。

*ar*<br/>
要存檔到或從存檔的存檔物件。

*p 元素*<br/>
指向要存檔的元素的指標。

*n( N) Count*<br/>
要歸檔的元素數

### <a name="remarks"></a>備註

預設實現執行位讀取或寫入。

有關實現此函數和其他説明器函數的資訊,請參閱文章[「集合:如何創建類型安全集合](../how-to-make-a-type-safe-collection.md)」。

### <a name="example"></a>範例

請參閱文章[「集合:如何創建類型安全集合」中](../how-to-make-a-type-safe-collection.md)的範例。

### <a name="requirements"></a>需求

  **頭**afxtempl.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CMap 類別](cmap-class.md)<br/>
[CList 類別](clist-class.md)<br/>
[CArray 類別](carray-class.md)
