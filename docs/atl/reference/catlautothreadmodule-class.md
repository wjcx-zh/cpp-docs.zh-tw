---
title: "CAtlAutoThreadModule 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 159b2f13dc573262bfab3a2e19209b29e3eaf5a5
ms.contentlocale: zh-tw
ms.lasthandoff: 03/31/2017

---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule 類別
這個類別會實作在集區執行緒的 apartment model COM 伺服器。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```  
  
## <a name="remarks"></a>備註  
 `CAtlAutoThreadModule`衍生自[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)並實作在集區執行緒的 apartment model COM 伺服器。 `CAtlAutoThreadModule`使用[CComApartment](../../atl/reference/ccomapartment-class.md)管理模組中的每個執行緒的 apartment。  
  
 您必須使用[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)巨集來指定物件的類別定義中[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)做為 class factory。 接著，您應該加入類別，衍生自的單一執行個體`CAtlAutoThreadModuleT`例如`CAtlAutoThreadModule`。 例如:   
  
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

