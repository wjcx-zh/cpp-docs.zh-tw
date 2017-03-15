---
title: "CAtlAutoThreadModule 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CAtlAutoThreadModule
- CAtlAutoThreadModule
- ATL::CAtlAutoThreadModule
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
caps.latest.revision: 19
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 09f4a7061ce1e4a09d0d27bd90dfcc16a37f4d5b
ms.lasthandoff: 02/24/2017

---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule 類別
這個類別會實作在執行緒集區的 apartment model COM 伺服器。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```  
  
## <a name="remarks"></a>備註  
 `CAtlAutoThreadModule`衍生自[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)並實作在執行緒集區的 apartment model COM 伺服器。 `CAtlAutoThreadModule`使用[CComApartment](../../atl/reference/ccomapartment-class.md)管理模組中的每個執行緒的 apartment。  
  
 您必須使用[DECLARE_CLASSFACTORY_AUTO_THREAD](http://msdn.microsoft.com/library/19d7105e-03e8-4412-9f5e-5384c8a5e18f)巨集來指定物件的類別定義中[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)作為類別處理站。 接著，您應該加入衍生自類別的單一執行個體`CAtlAutoThreadModuleT`例如`CAtlAutoThreadModule`。 例如:   
  
 `CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`  
  
> [!NOTE]
>  這個類別會取代過時[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IAtlAutoThreadModule`  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 `CAtlAutoThreadModule`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
## <a name="see-also"></a>另請參閱  
 [CAtlAutoThreadModuleT 類別](../../atl/reference/catlautothreadmodulet-class.md)   
 [IAtlAutoThreadModule 類別](../../atl/reference/iatlautothreadmodule-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)
