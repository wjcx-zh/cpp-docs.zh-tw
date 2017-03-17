---
title: "CAtlList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
dev_langs:
- C++
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
caps.latest.revision: 19
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
ms.openlocfilehash: b1ed350da625695f610980f9f48a6ae11394d3c8
ms.lasthandoff: 02/24/2017

---
# <a name="catllist-class"></a>CAtlList 類別
這個類別提供方法來建立和管理清單物件。  
  
## <a name="syntax"></a>語法  
  
```
template<typename E, class ETraits = CElementTraits<E>>  
class CAtlList
```  
  
#### <a name="parameters"></a>參數  
 `E`  
 元素類型。  
  
 `ETraits`  
 複製或移動項目使用的程式碼。 請參閱[CElementTraits 類別](../../atl/reference/celementtraits-class.md)如需詳細資訊。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlList::INARGTYPE](#inargtype)||  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlList::CAtlList](#catllist)|建構函式。|  
|[CAtlList:: ~ CAtlList](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlList::AddHead](#addhead)|呼叫這個方法將項目新增至清單的開頭。|  
|[CAtlList::AddHeadList](#addheadlist)|呼叫這個方法，以將現有的清單加入至清單的開頭。|  
|[CAtlList::AddTail](#addtail)|呼叫此方法以新增項目到此清單的結尾。|  
|[CAtlList::AddTailList](#addtaillist)|呼叫此方法，將現有的清單加入到此清單的結尾。|  
|[CAtlList::AssertValid](#assertvalid)|呼叫這個方法，以確認清單是有效的。|  
|[CAtlList::Find](#find)|呼叫這個方法來搜尋指定項目的清單。|  
|[CAtlList::FindIndex](#findindex)|呼叫這個方法來取得項目的位置指定的索引值。|  
|[CAtlList::GetAt](#getat)|呼叫這個方法來傳回清單中的指定位置處的項目。|  
|[CAtlList::GetCount](#getcount)|呼叫這個方法來傳回清單中的物件數目。|  
|[CAtlList::GetHead](#gethead)|呼叫這個方法來傳回清單的開頭處的項目。|  
|[CAtlList::GetHeadPosition](#getheadposition)|呼叫這個方法來取得清單的開頭位置。|  
|[CAtlList::GetNext](#getnext)|呼叫此方法以傳回下一個項目從清單中。|  
|[CAtlList::GetPrev](#getprev)|呼叫這個方法，傳回上一個項目從清單中。|  
|[CAtlList::GetTail](#gettail)|呼叫這個方法來傳回清單的結尾處的項目。|  
|[CAtlList::GetTailPosition](#gettailposition)|呼叫這個方法來取得清單的結尾的位置。|  
|[CAtlList::InsertAfter](#insertafter)|呼叫這個方法，以新的項目插入後的指定位置的清單。|  
|[CAtlList::InsertBefore](#insertbefore)|呼叫這個方法在指定位置的清單中插入新項目。|  
|[CAtlList::IsEmpty](#isempty)|呼叫這個方法來判斷是否清單是空白。|  
|[CAtlList::MoveToHead](#movetohead)|呼叫這個方法，將指定的項目移至清單的開頭。|  
|[CAtlList::MoveToTail](#movetotail)|呼叫這個方法，將指定的項目移至清單的結尾。|  
|[CAtlList::RemoveAll](#removeall)|呼叫此方法以從清單中移除所有項目。|  
|[CAtlList::RemoveAt](#removeat)|呼叫此方法以從清單中移除單一項目。|  
|[CAtlList::RemoveHead](#removehead)|呼叫此方法以移除清單的開頭處的項目。|  
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|呼叫此方法以移除清單的開頭處的項目，但不傳回值。|  
|[CAtlList::RemoveTail](#removetail)|呼叫此方法以移除清單結尾處的項目。|  
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|呼叫此方法以移除清單結尾處的項目，但不傳回值。|  
|[CAtlList::SetAt](#setat)|呼叫這個方法，在清單中的指定位置中設定項目的值。|  
|[CAtlList::SwapElements](#swapelements)|呼叫此方法來交換在清單中的項目。|  
  
## <a name="remarks"></a>備註  
 `CAtlList`類別支援循序或依值排序的非唯一可存取的物件清單。 `CAtlList`列出表現雙向連結清單。 每個清單具有一個頭部和尾部，而且新的項目 （或在某些情況下的清單） 可以加入至清單結尾或插入之前或之後的特定項目。  
  
 大部分的`CAtlList`方法會使用的位置值。 這個值用來參考的實際記憶體位置，其中項目會儲存並不應計算或預測直接方法。 如果有必要存取*n*個項目在清單中，此方法[CAtlList::FindIndex](#findindex)會傳回給定索引的對應位置值。 方法[CAtlList::GetNext](#getnext)和[CAtlList::GetPrev](#getprev)可用來逐一查看清單中的物件。  
  
 如需有關使用 ATL 集合類別的詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="addhead"></a>CAtlList::AddHead  
 呼叫這個方法將項目新增至清單的開頭。  
  
```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```  
  
### <a name="parameters"></a>參數  
 `element`  
 新的項目。  
  
### <a name="return-value"></a>傳回值  
 傳回新加入的項目位置。  
  
### <a name="remarks"></a>備註  
 如果使用的第一個版本，則會建立空項目，使用其預設建構函式，而不是複製建構函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&13;](../../atl/codesnippet/cpp/catllist-class_1.cpp)]  
  
##  <a name="addheadlist"></a>CAtlList::AddHeadList  
 呼叫這個方法，以將現有的清單加入至清單的開頭。  
  
```
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```  
  
### <a name="parameters"></a>參數  
 `plNew`  
 要加入的清單。  
  
### <a name="remarks"></a>備註  
 清單所指`plNew`插入現有清單的開頭。 在偵錯組建中，如果，就會發生判斷提示失敗`plNew`等於 NULL。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&14;](../../atl/codesnippet/cpp/catllist-class_2.cpp)]  
  
##  <a name="addtail"></a>CAtlList::AddTail  
 呼叫此方法以新增項目到此清單的結尾。  
  
```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```  
  
### <a name="parameters"></a>參數  
 `element`  
 要加入的項目。  
  
### <a name="return-value"></a>傳回值  
 傳回新加入的項目位置。  
  
### <a name="remarks"></a>備註  
 如果使用的第一個版本，則會建立空項目，使用其預設建構函式，而不是複製建構函式。 元素會加入至清單的結尾，所以它現在會變成結尾。 這個方法可使用空的清單。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&15;](../../atl/codesnippet/cpp/catllist-class_3.cpp)]  
  
##  <a name="addtaillist"></a>CAtlList::AddTailList  
 呼叫此方法，將現有的清單加入到此清單的結尾。  
  
```
void AddTailList(const CAtlList<E, ETraits>* plNew);
```  
  
### <a name="parameters"></a>參數  
 `plNew`  
 要加入的清單。  
  
### <a name="remarks"></a>備註  
 清單所指`plNew`後面插入最後一個項目 （如果有的話） 中的清單物件。 中的最後一個項目`plNew`因此成為清單的結尾。 在偵錯組建中，如果，就會發生判斷提示失敗*plNew*等於 NULL。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&16;](../../atl/codesnippet/cpp/catllist-class_4.cpp)]  
  
##  <a name="assertvalid"></a>CAtlList::AssertValid  
 呼叫這個方法，以確認清單是有效的。  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，如果不是有效的清單物件，會發生判斷提示失敗。 若要有效，空的清單必須同時開頭與結尾指標為 NULL，而且標頭和結尾指向有效的位址，必須不是空的清單。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&17;](../../atl/codesnippet/cpp/catllist-class_5.cpp)]  
  
##  <a name="catllist"></a>CAtlList::CAtlList  
 建構函式。  
  
```
CAtlList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 區塊大小。  
  
### <a name="remarks"></a>備註  
 建構函式`CAtlList`物件。 區塊大小是記憶體的一種配置需要新的項目時數量。 較大的區塊大小減少記憶體配置常式，但使用較多資源。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&18;](../../atl/codesnippet/cpp/catllist-class_6.cpp)]  
  
##  <a name="dtor"></a>CAtlList:: ~ CAtlList  
 解構函式。  
  
```
~CAtlList() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源，包括呼叫[CAtlList::RemoveAll](#removeall)從清單移除所有項目。  
  
 在偵錯組建中，如果清單仍會包含一些項目之後呼叫，就會發生判斷提示失敗`RemoveAll`。  
  
##  <a name="find"></a>CAtlList::Find  
 呼叫這個方法來搜尋指定項目的清單。  
  
```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```  
  
### <a name="parameters"></a>參數  
 `element`  
 要在清單中找到的項目。  
  
 `posStartAfter`  
 搜尋開始位置。 如果未不指定任何值，標頭項目將會開始搜尋。  
  
### <a name="return-value"></a>傳回值  
 傳回項目的位置值，如果找到，否則傳回 NULL。  
  
### <a name="remarks"></a>備註  
 在偵錯組建的清單物件是否不正確，或如果，就會發生判斷提示失敗`posStartAfter`值超出範圍。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&19;](../../atl/codesnippet/cpp/catllist-class_7.cpp)]  
  
##  <a name="findindex"></a>CAtlList::FindIndex  
 呼叫這個方法來取得項目的位置指定的索引值。  
  
```
POSITION FindIndex(size_t iElement) const throw();
```  
  
### <a name="parameters"></a>參數  
 `iElement`  
 必要的清單項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果傳回的對應位置的值或 NULL`iElement`超出範圍。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回對應於指定的索引值，允許存取的位置*n*個項目清單中的。  
  
 在偵錯組建中，如果不是有效的清單物件，會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&20;](../../atl/codesnippet/cpp/catllist-class_8.cpp)]  
  
##  <a name="getat"></a>CAtlList::GetAt  
 呼叫這個方法來傳回清單中的指定位置處的項目。  
  
```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置值，指定特定的項目。  
  
### <a name="return-value"></a>傳回值  
 參考或項目的複本。  
  
### <a name="remarks"></a>備註  
 如果清單是**const**，`GetAt`傳回項目的複本。 這可讓方法只能用在指派陳述式的右側，並防止修改的清單。  
  
 如果清單不是**const**，`GetAt`傳回之項目的參考。 這可讓方法用在指派陳述式的任一邊，而讓 要修改之清單項目。  
  
 在偵錯組建中，如果，就會發生判斷提示失敗`pos`等於 NULL。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlList::FindIndex](#findindex)。  
  
##  <a name="getcount"></a>CAtlList::GetCount  
 呼叫這個方法來傳回清單中的物件數目。  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回清單中項目的數目。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlList::Find](#find)。  
  
##  <a name="gethead"></a>CAtlList::GetHead  
 呼叫這個方法來傳回清單的開頭處的項目。  
  
```
E& GetHead() throw();
const E& GetHead() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的參考或開頭的清單項目的複本。  
  
### <a name="remarks"></a>備註  
 如果清單是**const**，`GetHead`傳回一份清單的開頭處的項目。 這可讓方法只能用在指派陳述式的右側，並防止修改的清單。  
  
 如果清單不是**const**，`GetHead`傳回的參考清單的開頭處的項目。 這可讓方法用在指派陳述式的任一邊，而讓 要修改之清單項目。  
  
 在偵錯組建中，如果對 list 的 head 點為 NULL，會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlList::AddHead](#addhead)。  
  
##  <a name="getheadposition"></a>CAtlList::GetHeadPosition  
 呼叫這個方法來取得清單的開頭位置。  
  
```
POSITION GetHeadPosition() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回清單的開頭處的項目對應的位置值。  
  
### <a name="remarks"></a>備註  
 如果清單是空的則傳回的值會是 NULL。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&21;](../../atl/codesnippet/cpp/catllist-class_9.cpp)]  
  
##  <a name="getnext"></a>CAtlList::GetNext  
 呼叫此方法以傳回下一個項目從清單中。  
  
```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 先前呼叫所傳回的位置值， `GetNext`， [CAtlList::GetHeadPosition](#getheadposition)，或其他`CAtlList`方法。  
  
### <a name="return-value"></a>傳回值  
 如果清單是**const**，`GetNext`傳回一份清單的下一個項目。 這可讓方法只能用在指派陳述式的右側，並防止修改的清單。  
  
 如果清單不是**const**，`GetNext`傳回清單的下一個元素的參考。 這可讓方法用在指派陳述式的任一邊，而讓 要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 [位置] 計數器`pos`，更新為指向下一個項目在清單中，或如果沒有更多的項目，則為 NULL。 在偵錯組建中，如果，就會發生判斷提示失敗`pos`等於 NULL。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlList::GetHeadPosition](#getheadposition)。  
  
##  <a name="getprev"></a>CAtlList::GetPrev  
 呼叫這個方法，傳回上一個項目從清單中。  
  
```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 先前呼叫所傳回的位置值， `GetPrev`， [CAtlList::GetTailPosition](#gettailposition)，或其他`CAtlList`方法。  
  
### <a name="return-value"></a>傳回值  
 如果清單是**const**，`GetPrev`傳回清單中項目的複本。 這可讓方法只能用在指派陳述式的右側，並防止修改的清單。  
  
 如果清單不是**const**，`GetPrev`傳回的項目清單的參考。 這可讓方法用在指派陳述式的任一邊，而讓 要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 [位置] 計數器`pos`，更新為指向上一個項目在清單中，或如果沒有更多的項目，則為 NULL。 在偵錯組建中，如果，就會發生判斷提示失敗`pos`等於 NULL。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlList::GetTailPosition](#gettailposition)。  
  
##  <a name="gettail"></a>CAtlList::GetTail  
 呼叫這個方法來傳回清單的結尾處的項目。  
  
```
E& GetTail() throw();
const E& GetTail() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的參考或尾端的清單項目的複本。  
  
### <a name="remarks"></a>備註  
 如果清單是**const**，`GetTail`傳回一份清單的開頭處的項目。 這可讓方法只能用在指派陳述式的右側，並防止修改的清單。  
  
 如果清單不是**const**，`GetTail`傳回的參考清單的開頭處的項目。 這可讓方法用在指派陳述式的任一邊，而讓 要修改之清單項目。  
  
 在偵錯組建中，如果清單的結尾點為 NULL，會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlList::AddTail](#addtail)。  
  
##  <a name="gettailposition"></a>CAtlList::GetTailPosition  
 呼叫這個方法來取得清單的結尾的位置。  
  
```
POSITION GetTailPosition() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回清單的結尾處的項目對應的位置值。  
  
### <a name="remarks"></a>備註  
 如果清單是空的則傳回的值會是 NULL。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&22;](../../atl/codesnippet/cpp/catllist-class_10.cpp)]  
  
##  <a name="inargtype"></a>CAtlList::INARGTYPE  
 輸入的引數傳遞的項目時所使用的類型。  
  
```
typedef ETraits::INARGTYPE INARGTYPE;
```  
  
##  <a name="insertafter"></a>CAtlList::InsertAfter  
 呼叫這個方法，以新的項目插入後的指定位置的清單。  
  
```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置值之後，就會插入新項目。  
  
 `element`  
 要插入的項目。  
  
### <a name="return-value"></a>傳回值  
 傳回新的項目位置值。  
  
### <a name="remarks"></a>備註  
 偵錯組建中發生判斷提示失敗便會發生清單無效，如果插入失敗，或嘗試結尾之後插入項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&23;](../../atl/codesnippet/cpp/catllist-class_11.cpp)]  
  
##  <a name="insertbefore"></a>CAtlList::InsertBefore  
 呼叫這個方法在指定位置的清單中插入新項目。  
  
```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 新的項目會插入在此位置值的清單。  
  
 `element`  
 要插入的項目。  
  
### <a name="return-value"></a>傳回值  
 傳回新的項目位置值。  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，如果清單無效，如果插入失敗，或嘗試插入標頭之前的項目，會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&24;](../../atl/codesnippet/cpp/catllist-class_12.cpp)]  
  
##  <a name="isempty"></a>CAtlList::IsEmpty  
 呼叫這個方法來判斷是否清單是空白。  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果清單不包含的物件，否則為 false，則傳回 true。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&25;](../../atl/codesnippet/cpp/catllist-class_13.cpp)]  
  
##  <a name="movetohead"></a>CAtlList::MoveToHead  
 呼叫這個方法，將指定的項目移至清單的開頭。  
  
```
void MoveToHead(POSITION pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 要移動之項目的位置值。  
  
### <a name="remarks"></a>備註  
 指定的項目從其目前位置移至清單的開頭。 在偵錯組建中，如果，就會發生判斷提示失敗`pos`等於 NULL。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&26;](../../atl/codesnippet/cpp/catllist-class_14.cpp)]  
  
##  <a name="movetotail"></a>CAtlList::MoveToTail  
 呼叫這個方法，將指定的項目移至清單的結尾。  
  
```
void MoveToTail(POSITION pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 要移動之項目的位置值。  
  
### <a name="remarks"></a>備註  
 指定的項目是從其目前位置移到清單的結尾。 在偵錯組建中，如果，就會發生判斷提示失敗`pos`等於 NULL。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlList::MoveToHead](#movetohead)。  
  
##  <a name="removeall"></a>CAtlList::RemoveAll  
 呼叫此方法以從清單中移除所有項目。  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>備註  
 這個方法會從清單中移除所有項目，並釋出配置的記憶體。 在偵錯組建中，如果不刪除所有項目，或清單結構已損毀，就會引發 ATLASSERT。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlList::IsEmpty](#isempty)。  
  
##  <a name="removeat"></a>CAtlList::RemoveAt  
 呼叫此方法以從清單中移除單一項目。  
  
```
void RemoveAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 若要移除的項目位置值。  
  
### <a name="remarks"></a>備註  
 所參考的項目`pos`移除，並釋放記憶體。 接受使用`RemoveAt`若要移除的開頭或尾端的清單。  
  
 在偵錯組建中，如果清單不正確，或移除項目，會讓清單存取記憶體，而不是清單結構的一部分，就會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&27;](../../atl/codesnippet/cpp/catllist-class_15.cpp)]  
  
##  <a name="removehead"></a>CAtlList::RemoveHead  
 呼叫此方法以移除清單的開頭處的項目。  
  
```
E RemoveHead();
```  
  
### <a name="return-value"></a>傳回值  
 傳回清單的開頭處的項目。  
  
### <a name="remarks"></a>備註  
 從清單中，刪除標頭項目，並釋放記憶體。 傳回項目的複本。 在偵錯組建中，如果清單是空的會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&28;](../../atl/codesnippet/cpp/catllist-class_16.cpp)]  
  
##  <a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn  
 呼叫此方法以移除清單的開頭處的項目，但不傳回值。  
  
```
void RemoveHeadNoReturn() throw();
```  
  
### <a name="remarks"></a>備註  
 從清單中，刪除標頭項目，並釋放記憶體。 在偵錯組建中，如果清單是空的會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlList::IsEmpty](#isempty)。  
  
##  <a name="removetail"></a>CAtlList::RemoveTail  
 呼叫此方法以移除清單結尾處的項目。  
  
```
E RemoveTail();
```  
  
### <a name="return-value"></a>傳回值  
 傳回清單的結尾處的項目。  
  
### <a name="remarks"></a>備註  
 從清單中，刪除結尾項目，並釋放記憶體。 傳回項目的複本。 在偵錯組建中，如果清單是空的會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&29;](../../atl/codesnippet/cpp/catllist-class_17.cpp)]  
  
##  <a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn  
 呼叫此方法以移除清單結尾處的項目，但不傳回值。  
  
```
void RemoveTailNoReturn() throw();
```  
  
### <a name="remarks"></a>備註  
 從清單中，刪除結尾項目，並釋放記憶體。 在偵錯組建中，如果清單是空的會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlList::IsEmpty](#isempty)。  
  
##  <a name="setat"></a>CAtlList::SetAt  
 呼叫這個方法，在清單中的指定位置中設定項目的值。  
  
```
void SetAt(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 位置值對應至要變更的項目。  
  
 `element`  
 新的項目值。  
  
### <a name="remarks"></a>備註  
 取代現有的值與`element`。 在偵錯組建中，如果，就會發生判斷提示失敗`pos`等於 NULL。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&30;](../../atl/codesnippet/cpp/catllist-class_18.cpp)]  
  
##  <a name="swapelements"></a>CAtlList::SwapElements  
 呼叫此方法來交換在清單中的項目。  
  
```
void SwapElements(POSITION pos1, POSITION pos2) throw();
```  
  
### <a name="parameters"></a>參數  
 *pos1*  
 第一個位置值。  
  
 *pos2*  
 第二個位置值。  
  
### <a name="remarks"></a>備註  
 交換兩個位置指定的項目。 在偵錯組建中，如果任一個位置的值等於 NULL，就會發生判斷提示失敗。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&31;](../../atl/codesnippet/cpp/catllist-class_19.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CList 類別](../../mfc/reference/clist-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

