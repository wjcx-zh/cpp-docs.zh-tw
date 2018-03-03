---
title: "CRBTree 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRBTree
- ATLCOLL/ATL::CRBTree
- ATLCOLL/ATL::CRBTree::KINARGTYPE
- ATLCOLL/ATL::CRBTree::KOUTARGTYPE
- ATLCOLL/ATL::CRBTree::VINARGTYPE
- ATLCOLL/ATL::CRBTree::VOUTARGTYPE
- ATLCOLL/ATL::CRBTree::FindFirstKeyAfter
- ATLCOLL/ATL::CRBTree::GetAt
- ATLCOLL/ATL::CRBTree::GetCount
- ATLCOLL/ATL::CRBTree::GetHeadPosition
- ATLCOLL/ATL::CRBTree::GetKeyAt
- ATLCOLL/ATL::CRBTree::GetNext
- ATLCOLL/ATL::CRBTree::GetNextAssoc
- ATLCOLL/ATL::CRBTree::GetNextKey
- ATLCOLL/ATL::CRBTree::GetNextValue
- ATLCOLL/ATL::CRBTree::GetPrev
- ATLCOLL/ATL::CRBTree::GetTailPosition
- ATLCOLL/ATL::CRBTree::GetValueAt
- ATLCOLL/ATL::CRBTree::IsEmpty
- ATLCOLL/ATL::CRBTree::RemoveAll
- ATLCOLL/ATL::CRBTree::RemoveAt
- ATLCOLL/ATL::CRBTree::SetValueAt
dev_langs:
- C++
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f436a3661f027ba1026a60982cb18b48a2c48cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crbtree-class"></a>CRBTree 類別
這個類別會提供建立和使用紅黑樹狀結構的方法。  
  
## <a name="syntax"></a>語法  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBTree
```  
  
#### <a name="parameters"></a>參數  
 `K`  
 索引鍵的項目類型。  
  
 *V*  
 值的項目型別。  
  
 `KTraits`  
 程式碼，用來複製或移動的索引鍵項目。 請參閱[CElementTraits 類別](../../atl/reference/celementtraits-class.md)如需詳細資訊。  
  
 `VTraits`  
 用於複製或移動的項目值的程式碼。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CRBTree::KINARGTYPE](#kinargtype)|機碼傳遞做為輸入的引數時所使用的類型。|  
|[CRBTree::KOUTARGTYPE](#koutargtype)|當做輸出引數傳回一個機碼時所使用的類型。|  
|[CRBTree::VINARGTYPE](#vinargtype)|將值傳遞做為輸入的引數時所使用的類型。|  
|[CRBTree::VOUTARGTYPE](#voutargtype)|將值當做輸出引數傳遞時所使用的類型。|  
  
### <a name="public-classes"></a>公用類別  
  
|名稱|描述|  
|----------|-----------------|  
|[CRBTree::CPair 類別](#cpair_class)|類別，其中包含索引鍵和值的項目。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CRBTree:: ~ CRBTree](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|呼叫這個方法，以找出該位置會使用下一個可用的索引鍵的項目。|  
|[CRBTree::GetAt](#getat)|呼叫這個方法來取得在樹狀目錄中的指定位置的項目。|  
|[CRBTree::GetCount](#getcount)|呼叫這個方法，在樹狀目錄中取得的項目數。|  
|[CRBTree::GetHeadPosition](#getheadposition)|呼叫這個方法，在樹狀結構的開頭處的項目取得的位置值。|  
|[CRBTree::GetKeyAt](#getkeyat)|呼叫這個方法來取得在樹狀目錄中的指定位置的機碼。|  
|[CRBTree::GetNext](#getnext)|呼叫這個方法來取得指向中預存項目的`CRBTree`物件，並前移至下一個元素的位置。|  
|[CRBTree::GetNextAssoc](#getnextassoc)|呼叫此方法以取得索引鍵和值儲存在 map 中的項目，並前移至下一個元素的位置。|  
|[CRBTree::GetNextKey](#getnextkey)|呼叫此方法來取得儲存在樹狀目錄中之元素的索引鍵，並前移至下一個元素的位置。|  
|[CRBTree::GetNextValue](#getnextvalue)|呼叫這個方法來取得儲存在樹狀目錄中之元素的值，並前移至下一個元素的位置。|  
|[CRBTree::GetPrev](#getprev)|呼叫這個方法來取得指向中預存項目的`CRBTree`物件，然後再更新上一個項目位置。|  
|[CRBTree::GetTailPosition](#gettailposition)|呼叫此方法以取得樹狀結構的結尾處的項目中的位置值。|  
|[CRBTree::GetValueAt](#getvalueat)|呼叫此方法以擷取儲存在指定位置的值`CRBTree`物件。|  
|[CRBTree::IsEmpty](#isempty)|呼叫此方法來測試空白樹狀物件。|  
|[CRBTree::RemoveAll](#removeall)|呼叫這個方法來移除所有項目從**CRBTree**物件。|  
|[CRBTree::RemoveAt](#removeat)|呼叫這個方法來移除在指定位置處的項目**CRBTree**物件。|  
|[CRBTree::SetValueAt](#setvalueat)|呼叫此方法以變更中的指定位置處儲存的值`CRBTree`物件。|  
  
## <a name="remarks"></a>備註  
 紅黑樹狀目錄會使用額外的二進位搜尋樹狀結構的每個節點，以確保它保持資訊的位元 「 平衡、 」 是、 樹狀結構高度不會成長到不當比例大，而且會影響效能。  
  
 此範本類別設計來供[CRBMap](../../atl/reference/crbmap-class.md)和[CRBMultiMap](../../atl/reference/crbmultimap-class.md)。 所提供的方法，這些衍生類別所組成的大量`CRBTree`。  
  
 如需更完整討論各種不同的集合類別和其功能和效能特性，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="cpair_class"></a>CRBTree::CPair 類別  
 類別，其中包含索引鍵和值的項目。  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>備註  
 方法會使用這個類別[CRBTree::GetAt](#getat)， [CRBTree::GetNext](#getnext)，和[CRBTree::GetPrev](#getprev)存取儲存在樹狀結構中的索引鍵和值的項目。  
  
 成員如下所示：  
  
|||  
|-|-|  
|`m_key`|資料成員儲存索引鍵的項目。|  
|`m_value`|資料成員，其儲存值的項目。|  
  
##  <a name="dtor"></a>CRBTree:: ~ CRBTree  
 解構函式。  
  
```
~CRBTree() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有配置的資源。 呼叫[CRBTree::RemoveAll](#removeall)刪除所有項目。  
  
##  <a name="findfirstkeyafter"></a>CRBTree::FindFirstKeyAfter  
 呼叫這個方法，以找出該位置會使用下一個可用的索引鍵的項目。  
  
```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```  
  
### <a name="parameters"></a>參數  
 `key`  
 索引鍵的值。  
  
### <a name="return-value"></a>傳回值  
 傳回位置的值會使用下一個可用的索引鍵的項目。 如果不有任何其他項目，則會傳回 NULL。  
  
### <a name="remarks"></a>備註  
 此方法可讓您輕鬆地周遊樹狀目錄，而不需要事先計算位置的值。  
  
##  <a name="getat"></a>CRBTree::GetAt  
 呼叫這個方法來取得在樹狀目錄中的指定位置的項目。  
  
```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置值。  
  
 `key`  
 變數會接收索引鍵。  
  
 *值*  
 變數接收值。  
  
### <a name="return-value"></a>傳回值  
 前兩個表單傳回的指標[CPair](#cpair_class)。 第三種形式取得索引鍵和值，指定的位置。  
  
### <a name="remarks"></a>備註  
 位置值可以先前透過方法呼叫這類[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::GetTailPosition](#gettailposition)。  
  
 在偵錯組建中，如果，就會發生判斷提示失敗`pos`等於 NULL。  
  
##  <a name="getcount"></a>CRBTree::GetCount  
 呼叫這個方法，在樹狀目錄中取得的項目數。  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的元素數目 （每個索引鍵/值組是一個項目） 儲存在樹狀目錄中。  
  
##  <a name="getheadposition"></a>CRBTree::GetHeadPosition  
 呼叫這個方法，在樹狀結構的開頭處的項目取得的位置值。  
  
```
POSITION GetHeadPosition() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回在樹狀結構的開頭處的項目位置值。  
  
### <a name="remarks"></a>備註  
 所傳回的值`GetHeadPosition`可以搭配方法例如[CRBTree::GetKeyAt](#getkeyat)或[CRBTree::GetNext](#getnext)周遊樹狀結構，和擷取值。  
  
##  <a name="getkeyat"></a>CRBTree::GetKeyAt  
 呼叫這個方法來取得在樹狀目錄中的指定位置的機碼。  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置值。  
  
### <a name="return-value"></a>傳回值  
 傳回儲存位置的索引鍵`pos`在樹狀目錄中。  
  
### <a name="remarks"></a>備註  
 如果`pos`不是有效的位置值，結果將無法預期。 在偵錯組建中，如果，就會發生判斷提示失敗`pos`等於 NULL。  
  
##  <a name="getnext"></a>CRBTree::GetNext  
 呼叫這個方法來取得指向中預存項目的`CRBTree`物件，並前移至下一個元素的位置。  
  
```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，例如先前方法呼叫所傳回[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。  
  
### <a name="return-value"></a>傳回值  
 傳回下指標[CPair](#cpair_class)在樹狀目錄中的值。  
  
### <a name="remarks"></a>備註  
 `pos`位置計數器會在每次呼叫之後更新。 擷取的項目是否在樹狀目錄中的最後一個`pos`設為 NULL。  
  
##  <a name="getnextassoc"></a>CRBTree::GetNextAssoc  
 呼叫此方法以取得索引鍵和值儲存在 map 中的項目，並前移至下一個元素的位置。  
  
```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，例如先前方法呼叫所傳回[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。  
  
 `key`  
 指定的樹狀目錄索引鍵的類型樣板參數。  
  
 *值*  
 指定的樹狀目錄值的類型樣板參數。  
  
### <a name="remarks"></a>備註  
 `pos`位置計數器會在每次呼叫之後更新。 擷取的項目是否在樹狀目錄中的最後一個`pos`設為 NULL。  
  
##  <a name="getnextkey"></a>CRBTree::GetNextKey  
 呼叫此方法來取得儲存在樹狀目錄中之元素的索引鍵，並前移至下一個元素的位置。  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，例如先前方法呼叫所傳回[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。  
  
### <a name="return-value"></a>傳回值  
 傳回在樹狀目錄中的下一個索引鍵的參考。  
  
### <a name="remarks"></a>備註  
 更新目前位置計數器， `pos`。 如果在樹狀目錄中有沒有更多的項目，則位置計數器是設為 NULL。  
  
##  <a name="getnextvalue"></a>CRBTree::GetNextValue  
 呼叫這個方法來取得儲存在樹狀目錄中之元素的值，並前移至下一個元素的位置。  
  
```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，例如先前方法呼叫所傳回[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。  
  
### <a name="return-value"></a>傳回值  
 傳回在樹狀目錄中的下一個值的參考。  
  
### <a name="remarks"></a>備註  
 更新目前位置計數器， `pos`。 如果在樹狀目錄中有沒有更多的項目，則位置計數器是設為 NULL。  
  
##  <a name="getprev"></a>CRBTree::GetPrev  
 呼叫這個方法來取得指向中預存項目的`CRBTree`物件，然後再更新上一個項目位置。  
  
```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，例如先前方法呼叫所傳回[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。  
  
### <a name="return-value"></a>傳回值  
 讓指標回到先前[CPair](#cpair_class)在樹狀目錄中儲存值。  
  
### <a name="remarks"></a>備註  
 更新目前位置計數器， `pos`。 如果在樹狀目錄中有沒有更多的項目，則位置計數器是設為 NULL。  
  
##  <a name="gettailposition"></a>CRBTree::GetTailPosition  
 呼叫此方法以取得樹狀結構的結尾處的項目中的位置值。  
  
```
POSITION GetTailPosition() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 會傳回樹狀結構的結尾處的項目位置值。  
  
### <a name="remarks"></a>備註  
 所傳回的值`GetTailPosition`可以搭配方法例如[CRBTree::GetKeyAt](#getkeyat)或[CRBTree::GetPrev](#getprev)周遊樹狀結構，和擷取值。  
  
##  <a name="getvalueat"></a>CRBTree::GetValueAt  
 呼叫此方法以擷取儲存在指定位置的值`CRBTree`物件。  
  
```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，例如先前方法呼叫所傳回[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。  
  
### <a name="return-value"></a>傳回值  
 傳回值中指定位置處儲存的參考`CRBTree`物件。  
  
##  <a name="isempty"></a>CRBTree::IsEmpty  
 呼叫此方法來測試空白樹狀物件。  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**樹狀結構是空的如果**false**否則。  
  
##  <a name="kinargtype"></a>CRBTree::KINARGTYPE  
 機碼傳遞做為輸入的引數時所使用的類型。  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="koutargtype"></a>CRBTree::KOUTARGTYPE  
 當做輸出引數傳回一個機碼時所使用的類型。  
  
```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```  
  
##  <a name="removeall"></a>CRBTree::RemoveAll  
 呼叫這個方法來移除所有項目從`CRBTree`物件。  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>備註  
 清除`CRBTree`物件，即釋放記憶體用來儲存項目。  
  
##  <a name="removeat"></a>CRBTree::RemoveAt  
 呼叫這個方法來移除在指定位置處的項目**CRBTree**物件。  
  
```
void RemoveAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，例如先前方法呼叫所傳回[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。  
  
### <a name="remarks"></a>備註  
 移除指定位置處儲存的索引鍵/值組。 用來儲存之項目的的記憶體，會釋放。 所參考位置`pos`失效，且在樹狀結構中的任何其他項目位置仍有效，這樣做不一定保留相同的順序。  
  
##  <a name="setvalueat"></a>CRBTree::SetValueAt  
 呼叫此方法以變更中的指定位置處儲存的值`CRBTree`物件。  
  
```
void SetValueAt(POSITION pos, VINARGTYPE value);
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置計數器，例如先前方法呼叫所傳回[CRBTree::GetHeadPosition](#getheadposition)或[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)。  
  
 *值*  
 要加入值`CRBTree`物件。  
  
### <a name="remarks"></a>備註  
 Value 元素中指定位置處儲存的變更`CRBTree`物件。  
  
##  <a name="vinargtype"></a>CRBTree::VINARGTYPE  
 將值傳遞做為輸入的引數時所使用的類型。  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="voutargtype"></a>CRBTree::VOUTARGTYPE  
 將值當做輸出引數傳遞時所使用的類型。  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
