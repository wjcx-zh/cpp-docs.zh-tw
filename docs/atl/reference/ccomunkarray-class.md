---
title: "CComUnkArray 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
caps.latest.revision: 17
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: 94f1062ff3808f527874a8890eca95c9b655b1bf
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ccomunkarray-class"></a>CComUnkArray 類別
這個類別會儲存**IUnknown**指標，而且設計來做為參數使用[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)樣板類別。  
  
## <a name="syntax"></a>語法  
  
```
template<unsigned int nMaxSize>
class CComUnkArray
```  
  
#### <a name="parameters"></a>參數  
 *nMaxSize*  
 最大數目**IUnknown**可以保留在靜態陣列的指標。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComUnkArray::CComUnkArray](#ccomunkarray)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComUnkArray::Add](#add)|呼叫這個方法可以加入**IUnknown**陣列指標。|  
|[CComUnkArray::begin](#begin)|將指標傳回至第一個**IUnknown**集合中的指標。|  
|[CComUnkArray::end](#end)|將指標傳回至越過最後一個**IUnknown**集合中的指標。|  
|[CComUnkArray::GetCookie](#getcookie)|呼叫此方法以取得相關聯的 cookie 指定**IUnknown**指標。|  
|[CComUnkArray::GetUnknown](#getunknown)|呼叫此方法來取得**IUnknown**指定 cookie 相關聯的指標。|  
|[CComUnkArray::Remove](#remove)|呼叫此方法以移除**IUnknown**從陣列的指標。|  
  
## <a name="remarks"></a>備註  
 **CComUnkArray**保留固定的數目的**IUnknown**指標，每個介面上的連接點。 **CComUnkArray**可以做為參數使用[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)樣板類別。 **CComUnkArray\<1 >**是樣板特製化的**CComUnkArray** ，已經過最佳化，一個連接點。  
  
 **CComUnkArray**方法[開始](#begin)和[結束](#end)可用來循環使用所有的連線點 （例如事件引發時）。  
  
 請參閱[新增至物件的連接點](../../atl/adding-connection-points-to-an-object.md)自動化建立連接的詳細資訊，請指向 proxy。  
  
> [!NOTE]
> **請注意**類別[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)由**加入類別**精靈建立具有連接點的控制項時。 如果您想要手動指定的連線點數目，將變更從參考**CComDynamicUnkArray**至`CComUnkArray<` *n* `>`，其中*n*是所需的連接點的數目。  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="add"></a>CComUnkArray::Add  
 呼叫這個方法可以加入**IUnknown**陣列指標。  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 呼叫這個方法可以加入**IUnknown**陣列指標。  
  
### <a name="return-value"></a>傳回值  
 傳回的 cookie，如果陣列不是大小足以包含新的指標相關聯的新加入的指標或 0。  
  
##  <a name="begin"></a>CComUnkArray::begin  
 傳回集合的開頭的指標**IUnknown**介面指標。  
  
```
IUnknown**
    begin();
```     
  
### <a name="return-value"></a>傳回值  
 指標**IUnknown**介面指標。  
  
### <a name="remarks"></a>備註  
 集合包含在本機儲存為介面的指標**IUnknown**。 您每個轉換**IUnknown**真正的介面類型的介面，然後再呼叫透過它。 您不需要先查詢的介面。  
  
 使用之前**IUnknown**介面，您應該檢查不是**NULL**。  
  
##  <a name="ccomunkarray"></a>CComUnkArray::CComUnkArray  
 建構函式。  
  
```
CComUnkArray();
```  
  
### <a name="remarks"></a>備註  
 設定集合來保有`nMaxSize` **IUnknown**指標，並初始化的指標**NULL**。  
  
##  <a name="end"></a>CComUnkArray::end  
 將指標傳回至越過最後一個**IUnknown**集合中的指標。  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>傳回值  
 指標**IUnknown**介面指標。  
  
### <a name="remarks"></a>備註  
 `CComUnkArray`方法**開始**和**結束**可用來循環使用所有的連線點，例如事件引發時。  
  
 [!code-cpp[NVC_ATL_COM&#44;](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]  
  
##  <a name="getcookie"></a>CComUnkArray::GetCookie  
 呼叫此方法以取得相關聯的 cookie 指定**IUnknown**指標。  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>參數  
 `ppFind`  
 **IUnknown**相關的 cookie 是必要的指標。  
  
### <a name="return-value"></a>傳回值  
 相關聯的 cookie 傳回**IUnknown**指標或 0，如果沒有相符的**IUnknown**找到指標。  
  
### <a name="remarks"></a>備註  
 是否有相同的多個執行個體**IUnknown**指標，此函數會傳回第一個 cookie。  
  
##  <a name="getunknown"></a>CComUnkArray::GetUnknown  
 呼叫此方法來取得**IUnknown**指定 cookie 相關聯的指標。  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>參數  
 `dwCookie`  
 Cookie 的相關聯**IUnknown**指標是必要。  
  
### <a name="return-value"></a>傳回值  
 傳回**IUnknown**指標或為 NULL，如果不找到任何相符的 cookie。  
  
##  <a name="remove"></a>CComUnkArray::Remove  
 呼叫此方法以移除**IUnknown**從陣列的指標。  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>參數  
 `dwCookie`  
 Cookie 參考**IUnknown**指標從陣列中移除。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**會移除指標，如果**FALSE**否則。  
  
## <a name="see-also"></a>另請參閱  
 [CComDynamicUnkArray 類別](../../atl/reference/ccomdynamicunkarray-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

