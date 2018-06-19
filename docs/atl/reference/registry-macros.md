---
title: 登錄巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed9b172217f1ca7ada7d8752151126b53055df37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365213"
---
# <a name="registry-macros"></a>登錄巨集
這些巨集會定義有用的型別程式庫和登錄設備。  
  
|||  
|-|-|  
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|指出您要登錄程式碼中的物件，以避免相依於 ATL 物件DLL。|  
|[DECLARE_LIBID](#declare_libid)|提供方法讓取得 ATL *libid*類型程式庫。|  
|[DECLARE_NO_REGISTRY](#declare_no_registry)|避免預設 ATL 登錄。|  
|[DECLARE_REGISTRY](#declare_registry)|輸入或移除系統登錄中的主要物件的項目。|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|指定自動註冊所需的資訊*appid*。|  
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|尋找具名的資源，並執行它內的登錄指令碼。|  
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|尋找識別碼所識別的資源，並執行它內的登錄指令碼。|  

## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
    
##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY  
 指出您要登錄程式碼中的物件，以避免 ATL 的相依性物件的符號DLL。  
  
```
#define _ATL_STATIC_REGISTRY
```  
  
### <a name="remarks"></a>備註  
 當您定義**ATL_STATIC_REGISTRY**，您應該使用下列程式碼：  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]  
  
##  <a name="declare_libid"></a>  DECLARE_LIBID  
 提供方法讓取得 ATL *libid*類型程式庫。  
  
```
DECLARE_LIBID( libid )
```  
  
### <a name="parameters"></a>參數  
 *libid*  
 類型程式庫的 GUID。  
  
### <a name="remarks"></a>備註  
 使用`DECLARE_LIBID`中`CAtlModuleT`-衍生的類別。  
  
### <a name="example"></a>範例  
 使用非屬性精靈產生的 ATL 專案必須使用這個巨集的範例。  
  
##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY  
 使用`DECLARE_NO_REGISTRY`如果您想要避免這個巨集所在的類別的任何預設 ATL 登錄。  
  
```
DECLARE_NO_REGISTRY()
```  
  
##  <a name="declare_registry"></a>  DECLARE_REGISTRY  
 進入系統登錄中的標準類別註冊或移除系統登錄。  
  
```
DECLARE_REGISTRY(
    class, 
    pid, 
    vpid, 
    nid, 
    flags )
```  
  
### <a name="parameters"></a>參數  
 `class`  
 [in]包含為了回溯相容性。  
  
 `pid`  
 [in]`LPCTSTR`也就是版本專屬的程式識別項。  
  
 *vpid*  
 [in]`LPCTSTR`也就是版本無關的程式識別項。  
  
 *nid*  
 [in]A **UINT**也就是要做為程式的描述在登錄中的資源字串的索引。  
  
 `flags`  
 [in]A`DWORD`包含程式的執行緒在登錄中的模型。 必須是下列值之一： **THREADFLAGS_APARTMENT**， **THREADFLAGS_BOTH**，或**AUTPRXFLAG**。  
  
### <a name="remarks"></a>備註  
 標準登錄包含 CLSID、 程式識別碼、 版本無關的程式識別碼、 描述字串和執行緒模型。  
  
 當您建立的物件，或使用 ATL 加入類別精靈時，精靈會自動實作指令碼為基礎的登錄支援，並將[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)巨集，以您的檔案。 如果不想使用指令碼為基礎的登錄支援，您需要取代這個巨集與`DECLARE_REGISTRY`。 `DECLARE_REGISTRY` 僅插入到登錄上面所述的五個基本按鍵。 您必須手動撰寫程式碼加入其他索引鍵插入登錄。  
  
##  <a name="declare_registry_appid_resourceid"></a>  DECLARE_REGISTRY_APPID_RESOURCEID  
 指定自動註冊所需的資訊*appid*。  
  
```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid, 
    appid )
```  
  
### <a name="parameters"></a>參數  
 *resid*  
 包含的相關資訊的.rgs 檔案的資源識別碼*appid*。  
  
 *appid*  
 GUID。  
  
### <a name="remarks"></a>備註  
 使用`DECLARE_REGISTRY_APPID_RESOURCEID`中`CAtlModuleT`-衍生的類別。  
  
### <a name="example"></a>範例  
 加入類別程式碼精靈加入 ATL 專案的類別必須使用這個巨集的範例。  
  
##  <a name="declare_registry_resource"></a>  DECLARE_REGISTRY_RESOURCE  
 取得包含登錄檔案的具名的資源並執行指令碼輸入到系統登錄中的物件或移除系統登錄。  
  
```
DECLARE_REGISTRY_RESOURCE( x )
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]字串之資源的識別項。  
  
### <a name="remarks"></a>備註  
 當您建立的物件，或使用 ATL 專案精靈時，精靈會自動實作指令碼為基礎的登錄支援，並新增[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)巨集，類似於`DECLARE_REGISTRY_RESOURCE`至程式檔案。  
  
 您可以以靜態方式連結與最佳化的登錄存取 ATL 登錄元件 （登錄器）。 若要以靜態方式連結的註冊機構的程式碼，請至您的 stdafx.h 檔案中加入下行：  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 如果您想要替代的取代值在執行階段的 ATL，請勿指定`DECLARE_REGISTRY_RESOURCE`或`DECLARE_REGISTRY_RESOURCEID`巨集。 相反地，建立陣列 **_ATL_REGMAP_ENTRIES**結構，其中每個項目都包含變數的預留位置搭配要在執行階段取代預留位置的值。 然後呼叫[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，並將陣列傳遞。 這會將所有中的取代值 **_ATL_REGMAP_ENTRIES**的註冊機構取代對應的結構。  

  
 如需可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。  
  
##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID  
 與相同[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)不同之處在於它會使用精靈產生**UINT**來識別資源，而不是字串名稱。  
  
```
DECLARE_REGISTRY_RESOURCEID( x )
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]您資源的精靈產生的識別項。  
  
### <a name="remarks"></a>備註  
 當您建立的物件，或使用 ATL 專案精靈時，精靈會自動實作指令碼為基礎的登錄支援，並新增`DECLARE_REGISTRY_RESOURCEID`巨集，以您的檔案。  
  
 您可以以靜態方式連結與最佳化的登錄存取 ATL 登錄元件 （登錄器）。 若要以靜態方式連結的註冊機構的程式碼，請至您的 stdafx.h 檔案中加入下行：  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 如果您想要替代的取代值在執行階段的 ATL，請勿指定`DECLARE_REGISTRY_RESOURCE`或`DECLARE_REGISTRY_RESOURCEID`巨集。 相反地，建立陣列 **_ATL_REGMAP_ENTRIES**結構，其中每個項目都包含變數的預留位置搭配要在執行階段取代預留位置的值。 然後呼叫[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，並將陣列傳遞。 這會將所有中的取代值 **_ATL_REGMAP_ENTRIES**的註冊機構取代對應的結構。  

  
 如需可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)
