---
title: "COM 對應巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
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
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 1c8e73fc4d6cab2e9052e74d68bddbb5796ebfa8
ms.lasthandoff: 03/31/2017

---
# <a name="com-map-macros"></a>COM 對應巨集
這些巨集會定義 COM 介面對應。  
  
|||  
|-|-|  
|[BEGIN_COM_MAP](#begin_com_map)|標記 COM 介面的對應項目的開頭。|  
|[END_COM_MAP](#end_com_map)|COM 介面的對應項目結束標記。|  

## <a name="requirements"></a>需求  
 **標頭︰** atlcom.h  
   
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
 與 ATL[呼叫器](../../visual-cpp-samples.md)範例︰  
  
 [!code-cpp[NVC_ATL_COM #1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  

  
##  <a name="end_com_map"></a>END_COM_MAP  
 結束您的 COM 介面對應的定義。  
  
```
END_COM_MAP()
```  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)   
 [COM 對應全域函式](../../atl/reference/com-map-global-functions.md)

