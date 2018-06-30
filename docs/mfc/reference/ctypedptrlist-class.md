---
title: CTypedPtrList 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3f74782241ec69d77ec55b8613c59f87adb40fb
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122826"
---
# <a name="ctypedptrlist-class"></a>CTypedPtrList 類別
為 `CPtrList`類別的物件提供類型安全「包裝函式」。  
  
## <a name="syntax"></a>語法  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>參數  
 *BASE_CLASS*  
 基底類別的具類型的指標清單類別;必須是指標的清單類別 (`CObList`或`CPtrList`)。  
  
 *型別*  
 基底類別清單中所儲存的項目類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTypedPtrList::AddHead](#addhead)|新增項目 （或另一個清單中的所有項目） 標頭的清單 （可讓新的標頭）。|  
|[CTypedPtrList::AddTail](#addtail)|加入的清單 （可讓新的結尾） 的結尾的項目 （或另一個清單中的所有項目）。|  
|[CTypedPtrList::GetAt](#getat)|取得指定位置的項目。|  
|[CTypedPtrList::GetHead](#gethead)|傳回的清單 （不能是空的） 的標頭的項目。|  
|[CTypedPtrList::GetNext](#getnext)|取得逐一查看下一個項目。|  
|[CTypedPtrList::GetPrev](#getprev)|取得逐一查看的上一個項目。|  
|[CTypedPtrList::GetTail](#gettail)|傳回結尾的項目清單 （不能是空的）。|  
|[CTypedPtrList::RemoveHead](#removehead)|從清單的開頭移除的項目。|  
|[CTypedPtrList::RemoveTail](#removetail)|從清單的結尾的項目。|  
|[CTypedPtrList::SetAt](#setat)|設定項目指定的位置。|  
  
## <a name="remarks"></a>備註  
 當您使用`CTypedPtrList`而`CObList`或`CPtrList`，c + + 型別檢查功能可協助消除不相符的指標類型所造成的錯誤。  
  
 此外，`CTypedPtrList`包裝函式會執行大部分的會是必要，如果您使用轉型`CObList`或`CPtrList`。  
  
 因為所有`CTypedPtrList`函式會以內嵌方式，使用此範本時並不會大幅影響大小或您的程式碼的速度。  
  
 清單衍生自`CObList`可以序列化，但衍生自`CPtrList`無法。  
  
 當 `CTypedPtrList` 物件被刪除，或當它的項目被移除時，只會移除指標，而非它們參考的實體。  
  
 如需有關使用`CTypedPtrList`，請參閱文章[集合](../../mfc/collections.md)和[樣板架構類別](../../mfc/template-based-classes.md)。  
  
## <a name="example"></a>範例  
 這個範例會建立的執行個體`CTypedPtrList`加入一個物件，序列化至磁碟，清單，然後刪除物件：  
  
 [!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## <a name="requirements"></a>需求  
 **Header:** afxtempl.h  
  
##  <a name="addhead"></a>  CTypedPtrList::AddHead  
 此成員函式呼叫`BASE_CLASS` **:: AddHead**。  
  
```  
POSITION AddHead(TYPE newElement);  
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 基底類別清單中所儲存的項目類型。  
  
 *newElement*  
 要加入至這個清單的物件指標。 允許 NULL 值。  
  
 *BASE_CLASS*  
 基底類別的具類型的指標清單類別;必須是指標的清單類別 ( [CObList](../../mfc/reference/coblist-class.md)或[CPtrList](../../mfc/reference/cptrlist-class.md))。  
  
 *pNewList*  
 指標，另一個[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)物件。 中的項目*pNewList*會加入此清單。  
  
### <a name="return-value"></a>傳回值  
 第一個版本會傳回新插入的元素的位置值。  
  
### <a name="remarks"></a>備註  
 第一版中新增新的項目清單的開頭之前。 第二個版本會加入另一個標頭之前的項目清單。  
  
##  <a name="addtail"></a>  CTypedPtrList::AddTail  
 此成員函式呼叫`BASE_CLASS` **:: AddTail**。  
  
```  
POSITION AddTail(TYPE newElement);  
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 基底類別清單中所儲存的項目類型。  
  
 *newElement*  
 要加入至這個清單的物件指標。 允許 NULL 值。  
  
 *BASE_CLASS*  
 基底類別的具類型的指標清單類別;必須是指標的清單類別 ( [CObList](../../mfc/reference/coblist-class.md)或[CPtrList](../../mfc/reference/cptrlist-class.md))。  
  
 *pNewList*  
 指標，另一個[CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md)物件。 中的項目*pNewList*會加入此清單。  
  
### <a name="return-value"></a>傳回值  
 第一個版本會傳回新插入的元素的位置值。  
  
### <a name="remarks"></a>備註  
 第一個版本之後清單的結尾新增新的項目。 第二個版本的清單結尾之後新增另一個項目清單。  
  
##  <a name="getat"></a>  CTypedPtrList::GetAt  
 位置類型的變數是索引鍵的清單。  
  
```  
TYPE& GetAt(POSITION position);  
TYPE GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在清單中的項目類型的樣板參數。  
  
 *位置*  
 傳回先前的位置值`GetHeadPosition`或`Find`成員函式呼叫。  
  
### <a name="return-value"></a>傳回值  
 如果清單透過指標存取`const CTypedPtrList`，然後`GetAt`傳回範本參數所指定之類型的指標*類型*。 這允許只能用在指派陳述式右邊的函式，並因此防止修改的清單。  
  
 如果清單直接或透過指標存取`CTypedPtrList`，然後`GetAt`傳回的範本參數所指定之類型的指標的參考*類型*。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 它不是索引，相同，您無法處理您自己的位置值。 `GetAt` 擷取`CObject`相關聯的指定位置的指標。  
  
 您必須確定您位置的值代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。  
  
 此內嵌函式呼叫`BASE_CLASS` **:: GetAt**。  
  
##  <a name="gethead"></a>  CTypedPtrList::GetHead  
 取得代表標頭項目，此清單的指標。  
  
```  
TYPE& GetHead();  
TYPE GetHead() const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在清單中的項目類型的樣板參數。  
  
### <a name="return-value"></a>傳回值  
 如果清單透過指標存取`const CTypedPtrList`，然後`GetHead`傳回範本參數所指定之類型的指標*類型*。 這允許只能用在指派陳述式右邊的函式，並因此防止修改的清單。  
  
 如果清單直接或透過指標存取`CTypedPtrList`，然後`GetHead`傳回的範本參數所指定之類型的指標的參考*類型*。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`GetHead`。 如果清單是空的偵錯版本的 Mfc 程式庫判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)確認清單包含項目。  
  
##  <a name="getnext"></a>  CTypedPtrList::GetNext  
 取得所識別的清單項目*rPosition*，然後設定*rPosition*位置的值清單中的下一個項目。  
  
```  
TYPE& GetNext(POSITION& rPosition);  
TYPE GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定此清單中包含的項目類型的樣板參數。  
  
 *rPosition*  
 傳回先前的位置值的參考`GetNext`， `GetHeadPosition`，或其他成員函式呼叫。  
  
### <a name="return-value"></a>傳回值  
 如果清單透過指標存取`const CTypedPtrList`，然後`GetNext`傳回範本參數所指定之類型的指標*類型*。 這允許只能用在指派陳述式右邊的函式，並因此防止修改的清單。  
  
 如果清單直接或透過指標存取`CTypedPtrList`，然後`GetNext`傳回的範本參數所指定之類型的指標的參考*類型*。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 您可以使用`GetNext`向前反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetHeadPosition`或[CPtrList::Find](../../mfc/reference/coblist-class.md#find)。  
  
 您必須確定您位置的值代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。  
  
 如果擷取的項目是在清單中，最後則新值*rPosition*設為 NULL。  
  
 很可能在反覆項目移除項目。 請參閱範例的[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)。  
  
##  <a name="getprev"></a>  CTypedPtrList::GetPrev  
 取得所識別的清單項目*rPosition*，然後設定*rPosition*先前的項目在清單中的位置值。  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
TYPE GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定此清單中包含的項目類型的樣板參數。  
  
 *rPosition*  
 傳回先前的位置值的參考`GetPrev`或其他成員函式呼叫。  
  
### <a name="return-value"></a>傳回值  
 如果清單透過指標存取`const CTypedPtrList`，然後`GetPrev`傳回範本參數所指定之類型的指標*類型*。 這允許只能用在指派陳述式右邊的函式，並因此防止修改的清單。  
  
 如果清單直接或透過指標存取`CTypedPtrList`，然後`GetPrev`傳回的範本參數所指定之類型的指標的參考*類型*。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 您可以使用`GetPrev`反向反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetTailPosition`或`Find`。  
  
 您必須確定您位置的值代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。  
  
 如果擷取的項目是在清單中，第一則的新值*rPosition*設為 NULL。  
  
##  <a name="gettail"></a>  CTypedPtrList::GetTail  
 取得代表標頭項目，此清單的指標。  
  
```  
TYPE& GetTail();  
TYPE GetTail() const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在清單中的項目類型的樣板參數。  
  
### <a name="return-value"></a>傳回值  
 如果清單透過指標存取`const CTypedPtrList`，然後`GetTail`傳回範本參數所指定之類型的指標*類型*。 這允許只能用在指派陳述式右邊的函式，並因此防止修改的清單。  
  
 如果清單直接或透過指標存取`CTypedPtrList`，然後`GetTail`傳回的範本參數所指定之類型的指標的參考*類型*。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`GetTail`。 如果清單是空的偵錯版本的 Mfc 程式庫判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)確認清單包含項目。  
  
##  <a name="removehead"></a>  CTypedPtrList::RemoveHead  
 從清單的開頭移除的項目，並傳回它。  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在清單中的項目類型的樣板參數。  
  
### <a name="return-value"></a>傳回值  
 先前位於清單頂端的指標。 此指標為範本參數所指定的型別*類型*。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`RemoveHead`。 如果清單是空的偵錯版本的 Mfc 程式庫判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)確認清單包含項目。  
  
##  <a name="removetail"></a>  CTypedPtrList::RemoveTail  
 從清單的結尾的項目，並傳回它。  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在清單中的項目類型的樣板參數。  
  
### <a name="return-value"></a>傳回值  
 先前位於清單結尾的指標。 此指標為範本參數所指定的型別*類型*。  
  
### <a name="remarks"></a>備註  
 您必須確定清單不是空的再呼叫`RemoveTail`。 如果清單是空的偵錯版本的 Mfc 程式庫判斷提示。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)確認清單包含項目。  
  
##  <a name="setat"></a>  CTypedPtrList::SetAt  
 此成員函式呼叫`BASE_CLASS` **:: SetAt**。  
  
```  
void SetAt(POSITION pos, TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 *pos*  
 要設定之項目的位置。  
  
 *型別*  
 基底類別清單中所儲存的項目類型。  
  
 *newElement*  
 要寫入至清單的物件指標。  
  
### <a name="remarks"></a>備註  
 位置類型的變數是索引鍵的清單。 它不是索引，相同，您無法處理您自己的位置值。 `SetAt` 寫入指定的位置清單中的物件指標。  
  
 您必須確定您位置的值代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。  
  
 如需詳細註解，請參閱[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例收集](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPtrList 類別](../../mfc/reference/cptrlist-class.md)   
 [CObList 類別](../../mfc/reference/coblist-class.md)
