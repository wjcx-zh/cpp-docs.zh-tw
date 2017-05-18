---
title: "連接點的巨集 |Microsoft 文件"
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
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
caps.latest.revision: 16
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
ms.sourcegitcommit: 8cdedc5cfac9d49df812ae6fcfcc548201b1edb5
ms.openlocfilehash: c16b6f2f889745270a51a32a1449add86dec6ecb
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="connection-point-macros"></a>連接點的巨集
這些巨集定義連接點對應和項目。  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|標記連接點對應項目的開頭。|  
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|輸入對應的連接點。|  
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017)CONNECTION_POINT_ENTRY 類似，但會 iid 的指標。|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|連接點對應項目結束標記。|  

## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h 
   
##  <a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP  
 標記連接點對應項目的開頭。  
  
```
BEGIN_CONNECTION_POINT_MAP(x)
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]包含連接點的類別名稱。  
  
### <a name="remarks"></a>備註  
 啟動與連接點對應`BEGIN_CONNECTION_POINT_MAP`巨集，將項目加入每個連接點與[CONNECTION_POINT_ENTRY](#connection_point_entry)巨集，並完成的對應[END_CONNECTION_POINT_MAP](#end_connection_point_map)巨集。  
  
 如需在 ATL 中的連接點的詳細資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&101;](../../atl/codesnippet/cpp/connection-point-macros_1.h)]  
  
##  <a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY 和 CONNECTION_POINT_ENTRY_P  
 輸入的連接點指定介面的連接點對應，以便它可以存取。  
  
```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]新增連接點對應至介面的 GUID。 
 
 `piid`  
 [in]正在加入了進行真實介面的 GUID 指標。   
  
### <a name="remarks"></a>備註  
 在對應中的連接點項目由[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)。 包含連接點對應的類別必須繼承自`IConnectionPointContainerImpl`。  
  
 啟動與連接點對應[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)巨集，將項目加入每個連接點與`CONNECTION_POINT_ENTRY`巨集，並完成的對應[END_CONNECTION_POINT_MAP](#end_connection_point_map)巨集。  
  
 如需在 ATL 中的連接點的詳細資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&120;](../../atl/codesnippet/cpp/connection-point-macros_2.h)]  
  
##  <a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP  
 連接點對應項目結束標記。  
  
```
END_CONNECTION_POINT_MAP()
```  
  
### <a name="remarks"></a>備註  
 啟動與連接點對應[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)巨集，將項目加入每個連接點與[CONNECTION_POINT_ENTRY](#connection_point_entry)巨集，並完成的對應`END_CONNECTION_POINT_MAP`巨集。  
  
 如需在 ATL 中的連接點的詳細資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&128;](../../atl/codesnippet/cpp/connection-point-macros_3.h)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)   
 [連接點全域函式](../../atl/reference/connection-point-global-functions.md)

