---
title: "CTypedPtrList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrList
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrList class
- type-safe collections
- lists [C++]
- template classes, CTypedPtrList class
- linked lists [C++]
- pointer lists
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
caps.latest.revision: 24
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
ms.openlocfilehash: ca8d868333aa977710e387fc1bb13271dc8f99fa
ms.lasthandoff: 02/24/2017

---
# <a name="ctypedptrlist-class"></a>CTypedPtrList 類別
為 `CPtrList`類別的物件提供類型安全「包裝函式」。  
  
## <a name="syntax"></a>語法  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>參數  
 `BASE_CLASS`  
 基底類別的類別型別的指標清單;必須是指標清單類別 (`CObList`或`CPtrList`)。  
  
 `TYPE`  
 基底類別清單中所儲存的項目型別。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTypedPtrList::AddHead](#addhead)|新增項目 （或另一個清單中的所有項目） 標頭的清單 （產生新的標頭）。|  
|[CTypedPtrList::AddTail](#addtail)|（產生新的結尾） 的清單結尾加入項目 （或另一個清單中的所有項目）。|  
|[CTypedPtrList::GetAt](#getat)|取得指定位置的項目。|  
|[CTypedPtrList::GetHead](#gethead)|傳回的清單 （不能是空的） 的標頭的項目。|  
|[CTypedPtrList::GetNext](#getnext)|取得逐一查看下一個項目。|  
|[CTypedPtrList::GetPrev](#getprev)|取得逐一查看的上一個項目。|  
|[CTypedPtrList::GetTail](#gettail)|傳回的結尾項目清單 （不能是空的）。|  
|[CTypedPtrList::RemoveHead](#removehead)|從清單的開頭移除的項目。|  
|[CTypedPtrList::RemoveTail](#removetail)|從清單的結尾的項目。|  
|[CTypedPtrList::SetAt](#setat)|設定位於指定位置的項目。|  
  
## <a name="remarks"></a>備註  
 當您使用`CTypedPtrList`而`CObList`或`CPtrList`，c + + 型別檢查功能，有助於排除不相符的指標類型所造成的錯誤。  
  
 此外，`CTypedPtrList`包裝函式會執行大部分的會是必要，如果您使用轉型`CObList`或`CPtrList`。  
  
 因為所有`CTypedPtrList`函式會以內嵌方式，使用此範本並不會大幅影響大小或您的程式碼的速度。  
  
 清單衍生自`CObList`可以序列化，但這些衍生自`CPtrList`無法。  
  
 當 `CTypedPtrList` 物件被刪除，或當它的項目被移除時，只會移除指標，而非它們參考的實體。  
  
 如需有關使用`CTypedPtrList`，請參閱文章[集合](../../mfc/collections.md)和[樣板架構類別](../../mfc/template-based-classes.md)。  
  
## <a name="example"></a>範例  
 這個範例會建立的執行個體`CTypedPtrList`、 將一個物件加入、 序列化至磁碟，清單，然後刪除物件︰  
  
 [!code-cpp[NVC_MFCCollections #&110;](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections #&111;](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## <a name="requirements"></a>需求  
 **Header:** afxtempl.h  
  
##  <a name="a-nameaddheada--ctypedptrlistaddhead"></a><a name="addhead"></a>CTypedPtrList::AddHead  
 此成員函式呼叫`BASE_CLASS` **:: AddHead**。  
  
```  
POSITION AddHead(TYPE newElement);  
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 基底類別清單中所儲存的項目型別。  
  
 `newElement`  
 要新增到此清單的物件指標。 A **NULL**允許值。  
  
 `BASE_CLASS`  
 基底類別的類別型別的指標清單;必須是指標清單類別 ( [CObList](../../mfc/reference/coblist-class.md)或[CPtrList](../../mfc/reference/cptrlist-class.md))。  
  
 `pNewList`  
 另一個指標[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)物件。 中的項目`pNewList`會新增到此清單。  
  
### <a name="return-value"></a>傳回值  
 第一個版本會傳回**位置**新插入的項目值。  
  
### <a name="remarks"></a>備註  
 第一個版本將加入新項目清單的開頭之前。 第二個版本新增另一個清單的開頭之前的項目。  
  
##  <a name="a-nameaddtaila--ctypedptrlistaddtail"></a><a name="addtail"></a>CTypedPtrList::AddTail  
 此成員函式呼叫`BASE_CLASS` **:: AddTail**。  
  
```  
POSITION AddTail(TYPE newElement);  
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 基底類別清單中所儲存的項目型別。  
  
 `newElement`  
 要新增到此清單的物件指標。 A **NULL**允許值。  
  
 `BASE_CLASS`  
 基底類別的類別型別的指標清單;必須是指標清單類別 ( [CObList](../../mfc/reference/coblist-class.md)或[CPtrList](../../mfc/reference/cptrlist-class.md))。  
  
 `pNewList`  
 另一個指標[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)物件。 中的項目`pNewList`會新增到此清單。  
  
### <a name="return-value"></a>傳回值  
 第一個版本會傳回**位置**新插入的項目值。  
  
### <a name="remarks"></a>備註  
 第一版會將新的項目加入清單的結尾之後。 第二個版本之後清單的結尾新增另一個清單項目。  
  
##  <a name="a-namegetata--ctypedptrlistgetat"></a><a name="getat"></a>CTypedPtrList::GetAt  
 型別的變數**位置**是索引鍵清單。  
  
```  
TYPE& GetAt(POSITION position);  
TYPE GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在清單中的項目類型的樣板參數。  
  
 *位置*  
 A**位置**前一個傳回值`GetHeadPosition`或**尋找**成員函式呼叫。  
  
### <a name="return-value"></a>傳回值  
 如果清單透過指標存取**const CTypedPtrList**，然後`GetAt`傳回範本參數所指定之類型的指標*類型*。 這可讓函式只能用在指派陳述式的右側，因此防止修改的清單。  
  
 如果清單直接或透過指標存取`CTypedPtrList`，然後`GetAt`傳回範本參數所指定之型別的指標參考*類型*。 這可讓函式來指派陳述式的任一邊，而讓 要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 不是索引，相同，而且無法用於**位置**自己的值。 `GetAt`擷取`CObject`與指定的位置相關聯的指標。  
  
 您必須確定您**位置**值代表在清單中的有效位置。 如果它是無效的 Mfc 程式庫的偵錯版本會判斷提示。  
  
 內嵌函式呼叫`BASE_CLASS` **:: GetAt**。  
  
##  <a name="a-namegetheada--ctypedptrlistgethead"></a><a name="gethead"></a>CTypedPtrList::GetHead  
 取得表示標頭項目，此清單的指標。  
  
```  
TYPE& GetHead();  
TYPE GetHead() const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在清單中的項目類型的樣板參數。  
  
### <a name="return-value"></a>傳回值  
 如果清單透過指標存取**const CTypedPtrList**，然後`GetHead`傳回範本參數所指定之類型的指標*類型*。 這可讓函式只能用在指派陳述式的右側，因此防止修改的清單。  
  
 如果清單直接或透過指標存取`CTypedPtrList`，然後`GetHead`傳回範本參數所指定之型別的指標參考*類型*。 這可讓函式來指派陳述式的任一邊，而讓 要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`GetHead`。 如果清單是空的 Mfc 程式庫的偵錯版本會判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)確認清單中含有項目。  
  
##  <a name="a-namegetnexta--ctypedptrlistgetnext"></a><a name="getnext"></a>CTypedPtrList::GetNext  
 取得所識別的清單項目`rPosition`，然後設定`rPosition`至**位置**清單中的下一個項目值。  
  
```  
TYPE& GetNext(POSITION& rPosition);  
TYPE GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定此清單中包含的項目類型的樣板參數。  
  
 `rPosition`  
 參考**位置**前一個傳回值`GetNext`， `GetHeadPosition`，或其他成員函式呼叫。  
  
### <a name="return-value"></a>傳回值  
 如果清單透過指標存取**const CTypedPtrList**，然後`GetNext`傳回範本參數所指定之類型的指標*類型*。 這可讓函式只能用在指派陳述式的右側，因此防止修改的清單。  
  
 如果清單直接或透過指標存取`CTypedPtrList`，然後`GetNext`傳回範本參數所指定之型別的指標參考*類型*。 這可讓函式來指派陳述式的任一邊，而讓 要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 您可以使用`GetNext`向前反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetHeadPosition`或[CPtrList::Find](../../mfc/reference/coblist-class.md#find)。  
  
 您必須確定您**位置**值代表在清單中的有效位置。 如果它是無效的 Mfc 程式庫的偵錯版本會判斷提示。  
  
 如果擷取的項目是在清單中，最後則新值`rPosition`設為**NULL**。  
  
 您可在反覆項目時移除的項目。 請參閱範例[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)。  
  
##  <a name="a-namegetpreva--ctypedptrlistgetprev"></a><a name="getprev"></a>CTypedPtrList::GetPrev  
 取得所識別的清單項目`rPosition`，然後設定`rPosition`至**位置**先前的項目清單中的值。  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
TYPE GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定此清單中包含的項目類型的樣板參數。  
  
 `rPosition`  
 參考**位置**前一個傳回值`GetPrev`或其他成員函式呼叫。  
  
### <a name="return-value"></a>傳回值  
 如果清單透過指標存取**const CTypedPtrList**，然後`GetPrev`傳回範本參數所指定之類型的指標*類型*。 這可讓函式只能用在指派陳述式的右側，因此防止修改的清單。  
  
 如果清單直接或透過指標存取`CTypedPtrList`，然後`GetPrev`傳回範本參數所指定之型別的指標參考*類型*。 這可讓函式來指派陳述式的任一邊，而讓 要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 您可以使用`GetPrev`反向反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetTailPosition`或**尋找**。  
  
 您必須確定您**位置**值代表在清單中的有效位置。 如果它是無效的 Mfc 程式庫的偵錯版本會判斷提示。  
  
 如果擷取的項目是在清單中，第一則新值`rPosition`設為**NULL**。  
  
##  <a name="a-namegettaila--ctypedptrlistgettail"></a><a name="gettail"></a>CTypedPtrList::GetTail  
 取得表示標頭項目，此清單的指標。  
  
```  
TYPE& GetTail();  
TYPE GetTail() const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在清單中的項目類型的樣板參數。  
  
### <a name="return-value"></a>傳回值  
 如果清單透過指標存取**const CTypedPtrList**，然後`GetTail`傳回範本參數所指定之類型的指標*類型*。 這可讓函式只能用在指派陳述式的右側，因此防止修改的清單。  
  
 如果清單直接或透過指標存取`CTypedPtrList`，然後`GetTail`傳回範本參數所指定之型別的指標參考*類型*。 這可讓函式來指派陳述式的任一邊，而讓 要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`GetTail`。 如果清單是空的 Mfc 程式庫的偵錯版本會判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)確認清單中含有項目。  
  
##  <a name="a-nameremoveheada--ctypedptrlistremovehead"></a><a name="removehead"></a>CTypedPtrList::RemoveHead  
 從清單的開頭移除的項目，並傳回它。  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在清單中的項目類型的樣板參數。  
  
### <a name="return-value"></a>傳回值  
 先前位於清單的開頭的指標。 這個指標是範本參數所指定之型別的*類型*。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`RemoveHead`。 如果清單是空的 Mfc 程式庫的偵錯版本會判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)確認清單中含有項目。  
  
##  <a name="a-nameremovetaila--ctypedptrlistremovetail"></a><a name="removetail"></a>CTypedPtrList::RemoveTail  
 移除清單結尾的項目，並將它傳回。  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在清單中的項目類型的樣板參數。  
  
### <a name="return-value"></a>傳回值  
 先前位於清單結尾的指標。 這個指標是範本參數所指定之型別的*類型*。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`RemoveTail`。 如果清單是空的 Mfc 程式庫的偵錯版本會判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)確認清單中含有項目。  
  
##  <a name="a-namesetata--ctypedptrlistsetat"></a><a name="setat"></a>CTypedPtrList::SetAt  
 此成員函式呼叫`BASE_CLASS` **:: SetAt**。  
  
```  
void SetAt(POSITION pos, TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 **位置**来設定的項目。  
  
 *型別*  
 基底類別清單中所儲存的項目型別。  
  
 `newElement`  
 要寫入至清單的物件指標。  
  
### <a name="remarks"></a>備註  
 型別的變數**位置**是索引鍵清單。 不是索引，相同，而且無法用於**位置**自己的值。 `SetAt`寫入指定的位置清單中的物件指標。  
  
 您必須確定您**位置**值代表在清單中的有效位置。 如果它是無效的 Mfc 程式庫的偵錯版本會判斷提示。  
  
 如需詳細註解，請參閱[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例收集](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPtrList 類別](../../mfc/reference/cptrlist-class.md)   
 [CObList 類別](../../mfc/reference/coblist-class.md)

