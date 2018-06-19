---
title: 使用可置換的參數 （ATL 登錄器） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AddReplacement
- ClearReplacements
dev_langs:
- C++
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91deabfd14d89c4a26384a14445fc51edbb3ac94
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362280"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>使用可置換的參數 (在註冊機構&#39;s 前置處理器)
可置換的參數允許註冊機構的用戶端指定執行階段資料。 若要這樣做，請在註冊機構會維護所在進入指令碼中可置換的參數相關聯的值取代對應。 在註冊機構會讓這些項目，在執行階段。  
  
##  <a name="_atl_using_.25.module.25"></a> 使用 %模組  
 [ATL 控制項精靈](../atl/reference/atl-control-wizard.md)會自動產生的指令碼使用`%MODULE%`。 ATL 實際伺服器的 DLL 或 EXE 的位置，使用這個可取代參數。  
  
## <a name="concatenating-run-time-data-with-script-data"></a>串連執行階段資料與指令碼資料  
 前置處理器的另一個用途是串連執行階段資料與指令碼資料。 例如，假設項目所包含的模組使用字串的完整路徑"`, 1`"附加結尾。 首先，定義下列擴充：  
  
```  
'MySampleKey' = s '%MODULE%, 1'  
```  
  
 然後，之前呼叫其中一個指令碼處理中所列方法[叫用指令碼](../atl/invoking-scripts.md)，新增至對應的取代：  
  
 [!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]  
  
 在剖析期間指令碼的註冊機構會展開`'%MODULE%, 1'`至`c:\mycode\mydll.dll, 1`。  
  
> [!NOTE]
>  登錄器指令碼，在 4 K 是語彙基元的大小上限。 （語彙基元是任何可辨識的項目語法中）。這包括建立或由前置處理器擴充的語彙基元。  
  
> [!NOTE]
>  在執行階段取代值，呼叫的指令碼中移除[DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid)巨集。 相反地，它取代成您自己`UpdateRegistry`方法呼叫[CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)，並傳遞您陣列的 **_ATL_REGMAP_ENTRY**結構。 您的陣列 **_ATL_REGMAP_ENTRY**必須有至少一個項目設為 {**NULL**，**NULL**}，且此項目應永遠為最後一個項目。 否則，將會發生存取違規錯誤時產生**UpdateRegistryFromResource**呼叫。  
  
> [!NOTE]
>  ATL 建置時，會輸出可執行檔專案，會自動新增以引號括住的路徑名稱，建立在執行階段使用 **%模組 %** 登錄器指令碼參數。 如果您不想要加上引號的路徑名稱，使用新 **%module_raw**參數改為。  
>   
>  建置時將輸出 DLL 的專案，ATL 會不加上引號的路徑名稱如果 **%模組 %** 或 **%module_raw**用。  
  
## <a name="see-also"></a>另請參閱  
 [建立登錄器指令碼](../atl/creating-registrar-scripts.md)

