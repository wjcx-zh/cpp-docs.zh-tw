---
title: 登錄巨集
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
ms.openlocfilehash: 8e05d6a47ea67138e8d1d456077526dd3178cc44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274638"
---
# <a name="registry-macros"></a>登錄巨集

這些巨集會定義很有用的型別程式庫 和 登錄 功能。

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|指出您要註冊程式碼中的物件，以避免相依於 ATL 物件DLL。|
|[DECLARE_LIBID](#declare_libid)|提供方法讓 ATL，以取得*libid*型別程式庫。|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|避免預設 ATL 登錄。|
|[DECLARE_REGISTRY](#declare_registry)|進入或移除系統登錄中的主要物件的項目。|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|指定自動註冊所需的資訊*appid*。|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|尋找具名的資源，並執行登錄指令碼，在其中。|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|找到識別碼所識別的資源，並執行登錄指令碼，在其中。|

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY

符號，指出您要註冊程式碼中的物件，以避免相依於 ATL 物件DLL。

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>備註

當您定義 ATL_STATIC_REGISTRY 時，您應該使用下列程式碼：

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>  DECLARE_LIBID

提供方法讓 ATL，以取得*libid*型別程式庫。

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>參數

*libid*<br/>
型別程式庫的 GUID。

### <a name="remarks"></a>備註

使用中的 DECLARE_LIBID `CAtlModuleT`-衍生的類別。

### <a name="example"></a>範例

非屬性化精靈產生的 ATL 專案必須使用這個巨集的範例。

##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY

如果您想要避免這個巨集隨即出現的類別的任何預設 ATL 登錄，請使用 DECLARE_NO_REGISTRY。

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

*class*<br/>
[in]包含為了與舊版相容。

*pid*<br/>
[in]若要 LPCTSTR 是版本專屬的程式識別項。

*vpid*<br/>
[in]LPCTSTR 版本無關的程式識別項。

*nid*<br/>
[in]UINT，是在登錄做為該程式的說明中的資源字串的索引。

*flags*<br/>
[in]DWORD，其中包含程式的登錄中的執行緒模型。 必須是下列值之一：THREADFLAGS_APARTMENT、 THREADFLAGS_BOTH 或 AUTPRXFLAG。

### <a name="remarks"></a>備註

標準登錄是由 CLSID、 程式識別碼、 版本無關的程式 ID、 描述字串和執行緒模型所組成。

當您建立的物件，或控制使用 ATL 加入類別精靈時，精靈會自動實作指令碼為基礎的登錄支援，並新增[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)巨集到您的檔案。 如果不想使用指令碼為基礎的登錄支援，您需要使用 DECLARE_REGISTRY 取代這個巨集。 DECLARE_REGISTRY 只會插入至登錄，上面所述的五個基本索引鍵。 您必須以手動方式撰寫程式碼來插入到登錄中的其他索引鍵。

##  <a name="declare_registry_appid_resourceid"></a>  DECLARE_REGISTRY_APPID_RESOURCEID

指定自動註冊所需的資訊*appid*。

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>參數

*resid*<br/>
.Rgs 檔案所包含的相關資訊的資源識別碼*appid*。

*appid*<br/>
GUID。

### <a name="remarks"></a>備註

使用中的 DECLARE_REGISTRY_APPID_RESOURCEID `CAtlModuleT`-衍生的類別。

### <a name="example"></a>範例

類別與加入類別程式碼精靈加入 ATL 專案必須使用這個巨集的範例。

##  <a name="declare_registry_resource"></a>  DECLARE_REGISTRY_RESOURCE

取得包含此登錄檔的具名的資源，並執行指令碼輸入到系統登錄中的物件，或移除系統登錄。

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>參數

*x*<br/>
[in]字串資源的識別碼。

### <a name="remarks"></a>備註

當您建立的物件，或使用 [ATL 專案精靈] 控制時，精靈會自動實作指令碼為基礎的登錄支援，並新增[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)巨集類似於 DECLARE_REGISTRY_檔案的資源。

您可以靜態連結 ATL 登錄元件 （登錄器） 進行最佳化的登錄存取。 若要以靜態方式連結登錄器程式碼，請將下行新增至您的 stdafx.h 檔案中：

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果您想在執行階段替換取代值的 ATL，請勿指定 DECLARE_REGISTRY_RESOURCE 或 DECLARE_REGISTRY_RESOURCEID 巨集。 相反地，建立陣列`_ATL_REGMAP_ENTRIES`配對來取代預留位置，在執行階段值的結構，其中每個項目包含變數的預留位置。 然後呼叫[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或是[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，將陣列傳遞。 這樣會加入所有中的取代值`_ATL_REGMAP_ENTRIES`註冊機構的取代對應的結構。

如需有關可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。

##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID

與相同[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)不同之處在於它會使用精靈所產生的單位，來識別資源，而不是字串名稱。

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>參數

*x*<br/>
[in]您資源的精靈所產生的識別項。

### <a name="remarks"></a>備註

當您建立的物件或使用 [ATL 專案精靈] 的控制項時，此精靈會自動實作指令碼為基礎的登錄支援，並將 DECLARE_REGISTRY_RESOURCEID 巨集新增至您的檔案。

您可以靜態連結 ATL 登錄元件 （登錄器） 進行最佳化的登錄存取。 若要以靜態方式連結登錄器程式碼，請將下行新增至您的 stdafx.h 檔案中：

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果您想在執行階段替換取代值的 ATL，請勿指定 DECLARE_REGISTRY_RESOURCE 或 DECLARE_REGISTRY_RESOURCEID 巨集。 相反地，建立陣列`_ATL_REGMAP_ENTRIES`配對來取代預留位置，在執行階段值的結構，其中每個項目包含變數的預留位置。 然後呼叫[CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或是[CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)，將陣列傳遞。 這樣會加入所有中的取代值`_ATL_REGMAP_ENTRIES`註冊機構的取代對應的結構。

如需有關可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
