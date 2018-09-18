---
title: 物件對應巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
dev_langs:
- C++
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b85d157cd6124bb0ef6e6167a415c018e14b046
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040436"
---
# <a name="object-map-macros"></a>物件對應巨集

這些巨集會定義物件的對應和項目。

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|可讓您指定的類別物件的文字描述，將輸入的物件對應。|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|物件對應中輸入的 ATL 物件，更新登錄中，並建立物件的執行個體。|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|可讓您指定應該註冊並初始化物件，而不應該透過 `CoCreateInstance` 從外部建立。|  

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="declare_object_description"></a>  DECLARE_OBJECT_DESCRIPTION

可讓您指定您的類別物件的文字描述。

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>參數

*x*<br/>
[in]類別物件的描述。

### <a name="remarks"></a>備註

ATL 物件對應到輸入這項描述[OBJECT_ENTRY_AUTO](#object_entry_auto)巨集。

實作 DECLARE_OBJECT_DESCRIPTION`GetObjectDescription`函式，可用來覆寫[CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription)方法。  

`GetObjectDescription`函式會呼叫`IComponentRegistrar::GetComponents`。 `IComponentRegistrar` 是一種自動化的介面，可讓您註冊和取消註冊 DLL 中的個別元件。 當您建立的支援元件登錄器物件使用 ATL 專案精靈 時，精靈會自動實作`IComponentRegistrar`介面。 `IComponentRegistrar` 通常會使用 Microsoft Transaction Server。

如需 ATL 專案精靈 的詳細資訊，請參閱文章[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

##  <a name="object_entry_auto"></a>  OBJECT_ENTRY_AUTO

物件對應中輸入的 ATL 物件，更新登錄中，並建立物件的執行個體。

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>參數

*clsid*<br/>
[in]藉由將名為的 c + + 類別的 COM 類別的 CLSID*類別*。

*class*<br/>
[in]實作所表示的 COM 類別的 c + + 類別名稱*clsid*。

### <a name="remarks"></a>備註

物件進入巨集會放在專案的全域範圍，以支援註冊、初始化和建立類別。

OBJECT_ENTRY_AUTO 進入函式指標的建立者類別和類別 factory 建立者類別`CreateInstance`自動產生 ATL 物件對應到這個物件的函式。 當[CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver)是呼叫，更新系統登錄的物件對應中每個物件。  

下表描述如何加入物件對應的資訊取自第二個參數給這個巨集的類別。

|資訊|取自|
|---------------------|-------------------|
|COM 註冊|[登錄巨集](../../atl/reference/registry-macros.md)|
|類別處理站的建立|[Class Factory 巨集](../../atl/reference/aggregation-and-class-factory-macros.md)|
|建立執行個體|[彙總巨集](../../atl/reference/aggregation-and-class-factory-macros.md)|
|元件類別註冊|[分類巨集](../../atl/reference/category-macros.md)|
|類別層級初始化和清除|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

##  <a name="object_entry_non_createable_ex_auto"></a>  OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

可讓您指定應該註冊並初始化物件，而不應該透過 `CoCreateInstance` 從外部建立。

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>參數

*clsid*<br/>
[in]藉由將名為的 c + + 類別的 COM 類別的 CLSID*類別*。

*class*<br/>
[in]實作所表示的 COM 類別的 c + + 類別名稱*clsid*。

### <a name="remarks"></a>備註

物件進入巨集會放在專案的全域範圍，以支援註冊、初始化和建立類別。

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO 可讓您指定應該註冊並初始化物件 (請參閱[OBJECT_ENTRY_AUTO](#object_entry_auto)如需詳細資訊)，但它不應該可透過建立`CoCreateInstance`。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
