---
title: "CArray 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CArray
dev_langs:
- C++
helpviewer_keywords:
- CArray class
- arrays [C++], classes
- templates, collection classes
- collection classes, template-based
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
caps.latest.revision: 33
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: bac8e08540ffead565d1097c6ef1efcae5e606c2
ms.lasthandoff: 02/24/2017

---
# <a name="carray-class"></a>CArray 類別
支援類似 C 陣列，但可以動態地減少或增加視的陣列。  
  
## <a name="syntax"></a>語法  
  
```  
template <class TYPE, class ARG_TYPE = const TYPE&>  
class CArray : public CObject  
```  
  
#### <a name="parameters"></a>參數  
 `TYPE`  
 指定儲存在陣列中的物件類型的樣板參數。 `TYPE`為參數，由`CArray`。  
  
 `ARG` *_* `TYPE`  
 樣板參數，指定用來存取儲存在陣列中的物件引數型別。 通常參考`TYPE`。 `ARG_TYPE`為參數傳遞至`CArray`。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CArray::CArray](#carray)|建構空陣列。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CArray::Add](#add)|將項目加入至陣列結尾；必要時讓陣列增長。|  
|[Carray:: Append](#append)|將其他陣列附加到陣列。如有必要，讓陣列成長|  
|[Carray:: Copy](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|  
|[CArray::ElementAt](#elementat)|傳回陣列中項目指標的臨時參考。|  
|[CArray::FreeExtra](#freeextra)|釋放超過目前上限的所有未使用記憶體。|  
|[CArray::GetAt](#getat)|傳回給定索引的值。|  
|[CArray::GetCount](#getcount)|取得此陣列中項目的數目。|  
|[CArray::GetData](#getdata)|容許存取陣列中的項目。 可以是**NULL**。|  
|[CArray::GetSize](#getsize)|取得此陣列中項目的數目。|  
|[CArray::GetUpperBound](#getupperbound)|傳回最大的有效索引。|  
|[CArray::InsertAt](#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|  
|[CArray::IsEmpty](#isempty)|判斷是否為空陣列。|  
|[CArray::RemoveAll](#removeall)|從此陣列移除所有項目。|  
|[CArray::RemoveAt](#removeat)|移除特定索引處的項目。|  
|[CArray::SetAt](#setat)|設定給定索引的值；不容許陣列成長。|  
|[CArray::SetAtGrow](#setatgrow)|設定給定索引的值；必要時讓陣列成長。|  
|[CArray::SetSize](#setsize)|設定此陣列中要包含的項目數目。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator&#91;&#93;](#operator_at)|設定或取得指定索引處的項目。|  
  
## <a name="remarks"></a>備註  
 陣列索引一定會開始於位置 0。 您可以決定是否要修正上限，或是啟用要展開，當您將新增項目超過目前的繫結的陣列。 記憶體配置連續上限，即使某些項目都是 null。  
  
> [!NOTE]
>  調整大小的大部分方法`CArray`物件，或新增項目，它使用[memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)移動項目。 這是問題，因為`memcpy_s`與任何需要的建構函式呼叫的物件不相容。 如果在項目`CArray`與不相容`memcpy_s`，您必須建立新`CArray`適當的大小。 然後，您必須使用[carray:: Copy](#copy)和[CArray::SetAt](#setat)來填入新的陣列，因為這些方法會使用指派運算子，而不是`memcpy_s`。  
  
 如同 C 陣列、 存取時間`CArray`索引的項目為常數，而且陣列大小無關。  
  
> [!TIP]
>  使用陣列時，才使用[SetSize](#setsize)來建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。  
  
 如果您需要傾印陣列中的個別項目，您必須設定的深度[CDumpContext](../../mfc/reference/cdumpcontext-class.md)為 1 或更大的物件。  
  
 全域 helper 函式，這個類別呼叫的特定成員函式必須是可自訂的大部分的使用`CArray`類別。 請參閱主題[集合類別 Helper](../../mfc/reference/collection-class-helpers.md) MFC 巨集和全域變數一節。  
  
 陣列類別衍生，就像是清單衍生。  
  
 如需有關如何使用`CArray`，請參閱文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CArray`  
  
## <a name="requirements"></a>需求  
 `Header:`afxtempl.h  
  
##  <a name="a-nameadda--carrayadd"></a><a name="add"></a>CArray::Add  
 將新的項目加入至陣列，陣列成長 1 結束。  
  
```  
INT_PTR Add(ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 `ARG_TYPE`  
 指定的引數參考此陣列中的項目類型的樣板參數。  
  
 `newElement`  
 要加入此陣列的項目。  
  
### <a name="return-value"></a>傳回值  
 加入項目的索引。  
  
### <a name="remarks"></a>備註  
 如果[SetSize](#setsize)已`nGrowBy`值大於 1，然後是額外的記憶體可配置。 不過，只有 1 將會增加上限。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&22;](../../mfc/codesnippet/cpp/carray-class_1.cpp)]  
  
##  <a name="a-nameappenda--carrayappend"></a><a name="append"></a>Carray:: Append  
 呼叫此成員函式，加入另一個陣列的內容。  
  
```  
INT_PTR Append(const CArray& src);
```  
  
### <a name="parameters"></a>參數  
 *src*  
 要附加至陣列元素的來源。  
  
### <a name="return-value"></a>傳回值  
 第一個附加的項目索引。  
  
### <a name="remarks"></a>備註  
 陣列必須是相同的型別。  
  
 如有必要，**附加**可能會配置額外的記憶體來容納附加至陣列的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&23;](../../mfc/codesnippet/cpp/carray-class_2.cpp)]  
  
##  <a name="a-namecarraya--carraycarray"></a><a name="carray"></a>CArray::CArray  
 建構空陣列。  
  
```  
CArray();
```  
  
### <a name="remarks"></a>備註  
 陣列會增加一個項目一次。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&24;](../../mfc/codesnippet/cpp/carray-class_3.cpp)]  
  
##  <a name="a-namecopya--carraycopy"></a><a name="copy"></a>Carray:: Copy  
 使用此成員函式複製到另一個陣列的元素。  
  
```  
void Copy(const CArray& src);
```  
  
### <a name="parameters"></a>參數  
 *src*  
 要複製到陣列項目的來源。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，以另一個陣列的項目覆寫一個陣列的元素。  
  
 **複製**不會釋放記憶體; 不過，如有必要，**複製**可能會配置額外的記憶體來容納的項目複製到陣列。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&25;](../../mfc/codesnippet/cpp/carray-class_4.cpp)]  
  
##  <a name="a-nameelementata--carrayelementat"></a><a name="elementat"></a>CArray::ElementAt  
 傳回指定的項目陣列中的臨時參考。  
  
```  
TYPE& ElementAt(INT_PTR nIndex);  
const TYPE& ElementAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 一個整數的索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。  
  
### <a name="return-value"></a>傳回值  
 陣列項目的參考。  
  
### <a name="remarks"></a>備註  
 它用來實作左邊的指派運算子為陣列。  
  
### <a name="example"></a>範例  
  請參閱範例[GetSize](#getsize)。  
  
##  <a name="a-namefreeextraa--carrayfreeextra"></a><a name="freeextra"></a>CArray::FreeExtra  
 任何額外的記憶體配置陣列已成長時，會釋出。  
  
```  
void FreeExtra();
```  
  
### <a name="remarks"></a>備註  
 此函式無效的大小和陣列的上限。  
  
### <a name="example"></a>範例  
  請參閱範例[GetData](#getdata)。  
  
##  <a name="a-namegetata--carraygetat"></a><a name="getat"></a>CArray::GetAt  
 傳回指定索引處的陣列元素。  
  
```  
TYPE& GetAt(INT_PTR nIndex);  
const TYPE& GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定的陣列元素的類型樣板參數。  
  
 `nIndex`  
 一個整數的索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。  
  
### <a name="return-value"></a>傳回值  
 在此索引目前陣列元素。  
  
### <a name="remarks"></a>備註  
 傳遞負數的值所傳回的值大於`GetUpperBound`會導致失敗的判斷提示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&26;](../../mfc/codesnippet/cpp/carray-class_5.cpp)]  
  
##  <a name="a-namegetcounta--carraygetcount"></a><a name="getcount"></a>CArray::GetCount  
 傳回陣列元素的數目。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 陣列中的項目數目。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來擷取陣列中的項目數。 以零為起始的索引，因為大小是 1 大於最大的索引。 呼叫這個方法會產生相同結果[CArray::GetSize](#getsize)方法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&27;](../../mfc/codesnippet/cpp/carray-class_6.cpp)]  
  
##  <a name="a-namegetdataa--carraygetdata"></a><a name="getdata"></a>CArray::GetData  
 使用此成員函式來直接存取陣列中的項目。  
  
```  
const TYPE* GetData() const; 
TYPE* GetData();
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定的陣列元素的類型樣板參數。  
  
### <a name="return-value"></a>傳回值  
 陣列項目的指標。  
  
### <a name="remarks"></a>備註  
 如果沒有項目可供使用，`GetData`會傳回 null 值。  
  
 雖然直接存取陣列的項目，協助您更快速地處理，請小心呼叫`GetData`; 您直接進行的任何錯誤會影響您的陣列的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&28;](../../mfc/codesnippet/cpp/carray-class_7.cpp)]  
  
##  <a name="a-namegetsizea--carraygetsize"></a><a name="getsize"></a>CArray::GetSize  
 傳回陣列的大小。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="remarks"></a>備註  
 以零為起始的索引，因為大小是 1 大於最大的索引。 呼叫這個方法會產生相同結果[CArray::GetCount](#getcount)方法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&29;](../../mfc/codesnippet/cpp/carray-class_8.cpp)]  
  
##  <a name="a-namegetupperbounda--carraygetupperbound"></a><a name="getupperbound"></a>CArray::GetUpperBound  
 傳回目前的上限，此陣列。  
  
```  
INT_PTR GetUpperBound() const;  
```  
  
### <a name="remarks"></a>備註  
 陣列索引是以零為起始，因為此函數會傳回 1 的值小於`GetSize`。  
  
 條件**GetUpperBound （)** =-1 表示陣列是否包含任何項目。  
  
### <a name="example"></a>範例  
  請參閱範例[CArray::GetAt](#getat)。  
  
##  <a name="a-nameinsertata--carrayinsertat"></a><a name="insertat"></a>CArray::InsertAt  
 第一版`InsertAt`陣列中指定索引處插入一個項目 （或多個項目的複本）。  
  
```  
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,  
    INT_PTR nCount = 1);
 
void InsertAt(
    INT_PTR nStartIndex,  
    CArray* pNewArray);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 可能會大於所傳回的值的整數索引`GetUpperBound`。  
  
 `ARG_TYPE`  
 在這個陣列中指定的項目類型的樣板參數。  
  
 `newElement`  
 要放在這個陣列中的項目。  
  
 `nCount`  
 這個項目應該是次數插入 （預設值為 1）。  
  
 `nStartIndex`  
 可能會大於所傳回的值的整數索引[GetUpperBound](#getupperbound)。  
  
 `pNewArray`  
 另一個陣列，包含要加入此陣列的項目。  
  
### <a name="remarks"></a>備註  
 在此程序，它會往上移動 （透過累加索引） 現有的項目，在此索引，並將其上方的所有項目。  
  
 第二個版本會將所有項目插入從另一個`CArray`集合，開始`nStartIndex`位置。  
  
 `SetAt`函式，相較之下，取代一個指定的陣列項目，並且不變更任何項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&30;](../../mfc/codesnippet/cpp/carray-class_9.cpp)]  
  
##  <a name="a-nameisemptya--carrayisempty"></a><a name="isempty"></a>CArray::IsEmpty  
 判斷是否為空陣列。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>傳回值  
 陣列會不包含任何項目; 如果為非零否則為 0。  
  
##  <a name="a-nameoperatorata--carrayoperator-"></a><a name="operator_at"></a>CArray::operator\[\]  
 這些註標運算子是很方便的替代[SetAt](#setat)和[GetAt](#getat)函式。  
  
```  
TYPE& operator[](int_ptr nindex);  
const TYPE& operator[](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 在這個陣列中指定的項目類型的樣板參數。  
  
 `nIndex`  
 若要存取的項目索引。  
  
### <a name="remarks"></a>備註  
 針對不是陣列的第一個運算子，呼叫**const**，可能會使用於權限 （右值） 或指派陳述式的左邊 （左值）。 第二個呼叫**const**陣列時，可能只能用在右邊。  
  
 程式庫的偵錯版本會判斷提示是否超出範圍的註標 （請在左側或右側指派陳述式）。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&34;](../../mfc/codesnippet/cpp/carray-class_10.cpp)]  
  
##  <a name="a-namerelocateelementsa--carrayrelocateelements"></a><a name="relocateelements"></a>CArray::RelocateElements  
 基底位址資料到新的緩衝區，當陣列應該成長或壓縮。  
  
```  
template<class TYPE, class ARG_TYPE>  
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,  
    const TYPE* pData,  
    INT_PTR nCount);
```  
  
### <a name="parameters"></a>參數  
 `pNewData`  
 新的緩衝區陣列的項目。  
  
 `pData`  
 舊的項目陣列。  
  
 `nCount`  
 舊陣列中的項目數目。  
  
### <a name="remarks"></a>備註  
 `pNewData`一律為足以容納所有`pData`項目。  
  
 [CArray](../../mfc/reference/carray-class.md)實作會使用這個方法來將舊資料複製到新的緩衝區陣列應該放大或縮小時 (當[SetSize](#setsize)或[FreeExtra](#freeextra)稱為)。 預設實作只會複製資料。  
  
 對於項目包含指向其中一個自己的成員，或另一個結構包含一個陣列元素的指標陣列，純文字複本不會更新指標。 在此情況下，您可以更正指標實作的特製化`RelocateElements`與相關的型別。 您也會負責將資料複製。  
  
##  <a name="a-nameremovealla--carrayremoveall"></a><a name="removeall"></a>CArray::RemoveAll  
 從此陣列移除所有項目。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>備註  
 如果陣列已經是空的函式仍能運作。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&31;](../../mfc/codesnippet/cpp/carray-class_11.cpp)]  
  
##  <a name="a-nameremoveata--carrayremoveat"></a><a name="removeat"></a>CArray::RemoveAt  
 移除陣列中的指定索引處開始的一或多個項目。  
  
```  
void RemoveAt(
    INT_PTR nIndex,  
    INT_PTR nCount = 1);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 一個整數的索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。  
  
 `nCount`  
 要移除的項目數目。  
  
### <a name="remarks"></a>備註  
 在過程中，它會將下移除的項目上方的所有項目。 它遞減右上陣列的繫結，但不是會釋放記憶體。  
  
 如果您嘗試移除比上述移除的點陣列中包含的項目，程式庫的偵錯版本會判斷提示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&32;](../../mfc/codesnippet/cpp/carray-class_12.cpp)]  
  
##  <a name="a-namesetata--carraysetat"></a><a name="setat"></a>CArray::SetAt  
 設定指定索引處的陣列元素。  
  
```  
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 一個整數的索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。  
  
 `ARG_TYPE`  
 指定用來參考陣列元素的引數的類型樣板參數。  
  
 `newElement`  
 新的項目值儲存在指定的位置。  
  
### <a name="remarks"></a>備註  
 `SetAt`不會造成要成長的陣列。 使用[SetAtGrow](#setatgrow)如果您想要自動成長的陣列。  
  
 您必須確定您的索引值，代表陣列中的有效位置。 如果它超出範圍時，程式庫的偵錯版本會判斷提示。  
  
### <a name="example"></a>範例  
  請參閱範例[GetAt](#getat)。  
  
##  <a name="a-namesetatgrowa--carraysetatgrow"></a><a name="setatgrow"></a>CArray::SetAtGrow  
 設定指定索引處的陣列元素。  
  
```  
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 大於或等於 0 的整數索引。  
  
 `ARG_TYPE`  
 陣列中指定的項目類型的樣板參數。  
  
 `newElement`  
 要加入此陣列的項目。 A **NULL**允許值。  
  
### <a name="remarks"></a>備註  
 必要時自動成長的陣列 （也就是以容納新項目調整上限）。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&33;](../../mfc/codesnippet/cpp/carray-class_13.cpp)]  
  
##  <a name="a-namesetsizea--carraysetsize"></a><a name="setsize"></a>CArray::SetSize  
 建立空的或現有的陣列; 的大小必要時，會配置記憶體。  
  
```  
void SetSize(
    INT_PTR nNewSize,  
    INT_PTR nGrowBy = -1);
```  
  
### <a name="parameters"></a>參數  
 `nNewSize`  
 新陣列的大小 （數字的項目）。 必須是大於或等於 0。  
  
 `nGrowBy`  
 配置大小增加時所需的項目位置的最小數目。  
  
### <a name="remarks"></a>備註  
 如果新的大小小於舊的大小，然後陣列會被截斷，並釋放所有未使用的記憶體。  
  
 若要設定您陣列的大小，開始使用陣列之前使用此函式。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。  
  
 `nGrowBy`參數會影響內部記憶體配置，而陣列成長。 其用途並不會影響陣列大小所報告[GetSize](#getsize)和[GetUpperBound](#getupperbound)。 如果使用預設值，MFC 會配置記憶體的方式計算，以避免記憶體分散程度並最佳化效率對大部分的情況。  
  
### <a name="example"></a>範例  
  請參閱範例[GetData](#getdata)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例收集](../../visual-cpp-samples.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObArray 類別](../../mfc/reference/cobarray-class.md)   
 [集合類別 Helper](../../mfc/reference/collection-class-helpers.md)

