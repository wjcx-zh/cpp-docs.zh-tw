---
title: 使用可置換的參數 （ATL 登錄器）
ms.date: 11/04/2016
f1_keywords:
- AddReplacement
- ClearReplacements
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: c820307ecb0e7fbfe5cce7cd579ff46eb1f3a0f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588184"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>使用可置換的參數 (在註冊機構&#39;s 前置處理器)

可置換的參數允許註冊機構的用戶端，來指定執行階段資料。 若要這樣做，註冊機構會維護取代對應至其中進入您的指令碼可置換的參數相關聯的值。 在註冊機構會讓這些項目，在執行階段。

##  <a name="_atl_using_.25.module.25"></a> 使用 %模組

[ATL 控制項精靈](../atl/reference/atl-control-wizard.md)會自動產生的指令碼使用`%MODULE%`。 ATL 會使用此可置換的參數，您的伺服器 DLL 或 EXE 的實際位置。

## <a name="concatenating-run-time-data-with-script-data"></a>串連指令碼資料的執行階段的資料

前置處理器的另一個用途是要串連的指令碼資料的執行階段資料。 例如，假設 需要的項目包含的模組，以字串的完整路徑"`, 1`"附加在結尾。 首先，定義下列的擴充：

```
'MySampleKey' = s '%MODULE%, 1'
```

然後，之前呼叫其中一個處理方法中所列的指令碼[叫用指令碼](../atl/invoking-scripts.md)，新增至對應的替代項目：

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

在指令碼剖析，註冊機構會展開`'%MODULE%, 1'`至`c:\mycode\mydll.dll, 1`。

> [!NOTE]
>  登錄器指令碼中 4k 是權杖的大小上限。 （語彙基元是任何可辨識的項目語法中）。這包括建立或由前置處理器展開的權杖。

> [!NOTE]
>  若要取代取代值，在執行階段，呼叫的指令碼中移除[DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource)或是[DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid)巨集。 相反地，它取代您自己`UpdateRegistry`呼叫的方法[CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced)或是[CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)，並傳遞您的 _ATL_REGMAP_ 的陣列項目結構。 _ATL_REGMAP_ENTRY 您陣列必須有至少一個項目設為 {NULL，NULL}，且此項目應永遠為最後一個項目。 否則，將會發生存取違規錯誤時產生`UpdateRegistryFromResource`呼叫。

> [!NOTE]
>  ATL 建置專案時，會輸出可執行檔，會自動將建立在執行階段使用的路徑名稱周圍加上引號 **%模組 %** 登錄器指令碼參數。 如果您不想要加上引號的路徑名稱，使用新**MODULE_RAW %** 參數改。
>
>  建置專案時，將輸出 DLL，ATL 會不加上引號的路徑名稱若**模組 %** 或是**MODULE_RAW %** 用。

## <a name="see-also"></a>另請參閱

[建立登錄器指令碼](../atl/creating-registrar-scripts.md)

