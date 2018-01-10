---
title: "CAtlMap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords: CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9166e8f7804a3138d3e891fbe15b54cb0e270811
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="catlmap-class"></a>CAtlMap 類別
這個類別會提供建立和管理對應物件的方法。  
  
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
 索引鍵的項目類型。  
  
 V  
 值的項目型別。  
  
 `KTraits`  
 程式碼，用來複製或移動的索引鍵項目。 請參閱[CElementTraits 類別](../../atl/reference/celementtraits-class.md)如需詳細資訊。  
  
 `VTraits`  
 用於複製或移動的項目值的程式碼。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlMap::KINARGTYPE](#kinargtype)|使用索引鍵做為輸入的引數傳遞時的型別|  
|[CAtlMap::KOUTARGTYPE](#koutargtype)|當做輸出引數傳回一個機碼時所使用的類型。|  
|[CAtlMap::VINARGTYPE](#vinargtype)|將值傳遞做為輸入的引數時所使用的類型。|  
|[CAtlMap::VOUTARGTYPE](#voutargtype)|將值當做輸出引數傳遞時所使用的類型。|  
  
### <a name="public-classes"></a>公用類別  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlMap::CPair 類別](#cpair_class)|類別，其中包含索引鍵和值的項目。|  

  
### <a name="cpair-data-members"></a>CPair 資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CPair::m_key](#m_key)|資料成員儲存索引鍵的項目。|  
|[CPair::m_value](#m_value)|資料成員，其儲存值的項目。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlMap::CAtlMap](#catlmap)|建構函式。|  
|[CAtlMap:: ~ CAtlMap](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlMap::AssertValid](#assertvalid)|呼叫這個方法會造成判斷提示，如果`CAtlMap`不正確。|  
|[CAtlMap::DisableAutoRehash](#disableautorehash)|呼叫此方法以停用的自動重新`CAtlMap`物件。|  
|[CAtlMap::EnableAutoRehash](#enableautorehash)|呼叫此方法以啟用自動重新的`CAtlMap`物件。|  
|[CAtlMap::GetAt](#getat)|呼叫此方法以傳回對應中的指定位置處的項目。|  
|[CAtlMap::GetCount](#getcount)|呼叫此方法以擷取在對應中的項目數。|  
|[CAtlMap::GetHashTableSize](#gethashtablesize)|呼叫這個方法來判斷對應的雜湊表中的分類收納數目。|  
|[CAtlMap::GetKeyAt](#getkeyat)|呼叫此方法以擷取儲存在指定位置的索引鍵`CAtlMap`物件。|  
|[CAtlMap::GetNext](#getnext)|呼叫此方法以取得組儲存在下一個元素的指標`CAtlMap`物件。|  
|[CAtlMap::GetNextAssoc](#getnextassoc)|取得逐一查看下一個項目。|  
|[CAtlMap::GetNextKey](#getnextkey)|呼叫這個方法來擷取下一個索引鍵，從`CAtlMap`物件。|  
|[CAtlMap::GetNextValue](#getnextvalue)|呼叫此方法來取得下一個值從`CAtlMap`物件。|  
|[CAtlMap::GetStartPosition](#getstartposition)|呼叫此方法以啟動對應的反覆項目。|  
|[CAtlMap::GetValueAt](#getvalueat)|呼叫此方法以擷取儲存在指定位置的值`CAtlMap`物件。|  
|[CAtlMap::InitHashTable](#inithashtable)|呼叫此方法以初始化雜湊表。|  
|[CAtlMap::IsEmpty](#isempty)|呼叫此方法來測試空白對應物件。|  
|[CAtlMap::Lookup](#lookup)|呼叫這個方法來查詢索引鍵或值`CAtlMap`物件。|  
|[CAtlMap::Rehash](#rehash)|呼叫此方法以 rehash`CAtlMap`物件。|  
|[CAtlMap::RemoveAll](#removeall)|呼叫這個方法來移除所有項目從`CAtlMap`物件。|  
|[CAtlMap::RemoveAtPos](#removeatpos)|呼叫這個方法來移除在指定位置處的項目`CAtlMap`物件。|  
|[CAtlMap::RemoveKey](#removekey)|呼叫這個方法來移除的項目從`CAtlMap`物件，指定的索引鍵。|  
|[CAtlMap::SetAt](#setat)|呼叫這個方法來插入對應中的項目組。|  
|[CAtlMap::SetOptimalLoad](#setoptimalload)|呼叫此方法以設定最佳的負載`CAtlMap`物件。|  
|[CAtlMap::SetValueAt](#setvalueat)|呼叫此方法以變更中的指定位置處儲存的值`CAtlMap`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|取代或加入新的項目`CAtlMap`。|  

  
## <a name="remarks"></a>備註  
 `CAtlMap`管理未排序的陣列索引鍵的項目和其關聯的任何的值指定類型的對應陣列提供支援。 使用雜湊演算法，可讓大量有效率地儲存並擷取資料的儲存 （組成的索引鍵和值） 的項目。  
  
 `KTraits`和`VTraits`參數是包含複製或移動的項目所需的任何補充程式碼的 traits 類別。  
  
 替代`CAtlMap`提供[CRBMap](../../atl/reference/crbmap-class.md)類別。 `CRBMap`也儲存索引鍵/值組，但展示不同效能特性。 要插入的項目所花費的時間查閱索引鍵，或刪除的索引鍵從`CRBMap`物件的順序是*log(n)*，其中 *n* 是項目數目。 如`CAtlMap`，所有這些作業通常會採用常數的時間，即使最壞情況下可能是順序的 *n* 。 因此，在一般情況下，`CAtlMap`的速度。  
  
 之間的差異`CRBMap`和`CAtlMap`反覆運算的預存的項目時就顯而易見。 在`CRBMap`，元素的造訪以排序順序。 在`CAtlMap`、 項目不會排序，而且可以推斷沒有順序。  
  
 當儲存需要少量的項目時，請考慮使用[CSimpleMap](../../atl/reference/csimplemap-class.md)類別。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="assertvalid"></a>CAtlMap::AssertValid  
 呼叫這個方法會造成判斷提示，如果`CAtlMap`物件無效。  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，這個方法會判斷提示如果`CAtlMap`物件無效。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlMap::CAtlMap](#catlmap)。  
  
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
 提供的預存的項目指標的分類收納數目。 稍後在本主題適用於分類收納的說明，請參閱 < 備註 >。  
  
 `fOptimalLoad`  
 最佳的負載比率。  
  
 `fLoThreshold`  
 負載率下限臨界值。  
  
 `fHiThreshold`  
 負載比率上限臨界值。  
  
 `nBlockSize`  
 區塊大小。  
  
### <a name="remarks"></a>備註  
 `CAtlMap`參考所有預存元素的第一個建立的索引鍵使用雜湊演算法。 這個索引參考"bin"包含指標的預存的項目。 如果 bin 已在使用中，連結清單會建立以存取後續項目。 周遊清單低於直接存取正確的項目，而且因此網站導覽結構必須針對效能的存放裝置需求之間取得平衡。 在大部分情況下會提供很好的結果已被選擇預設參數。  
  
 負載比例為 map 物件中儲存的項目數的數字分類收納數目的比率。 對應結構重新計算， *fOptimalLoad*參數值將會用來計算所需的分類收納數目。 這個值可以使用變更[CAtlMap::SetOptimalLoad](#setoptimalload)方法。  
  
 `fLoThreshold`參數是較低的值之前可以連線的負載比率`CAtlMap`會重新計算對應的最佳大小。  
  
 `fHiThreshold`參數是之前可以連線的負載比率。 上限數值`CAtlMap`物件將會重新計算對應的最佳大小。  
  
 預設會啟用此重新計算程序 （又稱為重新）。 如果您想要時，停用此程序，可能是輸入一次呼叫資料大量[CAtlMap::DisableAutoRehash](#disableautorehash)方法。 重新啟動它以[CAtlMap::EnableAutoRehash](#enableautorehash)方法。  
  
 `nBlockSize`參數是配置新的項目時所需的記憶體數量的量值。 較大的區塊大小減少記憶體配置常式，呼叫，但使用較多資源。  
  
 可儲存任何資料之前，就必須初始化雜湊表，藉由呼叫[CAtlMap::InitHashTable](#inithashtable)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlMap:: ~ CAtlMap  
 解構函式。  
  
```
~CAtlMap() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源。  
  
##  <a name="cpair_class"></a>CAtlMap::CPair 類別  
 類別，其中包含索引鍵和值的項目。  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>備註  
 方法會使用這個類別[CAtlMap::GetNext](#getnext)和[CAtlMap::Lookup](#lookup)存取儲存在對應結構的索引鍵和值的項目。  
  
##  <a name="disableautorehash"></a>CAtlMap::DisableAutoRehash  
 呼叫此方法以停用的自動重新`CAtlMap`物件。  
  
```
void DisableAutoRehash() throw();
```  
  
### <a name="remarks"></a>備註  
 自動重新啟用時 （其預設值），雜湊表中的分類收納數目將會自動重新計算值載入 （儲存在陣列中元素數目的分類收納數目的比率） 超過最大或最小值指定在建立對應的時間。  
  
 `DisableAutoRehash`當大量項目會加入至對應一次，則是最有用。 而不是每次超過限制，請觸發 rehashing 程序，會更有效率，無法呼叫`DisableAutoRehash`、 加入項目，以及最後呼叫[CAtlMap::EnableAutoRehash](#enableautorehash)。  
  
##  <a name="enableautorehash"></a>CAtlMap::EnableAutoRehash  
 呼叫此方法以啟用自動重新的`CAtlMap`物件。  
  
```
void EnableAutoRehash() throw();
```  
  
### <a name="remarks"></a>備註  
 自動重新啟用時 （其預設值），雜湊表中的分類收納數目將會自動重新計算值載入 （儲存在陣列中元素數目的分類收納數目的比率） 超過最大或最小值指定在建立對應的時間。  
  
 **EnableAutoRefresh**最常使用的呼叫之後[CAtlMap::DisableAutoRehash](#disableautorehash)。  
  
##  <a name="getat"></a>CAtlMap::GetAt  
 呼叫此方法以傳回對應中的指定位置處的項目。  
  
```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，先前呼叫所傳回[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
 `key`  
 指定地圖的索引鍵的類型樣板參數。  
  
 *值*  
 指定的對應值的類型樣板參數。  
  
### <a name="return-value"></a>傳回值  
 讓指標回到目前的索引鍵/值儲存在 map 中的項目組。  
  
### <a name="remarks"></a>備註  
 在偵錯組建，判斷提示就會發生錯誤，如果`pos`等於 NULL。  
  
##  <a name="getcount"></a>CAtlMap::GetCount  
 呼叫此方法以擷取在對應中的項目數。  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 Map 物件中傳回的項目數。 單一項目是索引鍵/值組。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="gethashtablesize"></a>CAtlMap::GetHashTableSize  
 呼叫這個方法來判斷對應的雜湊表中的分類收納數目。  
  
```
UINT GetHashTableSize() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回雜湊表中的分類收納數目。 請參閱[CAtlMap::CAtlMap](#catlmap)的說明。  
  
##  <a name="getkeyat"></a>CAtlMap::GetKeyAt  
 呼叫此方法以擷取儲存在指定位置的索引鍵`CAtlMap`物件。  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，先前呼叫所傳回[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>傳回值  
 傳回儲存在指定位置的索引鍵的參考`CAtlMap`物件。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getnext"></a>CAtlMap::GetNext  
 呼叫此方法以取得組儲存在下一個元素的指標`CAtlMap`物件。  
  
```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，先前呼叫所傳回[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>傳回值  
 讓指標回到下一個配對的索引鍵/值儲存在 map 中的項目。 `pos`位置計數器會在每次呼叫之後更新。 如果擷取的項目是在對應中，最後一個`pos`設為 NULL。  
  
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
 位置計數器，先前呼叫所傳回[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
 `key`  
 指定地圖的索引鍵的類型樣板參數。  
  
 *值*  
 指定的對應值的類型樣板參數。  
  
### <a name="remarks"></a>備註  
 `pos`位置計數器會在每次呼叫之後更新。 如果擷取的項目是在對應中，最後一個`pos`設為 NULL。  
  
##  <a name="getnextkey"></a>CAtlMap::GetNextKey  
 呼叫這個方法來擷取下一個索引鍵，從`CAtlMap`物件。  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，先前呼叫所傳回[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>傳回值  
 傳回對應中的下一個索引鍵的參考。  
  
### <a name="remarks"></a>備註  
 更新目前位置計數器， `pos`。 如果對應中有沒有更多的項目，則位置計數器是設為 NULL。  
  
##  <a name="getnextvalue"></a>CAtlMap::GetNextValue  
 呼叫此方法來取得下一個值從`CAtlMap`物件。  
  
```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，先前呼叫所傳回[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>傳回值  
 傳回對應中的下一個值的參考。  
  
### <a name="remarks"></a>備註  
 更新目前位置計數器， `pos`。 如果對應中有沒有更多的項目，則位置計數器是設為 NULL。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getstartposition"></a>CAtlMap::GetStartPosition  
 呼叫此方法以啟動對應的反覆項目。  
  
```
POSITION GetStartPosition() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的開始位置或為 NULL 會傳回如果 map 是空的。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以啟動對應的反覆項目，藉由傳回**位置**可以傳遞至值`GetNextAssoc`方法。  
  
> [!NOTE]
>  反覆項目順序不是可預測  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="getvalueat"></a>CAtlMap::GetValueAt  
 呼叫此方法以擷取儲存在指定位置的值`CAtlMap`物件。  
  
```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，先前呼叫所傳回[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="return-value"></a>傳回值  
 傳回值中指定位置處儲存的參考`CAtlMap`物件。  
  
##  <a name="inithashtable"></a>CAtlMap::InitHashTable  
 呼叫此方法以初始化雜湊表。  
  
```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```  
  
### <a name="parameters"></a>參數  
 `nBins`  
 雜湊資料表所用的分類收納數目。 請參閱[CAtlMap::CAtlMap](#catlmap)的說明。  
  
 `bAllocNow`  
 旗標指示應該配置記憶體時。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**上成功初始化、 **false**失敗。  
  
### <a name="remarks"></a>備註  
 `InitHashTable`雜湊表中儲存任何項目之前，必須呼叫。  如果未明確地呼叫這個方法，它將會自動呼叫第一次使用所指定的分類收納計數新增的項目**CAtlMap**建構函式。  否則，對應會初始化使用所指定的新分類收納計數`nBins`參數。  
  
 如果`bAllocNow`參數為 false，直到第一次是必要，不會配置所需的雜湊表的記憶體。 這很有用，如果不確定，如果將用於對應。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="isempty"></a>CAtlMap::IsEmpty  
 呼叫此方法來測試空白對應物件。  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果 map 是空的**false**否則。  
  
##  <a name="kinargtype"></a>CAtlMap::KINARGTYPE  
 機碼傳遞做為輸入的引數時所使用的類型。  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="koutargtype"></a>CAtlMap::KOUTARGTYPE  
 當做輸出引數傳回一個機碼時所使用的類型。  
  
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
  
 *值*  
 收到的查詢上值的變數。  
  
### <a name="return-value"></a>傳回值  
 第一種形式的方法會傳回 true，如果找到機碼，否則為 false。 第二個和第三個表單傳回的指標[CPair](#cpair_class)可用做為位置的呼叫[CAtlMap::GetNext](#getnext) ，依此類推。  
  
### <a name="remarks"></a>備註  
 `Lookup`以快速找出對應項目，包含與指定的索引鍵參數完全相符的索引鍵使用雜湊演算法。  
  
##  <a name="operator_at"></a>CAtlMap::operator\[\]  
 取代或加入新的項目`CAtlMap`。  
  
```
V& operator[](kinargtype key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 要加入或取代的項目索引鍵。  
  
### <a name="return-value"></a>傳回值  
 傳回與指定的索引鍵相關聯的值的參考。  
  
### <a name="example"></a>範例  
 如果金鑰已存在，就會取代項目。 如果索引鍵不存在，則會加入新項目。 請參閱範例的[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="rehash"></a>CAtlMap::Rehash  
 呼叫此方法以 rehash`CAtlMap`物件。  
  
```
void Rehash(UINT nBins = 0);
```  
  
### <a name="parameters"></a>參數  
 `nBins`  
 若要使用雜湊表中的分類收納新的數目。 請參閱[CAtlMap::CAtlMap](#catlmap)的說明。  
  
### <a name="remarks"></a>備註  
 如果`nBins`為 0，`CAtlMap`計算合理的數字，根據在對應與最佳的負載設定中的項目數。 通常 rehashing 程序會自動進行，但是如果[CAtlMap::DisableAutoRehash](#disableautorehash)已呼叫，這個方法會執行必要的調整大小。  
  
##  <a name="removeall"></a>CAtlMap::RemoveAll  
 呼叫這個方法來移除所有項目從`CAtlMap`物件。  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>備註  
 清除`CAtlMap`物件，即釋放記憶體用來儲存項目。  
  
##  <a name="removeatpos"></a>CAtlMap::RemoveAtPos  
 呼叫這個方法來移除在指定位置處的項目`CAtlMap`物件。  
  
```
void RemoveAtPos(POSITION pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，先前呼叫所傳回[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
### <a name="remarks"></a>備註  
 移除指定位置處儲存的索引鍵/值組。 用來儲存之項目的的記憶體，會釋放。 所參考位置`pos`就變成無效，並在地圖中的任何其他項目位置仍有效，這樣做不一定保留相同的順序。  
  
##  <a name="removekey"></a>CAtlMap::RemoveKey  
 呼叫這個方法來移除的項目從`CAtlMap`物件，指定的索引鍵。  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 您想要移除對應的項目組。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果找到索引鍵，而且移除， **false**失敗。  
  
### <a name="example"></a>範例  
 請參閱範例的[CAtlMap::CAtlMap](#catlmap)。  
  
##  <a name="setat"></a>CAtlMap::SetAt  
 呼叫這個方法來插入對應中的項目組。  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>參數  
 `key`  
 若要加入的索引鍵值`CAtlMap`物件。  
  
 *值*  
 要加入值`CAtlMap`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回的位置中的索引鍵/值項目組`CAtlMap`物件。  
  
### <a name="remarks"></a>備註  
 `SetAt`如果找到相符的索引鍵，會取代現有的項目。 如果找不到索引鍵，則會建立新的索引鍵/值組。  
  
##  <a name="setoptimalload"></a>CAtlMap::SetOptimalLoad  
 呼叫此方法以設定最佳的負載`CAtlMap`物件。  
  
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
 負載率下限臨界值。  
  
 `fHiThreshold`  
 負載比率上限臨界值。  
  
 `bRehashNow`  
 表示是否應該重新計算雜湊表的旗標。  
  
### <a name="remarks"></a>備註  
 這個方法會重新定義的最佳負載值`CAtlMap`物件。 請參閱[CAtlMap::CAtlMap](#catlmap)如的討論各種不同的參數。 如果`bRehashNow`為 true，而且項目數目超出最小和最大值，重新計算雜湊表。  
  
##  <a name="setvalueat"></a>CAtlMap::SetValueAt  
 呼叫此方法以變更中的指定位置處儲存的值`CAtlMap`物件。  
  
```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，先前呼叫所傳回[CAtlMap::GetNextAssoc](#getnextassoc)或[CAtlMap::GetStartPosition](#getstartposition)。  
  
 *值*  
 要加入值`CAtlMap`物件。  
  
### <a name="remarks"></a>備註  
 Value 元素中指定位置處儲存的變更`CAtlMap`物件。  
  
##  <a name="vinargtype"></a>CAtlMap::VINARGTYPE  
 將值傳遞做為輸入的引數時所使用的類型。  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="voutargtype"></a>CAtlMap::VOUTARGTYPE  
 將值當做輸出引數傳遞時所使用的類型。  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
##  <a name="m_key"></a>CAtlMap::CPair::m_key  
 資料成員儲存索引鍵的項目。  
  
```
const K m_key;
```    
  
### <a name="parameters"></a>參數  
 `K`  
 索引鍵的項目類型。  
  
##  <a name="m_value"></a>CAtlMap::CPair::m_value  
 資料成員，其儲存值的項目。  
  
```
V  m_value;
```    
  
### <a name="parameters"></a>參數  
 *V*  
 值的項目型別。  
  
## <a name="see-also"></a>請參閱  
 [跑馬燈範例](../../visual-cpp-samples.md)   
 [UpdatePV 範例](../../visual-cpp-samples.md)   
 [類別概觀](../../atl/atl-class-overview.md)
