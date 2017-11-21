---
title: "連接點巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
dev_langs: C++
helpviewer_keywords: connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 19eb60af9da72f3c158b9eacbfbfbdf478f1382d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="connection-point-macros"></a>連接點巨集
這些巨集會定義連接點對應和項目。  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|標記連接點對應項目的開頭。|  
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|輸入對應的連接點。|  
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017)類似於 CONNECTION_POINT_ENTRY 但接受 iid 的指標。|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|連接點對應項目結束標記。|  

## <a name="requirements"></a>需求  
 **標頭：** atlcom.h 
   
##  <a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP  
 標記連接點對應項目的開頭。  
  
```
BEGIN_CONNECTION_POINT_MAP(x)
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]包含連接點的類別名稱。  
  
### <a name="remarks"></a>備註  
 開始使用您的連接點對應`BEGIN_CONNECTION_POINT_MAP`巨集，將項目加入每個連接點與[CONNECTION_POINT_ENTRY](#connection_point_entry)巨集，並完成的對應[END_CONNECTION_POINT_MAP](#end_connection_point_map)巨集。  
  
 如需 ATL 中的連接點的詳細資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]  
  
##  <a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY 和 CONNECTION_POINT_ENTRY_P  
 輸入的連接點指定介面的連接點對應使它無法存取。  
  
```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]正在加入的連接點對應介面的 GUID。 
 
 `piid`  
 [in]正在 adde 介面的 GUID 的指標。   
  
### <a name="remarks"></a>備註  
 在對應中的連接點項目由[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)。 包含連接點對應的類別必須繼承自`IConnectionPointContainerImpl`。  
  
 開始使用您的連接點對應[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)巨集，將項目加入每個連接點與`CONNECTION_POINT_ENTRY`巨集，並完成的對應[END_CONNECTION_POINT_MAP](#end_connection_point_map)巨集。  
  
 如需 ATL 中的連接點的詳細資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]  
  
##  <a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP  
 連接點對應項目結束標記。  
  
```
END_CONNECTION_POINT_MAP()
```  
  
### <a name="remarks"></a>備註  
 開始使用您的連接點對應[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)巨集，將項目加入每個連接點與[CONNECTION_POINT_ENTRY](#connection_point_entry)巨集，並完成的對應`END_CONNECTION_POINT_MAP`巨集。  
  
 如需 ATL 中的連接點的詳細資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)   
 [連接點全域函式](../../atl/reference/connection-point-global-functions.md)
