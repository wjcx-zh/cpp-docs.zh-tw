---
title: CComUnkArray 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0de49180052a6fdb7bde32274e032ea1dd9bfb87
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ccomunkarray-class"></a>CComUnkArray 類別
這個類別會儲存**IUnknown**指標，以及設計用於為參數，以[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)範本類別。  
  
## <a name="syntax"></a>語法  
  
```
template<unsigned int nMaxSize>
class CComUnkArray
```  
  
#### <a name="parameters"></a>參數  
 *nMaxSize*  
 最大數目**IUnknown**靜態陣列中可以保存的指標。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComUnkArray::CComUnkArray](#ccomunkarray)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComUnkArray::Add](#add)|呼叫此方法以新增**IUnknown**陣列的指標。|  
|[CComUnkArray::begin](#begin)|讓指標回到第一個**IUnknown**指標集合中的。|  
|[CComUnkArray::end](#end)|讓指標回到越過最後一個**IUnknown**指標集合中的。|  
|[CComUnkArray::GetCookie](#getcookie)|呼叫此方法以取得相關聯的 cookie 給定**IUnknown**指標。|  
|[CComUnkArray::GetUnknown](#getunknown)|呼叫此方法來取得**IUnknown**指定 cookie 相關聯的指標。|  
|[CComUnkArray::Remove](#remove)|呼叫這個方法來移除**IUnknown**從陣列的指標。|  
  
## <a name="remarks"></a>備註  
 **CComUnkArray**保留固定的數目的**IUnknown**指標，每個介面的連接上的點。 **CComUnkArray**可以當做參數使用[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)範本類別。 **CComUnkArray\<1 >** 的樣板特製化**CComUnkArray** ，已經過最佳化，一個連接點。  
  
 **CComUnkArray**方法[開始](#begin)和[結束](#end)可用來循環 （例如，當引發事件時） 的所有連線點。  
  
 請參閱[加入至物件的連接點](../../atl/adding-connection-points-to-an-object.md)自動化建立連接的詳細資訊，請指向 proxy。  
  
> [!NOTE]
> **請注意**類別[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)正由**加入類別**精靈建立的連接點的控制項時。 如果您想要手動指定連接點數目，將變更從參考**CComDynamicUnkArray**至`CComUnkArray<` *n* `>`，其中*n*是所需的連接點的數目。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="add"></a>  CComUnkArray::Add  
 呼叫此方法以新增**IUnknown**陣列的指標。  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 呼叫此方法以新增**IUnknown**陣列的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回陣列是否不大小足以包含新的指標與新加入的指標或 0 相關聯的 cookie。  
  
##  <a name="begin"></a>  CComUnkArray::begin  
 傳回的集合開頭的指標**IUnknown**介面指標。  
  
```
IUnknown**
    begin();
```     
  
### <a name="return-value"></a>傳回值  
 指標**IUnknown**介面指標。  
  
### <a name="remarks"></a>備註  
 集合包含在本機儲存為介面的指標**IUnknown**。 您每個轉換**IUnknown**實際的介面類型的介面，然後再呼叫透過它。 您不需要先查詢的介面。  
  
 使用之前**IUnknown**介面，您應該檢查不是**NULL**。  
  
##  <a name="ccomunkarray"></a>  CComUnkArray::CComUnkArray  
 建構函式。  
  
```
CComUnkArray();
```  
  
### <a name="remarks"></a>備註  
 設定集合來保有`nMaxSize` **IUnknown**指標，並初始化指標**NULL**。  
  
##  <a name="end"></a>  CComUnkArray::end  
 讓指標回到越過最後一個**IUnknown**指標集合中的。  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>傳回值  
 指標**IUnknown**介面指標。  
  
### <a name="remarks"></a>備註  
 `CComUnkArray`方法**開始**和**結束**可用於事件引發時，所有連線點，例如，透過迴圈。  
  
 [!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]  
  
##  <a name="getcookie"></a>  CComUnkArray::GetCookie  
 呼叫此方法以取得相關聯的 cookie 給定**IUnknown**指標。  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>參數  
 `ppFind`  
 **IUnknown**相關聯的 cookie 是必要的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回與相關聯的 cookie **IUnknown**指標或 0，如果沒有相符的**IUnknown**找到指標。  
  
### <a name="remarks"></a>備註  
 是否有相同的多個執行個體**IUnknown**指標，此函數會傳回針對第一個 cookie。  
  
##  <a name="getunknown"></a>  CComUnkArray::GetUnknown  
 呼叫此方法來取得**IUnknown**指定 cookie 相關聯的指標。  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>參數  
 `dwCookie`  
 Cookie 的相關聯**IUnknown**指標是必要。  
  
### <a name="return-value"></a>傳回值  
 傳回**IUnknown**指標或為 NULL，如果不找到任何比對的 cookie。  
  
##  <a name="remove"></a>  CComUnkArray::Remove  
 呼叫這個方法來移除**IUnknown**從陣列的指標。  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>參數  
 `dwCookie`  
 Cookie 參考**IUnknown**指標從陣列中移除。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果移除指標， **FALSE**否則。  
  
## <a name="see-also"></a>另請參閱  
 [CComDynamicUnkArray 類別](../../atl/reference/ccomdynamicunkarray-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
