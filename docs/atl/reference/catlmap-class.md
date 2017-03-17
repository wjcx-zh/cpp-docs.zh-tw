---
title: "CAtlMap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
dev_langs:
- C++
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
caps.latest.revision: 21
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
ms.openlocfilehash: 3730827a56c47497db2fd8324f54c7ba88a584d6
ms.lasthandoff: 02/24/2017

---
# <a name="catlmap-class"></a>CAtlMap 類別
這個類別提供建立和管理對應物件的方法。  
  
## <a name="syntax"></a>語法  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>>
class CAtlMap
```  
  
#### <a name="parameters"></a>參數  
 `K`  
 索引鍵的項目型別。  
  
 V  
 值的項目型別。  
  
 `KTraits`  
 若要複製或移動索引鍵的項目使用的程式碼。 請參閱[CElementTraits 類別](../../atl/reference/celementtraits-class.md)如需詳細資訊。  
  
 `VTraits`  
 用於複製或移動的項目值的程式碼。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlMap::KINARGTYPE](#kinargtype)|使用索引鍵做為輸入引數傳遞時的類型|  
|[CAtlMap::KOUTARGTYPE](#koutargtype)|做為輸出引數傳回一個機碼時所使用的類型。|  
|[CAtlMap::VINARGTYPE](#vinargtype)|將值傳遞做為輸入引數時所使用的類型。|  
|[CAtlMap::VOUTARGTYPE](#voutargtype)|將值傳遞做為輸出引數時所使用的類型。|  
  
### <a name="public-classes"></a>公用類別  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlMap::CPair 類別](#cpair_class)|類別，包含索引鍵和值的項目。|  

  
### <a name="cpair-data-members"></a>CPair 資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CPair::m_key](#m_key)|儲存索引鍵的項目之資料成員。|  
|[CPair::m_value](#m_value)|儲存值的項目之資料成員。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlMap::CAtlMap](#catlmap)|建構函式。|  
|[CAtlMap:: ~ CAtlMap](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlMap::AssertValid](#assertvalid)|呼叫這個方法，讓判斷提示，如果`CAtlMap`不正確。|  
|[CAtlMap::DisableAutoRehash](#disableautorehash)|呼叫這個方法，以停用的自動重新`CAtlMap`物件。|  
|[CAtlMap::EnableAutoRehash](#enableautorehash)|呼叫此方法以啟用自動重新的`CAtlMap`物件。|  
|[CAtlMap::GetAt](#getat)|呼叫這個方法，傳回對應中的指定位置處的項目。|  
|[CAtlMap::GetCount](#getcount)|呼叫這個方法來擷取對應中的項目數。|  
|[CAtlMap::GetHashTableSize](#gethashtablesize)|呼叫這個方法來判斷對應的雜湊表中的分類收納數目。|  
|[CAtlMap::GetKeyAt](#getkeyat)|呼叫這個方法來擷取索引鍵中指定的位置儲存`CAtlMap`物件。|  
|[CAtlMap::GetNext](#getnext)|呼叫這個方法來取得對儲存在下一個元素的指標`CAtlMap`物件。|  
|[CAtlMap::GetNextAssoc](#getnextassoc)|取得逐一查看下一個項目。|  
|[CAtlMap::GetNextKey](#getnextkey)|呼叫這個方法來擷取下一個索引鍵，從`CAtlMap`物件。|  
|[CAtlMap::GetNextValue](#getnextvalue)|呼叫此方法來取得下一個值從`CAtlMap`物件。|  
|[CAtlMap::GetStartPosition](#getstartposition)|呼叫這個方法來啟動對應的反覆項目。|  
|[CAtlMap::GetValueAt](#getvalueat)|呼叫此方法以擷取儲存在指定的位置中的值`CAtlMap`物件。|  
|[CAtlMap::InitHashTable](#inithashtable)|呼叫此方法以初始化雜湊資料表。|  
|[CAtlMap::IsEmpty](#isempty)|呼叫此方法來測試空的對應物件。|  
|[CAtlMap::Lookup](#lookup)|呼叫這個方法來查詢索引鍵或值`CAtlMap`物件。|  
|[CAtlMap::Rehash](#rehash)|呼叫此方法以 rehash`CAtlMap`物件。|  
|[CAtlMap::RemoveAll](#removeall)|呼叫此方法以移除所有項目從`CAtlMap`物件。|  
|[CAtlMap::RemoveAtPos](#removeatpos)|呼叫此方法以移除在指定位置處的項目`CAtlMap`物件。|  
|[CAtlMap::RemoveKey](#removekey)|呼叫此方法以移除項目從`CAtlMap`指定索引鍵的物件。|  
|[CAtlMap::SetAt](#setat)|呼叫這個方法來插入對應的項目組。|  
|[CAtlMap::SetOptimalLoad](#setoptimalload)|呼叫這個方法來設定最佳的負載的`CAtlMap`物件。|  
|[CAtlMap::SetValueAt](#setvalueat)|呼叫此方法以變更儲存在指定的位置中的值`CAtlMap`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|取代或加入新的項目`CAtlMap`。|  

  
## <a name="remarks"></a>備註  
 `CAtlMap`提供管理未排序的陣列索引鍵的項目和其關聯的任何的值指定類型的對應陣列的支援。 使用雜湊演算法，可讓大量的有效儲存和擷取的資料儲存項目 （包含索引鍵和值）。  
  
 `KTraits`和`VTraits`參數是包含複製或移動的項目所需的任何補充程式碼的特性類別。  
  
 除了`CAtlMap`指由[CRBMap](../../atl/reference/crbmap-class.md)類別。 `CRBMap`也會儲存索引鍵/值組，但在展示不同效能特性。 插入項目，所花費的時間查閱索引鍵，或刪除機碼從`CRBMap`物件的順序是*log(n)*，其中*n*是元素數目。 如`CAtlMap`，所有這些作業通常需要固定的時間，即使最壞的狀況可能是順序的*n*。 因此，在一般情況下，`CAtlMap`速度較快。  
  
 之間的差異`CRBMap`和`CAtlMap`顯而易見的反覆運算的預存的項目時。 在`CRBMap`，依排序順序造訪項目。 在`CAtlMap`、 未排序的項目，和任何順序來推斷。  
  
 當項目數量少需要儲存時，請考慮使用[CSimpleMap](../../atl/reference/csimplemap-class.md)類別。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="assertvalid"></a>CAtlMap::AssertValid  
 呼叫這個方法，讓判斷提示，如果`CAtlMap`物件無效。  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，這個方法會判斷提示如果`CAtlMap`物件無效。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="catlmap"></a>CAtlMap::CAtlMap  
 建構函式。  
  
```
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```  
  
### <a name="parameters"></a>參數  
 `nBins`  
 提供的預存的項目指標的 bin 數目。 稍後在本主題說明的紙匣中，請參閱 < 備註 >。  
  
 `fOptimalLoad`  
 最佳的負載比率。  
  
 `fLoThreshold`  
 負載比率下限臨界值。  
  
 `fHiThreshold`  
 負載比率上限臨界值。  
  
 `nBlockSize`  
 區塊大小。  
  
### <a name="remarks"></a>備註  
 `CAtlMap`參考所有其預存的項目首先會建立索引的索引鍵上使用雜湊演算法。 這個索引參考"bin"包含指標的預存的項目。 如果 「 資源回收筒已在使用中，連結清單會建立以存取後續項目。 周遊清單低於直接存取正確的項目，並因此對應的結構必須對效能的儲存體需求之間取得平衡。 在大部分情況下提供很好的結果已選擇預設的參數。  
  
 負載比率是儲存在 map 物件中的元素數目的 bin 數目的比例。 當對應結構會重新計算時， *fOptimalLoad*參數值將會用來計算所需的分類收納數目。 這個值可以使用變更[CAtlMap::SetOptimalLoad](#setoptimalload)方法。  
  
 `fLoThreshold`參數值較低負載比率可供連接之前`CAtlMap`會重新計算對應的最佳大小。  
  
 `fHiThreshold`參數是負載比率可以連線到之前的上限值`CAtlMap`物件將會重新計算對應的最佳大小。  
  
 預設會啟用這個重新計算程序 （又稱為湊）。 如果您想要時停用此程序，可能是輸入一次呼叫資料大量[CAtlMap::DisableAutoRehash](#disableautorehash)方法。 重新啟動它以[CAtlMap::EnableAutoRehash](#enableautorehash)方法。  
  
 `nBlockSize`參數是配置新的項目時所需的記憶體數量的量值。 較大的區塊大小減少記憶體配置常式，但使用較多資源。  
  
 可以儲存任何資料之前，就必須初始化雜湊表，藉由呼叫[CAtlMap::InitHashTable](#inithashtable)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&72;](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlMap:: ~ CAtlMap  
 解構函式。  
  
```
~CAtlMap() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源。  
  
##  <a name="cpair_class"></a>CAtlMap::CPair 類別  
 類別，包含索引鍵和值的項目。  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>備註  
 方法使用這個類別[CAtlMap::GetNext](#getnext)和[CAtlMap::Lookup](#lookup)存取儲存在對應結構的索引鍵和值的項目。  
  
##  <a name="disableautorehash"></a>CAtlMap::DisableAutoRehash  
 呼叫這個方法，以停用的自動重新`CAtlMap`物件。  
  
```
void DisableAutoRehash() throw();
```  
  
### <a name="remarks"></a>備註  
 自動重新啟用時 （這是預設情況下），如果負載值 （儲存在陣列中元素數目的分類收納數目的比率） 超過在建立對應時所指定的最大或最小值將會自動重新計算雜湊表中的分類收納數目。  
  
 `DisableAutoRehash`當大量項目會加入至對應一次時，會十分實用。 而不是每次超過限制，請觸發 rehashing 程序，是更有效率的方式呼叫`DisableAutoRehash`、 加入項目，以及最後呼叫[CAtlMap::EnableAutoRehash](#enableautorehash)。  
  
##  <a name="enableautorehash"></a>CAtlMap::EnableAutoRehash  
 呼叫此方法以啟用自動重新的`CAtlMap`物件。  
  
```
void EnableAutoRehash() throw();
```  
  
### <a name="remarks"></a>備註  
 自動重新啟用時 （這是預設情況下），如果負載值 （儲存在陣列中元素數目的分類收納數目的比率） 超過在建立對應時所指定的最大或最小值，將會自動重新計算雜湊表中的分類收納數目。  
  
 **EnableAutoRefresh**最常使用呼叫後[CAtlMap::DisableAutoRehash](#disableautorehash)。  
  
##  <a name="getat"></a>CAtlMap::GetAt  
 呼叫這個方法，傳回對應中的指定位置處的項目。  
  
```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
 `key`  
 指定對應的索引鍵的類型樣板參數。  
  
 *value*  
 指定的對應值的類型樣板參數。  
  
### <a name="return-value"></a>傳回值  
 讓指標回到目前的索引鍵/值儲存在對應中的項目組。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果`pos`等於 NULL。  
  
##  <a name="getcount"></a>CAtlMap::GetCount  
 呼叫這個方法來擷取對應中的項目數。  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 Map 物件中傳回的項目數。 單一項目是索引鍵/值組。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="gethashtablesize"></a>CAtlMap::GetHashTableSize  
 呼叫這個方法來判斷對應的雜湊表中的分類收納數目。  
  
```
UINT GetHashTableSize() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回雜湊表中的分類收納數目。 請參閱[CAtlMap::CAtlMap](#catlmap)說明。  
  
##  <a name="getkeyat"></a>CAtlMap::GetKeyAt  
 呼叫這個方法來擷取索引鍵中指定的位置儲存`CAtlMap`物件。  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>傳回值  
 傳回儲存在指定的位置中的索引鍵的參考`CAtlMap`物件。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getnext"></a>CAtlMap::GetNext  
 呼叫這個方法來取得對儲存在下一個元素的指標`CAtlMap`物件。  
  
```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>傳回值  
 傳回下一個配對的索引鍵/值項目儲存在對應中的指標。 `pos`位置計數器會在每次呼叫之後更新。 如果擷取的項目是在對應中的最後一個`pos`設為 NULL。  
  
##  <a name="getnextassoc"></a>CAtlMap::GetNextAssoc  
 取得逐一查看下一個項目。  
  
```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
 `key`  
 指定對應的索引鍵的類型樣板參數。  
  
 *value*  
 指定的對應值的類型樣板參數。  
  
### <a name="remarks"></a>備註  
 `pos`位置計數器會在每次呼叫之後更新。 如果擷取的項目是在對應中的最後一個`pos`設為 NULL。  
  
##  <a name="getnextkey"></a>CAtlMap::GetNextKey  
 呼叫這個方法來擷取下一個索引鍵，從`CAtlMap`物件。  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>傳回值  
 傳回對應中的下一個索引鍵的參考。  
  
### <a name="remarks"></a>備註  
 更新的目前位置計數器`pos`。 如果在對應中有任何項目，位置計數器是設為 NULL。  
  
##  <a name="getnextvalue"></a>CAtlMap::GetNextValue  
 呼叫此方法來取得下一個值從`CAtlMap`物件。  
  
```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>傳回值  
 傳回對應中的下一個值的參考。  
  
### <a name="remarks"></a>備註  
 更新的目前位置計數器`pos`。 如果在對應中有任何項目，位置計數器是設為 NULL。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getstartposition"></a>CAtlMap::GetStartPosition  
 呼叫這個方法來啟動對應的反覆項目。  
  
```
POSITION GetStartPosition() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的開始位置或 NULL 傳回如果對應是空的。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來啟動對應的反覆項目，藉由傳回**位置**值傳遞至`GetNextAssoc`方法。  
  
> [!NOTE]
>  反覆項目序列不是可預測  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getvalueat"></a>CAtlMap::GetValueAt  
 呼叫此方法以擷取儲存在指定的位置中的值`CAtlMap`物件。  
  
```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>傳回值  
 傳回儲存在指定的位置中的值的參考`CAtlMap`物件。  
  
##  <a name="inithashtable"></a>CAtlMap::InitHashTable  
 呼叫此方法以初始化雜湊資料表。  
  
```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```  
  
### <a name="parameters"></a>參數  
 `nBins`  
 使用雜湊表的分類收納數目。 請參閱[CAtlMap::CAtlMap](#catlmap)說明。  
  
 `bAllocNow`  
 旗標指示應該配置記憶體時。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**上成功初始化、 **false**失敗。  
  
### <a name="remarks"></a>備註  
 `InitHashTable`必須在呼叫之前的任何項目會儲存在雜湊表。  如果未明確呼叫這個方法，它將會自動呼叫第一次新增的項目，使用所指定的紙匣計數**CAtlMap**建構函式。  否則，對應將會使用初始化所指定的新 bin 計數`nBins`參數。  
  
 如果`bAllocNow`參數為 false，直到它的第一個必要的雜湊資料表所需的記憶體不會配置。 這可以是不確定，如果將使用對應是否有用。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="isempty"></a>CAtlMap::IsEmpty  
 呼叫此方法來測試空的對應物件。  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**對應是空的如果**false**否則。  
  
##  <a name="kinargtype"></a>CAtlMap::KINARGTYPE  
 索引鍵做為輸入引數傳遞時所使用的類型。  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="koutargtype"></a>CAtlMap::KOUTARGTYPE  
 做為輸出引數傳回一個機碼時所使用的類型。  
  
```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```  
  
##  <a name="lookup"></a>CAtlMap::Lookup  
 呼叫這個方法來查詢索引鍵或值`CAtlMap`物件。  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 指定識別的項目是要查閱的索引鍵。  
  
 *value*  
 接收查詢最多值的變數。  
  
### <a name="return-value"></a>傳回值  
 第一種形式的方法會傳回 true，如果找到索引鍵為，否則為 false。 第二個和第三個表單傳回的指標[CPair](#cpair_class) ，可用於為位置呼叫[CAtlMap::GetNext](#getnext) ，依此類推。  
  
### <a name="remarks"></a>備註  
 `Lookup`快速尋找對應項目，包含完全符合指定的索引鍵參數的索引鍵使用雜湊演算法。  
  
##  <a name="operator_at"></a>CAtlMap::operator\[\]  
 取代或加入新的項目`CAtlMap`。  
  
```
V& operator[](kinargtype key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 若要新增或取代項目的索引鍵。  
  
### <a name="return-value"></a>傳回值  
 傳回指定索引鍵相關聯的值的參考。  
  
### <a name="example"></a>範例  
 如果索引鍵已經存在，會取代此項目。 如果索引鍵不存在，則會加入新項目。 請參閱範例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="rehash"></a>CAtlMap::Rehash  
 呼叫此方法以 rehash`CAtlMap`物件。  
  
```
void Rehash(UINT nBins = 0);
```  
  
### <a name="parameters"></a>參數  
 `nBins`  
 新的雜湊表中所使用的紙匣數目。 請參閱[CAtlMap::CAtlMap](#catlmap)說明。  
  
### <a name="remarks"></a>備註  
 如果`nBins`為 0，`CAtlMap`計算合理的數字為基礎的地圖與最佳的負載設定中的項目數。 通常 rehashing 程序會自動進行，但如果[CAtlMap::DisableAutoRehash](#disableautorehash)已呼叫，這個方法會執行必要的調整大小。  
  
##  <a name="removeall"></a>CAtlMap::RemoveAll  
 呼叫此方法以移除所有項目從`CAtlMap`物件。  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>備註  
 清除`CAtlMap`物件，即釋放記憶體，用來儲存項目。  
  
##  <a name="removeatpos"></a>CAtlMap::RemoveAtPos  
 呼叫此方法以移除在指定位置處的項目`CAtlMap`物件。  
  
```
void RemoveAtPos(POSITION pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="remarks"></a>備註  
 移除指定位置處儲存的索引鍵/值組。 在用來儲存項目，會釋放記憶體。 所參考位置`pos`失效，且在地圖中的任何其他項目位置仍有效，就不一定會保留相同的順序。  
  
##  <a name="removekey"></a>CAtlMap::RemoveKey  
 呼叫此方法以移除項目從`CAtlMap`指定索引鍵的物件。  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 您想要移除對應的項目組。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果金鑰已找到並移除， **false**失敗。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="setat"></a>CAtlMap::SetAt  
 呼叫這個方法來插入對應的項目組。  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 若要加入的索引鍵值`CAtlMap`物件。  
  
 *value*  
 要加入至值`CAtlMap`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回的位置中的索引鍵/值項目組`CAtlMap`物件。  
  
### <a name="remarks"></a>備註  
 `SetAt`如果找到相符的索引鍵，會取代現有的項目。 如果找不到索引鍵，會建立新的索引鍵/值組。  
  
##  <a name="setoptimalload"></a>CAtlMap::SetOptimalLoad  
 呼叫這個方法來設定最佳的負載的`CAtlMap`物件。  
  
```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```  
  
### <a name="parameters"></a>參數  
 `fOptimalLoad`  
 最佳的負載比率。  
  
 `fLoThreshold`  
 負載比率下限臨界值。  
  
 `fHiThreshold`  
 負載比率上限臨界值。  
  
 `bRehashNow`  
 旗標，指出如果應該重新計算雜湊表。  
  
### <a name="remarks"></a>備註  
 這個方法來重新定義的最佳負載值`CAtlMap`物件。 請參閱[CAtlMap::CAtlMap](#catlmap)討論的各種參數。 如果`bRehashNow`為 true，而且項目數目超出最小和最大值，則會重新計算雜湊表。  
  
##  <a name="setvalueat"></a>CAtlMap::SetValueAt  
 呼叫此方法以變更儲存在指定的位置中的值`CAtlMap`物件。  
  
```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
 *value*  
 要加入至值`CAtlMap`物件。  
  
### <a name="remarks"></a>備註  
 變更儲存在指定位置的值項目`CAtlMap`物件。  
  
##  <a name="vinargtype"></a>CAtlMap::VINARGTYPE  
 將值傳遞做為輸入引數時所使用的類型。  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="voutargtype"></a>CAtlMap::VOUTARGTYPE  
 將值傳遞做為輸出引數時所使用的類型。  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
##  <a name="m_key"></a>CAtlMap::CPair::m_key  
 儲存索引鍵的項目之資料成員。  
  
```
const K m_key;
```    
  
### <a name="parameters"></a>參數  
 `K`  
 索引鍵的項目型別。  
  
##  <a name="m_value"></a>CAtlMap::CPair::m_value  
 儲存值的項目之資料成員。  
  
```
V  m_value;
```    
  
### <a name="parameters"></a>參數  
 *V*  
 值的項目型別。  
  
## <a name="see-also"></a>另請參閱  
 [跑馬燈範例](../../visual-cpp-samples.md)   
 [UpdatePV 範例](../../visual-cpp-samples.md)   
 [類別概觀](../../atl/atl-class-overview.md)

