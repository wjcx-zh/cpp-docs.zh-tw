---
title: 類別巨集
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 1d8bbae4608aa661bbc612604f7d85855f325f5f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321603"
---
# <a name="category-macros"></a>類別巨集

這些宏定義類別映射。

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|標記類別映射的開頭。|
|[END_CATEGORY_MAP](#end_category_map)|標記類別映射的末尾。|
|[IMPLEMENTED_CATEGORY](#implemented_category)|指示由 COM 物件實現的類別。|
|[REQUIRED_CATEGORY](#required_category)|指示 COM 物件需要容器的類別。|

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="begin_category_map"></a><a name="begin_category_map"></a>BEGIN_CATEGORY_MAP

標記類別映射的開頭。

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>參數

*類別*<br/>
[在]包含類別映射的類的名稱。

### <a name="remarks"></a>備註

類別映射用於指定 COM 類將實現哪些元件類別,以及它需要從容器中實現哪些類別。

為 COM 類別實現的每個類別向地圖添加[IMPLEMENTED_CATEGORY](#implemented_category)條目。 為類要求其客戶端實現的每個類別向地圖添加[REQUIRED_CATEGORY](#required_category)項。 使用[END_CATEGORY_MAP](#end_category_map)宏標記地圖的末尾。

如果類具有關聯的[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO,](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)則映射中列出的元件類別將在註冊模組時自動註冊。

> [!NOTE]
> ATL 使用標準元件類別管理器來註冊元件類別。 如果在註冊模組時管理器不存在,則註冊成功,但不會為該類註冊元件類別。

有關元件類別的詳細資訊,請參閱[什麼是元件類別及其](/windows/win32/com/component-categories-and-how-they-work)在 Windows SDK 中的工作方式。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="end_category_map"></a><a name="end_category_map"></a>END_CATEGORY_MAP

標記類別映射的末尾。

```
END_CATEGORY_MAP()
```

### <a name="example"></a>範例

請參閱[BEGIN_CATEGORY_MAP](#begin_category_map)的示例。

## <a name="implemented_category"></a><a name="implemented_category"></a>IMPLEMENTED_CATEGORY

向元件的[類別映射](#begin_category_map)添加IMPLEMENTED_CATEGORY宏,以指定應將其註冊為實現*catID*參數標識的類別。

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>參數

*卡特ID*<br/>
[在]持有已實現類別全域唯一標識符 (GUID) 的 CATID 常量或變數。 *catID*的位址將被獲取並添加到地圖中。 有關股票類別的選擇,請參閱下表。

### <a name="remarks"></a>備註

如果類具有關聯的[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏,則在註冊模組時,將自動註冊地圖中列出的元件類別。

用戶端可以使用為類註冊的類別資訊來確定其功能和要求,而無需創建該類的實例。

有關元件類別的詳細資訊,請參閱[什麼是元件類別及其](/windows/win32/com/component-categories-and-how-they-work)在 Windows SDK 中的工作方式。

### <a name="a-selection-of-stock-categories"></a>類別類別的選擇

|描述|符號|註冊處|
|-----------------|------------|-------------------|
|腳本|CATID_SafeForScripting|[7DD95801-9882-11CF-9FA9-00A06C42C4]|
|安全初始化|CATID_SafeForInitializing|[7DD95802-9882-11CF-9FA9-00A06C42C4]|
|簡單的框架網站包含|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00A06C8166}|
|簡單資料繫結|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00A06C8166}|
|進階資料繫結|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00A06C8166}|
|無視窗控制項|CATID_WindowlessObject|[1D06B600-3AE3-11cf-87B9-00A06C8166]|
|網際網路感知物件|有關範例清單,請參閱 Windows SDK 中的[Internet 感知物件](/windows/win32/com/internet-aware-objects)。||

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="required_category"></a><a name="required_category"></a>REQUIRED_CATEGORY

將REQUIRED_CATEGORY宏添加到元件的[類別映射](#begin_category_map)中,以指定應將其註冊為需要*catID*參數標識的類別。

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>參數

*卡特ID*<br/>
[在]CATID 常量或變數,用於保存所需類別的全域唯一標識符 (GUID)。 *catID*的位址將被獲取並添加到地圖中。 有關股票類別的選擇,請參閱下表。

### <a name="remarks"></a>備註

如果類具有關聯的[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)宏,則在註冊模組時,將自動註冊地圖中列出的元件類別。

用戶端可以使用為類註冊的類別資訊來確定其功能和要求,而無需創建該類的實例。 例如,控制項可能要求容器支援數據綁定。 容器可以通過查詢該控制件所需的類別管理員來瞭解其是否具有承載控制項所需的功能。 如果容器不支援所需的功能,它可以拒絕承載 COM 物件。

有關元件類別(包括示例清單)的詳細資訊,請參閱[什麼是元件類別及其](/windows/win32/com/component-categories-and-how-they-work)在 Windows SDK 中的工作方式。

### <a name="a-selection-of-stock-categories"></a>類別類別的選擇

|描述|符號|註冊處|
|-----------------|------------|-------------------|
|腳本|CATID_SafeForScripting|[7DD95801-9882-11CF-9FA9-00A06C42C4]|
|安全初始化|CATID_SafeForInitializing|[7DD95802-9882-11CF-9FA9-00A06C42C4]|
|簡單的框架網站包含|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00A06C8166}|
|簡單資料繫結|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00A06C8166}|
|進階資料繫結|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00A06C8166}|
|無視窗控制項|CATID_WindowlessObject|[1D06B600-3AE3-11cf-87B9-00A06C8166]|
|網際網路感知物件|有關範例清單,請參閱 Windows SDK 中的[Internet 感知物件](/windows/win32/com/internet-aware-objects)。||

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
