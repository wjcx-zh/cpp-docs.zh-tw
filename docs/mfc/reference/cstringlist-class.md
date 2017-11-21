---
title: "CStringList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
dev_langs: C++
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 160f85f402ee7f44f348bcb4e2ca1ed59e3b0e22
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cstringlist-class"></a>CStringList 類別
支援 `CString` 物件的清單。  
  
## <a name="syntax"></a>語法  
  
```  
class CStringList : public CObject  
```  
  
## <a name="members"></a>成員  
 成員函式`CStringList`類別成員函式類似[CObList](../../mfc/reference/coblist-class.md)。 由於此相似性，您可以針對成員函式特性使用 `CObList` 參考文件。 無論在何處看到`CObject`指標做為傳回值，以取代`CString`(不`CString`指標)。 無論在何處看到`CObject`指標做為函式參數，以取代`LPCTSTR`。  
  
 `CObject*& CObList::GetHead() const;`  
  
 例如，轉換為  
  
 `CString& CStringList::GetHead() const;`  
  
 和  
  
 `POSITION AddHead( CObject* <newElement> );`  
  
 轉換為  
  
 `POSITION AddHead( LPCTSTR <newElement> );`  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)|建構空的清單。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CObList::AddHead](../../mfc/reference/coblist-class.md#addhead)|新增項目 （或另一個清單中的所有項目） 標頭的清單 （可讓新的標頭）。|  
|[CObList::AddTail](../../mfc/reference/coblist-class.md#addtail)|加入的清單 （可讓新的結尾） 的結尾的項目 （或另一個清單中的所有項目）。|  
|[CObList::Find](../../mfc/reference/coblist-class.md#find)|取得指標值所指定項目的位置。|  
|[CObList::FindIndex](../../mfc/reference/coblist-class.md#findindex)|取得指定的項目以零為起始的索引位置。|  
|[CObList::GetAt](../../mfc/reference/coblist-class.md#getat)|取得指定位置的項目。|  
|[CObList::GetCount](../../mfc/reference/coblist-class.md#getcount)|這份清單中傳回的項目數。|  
|[CObList::GetHead](../../mfc/reference/coblist-class.md#gethead)|傳回的清單 （不能是空的） 的標頭的項目。|  
|[CObList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|傳回的標頭的項目清單的位置。|  
|[CObList::GetNext](../../mfc/reference/coblist-class.md#getnext)|取得逐一查看下一個項目。|  
|[CObList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|取得逐一查看的上一個項目。|  
|[CObList::GetSize](../../mfc/reference/coblist-class.md#getsize)|這份清單中傳回的項目數。|  
|[CObList::GetTail](../../mfc/reference/coblist-class.md#gettail)|傳回結尾的項目清單 （不能是空的）。|  
|[CObList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|傳回清單的結尾項目的位置。|  
|[CObList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|之後的指定位置插入新項目。|  
|[CObList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|插入新項目指定的位置之前。|  
|[CObList::IsEmpty](../../mfc/reference/coblist-class.md#isempty)|空白清單條件 （沒有項目） 的測試。|  
|[CObList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|從這個清單中移除所有項目。|  
|[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)|從這個清單中，指定位置移除元素。|  
|[CObList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|從清單的開頭移除的項目。|  
|[CObList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|從清單的結尾的項目。|  
|[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)|設定項目指定的位置。|  
  
## <a name="remarks"></a>備註  
 值，這表示字串中的字元會比較而不是字串的位址來完成所有的比較。  
  
 `CStringList` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。 如果一份`CString`物件會儲存至封存，或是利用多載的插入運算子`Serialize`成員函式，每個`CString`並依序序列化項目。  
  
 如果您需要個別的傾印`CString`項目，您必須將傾印內容的深度為 1 或更大。  
  
 如需有關使用`CStringList`，請參閱文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringList`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcoll.h  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例收集](../../visual-cpp-samples.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



