---
title: "連接點全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
caps.latest.revision: 20
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 8271f512141e4d2cc274d180b31e1ad33bfc354e
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="connection-point-global-functions"></a>連接點全域函式
這些函式支援連接點，並接收對應。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlAdvise](#atladvise)|建立物件連接點與用戶端接收器之間的連接。|  
|[AtlUnadvise](#atlunadvise)|終止所建立的連線`AtlAdvise`。|  
|[AtlAdviseSinkMap](#atladvisesinkmap)|建議或取消通知事件接收對應中的項目。|  

## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
   
##  <a name="atladvise"></a>AtlAdvise  
 建立物件連接點與用戶端接收器之間的連接。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```  
  
### <a name="parameters"></a>參數  
 `pUnkCP`  
 [in]指標**IUnknown**物件的用戶端想要進行交流。  
  
 *pUnk*  
 [in]用戶端的指標**IUnknown**。  
  
 `iid`  
 [in]連接點的 GUID。 一般而言，這是輸出連接點所管理的介面相同。  
  
 `pdw`  
 [out]指標，可唯一識別連接 cookie。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 接收器會實作連接點所支援的輸出介面。 用戶端使用`pdw`cookie 來移除連接傳遞至[AtlUnadvise](#atlunadvise)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&91;](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]  
  
##  <a name="atlunadvise"></a>AtlUnadvise  
 終止所建立的連線[AtlAdvise](#atladvise)。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```  
  
### <a name="parameters"></a>參數  
 `pUnkCP`  
 [in]指標**IUnknown**用戶端連線使用的物件。  
  
 `iid`  
 [in]連接點的 GUID。 一般而言，這是輸出連接點所管理的介面相同。  
  
 `dw`  
 [in]可唯一識別連接 cookie。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&96;](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]  
  
##  <a name="atladvisesinkmap"></a>AtlAdviseSinkMap  
 呼叫此函式可通知或取消通知在物件接收器事件對應中的所有項目。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```  
  
### <a name="parameters"></a>參數  
 *pT*  
 [in]包含接收對應的物件指標。  
  
 `bAdvise`  
 [in]**true**接收的所有項目時接到通知。**false**如果接收的所有項目要 unadvised。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&92;](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)   
 [連接點的巨集](../../atl/reference/connection-point-macros.md)

