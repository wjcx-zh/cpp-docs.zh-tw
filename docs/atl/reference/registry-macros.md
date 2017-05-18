---
title: "登錄巨集 |Microsoft 文件"
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
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 3a3abf5ad29b50c7f6708f02fd7c5aa193b3591c
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="registry-macros"></a>登錄巨集
這些巨集定義有用的型別程式庫和登錄的設備。  
  
|||  
|-|-|  
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|指出您想要在物件，以避免相依於 ATL 物件的註冊程式碼DLL。|  
|[DECLARE_LIBID](#declare_libid)|提供方法讓取得 ATL *libid*型別程式庫。|  
|[DECLARE_NO_REGISTRY](#declare_no_registry)|可避免預設 ATL 登錄。|  
|[DECLARE_REGISTRY](#declare_registry)|輸入或移除系統登錄中的主要物件的項目。|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|指定自動註冊所需的資訊*appid*。|  
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|尋找具名的資源，並執行登錄指令碼中。|  
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|尋找識別碼所識別的資源，並執行登錄指令碼中。|  

## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
    
##  <a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY  
 一個符號，指出您想要在物件，以避免相依於 ATL 物件的註冊程式碼DLL。  
  
```
#define _ATL_STATIC_REGISTRY
```  
  
### <a name="remarks"></a>備註  
 當您定義**ATL_STATIC_REGISTRY**，您應該使用下列程式碼︰  
  
 [!code-cpp[NVC_ATL_EventHandlingSample #&5;](../../atl/codesnippet/cpp/registry-macros_1.cpp)]  
  
##  <a name="declare_libid"></a>DECLARE_LIBID  
 提供方法讓取得 ATL *libid*型別程式庫。  
  
```
DECLARE_LIBID( libid )
```  
  
### <a name="parameters"></a>參數  
 *libid*  
 型別程式庫 GUID。  
  
### <a name="remarks"></a>備註  
 使用`DECLARE_LIBID`中`CAtlModuleT`-衍生的類別。  
  
### <a name="example"></a>範例  
 非屬性化精靈產生的 ATL 專案都有使用這個巨集的範例。  
  
##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY  
 使用`DECLARE_NO_REGISTRY`如果您想要避免這個巨集隨即出現的類別的任何預設 ATL 登錄。  
  
```
DECLARE_NO_REGISTRY()
```  
  
##  <a name="declare_registry"></a>DECLARE_REGISTRY  
 進入系統登錄中的標準的類別註冊或移除系統登錄。  
  
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
 [in]包含的回溯相容性。  
  
 `pid`  
 [in]`LPCTSTR`也就是版本專屬的程式識別項。  
  
 *vpid*  
 [in]`LPCTSTR`也就是版本無關的程式識別項。  
  
 *nid*  
 [in]A **UINT**也就是在登錄做為程式的描述中的資源字串的索引。  
  
 `flags`  
 [in]A`DWORD`包含程式的執行緒在登錄中的模型。 必須是下列值之一︰ **THREADFLAGS_APARTMENT**， **THREADFLAGS_BOTH**，或**AUTPRXFLAG**。  
  
### <a name="remarks"></a>備註  
 標準的註冊包含 CLSID、 程式識別碼、 版本無關的程式 ID、 描述字串和執行緒模型。  
  
 當您建立的物件，或控制使用 ATL 加入類別精靈時，精靈會自動實作指令碼為基礎的登錄的支援，並將[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)巨集，以您的檔案。 若不想使用指令碼架構登錄支援，您需要使用這個巨集來取代`DECLARE_REGISTRY`。 `DECLARE_REGISTRY`只會插入到登錄上面所述的五個基本按鍵。 您必須手動撰寫程式碼中插入其他金鑰登錄。  
  
##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID  
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
  
##  <a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE  
 取得包含登錄檔的具名的資源，並執行指令碼，請輸入在系統登錄的物件，或移除系統登錄。  
  
```
DECLARE_REGISTRY_RESOURCE( x )
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]字串資源的識別碼。  
  
### <a name="remarks"></a>備註  
 當您建立的物件，或控制使用 ATL 專案精靈時，精靈會自動實作指令碼架構登錄支援，並新增[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)巨集，這類似於`DECLARE_REGISTRY_RESOURCE`，您的檔案。  
  
 您可以靜態連結 ATL 登錄元件 （登錄器） 進行最佳化的登錄存取。 要以靜態方式連結至登錄器程式碼，請在您的 stdafx.h 檔案中加入下列程式︰  
  
 [!code-cpp[NVC_ATL_COM&#56;](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 如果您想在執行階段取代值的 ATL，請勿指定`DECLARE_REGISTRY_RESOURCE`或`DECLARE_REGISTRY_RESOURCEID`巨集。 相反地，建立陣列**_ATL_REGMAP_ENTRIES**與要在執行階段取代預留位置的值配對的結構，其中每個項目都包含變數的預留位置。 然後呼叫[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，傳遞陣列。 這會將所有的取代值新增**_ATL_REGMAP_ENTRIES**註冊機構的取代對應的結構。  

  
 如需可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。  
  
##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID  
 相同[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)不同之處在於它會使用精靈產生**UINT**來識別資源，而不是字串名稱。  
  
```
DECLARE_REGISTRY_RESOURCEID( x )
```  
  
### <a name="parameters"></a>參數  
 *x*  
 [in]資源的精靈所產生的識別項。  
  
### <a name="remarks"></a>備註  
 當您建立的物件，或控制使用 ATL 專案精靈時，精靈會自動實作指令碼架構登錄支援，並新增`DECLARE_REGISTRY_RESOURCEID`巨集，以您的檔案。  
  
 您可以靜態連結 ATL 登錄元件 （登錄器） 進行最佳化的登錄存取。 要以靜態方式連結至登錄器程式碼，請在您的 stdafx.h 檔案中加入下列程式︰  
  
 [!code-cpp[NVC_ATL_COM&#56;](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 如果您想在執行階段取代值的 ATL，請勿指定`DECLARE_REGISTRY_RESOURCE`或`DECLARE_REGISTRY_RESOURCEID`巨集。 相反地，建立陣列**_ATL_REGMAP_ENTRIES**與要在執行階段取代預留位置的值配對的結構，其中每個項目都包含變數的預留位置。 然後呼叫[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，傳遞陣列。 這會將所有的取代值新增**_ATL_REGMAP_ENTRIES**註冊機構的取代對應的結構。  

  
 如需可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)

