---
title: "COM 對應巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e97db324dc8e130418419ef435e2665c84eb0b64
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="com-map-macros"></a>COM 對應巨集
這些巨集會定義 COM 介面對應。  
  
|||  
|-|-|  
|[BEGIN_COM_MAP](#begin_com_map)|標記 COM 介面的對應項目的開頭。|  
|[END_COM_MAP](#end_com_map)|COM 介面的對應項目結束標記。|  

## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
   
##  <a name="begin_com_map"></a>BEGIN_COM_MAP  
 COM 對應是透過用戶端物件上的介面公開 （expose） 的機制`QueryInterface`。  
  
```
BEGIN_COM_MAP(x)
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]您正在公開介面的類別物件的名稱。  
  
### <a name="remarks"></a>備註  
 [CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) COM 對應中只會傳回介面指標。 啟動您的介面對應與`BEGIN_COM_MAP`巨集，將項目加入您的介面，以及每個[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)巨集，或其中一個變數，並完成的對應[END_COM_MAP](#end_com_map)巨集。  

  
### <a name="example"></a>範例  
 與 ATL[呼叫器](../../visual-cpp-samples.md)範例：  
  
 [!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  

  
##  <a name="end_com_map"></a>END_COM_MAP  
 結束您的 COM 介面對應的定義。  
  
```
END_COM_MAP()
```  
  
## <a name="see-also"></a>請參閱  
 [巨集](../../atl/reference/atl-macros.md)   
 [COM 對應全域函式](../../atl/reference/com-map-global-functions.md)
