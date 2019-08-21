---
title: 登錄宏
ms.date: 08/19/2019
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
ms.openlocfilehash: c2a70c15473798ba6eb2ef35e0b7ded395708586
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630624"
---
# <a name="registry-macros"></a>登錄宏

這些宏會定義有用的型別程式庫和登錄工具。

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|表示您希望物件的註冊程式碼位於物件中, 以避免對 ATL 的相依性。URLMON.DLL.|
|[DECLARE_LIBID](#declare_libid)|提供一種方法, 讓 ATL 取得類型程式庫的*libid* 。|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|避免預設的 ATL 註冊。|
|[DECLARE_REGISTRY](#declare_registry)|在系統登錄中輸入或移除主要物件的專案。|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|指定自動註冊*appid*所需的資訊。|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|尋找已命名的資源, 並在其中執行登入指令檔。|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|尋找識別碼所識別的資源, 並在其中執行登入指令檔。|

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

符號, 表示您希望物件的註冊程式碼位於物件中, 以避免對 ATL 的相依性。URLMON.DLL.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>備註

當您定義 ATL_STATIC_REGISTRY 時, 您應該使用下列程式碼:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>  DECLARE_LIBID

提供一種方法, 讓 ATL 取得類型程式庫的*libid* 。

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>參數

*libid*<br/>
類型程式庫的 GUID。

### <a name="remarks"></a>備註

在衍生類別中`CAtlModuleT`使用 DECLARE_LIBID。

### <a name="example"></a>範例

非屬性化的 wizard 產生的 ATL 專案會有使用此宏的範例。

##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

如果您想要避免出現此宏的類別有任何預設 ATL 註冊, 請使用 DECLARE_NO_REGISTRY。

```
DECLARE_NO_REGISTRY()
```

##  <a name="declare_registry"></a>DECLARE_REGISTRY

輸入標準類別註冊到系統登錄中, 或將它從系統登錄中移除。

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
在包含以提供回溯相容性。

*pid*<br/>
在屬於特定版本程式識別碼的 LPCTSTR。

*vpid*<br/>
在LPCTSTR, 它是與版本無關的程式識別碼。

*nid*<br/>
在UINT, 這是登錄中的資源字串索引, 用來做為程式的描述。

*flags*<br/>
在DWORD, 包含登錄中的程式執行緒模型。 必須是下列其中一個值:THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

### <a name="remarks"></a>備註

標準註冊包含 CLSID、程式識別碼、與版本無關的程式識別碼、描述字串和執行緒模型。

當您使用 ATL 的 [加入類別] Wizard 建立物件或控制項時, 嚮導會自動執行以腳本為基礎的登錄支援, 並將[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏新增至您的檔案。 如果您不想要以腳本為基礎的登錄支援, 則必須以 DECLARE_REGISTRY 取代這個宏。 DECLARE_REGISTRY 只會將前述的五個基本金鑰插入登錄中。 您必須手動撰寫程式碼, 將其他金鑰插入登錄中。

##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

指定自動註冊*appid*所需的資訊。

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>參數

*resid*<br/>
.Rgs 檔案的資源識別碼, 其中包含*appid*的相關資訊。

*appid*<br/>
GUID。

### <a name="remarks"></a>備註

在衍生類別中`CAtlModuleT`使用 DECLARE_REGISTRY_APPID_RESOURCEID。

### <a name="example"></a>範例

新增至 ATL 專案的類別若使用 [加入類別程式碼] wizard, 將會有使用此宏的範例。

##  <a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

取得包含登錄檔的已命名資源, 並執行腳本以將物件輸入系統登錄中, 或從系統登錄中將它們移除。

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>參數

*x*<br/>
在資源的字串識別碼。

### <a name="remarks"></a>備註

當您使用 ATL 專案 Wizard 建立物件或控制項時, 嚮導會自動執行以腳本為基礎的登錄支援, 並將類似 DECLARE_REGISTRY_RESOURCE 的[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏新增至您的檔案。

您可以使用 ATL 登錄元件 (註冊機構) 以靜態方式連結, 以進行優化的登錄存取。 若要以靜態方式連結到註冊機構程式碼, 請將下行新增至您的*pch .h*檔案 (Visual Studio 2017 和更早版本中的*stdafx.h* ):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果您想要 ATL 在執行時間取代取代值, 請不要指定 DECLARE_REGISTRY_RESOURCE 或 DECLARE_REGISTRY_RESOURCEID 宏。 相反地, 請建立結構`_ATL_REGMAP_ENTRIES`的陣列, 其中每個專案都包含變數預留位置與值配對, 以在執行時間取代預留位置。 然後, 呼叫[CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), 傳遞陣列。 這會將`_ATL_REGMAP_ENTRIES`結構中的所有取代值新增至註冊機構的取代對應。

如需可取代參數和腳本的詳細資訊, 請參閱[ATL 登錄元件 (註冊機構)](../../atl/atl-registry-component-registrar.md)一文。

##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

與[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)相同, 不同之處在于它會使用 wizard 產生的 UINT 來識別資源, 而不是字串名稱。

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>參數

*x*<br/>
在Wizard 產生的資源識別碼。

### <a name="remarks"></a>備註

當您使用 ATL 專案 Wizard 建立物件或控制項時, 嚮導會自動執行以腳本為基礎的登錄支援, 並將 DECLARE_REGISTRY_RESOURCEID 宏新增至您的檔案。

您可以使用 ATL 登錄元件 (註冊機構) 以靜態方式連結, 以進行優化的登錄存取。 若要以靜態方式連結到註冊機構程式碼, 請將下行新增至您的*stdafx.h*檔案 (在 Visual Studio 2019 和更新版本中為*pch. h* ):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果您想要 ATL 在執行時間取代取代值, 請不要指定 DECLARE_REGISTRY_RESOURCE 或 DECLARE_REGISTRY_RESOURCEID 宏。 相反地, 請建立結構`_ATL_REGMAP_ENTRIES`的陣列, 其中每個專案都包含變數預留位置與值配對, 以在執行時間取代預留位置。 然後, 呼叫[CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), 傳遞陣列。 這會將`_ATL_REGMAP_ENTRIES`結構中的所有取代值新增至註冊機構的取代對應。

如需可取代參數和腳本的詳細資訊, 請參閱[ATL 登錄元件 (註冊機構)](../../atl/atl-registry-component-registrar.md)一文。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
