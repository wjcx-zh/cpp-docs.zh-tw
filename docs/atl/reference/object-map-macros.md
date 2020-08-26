---
title: 物件對應宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 2eb24914561a958a6d6d79dab6779e0ba0a70201
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835281"
---
# <a name="object-map-macros"></a>物件對應宏

這些宏會定義物件對應和專案。

|名稱|描述|
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|可讓您指定類別物件的文字描述，並將其輸入至物件對應中。|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|將 ATL 物件輸入物件對應、更新登錄，然後建立物件的實例。|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|可讓您指定應該註冊並初始化物件，而不應該透過 `CoCreateInstance` 從外部建立。|

## <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="declare_object_description"></a><a name="declare_object_description"></a> DECLARE_OBJECT_DESCRIPTION

可讓您指定類別物件的文字描述。

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>參數

*x*<br/>
在類別物件的描述。

### <a name="remarks"></a>備註

ATL 會透過 [OBJECT_ENTRY_AUTO](#object_entry_auto) 宏將此描述輸入至物件對應中。

DECLARE_OBJECT_DESCRIPTION 會實作為函式 `GetObjectDescription` ，您可以用它來覆寫 [CComCoClass：： GetObjectDescription](ccomcoclass-class.md#getobjectdescription) 方法。

`GetObjectDescription`呼叫函數的方法是 `IComponentRegistrar::GetComponents` 。 `IComponentRegistrar` 是自動化介面，可讓您註冊及取消註冊 DLL 中的個別元件。 當您使用 ATL 專案嚮導建立元件註冊機構物件時，嚮導會自動執行 `IComponentRegistrar` 介面。 `IComponentRegistrar` 通常是由 Microsoft 交易伺服器使用。

如需 ATL 專案 Wizard 的詳細資訊，請參閱 [建立 Atl 專案](../../atl/reference/creating-an-atl-project.md)的文章。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

## <a name="object_entry_auto"></a><a name="object_entry_auto"></a> OBJECT_ENTRY_AUTO

將 ATL 物件輸入物件對應、更新登錄，然後建立物件的實例。

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>參數

*Clsid*<br/>
在由 c + + 類別命名為 *class*的 COM 類別的 CLSID。

*class*<br/>
在C + + 類別的名稱，這個類別會執行 *clsid*所表示的 COM 類別。

### <a name="remarks"></a>備註

物件進入巨集會放在專案的全域範圍，以支援註冊、初始化和建立類別。

OBJECT_ENTRY_AUTO 進入 creator 類別的函式指標，以及這個物件的 class factory creator 類別函式， `CreateInstance` 以自動產生的 ATL 物件對應。 呼叫 [CAtlComModule：： RegisterServer](catlcommodule-class.md#registerserver) 時，它會針對物件對應中的每個物件更新系統登錄。

下表描述如何從指定為這個宏的第二個參數的類別，取得新增至物件對應的資訊。

|的相關資訊|取得者|
|---------------------|-------------------|
|COM 註冊|[登錄宏](../../atl/reference/registry-macros.md)|
|建立類別 factory|[Class Factory 宏](../../atl/reference/aggregation-and-class-factory-macros.md)|
|建立實例|[匯總宏](../../atl/reference/aggregation-and-class-factory-macros.md)|
|元件類別註冊|[類別宏](../../atl/reference/category-macros.md)|
|類別層級初始化和清除|[ObjectMain](ccomobjectrootex-class.md#objectmain)|

## <a name="object_entry_non_createable_ex_auto"></a><a name="object_entry_non_createable_ex_auto"></a> OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

可讓您指定應該註冊並初始化物件，而不應該透過 `CoCreateInstance` 從外部建立。

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>參數

*Clsid*<br/>
在由 c + + 類別命名為 *class*的 COM 類別的 CLSID。

*class*<br/>
在C + + 類別的名稱，這個類別會執行 *clsid*所表示的 COM 類別。

### <a name="remarks"></a>備註

物件進入巨集會放在專案的全域範圍，以支援註冊、初始化和建立類別。

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO 可讓您指定應該註冊並初始化物件 (如需) 的詳細資訊，請參閱 [OBJECT_ENTRY_AUTO](#object_entry_auto) `CoCreateInstance` 。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
