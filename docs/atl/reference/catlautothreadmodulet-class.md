---
title: "CAtlAutoThreadModuleT 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 86b35f0a6a3ab43c170ee710838ec9ba0e2fc5b0
ms.lasthandoff: 02/24/2017

---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT 類別
這個類別提供方法來實作執行緒集區、 公寓模型 COM 伺服器。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, 
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 類別會實作 COM 伺服器。  
  
 `ThreadAllocator`  
 管理執行緒選取項目類別。 預設值是[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
 `dwWait`  
 指定的逾時間隔，以毫秒為單位。 預設為無限，表示永遠不會超過方法的逾時間隔。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|這個靜態函式會動態計算，並傳回 EXE 模組，根據處理器數目的執行緒數目上限。|  
  
## <a name="remarks"></a>備註  
 類別[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)衍生自`CAtlAutoThreadModuleT`為了實作執行緒集區、 apartment 模型的 COM 伺服器。 它會取代過時類別[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
> [!NOTE]
>  這個類別不應在 DLL 中，預設值為`dwWait`的無限值在卸載 DLL 時，會造成死結。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IAtlAutoThreadModule`  
  
 `CAtlAutoThreadModuleT`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads  
 這個靜態函式會動態計算，並傳回 EXE 模組，根據處理器數目的執行緒數目上限。  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>傳回值  
 在 EXE 模組中建立的執行緒數目。  
  
### <a name="remarks"></a>備註  
 如果您想要使用不同的方法來計算的執行緒數目，請覆寫這個方法。 根據預設，執行緒數目根據處理器數目。  
  
## <a name="see-also"></a>另請參閱  
 [IAtlAutoThreadModule 類別](../../atl/reference/iatlautothreadmodule-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [IAtlAutoThreadModule 類別](../../atl/reference/iatlautothreadmodule-class.md)   
 [模組類別](../../atl/atl-module-classes.md)

