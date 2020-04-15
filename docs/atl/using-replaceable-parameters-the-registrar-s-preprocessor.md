---
title: 使用可更換參數 (ATL 註冊器)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 2474db2de384baa9113ed39aef4d3d9c9048903d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329222"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>使用可取代參數(註冊器&#39;預處理器)

可替換參數允許註冊器的用戶端指定運行時數據。 為此,註冊器維護一個替換映射,在其中輸入與腳本中可替換參數關聯的值。 註冊器在運行時進行這些條目。

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>使用 %MODULE%

[ATL 控制精靈](../atl/reference/atl-control-wizard.md)會自動生成`%MODULE%`使用的腳本。 ATL 使用此可替換參數來定位伺服器的 DLL 或 EXE 的實際位置。

## <a name="concatenating-run-time-data-with-script-data"></a>將執行時資料與文稿資料串聯

預處理器的另一個用途是將運行時數據與腳本數據串聯。 例如,假設需要一個條目,其中包含一個包含一個完整路徑的模組,末尾附加`, 1`了字串"""。 首先,定義以下延伸:

```
'MySampleKey' = s '%MODULE%, 1'
```

然後,在調用引[言 文稿](../atl/invoking-scripts.md)列出的文稿處理方法之一之前,向地圖添加替換:

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

在分析文稿期間,註冊器將`'%MODULE%, 1'``c:\mycode\mydll.dll, 1`延伸到 。

> [!NOTE]
> 在註冊器腳本中,4K 是最大令牌大小。 (令牌是語法中的任何可識別元素。這包括由預處理器創建或擴展的權杖。

> [!NOTE]
> 在執行時替換替換值,請刪除文本中對[DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid)宏的調用。 相反,請用調用`UpdateRegistry` [CAtlModule::更新註冊表從資源D](../atl/reference/catlmodule-class.md#updateregistryfromresourced)或[CAtlModule::更新註冊表從資源S](../atl/reference/catlmodule-class.md#updateregistryfromresources)替換它,並傳遞_ATL_REGMAP_ENTRY結構的陣列。 _ATL_REGMAP_ENTRY陣列必須至少有一個設置為 [NULL, NULL] 的條目,並且此條目應始終是最後一個條目。 否則,在調用時`UpdateRegistryFromResource`將生成訪問衝突錯誤。

> [!NOTE]
> 編譯輸出執行檔的項目時,ATL 會自動在執行時建立的路徑名稱周圍使用 **%MODULE%** 註冊器腳本參數添加引號。 若您要指定 **%MODULE_RAW%s 參數**。
>
> 產生輸出 DLL 的項目時,如果使用 **%MODULE%** 或 **%MODULE_RAW%,ATL**將不會向路徑名稱添加引號。

## <a name="see-also"></a>另請參閱

[建立註冊器文稿](../atl/creating-registrar-scripts.md)
