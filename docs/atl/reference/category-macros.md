---
title: 類別宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 0db32c9550cd76fbc8e1f6776b8ecf4cceffebd7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833890"
---
# <a name="category-macros"></a>類別宏

這些宏會定義類別對應。

|巨集|描述|
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|標記類別目錄對應的開頭。|
|[END_CATEGORY_MAP](#end_category_map)|標記類別目錄對應的結尾。|
|[IMPLEMENTED_CATEGORY](#implemented_category)|指出由 COM 物件所執行的類別。|
|[REQUIRED_CATEGORY](#required_category)|表示 COM 物件所需的類別目錄。|

## <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="begin_category_map"></a><a name="begin_category_map"></a> BEGIN_CATEGORY_MAP

標記類別目錄對應的開頭。

```cpp
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
在包含分類對應之類別的名稱。

### <a name="remarks"></a>備註

類別對應是用來指定 COM 類別將執行的元件類別目錄，以及其容器所需的類別。

將 [IMPLEMENTED_CATEGORY](#implemented_category) 專案加入至 COM 類別所執行之每個類別目錄的對應中。 針對類別需要其用戶端執行的每個類別目錄，將 [REQUIRED_CATEGORY](#required_category) 專案新增至地圖。 以 [END_CATEGORY_MAP](#end_category_map) 宏標示地圖的結尾。

如果該類別有相關聯的 [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) 或 [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)，則在註冊模組時，會自動註冊對應中列出的元件類別。

> [!NOTE]
> ATL 會使用標準元件類別管理員來註冊元件類別。 如果系統管理員未在註冊模組時存在於系統上，則註冊會成功，但不會為該類別註冊元件類別。

如需元件類別的詳細資訊，請參閱 [什麼是元件類別以及它們](/windows/win32/com/component-categories-and-how-they-work) 在 Windows SDK 中的運作方式。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="end_category_map"></a><a name="end_category_map"></a> END_CATEGORY_MAP

標記類別目錄對應的結尾。

```cpp
END_CATEGORY_MAP()
```

### <a name="example"></a>範例

請參閱 [BEGIN_CATEGORY_MAP](#begin_category_map)的範例。

## <a name="implemented_category"></a><a name="implemented_category"></a> IMPLEMENTED_CATEGORY

將 IMPLEMENTED_CATEGORY 宏新增至元件的 [類別目錄對應](#begin_category_map) ，以指定它應該註冊為執行 *catID* 參數所識別的類別。

```cpp
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>參數

*catID*<br/>
在具有所實類別的全域唯一識別碼 (GUID) 的 CATID 常數或變數。 將會取得 *catID* 的位址，並將其新增至地圖。 請參閱下表以取得股票類別的選取專案。

### <a name="remarks"></a>備註

如果類別具有相關聯的 [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) 或 [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) 宏，則在註冊模組時，會自動註冊對應中列出的元件類別。

用戶端可以使用針對類別註冊的類別資訊來判斷其功能和需求，而不需要建立它的實例。

如需元件類別的詳細資訊，請參閱 [什麼是元件類別以及它們](/windows/win32/com/component-categories-and-how-they-work) 在 Windows SDK 中的運作方式。

### <a name="a-selection-of-stock-categories"></a>庫存類別的選取範圍

|描述|符號|登錄 GUID|
|-----------------|------------|-------------------|
|安全的腳本撰寫|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|安全的初始化|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|簡易框架網站內含專案|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|簡單資料繫結|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Advanced Data Binding|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|無視窗控制項|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|網際網路感知的物件|如需範例清單，請參閱 Windows SDK 中的 [網際網路感知物件](/windows/win32/com/internet-aware-objects) 。||

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="required_category"></a><a name="required_category"></a> REQUIRED_CATEGORY

將 REQUIRED_CATEGORY 宏新增至元件的 [類別目錄對應](#begin_category_map) ，以指定它應該註冊為需要由 *catID* 參數識別的類別。

```cpp
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>參數

*catID*<br/>
在具有必要類別的全域唯一識別碼 (GUID) 的 CATID 常數或變數。 將會取得 *catID* 的位址，並將其新增至地圖。 請參閱下表以取得股票類別的選取專案。

### <a name="remarks"></a>備註

如果類別具有相關聯的 [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) 或 [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) 宏，則在註冊模組時，會自動註冊對應中列出的元件類別。

用戶端可以使用針對類別註冊的類別資訊來判斷其功能和需求，而不需要建立它的實例。 例如，控制項可能需要容器支援資料系結。 如果容器具有裝載控制項所需的功能，您可以針對該控制項所需的類別查詢類別目錄管理員，以找出這項功能。 如果容器不支援必要的功能，它可能會拒絕裝載 COM 物件。

如需元件類別的詳細資訊（包括範例清單），請參閱 [什麼是元件類別以及它們](/windows/win32/com/component-categories-and-how-they-work) 在 Windows SDK 中的運作方式。

### <a name="a-selection-of-stock-categories"></a>庫存類別的選取範圍

|描述|符號|登錄 GUID|
|-----------------|------------|-------------------|
|安全的腳本撰寫|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|安全的初始化|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|簡易框架網站內含專案|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|簡單資料繫結|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Advanced Data Binding|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|無視窗控制項|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|網際網路感知的物件|如需範例清單，請參閱 Windows SDK 中的 [網際網路感知物件](/windows/win32/com/internet-aware-objects) 。||

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
