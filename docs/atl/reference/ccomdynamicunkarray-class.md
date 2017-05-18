---
title: "CComDynamicUnkArray 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 69fc2c9dbb86f88c85461e765182fd88050521e9
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray 類別
這個類別會儲存一組**IUnknown**指標。  
  
## <a name="syntax"></a>語法  
  
```
class CComDynamicUnkArray
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|建構函式。 初始化集合值**NULL**和集合大小為零。|  
|[CComDynamicUnkArray:: ~ CComDynamicUnkArray](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComDynamicUnkArray::Add](#add)|呼叫這個方法可以加入`IUnknown`陣列指標。|  
|[CComDynamicUnkArray::begin](#begin)|將指標傳回至第一個`IUnknown`集合中的指標。|  
|[CComDynamicUnkArray::clear](#clear)|清空陣列。|  
|[CComDynamicUnkArray::end](#end)|將指標傳回至越過最後一個**IUnknown**集合中的指標。|  
|[CComDynamicUnkArray::GetAt](#getat)|擷取指定索引處的項目。|  
|[CComDynamicUnkArray::GetCookie](#getcookie)|呼叫此方法以取得相關聯的 cookie 指定**IUnknown**指標。|  
|[CComDynamicUnkArray::GetSize](#getsize)|傳回陣列的長度。|  
|[CComDynamicUnkArray::GetUnknown](#getunknown)|呼叫此方法來取得**IUnknown**指定 cookie 相關聯的指標。|  
|[CComDynamicUnkArray::Remove](#remove)|呼叫此方法以移除**IUnknown**從陣列的指標。|  
  
## <a name="remarks"></a>備註  
 **CComDynamicUnkArray**保存的動態配置的陣列**IUnknown**指標，每個介面上的連接點。 **CComDynamicUnkArray**可以做為參數使用[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)樣板類別。  
  
 **CComDynamicUnkArray**方法[開始](#begin)和[結束](#end)可用來循環使用所有的連線點 （例如事件引發時）。  
  
 請參閱[新增至物件的連接點](../../atl/adding-connection-points-to-an-object.md)自動化建立連接的詳細資訊，請指向 proxy。  
  
> [!NOTE]
> **請注意**類別**CComDynamicUnkArray**由**加入類別**精靈建立具有連接點的控制項時。 如果您想要手動指定的連線點數目，將變更從參考**CComDynamicUnkArray**至`CComUnkArray<` *n* `>`，其中*n*是所需的連接點的數目。  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="add"></a>CComDynamicUnkArray::Add  
 呼叫這個方法可以加入**IUnknown**陣列指標。  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 **IUnknown**加入至陣列的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回新加入的指標相關聯的 cookie。  
  
##  <a name="begin"></a>CComDynamicUnkArray::begin  
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
  
##  <a name="clear"></a>CComDynamicUnkArray::clear  
 清空陣列。  
  
```
void clear();
```  
  
##  <a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray  
 建構函式。  
  
```
CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>備註  
 將集合的大小設定為零，並初始化的值**NULL**。 解構函式釋放該集合，如有必要。  
  
##  <a name="dtor"></a>CComDynamicUnkArray:: ~ CComDynamicUnkArray  
 解構函式。  
  
```
~CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>備註  
 類別建構函式所配置的資源會釋出。  
  
##  <a name="end"></a>CComDynamicUnkArray::end  
 將指標傳回至越過最後一個**IUnknown**集合中的指標。  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>傳回值  
 指標**IUnknown**介面指標。  
  
##  <a name="getat"></a>CComDynamicUnkArray::GetAt  
 擷取指定索引處的項目。  
  
```
IUnknown* GetAt(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要擷取之項目的索引。  
  
### <a name="return-value"></a>傳回值  
 指標[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)介面。  
  
##  <a name="getcookie"></a>CComDynamicUnkArray::GetCookie  
 呼叫此方法以取得相關聯的 cookie 指定**IUnknown**指標。  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>參數  
 `ppFind`  
 **IUnknown**相關的 cookie 是必要的指標。  
  
### <a name="return-value"></a>傳回值  
 相關聯的 cookie 傳回**IUnknown**指標或如果沒有相符的零**IUnknown**找到指標。  
  
### <a name="remarks"></a>備註  
 是否有相同的多個執行個體**IUnknown**指標，此函數會傳回第一個 cookie。  
  
##  <a name="getsize"></a>CComDynamicUnkArray::GetSize  
 傳回陣列的長度。  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>傳回值  
 陣列的長度。  
  
##  <a name="getunknown"></a>CComDynamicUnkArray::GetUnknown  
 呼叫此方法來取得**IUnknown**指定 cookie 相關聯的指標。  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>參數  
 `dwCookie`  
 Cookie 的相關聯**IUnknown**指標是必要。  
  
### <a name="return-value"></a>傳回值  
 傳回**IUnknown**指標或為 NULL，如果不找到任何相符的 cookie。  
  
##  <a name="remove"></a>CComDynamicUnkArray::Remove  
 呼叫此方法以移除**IUnknown**從陣列的指標。  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>參數  
 `dwCookie`  
 Cookie 參考**IUnknown**指標從陣列中移除。  
  
### <a name="return-value"></a>傳回值  
 如果指標已移除; 為 true，則傳回否則為 FALSE。  
  
## <a name="see-also"></a>另請參閱  
 [CComUnkArray 類別](../../atl/reference/ccomunkarray-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

