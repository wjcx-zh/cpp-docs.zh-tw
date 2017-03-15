---
title: "類別巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
caps.latest.revision: 17
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 26eea5cc8ce8e18af84a9ca89e5ddc94272be44c
ms.lasthandoff: 02/24/2017

---
# <a name="category-macros"></a>類別巨集
這些巨集定義分類的對應。  
  
|||  
|-|-|  
|[BEGIN_CATEGORY_MAP](#begin_category_map)|標記類別對應的開頭。|  
|[END_CATEGORY_MAP](#end_category_map)|將類別對應的結尾的標記。|  
|[IMPLEMENTED_CATEGORY](#implemented_category)|表示 COM 物件所實作的類別。|  
|[REQUIRED_CATEGORY](#required_category)|表示容器的 COM 物件所需的類別。|  

## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  

##  <a name="a-namebegincategorymapa--begincategorymap"></a><a name="begin_category_map"></a>BEGIN_CATEGORY_MAP  
 標記類別對應的開頭。  
  
```
BEGIN_CATEGORY_MAP(theClass)
```  
  
### <a name="parameters"></a>參數  
 `theClass`  
 [in]包含類別對應之類別名稱。  
  
### <a name="remarks"></a>備註  
 類別對應用來指定哪些元件類別會實作 COM 類別，而且需要從其容器所屬的類別目錄。  
  
 新增[IMPLEMENTED_CATEGORY](#implemented_category) COM 類別所實作的每個分類的對應項目。 新增[REQUIRED_CATEGORY](#required_category)類別來實作其用戶端所需的每個分類的對應項目。 將標記與對應的結尾[END_CATEGORY_MAP](#end_category_map)巨集。  
  
 如果類別都有相關聯註冊模組時在對應中所列的元件類別也會自動註冊[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)。  
  
> [!NOTE]
>  ATL 登錄元件類別使用標準的元件類別目錄管理員。 如果註冊模組時，管理員不存在於系統上，註冊就會成功，但元件類別不會登錄為該類別。  
  
 如需元件類別的詳細資訊，請參閱[為何元件類別，以及它們是如何運作](http://msdn.microsoft.com/library/windows/desktop/ms694322)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&100;](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="a-nameendcategorymapa--endcategorymap"></a><a name="end_category_map"></a>END_CATEGORY_MAP  
 將類別對應的結尾的標記。  
  
```
END_CATEGORY_MAP()
```  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_CATEGORY_MAP](#begin_category_map)。  
  
##  <a name="a-nameimplementedcategorya--implementedcategory"></a><a name="implemented_category"></a>IMPLEMENTED_CATEGORY  
 新增`IMPLEMENTED_CATEGORY`巨集，以您的元件[類別對應](#begin_category_map)來指定它應該註冊為實作所識別的類別目錄`catID`參數。  
  
```
IMPLEMENTED_CATEGORY(catID)
```  
  
### <a name="parameters"></a>參數  
 `catID`  
 [in]A **CATID**常數或變數保留實作的類別目錄的全域唯一識別碼 (GUID)。 位址`catID`會採取並加入至地圖中。 請參閱下表中的內建類別選項。  
  
### <a name="remarks"></a>備註  
 如果類別都有相關聯註冊模組時在對應中所列的元件類別也會自動註冊[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)巨集。  
  
 用戶端可用來判斷它的功能與需求，而不需要建立它的執行個體登錄類別的類別目錄資訊。  
  
 如需元件類別的詳細資訊，請參閱[為何元件類別，以及它們是如何運作](http://msdn.microsoft.com/library/windows/desktop/ms694322)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="a-selection-of-stock-categories"></a>內建類別選項  
  
|描述|符號|登錄 GUID|  
|-----------------|------------|-------------------|  
|指令碼的安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|初始化的安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|簡單框架網站內含項目|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|簡單資料繫結|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|進階的資料繫結|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|無視窗控制項|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|可感知網際網路功能的物件|請參閱[網際網路知道物件](http://msdn.microsoft.com/library/windows/desktop/ms690561)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]範例清單。||  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&100;](../../atl/codesnippet/cpp/category-macros_1.h)]  
  
##  <a name="a-namerequiredcategorya--requiredcategory"></a><a name="required_category"></a>REQUIRED_CATEGORY  
 新增`REQUIRED_CATEGORY`巨集，以您的元件[類別對應](#begin_category_map)來指定它應該註冊為需要所識別的類別目錄`catID`參數。  
  
```
REQUIRED_CATEGORY( catID )
```  
  
### <a name="parameters"></a>參數  
 `catID`  
 [in]A **CATID**常數或變數保留所需的類別目錄的全域唯一識別碼 (GUID)。 位址`catID`會採取並加入至地圖中。 請參閱下表中的內建類別選項。  
  
### <a name="remarks"></a>備註  
 如果類別都有相關聯註冊模組時在對應中所列的元件類別也會自動註冊[OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)或[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)巨集。  
  
 用戶端可用來判斷它的功能與需求，而不需要建立它的執行個體登錄類別的類別目錄資訊。 例如，控制項可能需要一個容器，支援資料繫結。 容器可以找出是否有必要查詢，以控制所需的類別的類別目錄管理員裝載控制項的功能。 如果容器不支援某項必要的功能，它可以拒絕裝載 COM 物件。  
  
 如需有關元件的類別，包括範例清單，請參閱[為何元件類別，以及它們是如何運作](http://msdn.microsoft.com/library/windows/desktop/ms694322)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="a-selection-of-stock-categories"></a>內建類別選項  
  
|描述|符號|登錄 GUID|  
|-----------------|------------|-------------------|  
|指令碼的安全|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|  
|初始化的安全|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|  
|簡單框架網站內含項目|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|  
|簡單資料繫結|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|  
|進階的資料繫結|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|  
|無視窗控制項|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|  
|可感知網際網路功能的物件|請參閱[網際網路知道物件](http://msdn.microsoft.com/library/windows/desktop/ms690561)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]範例清單。||  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&135;](../../atl/codesnippet/cpp/category-macros_2.h)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)

