---
title: 註冊表宏
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
ms.openlocfilehash: fd012b4300f4cd72cdc9ab363b770ac1dbefa06e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326048"
---
# <a name="registry-macros"></a>註冊表宏

這些宏定義有用的類型庫和註冊表工具。

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|指示您希望物件的註冊代碼位於物件中,以避免依賴 ATL。Dll。|
|[DECLARE_LIBID](#declare_libid)|為 ATL 提供了獲取類型庫的*升標*的方法。|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|避免預設 ATL 註冊。|
|[DECLARE_REGISTRY](#declare_registry)|在系統註冊表中輸入或刪除主物件的條目。|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|指定自動註冊*應用程式所需的*資訊。|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|查找命名資源並在其中運行註冊表腳本。|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|查找由 ID 號標識的資源,並在其中運行註冊表腳本。|

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="_atl_static_registry"></a><a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

指示您希望物件的註冊代碼位於物件中以避免依賴 ATL 的符號。Dll。

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>備註

定義ATL_STATIC_REGISTRY時,應使用以下代碼:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

## <a name="declare_libid"></a><a name="declare_libid"></a>DECLARE_LIBID

為 ATL 提供了獲取類型庫的*升標*的方法。

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>參數

*利比德*<br/>
型別程式庫的 GUID。

### <a name="remarks"></a>備註

在`CAtlModuleT`派生類中使用DECLARE_LIBID。

### <a name="example"></a>範例

非屬性化精靈生成的 ATL 專案將具有使用此巨集的範例。

## <a name="declare_no_registry"></a><a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

如果要避免顯示此宏的類的任何預設 ATL 註冊,請使用DECLARE_NO_REGISTRY。

```
DECLARE_NO_REGISTRY()
```

## <a name="declare_registry"></a><a name="declare_registry"></a>DECLARE_REGISTRY

將標準類註冊輸入系統註冊表,或將其從系統註冊表中刪除。

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
[在]包括用於向後相容性。

*pid*<br/>
[在]LPCTSTR,它是特定於版本的程序標識碼。

*vpid*<br/>
[在]LPCTSTR,它是一個獨立於版本的程序標識符。

*尼德*<br/>
[在]UINT,它是註冊表中資源字串的索引,用於用作程式的說明。

*標誌*<br/>
[在]包含註冊表中程式線程模型的 DWORD。 必須為以下值之一:THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

### <a name="remarks"></a>備註

標準註冊由 CLSID、程式 ID、獨立於版本的程式 ID、描述字串和線程模型組成。

使用 ATL 添加類嚮導創建物件或控制項時,精靈將自動實現基於文稿的註冊表支援,並將[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏添加到檔中。 如果不需要基於腳本的註冊表支援,則需要將此宏替換為DECLARE_REGISTRY。 DECLARE_REGISTRY僅將上述五個基本鍵插入註冊表。 您必須手動編寫代碼才能將其他鍵插入註冊表。

## <a name="declare_registry_appid_resourceid"></a><a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

指定自動註冊*應用程式所需的*資訊。

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>參數

*渣 油*<br/>
包含有關*應用程式*的資訊的 .rgs 檔案的資源識別碼。

*應用程式*<br/>
GUID。

### <a name="remarks"></a>備註

在`CAtlModuleT`派生類中使用DECLARE_REGISTRY_APPID_RESOURCEID。

### <a name="example"></a>範例

使用「添加類」代碼向導添加到 ATL 專案的類將具有使用此宏的範例。

## <a name="declare_registry_resource"></a><a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

獲取包含註冊表檔的命名資源,並運行文稿以將物件輸入到系統註冊表中或從系統註冊表中刪除它們。

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]資源的字串標識碼。

### <a name="remarks"></a>備註

使用 ATL 專案精靈建立物件或控制項時,精靈將自動實現基於文稿的註冊表支援,並將[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)宏(類似於DECLARE_REGISTRY_RESOURCE)添加到檔中。

您可以靜態地與 ATL 註冊表元件 (註冊器) 連結,以優化註冊表訪問。 要靜態連結到註冊器代碼,請向*pch.h*檔添加以下行(Visual Studio 2017 和更早版本中的*stdafx.h):*

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果希望 ATL 在運行時替換替換值,請不要指定DECLARE_REGISTRY_RESOURCE或DECLARE_REGISTRY_RESOURCEID宏。 相反,請創建一個`_ATL_REGMAP_ENTRIES`結構陣列,其中每個條目包含一個變數占位符,該占位符與值配對,以在運行時替換佔位符。 然後調用[CAtlModule::從資源D](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule 更新註冊表:更新註冊表從資源](catlmodule-class.md#updateregistryfromresources),傳遞陣列。 這會將`_ATL_REGMAP_ENTRIES`結構中的所有替換值添加到註冊器的替換映射中。

有關可替換參數和腳本的詳細資訊,請參閱[ATL 註冊表元件 (註冊) 一](../../atl/atl-registry-component-registrar.md)文。

## <a name="declare_registry_resourceid"></a><a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

與[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)相同,只不過它使用嚮導生成的 UINT 來標識資源,而不是字串名稱。

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]嚮導生成的資源標識碼。

### <a name="remarks"></a>備註

使用 ATL 專案精靈建立物件或控制項時,精靈將自動實現基於文稿的註冊表支援,並將DECLARE_REGISTRY_RESOURCEID宏添加到檔中。

您可以靜態地與 ATL 註冊表元件 (註冊器) 連結,以優化註冊表訪問。 要靜態鏈接到註冊器代碼,請向*stdafx.h*檔添加以下行(Visual Studio 2019 及更高版本中*的 pch.h):*

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

如果希望 ATL 在運行時替換替換值,請不要指定DECLARE_REGISTRY_RESOURCE或DECLARE_REGISTRY_RESOURCEID宏。 相反,請創建一個`_ATL_REGMAP_ENTRIES`結構陣列,其中每個條目包含一個變數占位符,該占位符與值配對,以在運行時替換佔位符。 然後調用[CAtlModule::從資源D](catlmodule-class.md#updateregistryfromresourced)或[CAtlModule 更新註冊表:更新註冊表從資源](catlmodule-class.md#updateregistryfromresources),傳遞陣列。 這會將`_ATL_REGMAP_ENTRIES`結構中的所有替換值添加到註冊器的替換映射中。

有關可替換參數和腳本的詳細資訊,請參閱[ATL 註冊表元件 (註冊) 一](../../atl/atl-registry-component-registrar.md)文。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
