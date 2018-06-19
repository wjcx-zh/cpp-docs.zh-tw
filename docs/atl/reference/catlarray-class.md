---
title: CAtlArray 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ceeaf5250cc9dc5cb4cb25c47b3fe179c7c5295
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365545"
---
# <a name="catlarray-class"></a>CAtlArray 類別
這個類別會實作陣列物件。  
  
## <a name="syntax"></a>語法  
  
```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```  
  
#### <a name="parameters"></a>參數  
 *E*  
 陣列中儲存之資料的類型。  
  
 *ETraits*  
 程式碼，用來複製或移動項目。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[[新增]](#add)|呼叫此方法以將項目加入至陣列物件。|  
|[附加](#append)|呼叫這個方法，以加入另一個陣列的內容。|  
|[AssertValid](#assertvalid)|呼叫這個方法來確認陣列物件有效。|  
|[CAtlArray](#catlarray)|建構函式。|  
|[~ CAtlArray](#dtor)|解構函式。|  
|[複製](#copy)|呼叫這個方法將複製到另一個陣列的項目。|  
|[FreeExtra](#freeextra)|呼叫此方法以從陣列中移除任何空的項目。|  
|[GetAt](#getat)|呼叫此方法以從陣列物件中擷取單一項目。|  
|[GetCount](#getcount)|呼叫此方法以傳回儲存在陣列中的項目數目。|  
|[GetData](#getdata)|呼叫此方法以傳回陣列中的第一個元素的指標。|  
|[InsertArrayAt](#insertarrayat)|呼叫這個方法來插入另一個陣列。|  
|[InsertAt](#insertat)|陣列物件呼叫這個方法來插入新項目 （或多個項目的複本）。|  
|[IsEmpty](#isempty)|呼叫此方法以測試是否是空的陣列。|  
|[RemoveAll](#removeall)|呼叫此方法以從陣列物件中移除所有項目。|  
|[RemoveAt](#removeat)|呼叫此方法以從陣列中移除一或多個項目。|  
|[SetAt](#setat)|呼叫此方法以設定項目的值的陣列物件中。|  
|[SetAtGrow](#setatgrow)|呼叫這個方法，在陣列物件中，展開所需的陣列，設定項目的值。|  
|[SetCount](#setcount)|呼叫此方法以設定陣列物件的大小。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子&#91;&#93;](#operator_at)|呼叫以傳回陣列中的項目參考這個運算子。|  

  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[INARGTYPE](#inargtype)|要用來將項目加入至陣列的資料類型。|  
|[OUTARGTYPE](#outargtype)|要用來擷取項目陣列中的資料類型。|  
  
## <a name="remarks"></a>備註  
 **CAtlArray**提供方法來建立及管理使用者定義類型的元素的陣列。 雖然類似於標準的 C 陣列**CAtlArray**物件可以動態壓縮並根據需要增大。 陣列索引一律會從位置 0，且上限可以是固定的或允許依序展開 加入新項目時。  
  
 較少的項目，ATL 類別陣列[CSimpleArray](../../atl/reference/csimplearray-class.md)可用。  
  
 **CAtlArray**與 MFC 的密切相關**CArray**類別，並將不必在 MFC 專案中，雖然序列化支援。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="add"></a>  CAtlArray::Add  
 呼叫此方法以將項目加入至陣列物件。  
  
```
size_t Add(INARGTYPE element);
size_t Add();
```  
  
### <a name="parameters"></a>參數  
 `element`  
 要加入至陣列的項目。  
  
### <a name="return-value"></a>傳回值  
 傳回加入的項目索引。  
  
### <a name="remarks"></a>備註  
 新的項目會加入至陣列的結尾。 如果沒有任何項目提供，加入空白的項目。也就是說，陣列會增加的大小一樣的實際項目已加入。 如果作業失敗， [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) E_OUTOFMEMORY 引數呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]  
  
##  <a name="append"></a>  CAtlArray::Append  
 呼叫這個方法，以加入另一個陣列的內容。  
  
```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>參數  
 `aSrc`  
 要附加的陣列。  
  
### <a name="return-value"></a>傳回值  
 傳回第一個附加的項目的索引。  
  
### <a name="remarks"></a>備註  
 提供的陣列中的項目會加入至現有陣列的結尾。 如有必要，則會配置記憶體，以容納新項目。  
  
 陣列必須是相同的型別，而且不可能將陣列附加至本身。  
  
 偵錯組建 ATLASSERT 就會引發如果`CAtlArray`引數不是有效陣列或`aSrc`指的是相同的物件。 在發行組建中無效的引數可能會導致無法預期的行為。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]  
  
##  <a name="assertvalid"></a>  CAtlArray::AssertValid  
 呼叫這個方法來確認陣列物件有效。  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>備註  
 如果陣列物件不是有效的`ATLASSERT`將會擲回的判斷提示。 這個方法是定義 _DEBUG 時，才可以使用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]  
  
##  <a name="catlarray"></a>  CAtlArray::CAtlArray  
 建構函式。  
  
```
CAtlArray() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化陣列物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]  
  
##  <a name="dtor"></a>  CAtlArray:: ~ CAtlArray  
 解構函式。  
  
```
~CAtlArray() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放陣列物件所使用的任何資源。  
  
##  <a name="copy"></a>  CAtlArray::Copy  
 呼叫這個方法將複製到另一個陣列的項目。  
  
```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>參數  
 `aSrc`  
 要複製至陣列之項目的來源。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來覆寫一個陣列的項目與另一個陣列的項目。 如有必要，則會配置記憶體，以容納新項目。 您不可能將陣列的元素複製到本身。  
  
 如果要保留現有陣列的內容，請使用[CAtlArray::Append](#append)改為。  
  
 偵錯組建 ATLASSERT 就會引發如果現有`CAtlArray`物件不是有效的或者如果`aSrc`指的是相同的物件。 在發行組建中無效的引數可能會導致無法預期的行為。  
  
> [!NOTE]
> `CAtlArray::Copy` 不支援使用建立的項目所組成的陣列[CAutoPtr](../../atl/reference/cautoptr-class.md)類別。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]  
  
##  <a name="freeextra"></a>  CAtlArray::FreeExtra  
 呼叫此方法以從陣列中移除任何空的項目。  
  
```
void FreeExtra() throw();
```  
  
### <a name="remarks"></a>備註  
 任何空的項目會遭到移除，但大小和陣列的上限維持不變。  
  
 在偵錯組建中，如果 CAtlArray 物件不是有效的或是陣列會超過其大小上限，就會引發 ATLASSERT。  
  
##  <a name="getat"></a>  CAtlArray::GetAt  
 呼叫這個方法，以從陣列物件擷取單一項目。  
  
```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```  
  
### <a name="parameters"></a>參數  
 `iElement`  
 要傳回之陣列項目的索引值。  
  
### <a name="return-value"></a>傳回值  
 傳回所需的陣列元素的參考。  
  
### <a name="remarks"></a>備註  
 偵錯組建 ATLASSERT 就會引發如果`iElement`超出陣列中的元素數目。 在發行組建中無效的引數可能會導致無法預期的行為。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]  
  
##  <a name="getcount"></a>  CAtlArray::GetCount  
 呼叫此方法以傳回儲存在陣列中的項目數目。  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回儲存在陣列中元素數目。  
  
### <a name="remarks"></a>備註  
 所傳回的值為陣列中的第一個項目是在位置 0，`GetCount`永遠為 1 大於最大的索引。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlArray::GetAt](#getat)。  
  
##  <a name="getdata"></a>  CAtlArray::GetData  
 呼叫此方法以傳回陣列中的第一個元素的指標。  
  
```
E* GetData() throw();
const E* GetData() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回儲存在陣列中的第一個項目之記憶體位置的指標。 如果有任何項目，則傳回 NULL。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]  
  
##  <a name="inargtype"></a>  CAtlArray::INARGTYPE  
 要用來將項目加入至陣列的資料類型。  
  
```
typedef ETraits::INARGTYPE INARGTYPE;
```  
  
##  <a name="insertarrayat"></a>  CAtlArray::InsertArrayAt  
 呼叫這個方法來插入另一個陣列。  
  
```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```  
  
### <a name="parameters"></a>參數  
 `iStart`  
 陣列是要插入的索引。  
  
 `paNew`  
 要插入的陣列。  
  
### <a name="remarks"></a>備註  
 從陣列的項目`paNew`複製到陣列物件，從項目開始`iStart`。 現有的陣列項目會移至避免遭到覆寫。  
  
 偵錯組建 ATLASSERT 就會引發如果`CAtlArray`物件不是有效的或者如果`paNew`指標為 NULL 或無效。  
  
> [!NOTE]
> `CAtlArray::InsertArrayAt` 不支援使用建立的項目所組成的陣列[CAutoPtr](../../atl/reference/cautoptr-class.md)類別。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]  
  
##  <a name="insertat"></a>  CAtlArray::InsertAt  
 陣列物件呼叫這個方法來插入新項目 （或多個項目的複本）。  
  
```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```  
  
### <a name="parameters"></a>參數  
 `iElement`  
 索引中的項目或項目會插入。  
  
 `element`  
 要插入的元素值。  
  
 `nCount`  
 若要加入的項目數目。  
  
### <a name="remarks"></a>備註  
 一或多個項目插入陣列索引開始`iElement`。 若要避免覆寫移動現有項目。  
  
 偵錯組建 ATLASSERT 就會引發如果`CAtlArray`物件無效、 可加入的項目數為零，或合併的元素數目的陣列，包含太大。 在零售組建中傳遞無效的參數可能會造成無法預期的結果。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]  
  
##  <a name="isempty"></a>  CAtlArray::IsEmpty  
 呼叫此方法以測試是否是空的陣列。  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果陣列為空的否則傳回 false，則傳回 true。  
  
### <a name="remarks"></a>備註  
 即稱為陣列，如果它沒有包含任何元素是空的。 因此，即使此陣列包含空的元素，它是不空的。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]  
  
##  <a name="operator_at"></a>  CAtlArray::operator]  
 呼叫以傳回陣列中的項目參考這個運算子。  
  
```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```  
  
### <a name="parameters"></a>參數  
 `iElement`  
 要傳回之陣列項目的索引值。  
  
### <a name="return-value"></a>傳回值  
 傳回所需的陣列元素的參考。  
  
### <a name="remarks"></a>備註  
 執行類似的函數，以[CAtlArray::GetAt](#getat)。 不同於 MFC 類別[CArray](../../mfc/reference/carray-class.md)，這個運算子不能用來取代[CAtlArray::SetAt](#setat)。  
  
 偵錯組建 ATLASSERT 就會引發如果`iElement`超過陣列中的項目總數。 在零售組建中，無效的參數可能會導致無法預期的結果。  
  
##  <a name="outargtype"></a>  CAtlArray::OUTARGTYPE  
 要用來擷取項目陣列中的資料類型。  
  
```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```  
  
##  <a name="removeall"></a>  CAtlArray::RemoveAll  
 呼叫此方法以從陣列物件中移除所有項目。  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>備註  
 從陣列物件中移除所有項目。  
  
 這個方法會呼叫[CAtlArray::SetCount](#setcount)調整陣列的大小和後續釋放已配置的記憶體。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlArray::IsEmpty](#isempty)。  
  
##  <a name="removeat"></a>  CAtlArray::RemoveAt  
 呼叫此方法以從陣列中移除一或多個項目。  
  
```
void RemoveAt(size_t iElement, size_t nCount = 1);
```  
  
### <a name="parameters"></a>參數  
 `iElement`  
 要移除之第一個項目的索引。  
  
 `nCount`  
 要移除的項目數目。  
  
### <a name="remarks"></a>備註  
 從陣列中移除一或多個項目。 任何其餘的項目會向下移動。 上限就會減少，但呼叫之前，不釋放記憶體[CAtlArray::FreeExtra](#freeextra)進行。  
  
 偵錯組建 ATLASSERT 就會引發如果`CAtlArray`物件不是有效的或者如果合併的總計`iElement`和`nCount`超過陣列中的項目總數。 在零售組建中，無效的參數可能會造成無法預期的結果。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]  
  
##  <a name="setat"></a>  CAtlArray::SetAt  
 呼叫此方法以設定項目的值的陣列物件中。  
  
```
void SetAt(size_t iElement, INARGTYPE element);
```  
  
### <a name="parameters"></a>參數  
 `iElement`  
 指向要設定之陣列項目的索引。  
  
 `element`  
 指定的項目新值。  
  
### <a name="remarks"></a>備註  
 偵錯組建 ATLASSERT 就會引發如果`iElement`超出陣列中的元素數目。 在零售組建中，無效的參數可能會導致無法預期的結果。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlArray::GetAt](#getat)。  
  
##  <a name="setcount"></a>  CAtlArray::SetCount  
 呼叫此方法以設定陣列物件的大小。  
  
```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```  
  
### <a name="parameters"></a>參數  
 `nNewSize`  
 陣列的所需的大小。  
  
 `nGrowBy`  
 值，用來判斷將緩衝區的大小。 值為-1 會使用於內部導出的值。  
  
### <a name="return-value"></a>傳回值  
 如果陣列否則就會成功地調整大小，則為 false，則傳回 true。  
  
### <a name="remarks"></a>備註  
 陣列可以增加或減少的大小。 如果增加，額外的空白項目會加入至陣列。 如果減少，具有最大索引的項目將會被刪除，並釋放記憶體。  
  
 使用這個方法來設定陣列的大小後才能使用它。 如果`SetCount`不使用的程序加入項目-執行後續的記憶體配置和 — 將會降低效能，且讓記憶體分段。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlArray::GetData](#getdata)。  
  
##  <a name="setatgrow"></a>  CAtlArray::SetAtGrow  
 呼叫這個方法，在陣列物件中，展開所需的陣列，設定項目的值。  
  
```
void SetAtGrow(size_t iElement, INARGTYPE element);
```  
  
### <a name="parameters"></a>參數  
 `iElement`  
 指向要設定之陣列項目的索引。  
  
 `element`  
 指定的項目新值。  
  
### <a name="remarks"></a>備註  
 取代的項目之索引所指向的值。 如果`iElement`大於目前大小的陣列，陣列會自動增加使用的呼叫[CAtlArray::SetCount](#setcount)。 偵錯組建 ATLASSERT 就會引發如果`CAtlArray`物件無效。 在零售組建中，無效的參數可能會造成無法預期的結果。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MMXSwarm 範例](../../visual-cpp-samples.md)   
 [DynamicConsumer 範例](../../visual-cpp-samples.md)   
 [UpdatePV 範例](../../visual-cpp-samples.md)   
 [跑馬燈範例](../../visual-cpp-samples.md)   
 [CArray 類別](../../mfc/reference/carray-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
