---
title: "CList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- lists
- lists, base class for
- CList class
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 05d35419f70ab039e6981938c516201b252878d4
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="clist-class"></a>CList 類別
支援可循序或依值存取之非唯一物件的排序清單。  
  
## <a name="syntax"></a>語法  
  
```  
template<class TYPE, class ARG_TYPE = const TYPE&>  
class CList : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CList::CList](#clist)|建構空的已排序的清單。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CList::AddHead](#addhead)|新增項目 （或另一個清單中的所有項目） 標頭的清單 （產生新的標頭）。|  
|[CList::AddTail](#addtail)|（產生新的結尾） 的清單結尾加入項目 （或另一個清單中的所有項目）。|  
|[CList::Find](#find)|取得指標值所指定的項目位置。|  
|[CList::FindIndex](#findindex)|取得指定的項目以零為起始的索引位置。|  
|[CList::GetAt](#getat)|取得指定位置的項目。|  
|[CList::GetCount](#getcount)|這份清單中傳回的項目數。|  
|[CList::GetHead](#gethead)|傳回的清單 （不能是空的） 的標頭的項目。|  
|[CList::GetHeadPosition](#getheadposition)|傳回的標頭的項目清單的位置。|  
|[CList::GetNext](#getnext)|取得逐一查看下一個項目。|  
|[CList::GetPrev](#getprev)|取得逐一查看的上一個項目。|  
|[CList::GetSize](#getsize)|這份清單中傳回的項目數。|  
|[CList::GetTail](#gettail)|傳回的結尾項目清單 （不能是空的）。|  
|[CList::GetTailPosition](#gettailposition)|傳回清單的結尾項目的位置。|  
|[CList::InsertAfter](#insertafter)|指定的位置之後插入新項目。|  
|[CList::InsertBefore](#insertbefore)|將指定的位置之前的新項目。|  
|[CList::IsEmpty](#isempty)|空白清單條件 （沒有項目） 的測試。|  
|[CList::RemoveAll](#removeall)|從這個清單中移除所有項目。|  
|[CList::RemoveAt](#removeat)|從此清單中，指定位置移除元素。|  
|[CList::RemoveHead](#removehead)|從清單的開頭移除的項目。|  
|[CList::RemoveTail](#removetail)|從清單的結尾的項目。|  
|[CList::SetAt](#setat)|設定位於指定位置的項目。|  
  
#### <a name="parameters"></a>參數  
 `TYPE`  
 在清單中物件的類型。  
  
 `ARG` *_* `TYPE`  
 用來參考儲存在清單中的物件類型。 可以是參考。  
  
## <a name="remarks"></a>備註  
 `CList`列出表現雙向連結清單。  
  
 型別的變數**位置**是索引鍵清單。 您可以使用**位置**變數為迭代器周遊循序清單，以及要保留圖形的位置的書籤。 位置不是相同的索引，不過。  
  
 插入項目是非常快速在清單的開頭、 結尾，以及在已知**位置**。 循序搜尋的必要值或索引來查閱某個元素。 這項搜尋可能會很慢，如果清單很長的。  
  
 如果您需要在清單中的個別項目傾印，您必須設定為 1 或更高的傾印內容的深度。  
  
 全域 helper 函式，這個類別呼叫的特定成員函式必須是可自訂的大部分的使用`CList`類別。 請參閱[集合類別 Helper](../../mfc/reference/collection-class-helpers.md) 」 巨集和全域變數 」 一節。  
  
 如需有關使用`CList`，請參閱文章[集合](../../mfc/collections.md)。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&35;](../../mfc/codesnippet/cpp/clist-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CList`  
  
## <a name="requirements"></a>需求  
 **Header:** afxtempl.h  
  
##  <a name="addhead"></a>CList::AddHead  
 這份清單的開頭加入新項目或項目清單。  
  
```  
POSITION AddHead(ARG_TYPE newElement);  
void AddHead(CList* pNewList);
```  
  
### <a name="parameters"></a>參數  
 `ARG_TYPE`  
 指定清單項目 (可以是參考) 之類型的樣板參數。  
  
 `newElement`  
 新的項目。  
  
 `pNewList`  
 另一個指標`CList`清單。 中的項目`pNewList`會新增到此清單。  
  
### <a name="return-value"></a>傳回值  
 第一個版本會傳回**位置**新插入的項目值。  
  
### <a name="remarks"></a>備註  
 清單可以是空的作業之前。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&36;](../../mfc/codesnippet/cpp/clist-class_2.cpp)]  
  
##  <a name="addtail"></a>CList::AddTail  
 這份清單的結尾加入新項目或項目清單。  
  
```  
POSITION AddTail(ARG_TYPE newElement);  
void AddTail(CList* pNewList);
```  
  
### <a name="parameters"></a>參數  
 `ARG_TYPE`  
 指定清單項目 (可以是參考) 之類型的樣板參數。  
  
 `newElement`  
 要加入這份清單中的項目。  
  
 `pNewList`  
 另一個指標`CList`清單。 中的項目`pNewList`會新增到此清單。  
  
### <a name="return-value"></a>傳回值  
 第一個版本會傳回**位置**新插入的項目值。  
  
### <a name="remarks"></a>備註  
 清單可以是空的作業之前。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&37;](../../mfc/codesnippet/cpp/clist-class_3.cpp)]  
  
##  <a name="clist"></a>CList::CList  
 建構空的已排序的清單。  
  
```  
CList(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 記憶體配置資料粒度的延伸清單。  
  
### <a name="remarks"></a>備註  
 隨著清單時，配置單位的記憶體`nBlockSize`項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&38;](../../mfc/codesnippet/cpp/clist-class_4.cpp)]  
  
##  <a name="find"></a>CList::Find  
 搜尋以尋找符合指定的第一個項目清單`searchValue`。  
  
```  
POSITION Find(
    ARG_TYPE searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 `ARG_TYPE`  
 指定清單項目 (可以是參考) 之類型的樣板參數。  
  
 `searchValue`  
 要在清單中找到的值。  
  
 `startAfter`  
 搜尋開始位置。 如果未不指定任何值，標頭項目將會開始搜尋。  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，可用於反覆項目或物件指標擷取。**NULL**如果找不到物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&39;](../../mfc/codesnippet/cpp/clist-class_5.cpp)]  
  
##  <a name="findindex"></a>CList::FindIndex  
 使用的值`nIndex`以清單的索引。  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要找的清單項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，可用於反覆項目或物件指標擷取。**NULL**如果`nIndex`為負數或太大。  
  
### <a name="remarks"></a>備註  
 從清單中，停止上的開頭開始循序掃描*n*個項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&40;](../../mfc/codesnippet/cpp/clist-class_6.cpp)]  
  
##  <a name="getat"></a>CList::GetAt  
 取得位於指定位置的清單項目。  
  
```  
TYPE& GetAt(POSITION position);  
const TYPE& GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 樣板參數清單中指定的物件類型。  
  
 *位置*  
 要取得項目清單中的位置。  
  
### <a name="return-value"></a>傳回值  
 請參閱的傳回值描述`GetHead`。  
  
### <a name="remarks"></a>備註  
 `GetAt`傳回指定的位置與關聯的項目 （或項目的參考）。 不是索引，相同，而且無法用於**位置**自己的值。 型別的變數**位置**是索引鍵清單。  
  
 您必須確定您**位置**值代表在清單中的有效位置。 如果它是無效的 Mfc 程式庫的偵錯版本會判斷提示。  
  
### <a name="example"></a>範例  
  請參閱範例[CList::GetHeadPosition](#getheadposition)。  
  
##  <a name="getcount"></a>CList::GetCount  
 這份清單中取得的項目數。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 整數值，包含項目計數。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法會產生相同結果[CList::GetSize](#getsize)方法。  
  
### <a name="example"></a>範例  
  請參閱範例[CList::RemoveHead](#removehead)。  
  
##  <a name="gethead"></a>CList::GetHead  
 取得此清單的標頭項目 （或標頭項目的參考）。  
  
```  
const TYPE& GetHead() const;  
  
TYPE& GetHead();
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 樣板參數清單中指定的物件類型。  
  
### <a name="return-value"></a>傳回值  
 如果清單是**const**，`GetHead`傳回一份清單的開頭處的項目。 這可讓函式只能用在指派陳述式的右側，並防止修改的清單。  
  
 如果清單不是**const**，`GetHead`傳回的參考清單的開頭處的項目。 這可讓函式來指派陳述式的任一邊，而讓 要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`GetHead`。 如果清單是空的 Mfc 程式庫的偵錯版本會判斷提示。 使用[IsEmpty](#isempty)確認清單中含有項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&41;](../../mfc/codesnippet/cpp/clist-class_7.cpp)]  
  
##  <a name="getheadposition"></a>CList::GetHeadPosition  
 取得標頭項目，此清單的位置。  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，可用於反覆項目或物件指標擷取。**NULL**如果清單是空的。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&42;](../../mfc/codesnippet/cpp/clist-class_8.cpp)]  
  
##  <a name="getnext"></a>CList::GetNext  
 取得所識別的清單項目`rPosition`，然後設定`rPosition`至**位置**清單中的下一個項目值。  
  
```  
TYPE& GetNext(POSITION& rPosition);  
const TYPE& GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 樣板參數清單中指定的項目類型。  
  
 `rPosition`  
 參考**位置**前一個傳回值`GetNext`， [GetHeadPosition](#getheadposition)，或其他成員函式呼叫。  
  
### <a name="return-value"></a>傳回值  
 如果清單是**const**，`GetNext`傳回清單中項目的複本。 這可讓函式只能用在指派陳述式的右側，並防止修改的清單。  
  
 如果清單不是**const**，`GetNext`傳回的項目清單的參考。 這可讓函式來指派陳述式的任一邊，而讓 要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 您可以使用`GetNext`向前反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetHeadPosition`或**尋找**。  
  
 您必須確定您**位置**值代表在清單中的有效位置。 如果它是無效的 Mfc 程式庫的偵錯版本會判斷提示。  
  
 如果擷取的項目是在清單中，最後則新值`rPosition`設為**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&43;](../../mfc/codesnippet/cpp/clist-class_9.cpp)]  
  
##  <a name="getprev"></a>CList::GetPrev  
 取得所識別的清單項目`rPosition`，然後設定`rPosition`至**位置**先前的項目清單中的值。  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
const TYPE& GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 樣板參數清單中指定的項目類型。  
  
 `rPosition`  
 參考**位置**前一個傳回值`GetPrev`或其他成員函式呼叫。  
  
### <a name="return-value"></a>傳回值  
 如果清單是**const**，`GetPrev`傳回一份清單的開頭處的項目。 這可讓函式只能用在指派陳述式的右側，並防止修改的清單。  
  
 如果清單不是**const**，`GetPrev`傳回的項目清單的參考。 這可讓函式來指派陳述式的任一邊，而讓 要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 您可以使用`GetPrev`反向反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetTailPosition`或**尋找**。  
  
 您必須確定您**位置**值代表在清單中的有效位置。 如果它是無效的 Mfc 程式庫的偵錯版本會判斷提示。  
  
 如果擷取的項目是在清單中，第一則新值`rPosition`設為**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&44;](../../mfc/codesnippet/cpp/clist-class_10.cpp)]  
  
##  <a name="getsize"></a>CList::GetSize  
 傳回清單項目數目。  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單中的項目數。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以擷取清單中的項目數。  呼叫這個方法會產生相同結果[CList::GetCount](#getcount)方法。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&45;](../../mfc/codesnippet/cpp/clist-class_11.cpp)]  
  
##  <a name="gettail"></a>CList::GetTail  
 取得`CObject`指標，表示此清單的結尾項目。  
  
```  
TYPE& GetTail();  
const TYPE& GetTail() const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 樣板參數清單中指定的項目類型。  
  
### <a name="return-value"></a>傳回值  
 請參閱的傳回值描述[GetHead](../../mfc/reference/coblist-class.md#gethead)。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`GetTail`。 如果清單是空的 Mfc 程式庫的偵錯版本會判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)確認清單中含有項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&46;](../../mfc/codesnippet/cpp/clist-class_12.cpp)]  
  
##  <a name="gettailposition"></a>CList::GetTailPosition  
 取得這份清單; 的結尾項目位置**NULL**如果清單是空的。  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，可用於反覆項目或物件指標擷取。**NULL**如果清單是空的。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&47;](../../mfc/codesnippet/cpp/clist-class_13.cpp)]  
  
##  <a name="insertafter"></a>CList::InsertAfter  
 將這份清單的項目之後的指定位置處的項目。  
  
```  
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 *位置*  
 先前的 **、** 或 `GetNext`Find `GetPrev`成員函式呼叫所傳回的 **POSITION** 值。  
  
 `ARG_TYPE`  
 指定清單項目類型的樣板參數。  
  
 `newElement`  
 要加入這份清單中的項目。  
  
### <a name="return-value"></a>傳回值  
 可用於反覆項目或清單項目擷取的 **POSITION** 值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&48;](../../mfc/codesnippet/cpp/clist-class_14.cpp)]  
  
##  <a name="insertbefore"></a>CList::InsertBefore  
 將項目加入這份清單中相同項目之前的指定位置。  
  
```  
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 *位置*  
 先前的 **、** 或 `GetNext`Find `GetPrev`成員函式呼叫所傳回的 **POSITION** 值。  
  
 `ARG_TYPE`  
 指定清單項目 (可以是參考) 之類型的樣板參數。  
  
 `newElement`  
 要加入這份清單中的項目。  
  
### <a name="return-value"></a>傳回值  
 可用於反覆項目或清單項目擷取的 **POSITION** 值。  
  
### <a name="remarks"></a>備註  
 如果 *position* 為 **NULL**，則會在清單頂端插入項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&49;](../../mfc/codesnippet/cpp/clist-class_15.cpp)]  
  
##  <a name="isempty"></a>CList::IsEmpty  
 指出此清單是否包含任何項目。  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果此清單是空的。否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&50;](../../mfc/codesnippet/cpp/clist-class_16.cpp)]  
  
##  <a name="removeall"></a>CList::RemoveAll  
 從這個清單中移除所有項目，然後釋放相關聯的記憶體。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>備註  
 如果已經是空的清單，會不產生任何錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&51;](../../mfc/codesnippet/cpp/clist-class_17.cpp)]  
  
##  <a name="removeat"></a>CList::RemoveAt  
 從這個清單中移除指定的項目。  
  
```  
void RemoveAt(POSITION position);
```  
  
### <a name="parameters"></a>參數  
 *位置*  
 要從清單中移除之項目的位置。  
  
### <a name="remarks"></a>備註  
 您必須確定您**位置**值代表在清單中的有效位置。 如果它是無效的 Mfc 程式庫的偵錯版本會判斷提示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&52;](../../mfc/codesnippet/cpp/clist-class_18.cpp)]  
  
##  <a name="removehead"></a>CList::RemoveHead  
 從清單的開頭移除的項目，並傳回的指標。  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 樣板參數清單中指定的項目類型。  
  
### <a name="return-value"></a>傳回值  
 先前在對 list 的 head 項目。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`RemoveHead`。 如果清單是空的 Mfc 程式庫的偵錯版本會判斷提示。 使用[IsEmpty](#isempty)確認清單中含有項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&53;](../../mfc/codesnippet/cpp/clist-class_19.cpp)]  
  
##  <a name="removetail"></a>CList::RemoveTail  
 從清單的結尾的項目，並傳回的指標。  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 樣板參數清單中指定的項目類型。  
  
### <a name="return-value"></a>傳回值  
 在清單結尾的項目。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`RemoveTail`。 如果清單是空的 Mfc 程式庫的偵錯版本會判斷提示。 使用[IsEmpty](#isempty)確認清單中含有項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&54;](../../mfc/codesnippet/cpp/clist-class_20.cpp)]  
  
##  <a name="setat"></a>CList::SetAt  
 型別的變數**位置**是索引鍵清單。  
  
```  
void SetAt(POSITION pos, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 **位置**来設定的項目。  
  
 `ARG_TYPE`  
 指定清單項目 (可以是參考) 之類型的樣板參數。  
  
 `newElement`  
 要加入至清單的項目。  
  
### <a name="remarks"></a>備註  
 不是索引，相同，而且無法用於**位置**自己的值。 `SetAt`項目寫入至清單中指定的位置。  
  
 您必須確定您**位置**值代表在清單中的有效位置。 如果它是無效的 Mfc 程式庫的偵錯版本會判斷提示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCCollections #&55;](../../mfc/codesnippet/cpp/clist-class_21.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例收集](../../visual-cpp-samples.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMap 類別](../../mfc/reference/cmap-class.md)   
 [CArray 類別](../../mfc/reference/carray-class.md)

