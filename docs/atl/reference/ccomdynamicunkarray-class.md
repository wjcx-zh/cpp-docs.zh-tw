---
title: CComDynamicUnkArray 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a83ab3aa6506e9ee620d3604149bfd181678a05
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879805"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray 類別
此類別會儲存在陣列`IUnknown`指標。  
  
## <a name="syntax"></a>語法  
  
```
class CComDynamicUnkArray
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|建構函式。 會初始化為 NULL 的集合值和集合大小為零。|  
|[CComDynamicUnkArray:: ~ CComDynamicUnkArray](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComDynamicUnkArray::Add](#add)|呼叫這個方法來加入`IUnknown`陣列的指標。|  
|[CComDynamicUnkArray::begin](#begin)|讓指標回到第一個`IUnknown`集合中的指標。|  
|[CComDynamicUnkArray::clear](#clear)|清空陣列。|  
|[CComDynamicUnkArray::end](#end)|讓指標回到越過最後一個`IUnknown`集合中的指標。|  
|[CComDynamicUnkArray::GetAt](#getat)|擷取指定之索引處的項目。|  
|[CComDynamicUnkArray::GetCookie](#getcookie)|呼叫此方法，以取得相關聯的 cookie 指定`IUnknown`指標。|  
|[CComDynamicUnkArray::GetSize](#getsize)|傳回陣列的長度。|  
|[CComDynamicUnkArray::GetUnknown](#getunknown)|呼叫這個方法來取得`IUnknown`與指定的 cookie 相關聯的指標。|  
|[CComDynamicUnkArray::Remove](#remove)|呼叫這個方法來移除`IUnknown`從陣列的指標。|  
  
## <a name="remarks"></a>備註  
 `CComDynamicUnkArray` 保留的動態配置的陣列`IUnknown`指標，每個介面的連接上的點。 `CComDynamicUnkArray` 可用的參數當做[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)範本類別。  
  
 `CComDynamicUnkArray`方法[開始](#begin)並[結束](#end)可用來循環 （例如，當引發事件時） 的所有連接點。  
  
 請參閱[新增連接點物件](../../atl/adding-connection-points-to-an-object.md)如需有關自動建立連接點 proxy。  
  
> [!NOTE]
> **附註**類別`CComDynamicUnkArray`正由**加入類別**精靈建立具有連接點的控制項時。 如果您想要以手動方式指定連接點的數目，變更 從參考`CComDynamicUnkArray`要`CComUnkArray<` *n* `>`，其中*n*是連接點的數目必要的。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="add"></a>  CComDynamicUnkArray::Add  
 呼叫這個方法來加入`IUnknown`陣列的指標。  
  
```
DWORD Add(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 `IUnknown`加入至陣列的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回新加入指標與相關聯的 cookie。  
  
##  <a name="begin"></a>  CComDynamicUnkArray::begin  
 傳回的集合開頭的指標`IUnknown`介面指標。  
  
```
IUnknown**
    begin();
```     
  
### <a name="return-value"></a>傳回值  
 指標`IUnknown`介面指標。  
  
### <a name="remarks"></a>備註  
 集合包含儲存在本機作為的介面指標`IUnknown`。 您將每個轉換`IUnknown`介面為實際的介面型別，並透過它然後呼叫。 您不需要先查詢介面。  
  
 使用之前`IUnknown`介面，您應該檢查，它不是 NULL。  
  
##  <a name="clear"></a>  CComDynamicUnkArray::clear  
 清空陣列。  
  
```
void clear();
```  
  
##  <a name="ccomdynamicunkarray"></a>  CComDynamicUnkArray::CComDynamicUnkArray  
 建構函式。  
  
```
CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>備註  
 將集合大小為零，並初始化為 NULL 的值。 如有必要，則解構函式會釋出集合。  
  
##  <a name="dtor"></a>  CComDynamicUnkArray:: ~ CComDynamicUnkArray  
 解構函式。  
  
```
~CComDynamicUnkArray();
```  
  
### <a name="remarks"></a>備註  
 釋出的類別建構函式所配置的資源。  
  
##  <a name="end"></a>  CComDynamicUnkArray::end  
 讓指標回到越過最後一個`IUnknown`集合中的指標。  
  
```
IUnknown**
    end();
```     
  
### <a name="return-value"></a>傳回值  
 指標`IUnknown`介面指標。  
  
##  <a name="getat"></a>  CComDynamicUnkArray::GetAt  
 擷取指定之索引處的項目。  
  
```
IUnknown* GetAt(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 *nIndex*  
 要擷取之項目的索引。  
  
### <a name="return-value"></a>傳回值  
 指標[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)介面。  
  
##  <a name="getcookie"></a>  CComDynamicUnkArray::GetCookie  
 呼叫此方法，以取得相關聯的 cookie 指定`IUnknown`指標。  
  
```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```  
  
### <a name="parameters"></a>參數  
 *ppFind*  
 `IUnknown`相關聯的 cookie 是必要的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回具有相關聯的 cookie`IUnknown`指標或如果沒有相符的零`IUnknown`找到指標。  
  
### <a name="remarks"></a>備註  
 如果有一個以上的執行個體的相同`IUnknown`指標，此函數會傳回第一個 cookie。  
  
##  <a name="getsize"></a>  CComDynamicUnkArray::GetSize  
 傳回陣列的長度。  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>傳回值  
 陣列的長度。  
  
##  <a name="getunknown"></a>  CComDynamicUnkArray::GetUnknown  
 呼叫這個方法來取得`IUnknown`與指定的 cookie 相關聯的指標。  
  
```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```  
  
### <a name="parameters"></a>參數  
 *dwCookie*  
 Cookie 的相關聯`IUnknown`指標是必要。  
  
### <a name="return-value"></a>傳回值  
 傳回`IUnknown`指標或如果找不到任何相符的 cookie 是 NULL。  
  
##  <a name="remove"></a>  CComDynamicUnkArray::Remove  
 呼叫這個方法來移除`IUnknown`從陣列的指標。  
  
```
BOOL Remove(DWORD dwCookie);
```  
  
### <a name="parameters"></a>參數  
 *dwCookie*  
 Cookie 參考`IUnknown`移除從陣列的指標。  
  
### <a name="return-value"></a>傳回值  
 如果已移除的指標; 為 true，則傳回否則為 FALSE。  
  
## <a name="see-also"></a>另請參閱  
 [CComUnkArray 類別](../../atl/reference/ccomunkarray-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
