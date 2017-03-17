---
title: "Ccomsafearray 的 Safearray 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: e78c0cb7a0e2fb6cc1e1ac4bba9186d4beee98b4
ms.lasthandoff: 02/24/2017

---
# <a name="ccomsafearray-class"></a>CComSafeArray 類別
此類別是 **SAFEARRAY** 結構的包裝函式。  
  
## <a name="syntax"></a>語法  
  
```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 陣列中儲存之資料的類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComSafeArray::CComSafeArray](#ccomsafearray)|建構函式。|  
|[Ccomsafearray 的 Safearray:: ~ ccomsafearray 的 Safearray](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComSafeArray::Add](#add)|將一或多個項目 (或 **SAFEARRAY** 結構) 加入 `CComSafeArray`。|  
|[CComSafeArray::Attach](#attach)|將 **SAFEARRAY** 結構附加至 `CComSafeArray` 物件。|  
|[CComSafeArray::CopyFrom](#copyfrom)|將 **SAFEARRAY** 結構的內容複製到 `CComSafeArray` 物件中。|  
|[CComSafeArray::CopyTo](#copyto)|建立 `CComSafeArray` 物件的複本。|  
|[CComSafeArray::Create](#create)|建立 `CComSafeArray` 物件。|  
|[CComSafeArray::Destroy](#destroy)|終結 `CComSafeArray` 物件。|  
|[CComSafeArray::Detach](#detach)|從 **物件卸離** SAFEARRAY `CComSafeArray` 。|  
|[CComSafeArray::GetAt](#getat)|從一維陣列中擷取單一項目。|  
|[CComSafeArray::GetCount](#getcount)|傳回陣列中的元素數目。|  
|[CComSafeArray::GetDimensions](#getdimensions)|傳回陣列中的維度數目。|  
|[CComSafeArray::GetLowerBound](#getlowerbound)|傳回陣列中指定維度的下限。|  
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|傳回 `m_psa` 資料成員的位址。|  
|[CComSafeArray::GetType](#gettype)|傳回陣列中儲存之資料的類型。|  
|[CComSafeArray::GetUpperBound](#getupperbound)|傳回陣列中任何維度的上限。|  
|[CComSafeArray::IsSizable](#issizable)|測試是否可以調整 `CComSafeArray` 物件大小。|  
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|從多維陣列中擷取單一項目。|  
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|設定多維陣列中的項目值。|  
|[CComSafeArray::Resize](#resize)|調整 `CComSafeArray` 物件大小。|  
|[CComSafeArray::SetAt](#setat)|設定一維陣列中的項目值。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|將值轉換成 **SAFEARRAY** 指標。|  
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|從陣列中擷取項目。|  
|[CComSafeArray::operator =](#operator_eq)|指派運算子。|  

  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComSafeArray::m_psa](#m_psa)|此資料成員包含 **SAFEARRAY** 結構的位址。|  
  
## <a name="remarks"></a>備註  
 `CComSafeArray`提供的包裝函式[SAFEARRAY 資料型別](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e)類別，讓它的簡單的方式來建立及管理單一和多維度陣列幾乎是任何支援變數的型別。  
  
 `CComSafeArray` 不僅簡化了在處理序之間傳遞陣列的作業，還藉由針對上下限檢查陣列索引值，來提供額外的安全性。  
  
 `CComSafeArray` 的下限開頭可以是任何使用者定義值；不過，透過 C++ 存取的陣列應該使用下限 0。 Visual Basic 等其他語言可能會使用其他界限值 (例如 -10 到 10)。  
  
 使用[CComSafeArray::Create](#create)建立`CComSafeArray`物件，和[CComSafeArray::Destroy](#destroy)將它刪除。  
  
 `CComSafeArray` 可包含以下 VARIANT 資料類型的子集︰  
  
|VARTYPE|描述|  
|-------------|-----------------|  
|VT_I1|char|  
|VT_I2|short|  
|VT_I4|int|  
|VT_I4|long|  
|VT_I8|longlong|  
|VT_UI1|byte|  
|VT_UI2|ushort|  
|VT_UI4|uint|  
|VT_UI4|ulong|  
|VT_UI8|ulonglong|  
|VT_R4|float|  
|VT_R8|double|  
|VT_DECIMAL|decimal 指標|  
|VT_VARIANT|variant 指標|  
|VT_CY|Currency 資料類型|  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlsafe.h  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&75;](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]  
  
##  <a name="add"></a>CComSafeArray::Add  
 將一或多個項目 (或 **SAFEARRAY** 結構) 加入 `CComSafeArray`。  
  
```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `psaSrc`  
 指標**SAFEARRAY**物件。  
  
 `ulCount`  
 要加入至陣列的物件數目。  
  
 *pT*  
 若要加入至陣列的一或多個物件指標。  
  
 *t*  
 若要加入至陣列物件的參考。  
  
 `bCopy`  
 指出是否應該建立一份資料。 預設值是**TRUE**。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 新的物件會附加至現有的結尾**SAFEARRAY**物件。 將物件加入至多維度**SAFEARRAY**不支援物件。 新增現有物件的陣列，當兩個陣列必須包含相同類型的項目。  
  
 `bCopy`旗標考慮到當項目類型的`BSTR`或**VARIANT**會加入至陣列。 預設值的**TRUE**會確保新的複本是資料的項目加入至陣列時。  
  
##  <a name="attach"></a>CComSafeArray::Attach  
 將 **SAFEARRAY** 結構附加至 `CComSafeArray` 物件。  
  
```
HRESULT Attach(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>參數  
 `psaSrc`  
 指標**SAFEARRAY**結構。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 附加**SAFEARRAY**結構以`CComSafeArray`的物件，使現有`CComSafeArray`可用方法。  
  
##  <a name="ccomsafearray"></a>CComSafeArray::CComSafeArray  
 建構函式。  
  
```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>參數  
 `bound`  
 A **SAFEARRAYBOUND**結構。  
  
 `ulCount`  
 陣列中的項目數。  
  
 `lLBound`  
 下限值。也就是說，陣列中的第一個元素的索引。  
  
 `pBound`  
 指標**SAFEARRAYBOUND**結構。  
  
 `uDims`  
 陣列中的維度數目。  
  
 `saSrc`  
 參考**SAFEARRAY**結構或`CComSafeArray`物件。 在任一情況下建構函式會使用這個參考陣列的複本，讓建構完成之後不參考之陣列。  
  
 `psaSrc`  
 指標**SAFEARRAY**結構。 建構函式會使用這個位址，陣列的複本，讓建構完成之後不參考之陣列。  
  
### <a name="remarks"></a>備註  
 建立 `CComSafeArray` 物件。  
  
##  <a name="dtor"></a>Ccomsafearray 的 Safearray:: ~ ccomsafearray 的 Safearray  
 解構函式。  
  
```
~CComSafeArray() throw()
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源。  
  
##  <a name="copyfrom"></a>CComSafeArray::CopyFrom  
 將 **SAFEARRAY** 結構的內容複製到 `CComSafeArray` 物件中。  
  
```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>參數  
 `ppArray`  
 指標**SAFEARRAY**複製。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個方法的內容複製**SAFEARRAY**到目前`CComSafeArray`物件。 會取代現有的陣列的內容。  
  
##  <a name="copyto"></a>CComSafeArray::CopyTo  
 建立 `CComSafeArray` 物件的複本。  
  
```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>參數  
 `ppArray`  
 要在其中建立新的位置指標**SAFEARRAY**。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個方法的內容複製`CComSafeArray`物件插入**SAFEARRAY**結構。  
  
##  <a name="create"></a>CComSafeArray::Create  
 建立 `CComSafeArray`。  
  
```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>參數  
 `pBound`  
 指標**SAFEARRAYBOUND**物件。  
  
 `uDims`  
 陣列中的維度數目。  
  
 `ulCount`  
 陣列中的項目數。  
  
 `lLBound`  
 下限值。也就是說，陣列中的第一個元素的索引。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 A`CComSafeArray`物件可以建立從現有**SAFEARRAYBOUND**結構和數字的維度，或藉由在陣列與下限指定的項目數。 如果陣列是從 Visual c + + 存取，而下限應該是 0。 其他語言可能可以使用其他值下限 （例如，項目，例如-10 到 10 的範圍的 Visual Basic 支援陣列）。  
  
##  <a name="destroy"></a>CComSafeArray::Destroy  
 終結 `CComSafeArray` 物件。  
  
```
HRESULT Destroy();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 終結的現有`CComSafeArray`物件及其所有包含的資料。  
  
##  <a name="detach"></a>CComSafeArray::Detach  
 從 **物件卸離** SAFEARRAY `CComSafeArray` 。  
  
```
LPSAFEARRAY Detach();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的指標**SAFEARRAY**物件。  
  
### <a name="remarks"></a>備註  
 這個方法會卸離**SAFEARRAY**物件從`CComSafeArray`物件。  
  
##  <a name="getat"></a>CComSafeArray::GetAt  
 從一維陣列中擷取單一項目。  
  
```
T& GetAt(LONG lIndex) const;
```  
  
### <a name="parameters"></a>參數  
 `lIndex`  
 這個引數傳回陣列中的值。  
  
### <a name="return-value"></a>傳回值  
 傳回所需的陣列元素的參考。  
  
##  <a name="getcount"></a>CComSafeArray::GetCount  
 傳回陣列中的元素數目。  
  
```
ULONG GetCount(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>參數  
 `uDim`  
 陣列的維度。  
  
### <a name="return-value"></a>傳回值  
 傳回陣列中的元素數目。  
  
### <a name="remarks"></a>備註  
 多維陣列搭配使用時，這個方法會傳回的項目數特定維度中。  
  
##  <a name="getdimensions"></a>CComSafeArray::GetDimensions  
 傳回陣列中的維度數目。  
  
```
UINT GetDimensions() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回陣列中的維度數目。  
  
##  <a name="getlowerbound"></a>CComSafeArray::GetLowerBound  
 傳回陣列中指定維度的下限。  
  
```
LONG GetLowerBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>參數  
 `uDim`  
 要取得最小值的陣列維度。 如果省略，預設值為 0。  
  
### <a name="return-value"></a>傳回值  
 傳回下限。  
  
### <a name="remarks"></a>備註  
 如果下限為 0，這表示類似 C 陣列，其第一個項目都是項目編號 0。 發生錯誤時，例如，無效的維度引數，這個方法會呼叫`AtlThrow`，描述錯誤的 HRESULT。  
  
##  <a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr  
 傳回 `m_psa` 資料成員的位址。  
  
```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的指標[CComSafeArray::m_psa](#m_psa)資料成員。  
  
##  <a name="gettype"></a>CComSafeArray::GetType  
 傳回陣列中儲存之資料的類型。  
  
```
VARTYPE GetType() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回儲存在陣列中，可能是下列類型的資料類型︰  
  
|VARTYPE|描述|  
|-------------|-----------------|  
|VT_I1|char|  
|VT_I2|short|  
|VT_I4|int|  
|VT_I4|long|  
|VT_I8|longlong|  
|VT_UI1|byte|  
|VT_UI2|ushort|  
|VT_UI4|uint|  
|VT_UI4|ulong|  
|VT_UI8|ulonglong|  
|VT_R4|float|  
|VT_R8|double|  
|VT_DECIMAL|decimal 指標|  
|VT_VARIANT|variant 指標|  
|VT_CY|Currency 資料類型|  
  
##  <a name="getupperbound"></a>CComSafeArray::GetUpperBound  
 傳回陣列中任何維度的上限。  
  
```
LONG GetUpperBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>參數  
 `uDim`  
 要取得上限的陣列維度。 如果省略，預設值為 0。  
  
### <a name="return-value"></a>傳回值  
 傳回上限。 這個值是內含值，這個維度的最大的有效索引。  
  
### <a name="remarks"></a>備註  
 發生錯誤時，例如，無效的維度引數，這個方法會呼叫`AtlThrow`，描述錯誤的 HRESULT。  
  
##  <a name="issizable"></a>CComSafeArray::IsSizable  
 測試是否可以調整 `CComSafeArray` 物件大小。  
  
```
bool IsSizable() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果`CComSafeArray`可調整大小， **false**如果不行。  
  
##  <a name="m_psa"></a>CComSafeArray::m_psa  
 保留的位址**SAFEARRAY**結構的存取。  
  
```
LPSAFEARRAY m_psa;
```  
  
##  <a name="multidimgetat"></a>CComSafeArray::MultiDimGetAt  
 從多維陣列中擷取單一項目。  
  
```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```  
  
### <a name="parameters"></a>參數  
 `alIndex`  
 指標的陣列中每個維度的索引向量。 最左邊 （最大） 的維度是`alIndex`[0] *。*  
  
 *t*  
 傳回資料的參考。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="multidimsetat"></a>CComSafeArray::MultiDimSetAt  
 設定多維陣列中的項目值。  
  
```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```  
  
### <a name="parameters"></a>參數  
 `alIndex`  
 指標的陣列中每個維度的索引向量。 最右邊 （最不重要） 的維度是`alIndex`[0]。  
  
 *T*  
 指定新項目的值。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這是多維度版本[CComSafeArray::SetAt](#setat)。  
  
##  <a name="operator_at"></a>CComSafeArray::operator\[\]  
 從陣列中擷取項目。  
  
```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```  
  
### <a name="parameters"></a>參數  
 *lIndex nIndex*  
 必要的項目陣列中的索引編號。  
  
### <a name="return-value"></a>傳回值  
 傳回適當的陣列項目。  
  
### <a name="remarks"></a>備註  
 執行類似的功能[CComSafeArray::GetAt](#getat)，但是這個運算子只能搭配一維陣列。  
  
##  <a name="operator_eq"></a>CComSafeArray::operator =  
 指派運算子。  
  
```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>參數  
 `saSrc`  
 對 `CComSafeArray` 物件的參考。  
  
 `psaSrc`  
 指標**SAFEARRAY**物件。  
  
### <a name="return-value"></a>傳回值  
 傳回陣列中儲存之資料的類型。  
  
##  <a name="operator_lpsafearray"></a>CComSafeArray::operator LPSAFEARRAY  
 將值轉換成 **SAFEARRAY** 指標。  
  
```
operator LPSAFEARRAY() const;
```  
  
### <a name="return-value"></a>傳回值  
 將值轉換成 **SAFEARRAY** 指標。  
  
##  <a name="resize"></a>CComSafeArray::Resize  
 調整 `CComSafeArray` 物件大小。  
  
```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>參數  
 `pBound`  
 指標**SAFEARRAYBOUND**結構，其中包含有關項目的數目和陣列的下限。  
  
 `ulCount`  
 要求的已調整大小的陣列中的物件數目。  
  
 `lLBound`  
 下限。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個方法只會調整大小的最右邊的維度。 它不會調整大小，傳回的陣列**IsResizable**為**false**。  
  
##  <a name="setat"></a>CComSafeArray::SetAt  
 設定一維陣列中的項目值。  
  
```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `lIndex`  
 若要設定的陣列元素的索引編號。  
  
 *t*  
 指定的項目新值。  
  
 `bCopy`  
 指出是否應該建立一份資料。 預設值是**TRUE**。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 `bCopy`旗標考慮到當項目類型的`BSTR`或**VARIANT**會加入至陣列。 預設值的**TRUE**會確保新的複本是資料的項目加入至陣列時。  
  
## <a name="see-also"></a>另請參閱  
 [SAFEARRAY 資料類型](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e)   
 [CComSafeArray::Create](#create)   
 [CComSafeArray::Destroy](#destroy)   
 [類別概觀](../../atl/atl-class-overview.md)

