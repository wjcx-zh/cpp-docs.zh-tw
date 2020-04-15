---
title: 物件對應巨集
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 66a418019ba506a5832c8e3ad86a3764c1186df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326206"
---
# <a name="object-map-macros"></a>物件對應巨集

這些宏定義物件映射和條目。

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|允許您指定類物件的文本描述,該描述將輸入到物件映射中。|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|將 ATL 物件輸入物件映射,更新註冊表,並創建物件的實例。|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|可讓您指定應該註冊並初始化物件，而不應該透過 `CoCreateInstance` 從外部建立。|

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="declare_object_description"></a><a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION

允許您為類物件指定文本說明。

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]類對象的描述。

### <a name="remarks"></a>備註

ATL 通過[OBJECT_ENTRY_AUTO](#object_entry_auto)宏將此描述輸入到對象映射中。

DECLARE_OBJECT_DESCRIPTION實現一`GetObjectDescription`個函數,可用於重寫[CComCoClass::getObject 描述](ccomcoclass-class.md#getobjectdescription)方法。

函數`GetObjectDescription`由`IComponentRegistrar::GetComponents`呼叫 。 `IComponentRegistrar`是一個自動化介面,允許您在 DLL 中註冊和取消註冊單個元件。 使用 ATL 專案精靈創建元件註冊器物件時,嚮導將自動實現`IComponentRegistrar`介面。 `IComponentRegistrar`通常用於 Microsoft 事務伺服器。

有關 ATL 專案精靈的詳細資訊,請參閱創建[ATL 專案](../../atl/reference/creating-an-atl-project.md)的文章。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

## <a name="object_entry_auto"></a><a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO

將 ATL 物件輸入物件映射,更新註冊表,並創建物件的實例。

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>參數

*Clsid*<br/>
[在]由名為*類*的C++類實現的 COM 類的 CLSID。

*class*<br/>
[在]實現由*clsid*表示的 COM 類的 C++類的名稱。

### <a name="remarks"></a>備註

物件進入巨集會放在專案的全域範圍，以支援註冊、初始化和建立類別。

OBJECT_ENTRY_AUTO此物件的建立者類和類工廠創建者類`CreateInstance`函數的函數指標輸入到自動生成的 ATL 物件映射中。 當調用[CAtlComModule:註冊伺服器](catlcommodule-class.md#registerserver)時,它會更新物件映射中每個物件的系統註冊表。

下表描述了如何從作為此宏的第二個參數給出的類獲取添加到對象映射的資訊。

|資訊|從|
|---------------------|-------------------|
|COM 註冊|[註冊表宏](../../atl/reference/registry-macros.md)|
|類別工廠建立|[類工廠宏](../../atl/reference/aggregation-and-class-factory-macros.md)|
|實體建立|[聚合宏](../../atl/reference/aggregation-and-class-factory-macros.md)|
|元件類別註冊|[類別巨集](../../atl/reference/category-macros.md)|
|類別初始化和清除|[物件主](ccomobjectrootex-class.md#objectmain)|

## <a name="object_entry_non_createable_ex_auto"></a><a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

可讓您指定應該註冊並初始化物件，而不應該透過 `CoCreateInstance` 從外部建立。

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>參數

*Clsid*<br/>
[在]由名為*類*的C++類實現的 COM 類的 CLSID。

*class*<br/>
[在]實現由*clsid*表示的 COM 類的 C++類的名稱。

### <a name="remarks"></a>備註

物件進入巨集會放在專案的全域範圍，以支援註冊、初始化和建立類別。

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO允許您指定應註冊和初始化物件(有關詳細資訊[,請參閱OBJECT_ENTRY_AUTO),](#object_entry_auto)但它不`CoCreateInstance`應通過 進行創建。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
