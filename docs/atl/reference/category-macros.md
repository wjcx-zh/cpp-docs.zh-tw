---
title: "類別巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
dev_langs: C++
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 752a0c0c9de5c726a106ca08a574844369c6bdc5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="category-macros"></a>類別巨集
這些巨集會定義類別目錄對應。  
  
|||  
|-|-|  
|[BEGIN_CATEGORY_MAP](#begin_category_map)|將類別對應的開頭的標記。|  
|[END_CATEGORY_MAP](#end_category_map)|標示的類別對應的結尾。|  
|[IMPLEMENTED_CATEGORY](#implemented_category)|表示 COM 物件所實作的類別。|  
|[REQUIRED_CATEGORY](#required_category)|指出容器的 COM 物件所需的類別。|  

## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  

##  <a name="begin_category_map"></a>BEGIN_CATEGORY_MAP  
 將類別對應的開頭的標記。  
  
```
BEGIN_CATEGORY_MAP(theClass)
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 [in]包含類別目錄對應的類別名稱。  
  
### <a name="remarks"></a>備註  
 分類對應用來指定哪些元件類別之 COM 類別會實作，而且需要從其容器所屬的類別目錄。  
  
 新增[IMPLEMENTED_CATEGORY](#implemented_category)要對應之 COM 類別所實作的每個類別目錄項目。 新增[REQUIRED_CATEGORY](#required_category)類別會要求其用戶端實作的每個分類的對應項目。 標記地圖的結尾[END_CATEGORY_MAP](#end_category_map)巨集。  
  
 如果類別具有相關聯，模組的註冊時對應中列出的元件類別也會自動註冊[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto).  
  
> [!NOTE]
>  ATL 登錄元件類別使用標準的元件類別目錄管理員。 如果註冊模組時，管理員不存在於系統上，註冊就會成功，但元件類別將不會註冊為該類別。  
  
 如需元件類別的詳細資訊，請參閱[為何元件類別，以及如何運作](http://msdn.microsoft.com/library/windows/desktop/ms694322)Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="end_category_map"></a>END_CATEGORY_MAP  
 標示的類別對應的結尾。  
  
```
END_CATEGORY_MAP()
```  
  
### <a name="example"></a>範例  
 請參閱範例的[BEGIN_CATEGORY_MAP](#begin_category_map)。  
  
##  <a name="implemented_category"></a>IMPLEMENTED_CATEGORY  
 新增`IMPLEMENTED_CATEGORY`巨集，以您的元件[類別對應](#begin_category_map)來指定它應該註冊為實作所識別的類別目錄`catID`參數。  
  
```
IMPLEMENTED_CATEGORY(catID)
```  
  
### <a name="parameters"></a>參數  
 `catID`  
 [in]A **CATID**常數或變數保留實作的類別目錄的全域唯一識別碼 (GUID)。 位址`catID`會採取並加入至地圖中。 請參閱下表的選取範圍的內建的分類。  
  
### <a name="remarks"></a>備註  
 如果類別具有相關聯，模組的註冊時對應中列出的元件類別也會自動註冊[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)巨集。  
  
 用戶端可用來判斷其功能與需求，而不需要建立它的執行個體註冊為類別的類別目錄資訊。  
  
 如需元件類別的詳細資訊，請參閱[為何元件類別，以及如何運作](http://msdn.microsoft.com/library/windows/desktop/ms694322)Windows SDK 中。  
  
### <a name="a-selection-of-stock-categories"></a>選取的內建類別  
  
|描述|符號|登錄的 GUID|  
|-----------------|------------|-------------------|  
|指令碼的安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|用於初始化安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|簡單的框架站台內含項目|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|簡單資料繫結|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|進階的資料繫結|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|無視窗控制項|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|可感知網際網路功能的物件|請參閱[網際網路注意物件](http://msdn.microsoft.com/library/windows/desktop/ms690561)Windows SDK 範例清單中。||  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="required_category"></a>REQUIRED_CATEGORY  
 新增`REQUIRED_CATEGORY`巨集，以您的元件[類別對應](#begin_category_map)來指定它應該註冊為需要所識別的類別目錄`catID`參數。  
  
```
REQUIRED_CATEGORY( catID )
```  
  
### <a name="parameters"></a>參數  
 `catID`  
 [in]A **CATID**常數或變數保留所需的分類的全域唯一識別碼 (GUID)。 位址`catID`會採取並加入至地圖中。 請參閱下表的選取範圍的內建的分類。  
  
### <a name="remarks"></a>備註  
 如果類別具有相關聯，模組的註冊時對應中列出的元件類別也會自動註冊[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)巨集。  
  
 用戶端可用來判斷其功能與需求，而不需要建立它的執行個體註冊為類別的類別目錄資訊。 例如，控制項可能需要一個容器，支援資料繫結。 容器可以找出是否有必要將控制項裝載藉由查詢該控制項所需的類別目錄的類別目錄管理員的功能。 如果容器不支援必要的功能，它可以拒絕裝載 COM 物件。  
  
 如需有關元件的類別，包括範例清單，請參閱[為何元件類別，以及如何運作](http://msdn.microsoft.com/library/windows/desktop/ms694322)Windows SDK 中。  
  
### <a name="a-selection-of-stock-categories"></a>選取的內建類別  
  
|描述|符號|登錄的 GUID|  
|-----------------|------------|-------------------|  
|指令碼的安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|用於初始化安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|簡單的框架站台內含項目|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|簡單資料繫結|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|進階的資料繫結|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|無視窗控制項|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|可感知網際網路功能的物件|請參閱[網際網路注意物件](http://msdn.microsoft.com/library/windows/desktop/ms690561)Windows SDK 範例清單中。||  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]  
  
## <a name="see-also"></a>請參閱  
 [巨集](../../atl/reference/atl-macros.md)
