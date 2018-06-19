---
title: CArray 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
dev_langs:
- CPP
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4e4e4fd0106687927706b0ba303035258de7e651
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357179"
---
# <a name="carray-class"></a>CArray 類別
支援類似 C 陣列，但可以動態減少或增加視的陣列。  
  
## <a name="syntax"></a>語法  
  
```  
template <class TYPE, class ARG_TYPE = const TYPE&>  
class CArray : public CObject  
```  
  
#### <a name="parameters"></a>參數  
 `TYPE`  
 指定儲存在陣列中的物件類型的樣板參數。 `TYPE` 為參數，由`CArray`。  
  
 `ARG` *_* `TYPE`  
 指定用來存取儲存在陣列中物件的引數類型的樣板參數。 通常參考`TYPE`。 `ARG_TYPE` 為參數傳遞給`CArray`。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CArray::CArray](#carray)|建構空陣列。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CArray::Add](#add)|將項目加入至陣列結尾；必要時讓陣列增長。|  
|[Carray:: Append](#append)|將其他陣列附加至陣列。如有必要，讓陣列成長|  
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
 陣列索引一律從開始位置 0。 您可以決定是否要修正上限，或是啟用以展開，當您新增超過目前的繫結項目陣列。 記憶體配置連續的上限，即使某些項目都是 null。  
  
> [!NOTE]
>  調整大小的大部分方法`CArray`物件或加入項目，它使用[memcpy_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)来移動的項目。 這是一個問題，因為`memcpy_s`不相容的任何要求所要呼叫建構函式的物件。 如果中的項目`CArray`與不相容`memcpy_s`，您必須建立新`CArray`適當的大小。 然後，您必須使用[carray:: Copy](#copy)和[CArray::SetAt](#setat)來填入新的陣列，因為這些方法會使用指派運算子，而不是`memcpy_s`。  
  
 如同 C 陣列、 存取時間`CArray`索引的項目是常數，而且陣列大小無關。  
  
> [!TIP]
>  使用陣列，之前先使用[SetSize](#setsize)建立其大小，並為它配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。  
  
 如果您需要在陣列中的個別項目的傾印，您必須設定的深度[CDumpContext](../../mfc/reference/cdumpcontext-class.md)為 1 或更大的物件。  
  
 全域 helper 函式，這個類別呼叫的特定成員函式必須是可自訂的大部分的使用`CArray`類別。 請參閱主題[集合類別 Helper](../../mfc/reference/collection-class-helpers.md) MFC 巨集和全域變數的區段中。  
  
 陣列類別衍生，就像衍生清單。  
  
 如需有關如何使用`CArray`，請參閱文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CArray`  
  
## <a name="requirements"></a>需求  
 `Header:` afxtempl.h  
  
##  <a name="add"></a>  CArray::Add  
 將新的項目加入至陣列，1 成長陣列的結尾。  
  
```  
INT_PTR Add(ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 `ARG_TYPE`  
 指定的參考項目，這個陣列中的引數類型的樣板參數。  
  
 `newElement`  
 要加入此陣列的項目。  
  
### <a name="return-value"></a>傳回值  
 加入項目的索引。  
  
### <a name="remarks"></a>備註  
 如果[SetSize](#setsize)已搭配`nGrowBy`值大於 1，則額外的記憶體可以配置。 不過，只有 1 提高上限。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]  
  
##  <a name="append"></a>  Carray:: Append  
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
 [!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]  
  
##  <a name="carray"></a>  CArray::CArray  
 建構空陣列。  
  
```  
CArray();
```  
  
### <a name="remarks"></a>備註  
 陣列逐漸增加一個項目，一次。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]  
  
##  <a name="copy"></a>  Carray:: Copy  
 使用此成員函式複製到另一個陣列的項目。  
  
```  
void Copy(const CArray& src);
```  
  
### <a name="parameters"></a>參數  
 *src*  
 要複製到陣列之項目的來源。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，另一個陣列的項目以覆寫一個陣列的項目。  
  
 **複製**不會釋放記憶體; 不過，如有必要，**複製**可能會配置額外的記憶體來容納的項目複製到陣列。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]  
  
##  <a name="elementat"></a>  CArray::ElementAt  
 傳回指定的項目陣列中的臨時參考。  
  
```  
TYPE& ElementAt(INT_PTR nIndex);  
const TYPE& ElementAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 整數索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。  
  
### <a name="return-value"></a>傳回值  
 陣列項目的參考。  
  
### <a name="remarks"></a>備註  
 它用來實作的左側的指派運算子的陣列。  
  
### <a name="example"></a>範例  
  請參閱範例的[GetSize](#getsize)。  
  
##  <a name="freeextra"></a>  CArray::FreeExtra  
 釋出時已成長陣列配置任何額外的記憶體。  
  
```  
void FreeExtra();
```  
  
### <a name="remarks"></a>備註  
 此函式會有任何影響陣列的大小或上限。  
  
### <a name="example"></a>範例  
  請參閱範例的[GetData](#getdata)。  
  
##  <a name="getat"></a>  CArray::GetAt  
 傳回指定索引處的陣列元素。  
  
```  
TYPE& GetAt(INT_PTR nIndex);  
const TYPE& GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定的陣列元素的類型樣板參數。  
  
 `nIndex`  
 整數索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。  
  
### <a name="return-value"></a>傳回值  
 在這個索引的目前陣列項目。  
  
### <a name="remarks"></a>備註  
 傳遞負數的值所傳回的值大於`GetUpperBound`會導致失敗的判斷提示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]  
  
##  <a name="getcount"></a>  CArray::GetCount  
 傳回陣列元素的數目。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 陣列中的項目數目。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以擷取陣列中的項目數。 因為索引會以零為起始，大小為 1 大於最大的索引。 呼叫這個方法會產生相同結果[CArray::GetSize](#getsize)方法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]  
  
##  <a name="getdata"></a>  CArray::GetData  
 您可以使用此成員函式來直接存取陣列中的項目。  
  
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
 如果沒有元素可用`GetData`會傳回 null 值。  
  
 雖然直接存取陣列的項目可協助您更快速地處理，請呼叫時謹慎小心`GetData`; 您直接進行的任何錯誤會影響您陣列的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]  
  
##  <a name="getsize"></a>  CArray::GetSize  
 傳回陣列的大小。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="remarks"></a>備註  
 因為索引會以零為起始，大小為 1 大於最大的索引。 呼叫這個方法會產生相同結果[CArray::GetCount](#getcount)方法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]  
  
##  <a name="getupperbound"></a>  CArray::GetUpperBound  
 傳回目前的上限，此陣列。  
  
```  
INT_PTR GetUpperBound() const;  
```  
  
### <a name="remarks"></a>備註  
 因為是以零為起始的陣列索引，此函數會傳回值 1 小於`GetSize`。  
  
 條件**GetUpperBound （)** =-1 表示陣列是否包含任何項目。  
  
### <a name="example"></a>範例  
  請參閱範例的[CArray::GetAt](#getat)。  
  
##  <a name="insertat"></a>  CArray::InsertAt  
 第一個版本`InsertAt`陣列中指定索引處插入一個項目 （或多個項目的複本）。  
  
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
 這個陣列中指定的項目類型的樣板參數。  
  
 `newElement`  
 要放在這個陣列的項目。  
  
 `nCount`  
 這個項目應該是次數插入 （預設值為 1）。  
  
 `nStartIndex`  
 可能會大於所傳回的值的整數索引[GetUpperBound](#getupperbound)。  
  
 `pNewArray`  
 另一個陣列，包含要加入至這個陣列的項目。  
  
### <a name="remarks"></a>備註  
 在過程中，它會往上移動這個索引及它在現有的項目移位上面的所有項目 （依遞增索引）。  
  
 第二個版本從另一個插入的所有項目`CArray`集合中，開始`nStartIndex`位置。  
  
 `SetAt`函式，相較之下，取代一個指定的陣列項目，並且不移動任何項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]  
  
##  <a name="isempty"></a>  CArray::IsEmpty  
 判斷是否為空陣列。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果陣列不包含任何項目; 非零，否則便是 0。  
  
##  <a name="operator_at"></a>  CArray::operator \[\]  
 這些註標運算子是方便的替代[SetAt](#setat)和[GetAt](#getat)函式。  
  
```  
TYPE& operator[](int_ptr nindex);  
const TYPE& operator[](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 這個陣列中指定的項目類型的樣板參數。  
  
 `nIndex`  
 若要存取的項目索引。  
  
### <a name="remarks"></a>備註  
 針對陣列不是呼叫第一個運算子， **const**，可能的權限 （右值） 或指派陳述式的左邊 （左值） 上使用。 第二個，針對呼叫**const**陣列可能只能用在右邊。  
  
 偵錯版本的程式庫判斷提示的註標 （請在左邊或右邊指派陳述式） 是否超出範圍。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]  
  
##  <a name="relocateelements"></a>  CArray::RelocateElements  
 當陣列應該成長或壓縮時，基底位址資料到新的緩衝區。  
  
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
 舊的陣列中的元素數目。  
  
### <a name="remarks"></a>備註  
 `pNewData` 一定是足以容納所有`pData`項目。  
  
 [CArray](../../mfc/reference/carray-class.md)實作會使用這個方法時，要複製的舊資料到新的緩衝區陣列應該擴張或縮小 (當[SetSize](#setsize)或[FreeExtra](#freeextra)稱為)。 預設實作只複製資料。  
  
 對於陣列，其中某個元素包含它自己的成員，其中的指標或另一個結構包含其中一個陣列元素的指標，不會更新指標中純文字複本。 在此情況下，您可以更正指標實作的特製化`RelocateElements`與相關的型別。 您必須也負責複製資料。  
  
##  <a name="removeall"></a>  CArray::RemoveAll  
 從此陣列移除所有項目。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>備註  
 如果陣列已經是空的此函式仍能運作。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]  
  
##  <a name="removeat"></a>  CArray::RemoveAt  
 移除陣列中的指定索引處開始的一或多個項目。  
  
```  
void RemoveAt(
    INT_PTR nIndex,  
    INT_PTR nCount = 1);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 整數索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。  
  
 `nCount`  
 要移除的項目數目。  
  
### <a name="remarks"></a>備註  
 在過程中，它會進入下移除的項目上方的所有項目。 它遞減上層陣列的繫結，但不是會釋放記憶體。  
  
 如果您嘗試移除比上述移除點陣列中所包含的項目，然後判斷提示的程式庫的偵錯版本。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]  
  
##  <a name="setat"></a>  CArray::SetAt  
 設定指定索引處的陣列項目。  
  
```  
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 整數索引大於或等於 0 且小於或等於所傳回的值[GetUpperBound](#getupperbound)。  
  
 `ARG_TYPE`  
 指定的引數是用來參考陣列項目類型的樣板參數。  
  
 `newElement`  
 新的項目值儲存在指定的位置。  
  
### <a name="remarks"></a>備註  
 `SetAt` 不會導致要成長的陣列。 使用[SetAtGrow](#setatgrow)如果您想要自動成長的陣列。  
  
 您必須確定您的索引值，代表陣列中的有效位置。 如果它超出範圍時，偵錯版本的程式庫判斷提示。  
  
### <a name="example"></a>範例  
  請參閱範例的[GetAt](#getat)。  
  
##  <a name="setatgrow"></a>  CArray::SetAtGrow  
 設定指定索引處的陣列項目。  
  
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
 必要時自動成長陣列 （也就是上限會調整來容納新項目）。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]  
  
##  <a name="setsize"></a>  CArray::SetSize  
 建立空的或現有陣列; 的大小如有必要，請配置記憶體。  
  
```  
void SetSize(
    INT_PTR nNewSize,  
    INT_PTR nGrowBy = -1);
```  
  
### <a name="parameters"></a>參數  
 `nNewSize`  
 新陣列的大小 （數字的項目）。 必須是大於或等於 0。  
  
 `nGrowBy`  
 如果是必要的大小增加配置項目位置最小數目。  
  
### <a name="remarks"></a>備註  
 如果新的大小小於舊的大小，然後陣列會被截斷，並釋放所有未使用的記憶體。  
  
 使用這個函數來開始使用陣列之前，設定您的陣列的大小。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。  
  
 `nGrowBy`陣列成長的情況時，參數會影響內部記憶體配置。 其用途並不會影響陣列大小所報告[GetSize](#getsize)和[GetUpperBound](#getupperbound)。 如果使用預設值時，MFC 會配置記憶體的方式計算，以避免記憶體分散的情形，並最佳化大部分的情況下的效率。  
  
### <a name="example"></a>範例  
  請參閱範例的[GetData](#getdata)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例收集](../../visual-cpp-samples.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CObArray 類別](../../mfc/reference/cobarray-class.md)   
 [集合類別協助程式](../../mfc/reference/collection-class-helpers.md)
