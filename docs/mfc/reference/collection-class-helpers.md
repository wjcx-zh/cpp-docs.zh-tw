---
title: "集合類別 Helper |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.classes
dev_langs: C++
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 82b11c4cbe8f862121d89c308ab11d53582931d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="collection-class-helpers"></a>集合類別 Helper
集合類別`CMap`， `CList`，和`CArray`樣板化的全域 helper 函式用於等目的的比較、 複製和序列化項目。 為您的基礎類別實作的一部分`CMap`， `CList`，和`CArray`，您必須使用符合您地圖、 清單或陣列中儲存的資料類型的版本覆寫視需要這些函式。 如需覆寫 helper 函式時，例如`SerializeElements`，請參閱文章[集合： 如何製作類型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。 請注意， **ConstructElements**和**DestructElements**已被取代。  
  
 Microsoft Foundation 類別庫提供 afxtempl.h 來協助您自訂您的集合類別的下列全域函式：  
  
### <a name="collection-class-helpers"></a>集合類別 Helper  
  
|||  
|-|-|  
|[CompareElements](#compareelements)|表示項目是否相同。|  
|[CopyElements](#copyelements)|複製的項目一個陣列至另一個。|  
|[DumpElements](#dumpelements)|提供資料流導向診斷輸出。|  
|[HashKey](#hashkey)|計算的雜湊索引鍵。|  
|[SerializeElements](#serializeelements)|儲存或擷取項目，或從封存。|  
  
##  <a name="compareelements"></a>CompareElements  
 直接呼叫 [CList::Find] (clist class.md #not_found.md #clist__find 和間接[cmap__lookup](cmap-class.md#lookup)和[cmap__operator &#91; &#93;](cmap-class.md#operator_at)。  
  
```   
template<class TYPE, class ARG_TYPE>  
BOOL AFXAPI  
CompareElements(
    const TYPE* pElement1,  
    const ARG_TYPE* pElement2);  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 要比較的第一個項目類型。  
  
 `pElement1`  
 要比較的第一個元素的指標。  
  
 `ARG_TYPE`  
 要比較的第二個項目類型。  
  
 `pElement2`  
 要比較的第二個項目指標。  
  
### <a name="return-value"></a>傳回值  
 如果指向的物件則為非零`pElement1`所指向的物件等於`pElement2`; 否則為 0。  
  
### <a name="remarks"></a>備註  
 `CMap`呼叫使用`CMap`範本參數*金鑰*和`ARG_KEY`。  
  
 預設實作會傳回的比較結果的 *\*pElement1*和 *\*pElement2*。 因此，它會比較適合您的應用程式的方法中的項目，請覆寫此函數。  
  
 C + + 語言定義比較運算子 ( `==`) 的簡單型別 ( `char`， `int`， **float**等等)，但沒有定義比較運算子的類別和結構。 如果您想要使用`CompareElements`或具現化的其中一個使用該集合類別，您必須定義比較運算子，或多載`CompareElements`傳回適當的值的版本。  
  
### <a name="requirements"></a>需求  
   **Header:** afxtempl.h   
  
##  <a name="copyelements"></a>CopyElements  
 呼叫此函式是直接以[carray:: Append](carray-class.md#append)和[carray:: Copy](carray-class.md#copy)。  
  
```   
template<class TYPE>  
void AFXAPI CopyElements(
    TYPE* pDest,  
    const TYPE* pSrc,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定要複製之項目的類型的樣板參數。  
  
 `pDest`  
 指向項目複製目的地的指標。  
  
 `pSrc`  
 指向要複製項目之來源的指標。  
  
 `nCount`  
 要複製項目的數目。  
  
### <a name="remarks"></a>備註  
 預設實作會使用簡單指派運算子 (  **=**  ) 來執行複製作業。 如果要複製的類型沒有多載的 operator=，則預設實作會執行位元複製。  
  
 如需實作此函式和其他 helper 函式的資訊，請參閱文章[集合： 如何製作類型安全集合](../how-to-make-a-type-safe-collection.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxtempl.h  
  
##  <a name="dumpelements"></a>DumpElements  
 覆寫時，將集合的項目提供文字格式的資料流導向診斷的輸出。  
  
```   
template<class TYPE>  
void  AFXAPI DumpElements(
    CDumpContext& dc,  
    const TYPE* pElements,  
    INT_PTR nCount);  
```  
  
### <a name="parameters"></a>參數  
 `dc`  
 傾印內容傾印項目。  
  
 *型別*  
 指定的項目類型的樣板參數。  
  
 `pElements`  
 可傾印之項目的指標。  
  
 `nCount`  
 會傾印的項目數目。  
  
### <a name="remarks"></a>備註  
 **CArray::Dump**， **CList::Dump**，和**CMap::Dump**函式會呼叫這個如果傾印的深度大於 0。  
  
 預設實作不做任何動作。 如果您的集合的項目衍生自`CObject`，覆寫會通常逐一查看集合的項目，呼叫`Dump`中開啟每個元素。  
  

### <a name="requirements"></a>需求  
  **標頭**afxtempl.h  
  
##  <a name="hashkey"></a>HashKey  
 計算指定的索引鍵的雜湊值。  
  
```  
template<class ARG_KEY>  
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key); 
```  
  
### <a name="parameters"></a>參數  
 `ARG_KEY`  
 指定用來存取的對應索引鍵的資料類型的樣板參數。  
  
 `key`  
 雜湊值會計算索引鍵。  
  
### <a name="return-value"></a>傳回值  
 索引鍵的雜湊值。  
  
### <a name="remarks"></a>備註  
 呼叫此函式是直接以[CMap::RemoveKey](cmap-class.md#removekey)和間接[CMap::Lookup](cmap-class.md#lookup)和[CMap::Operator &#91; &#93;](cmap-class.md#operator_at)。
  
 預設實作會建立雜湊值的移位`key`的四個位置。 覆寫這個函式，使它傳回雜湊值適用於您的應用程式。  
  
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
  
##  <a name="serializeelements"></a>SerializeElements  
 [CArray](carray-class.md)， [CList](clist-class.md)，和[CMap](cmap-class.md)呼叫此函式可序列化的項目。  
  
```   
template<class TYPE>  
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定的項目類型的樣板參數。  
  
 `ar`  
 若要封存往或來自保存物件。  
  
 `pElements`  
 封存項目指標。  
  
 `nCount`  
 封存項目數目  
  
### <a name="remarks"></a>備註  
 預設實作未位元讀取或寫入。  
  
 如需實作此函式和其他 helper 函式的資訊，請參閱文章[集合： 如何製作類型安全集合](../how-to-make-a-type-safe-collection.md)。  
  
### <a name="example"></a>範例  
 請參閱文件中的範例[集合： 如何製作類型安全集合](../how-to-make-a-type-safe-collection.md)。  
 
### <a name="requirements"></a>需求  
  **標頭**afxtempl.h 
    
## <a name="see-also"></a>請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [CMap 類別](cmap-class.md)   
 [CList 類別](clist-class.md)   
 [CArray 類別](carray-class.md)