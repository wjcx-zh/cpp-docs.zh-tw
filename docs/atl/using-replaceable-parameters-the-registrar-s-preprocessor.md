---
title: 使用可取代的參數（ATL 註冊機構）
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: debbccea5836fa63282b62ff87573160069fb169
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168679"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>使用可取代的參數（註冊機構&#39;s 預處理器）

可取代的參數允許註冊機構的用戶端指定執行時間資料。 為此，註冊機構會維護一個取代對應，在其中輸入與您的腳本中可取代參數相關聯的值。 註冊機構會在執行時間建立這些專案。

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>使用% MODULE%

[ATL 控制項嚮導](../atl/reference/atl-control-wizard.md)會自動產生使用`%MODULE%`的腳本。 ATL 會針對您伺服器的 DLL 或 EXE 的實際位置使用這個可取代的參數。

## <a name="concatenating-run-time-data-with-script-data"></a>使用腳本資料串連執行時間資料

預處理器的另一種用法是將執行時間資料與腳本資料串連在一起。 例如，假設需要一個專案，其中包含在結尾附加字串 "`, 1`" 之模組的完整路徑。 首先，定義下列擴充：

```rgs
'MySampleKey' = s '%MODULE%, 1'
```

然後，在呼叫叫用[腳本](../atl/invoking-scripts.md)中所列的其中一個腳本處理方法之前，新增對應的取代：

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

在剖析腳本期間，註冊機構會展開`'%MODULE%, 1'`至。 `c:\mycode\mydll.dll, 1`

> [!NOTE]
> 在註冊機構腳本中，4K 是 token 大小的上限。 （Token 是語法中任何可辨識的元素）。這包括預處理器所建立或擴充的權杖。

> [!NOTE]
> 若要在執行時間取代取代值，請移除腳本中對[DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid)宏的呼叫。 相反地，請將它取代`UpdateRegistry`為您自己的方法，它會呼叫[CAtlModule：： UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced)或[CAtlModule：： UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)，並傳遞 _ATL_REGMAP_ENTRY 結構的陣列。 您的 _ATL_REGMAP_ENTRY 陣列至少必須有一個設定為 {Null，Null} 的專案，而此專案應一律為最後一個專案。 否則，當呼叫時`UpdateRegistryFromResource` ，將會產生存取違規錯誤。

> [!NOTE]
> 建立輸出可執行檔的專案時，ATL 會自動在執行時間使用 **% MODULE%** 註冊機構腳本參數建立的路徑名稱前後加上引號。 如果您不想要路徑名稱包含引號，請改用新的 **% MODULE_RAW%** 參數。
>
> 建立輸出 DLL 的專案時，如果使用 **% MODULE%** 或 **% MODULE_RAW%** ，ATL 將不會在路徑名稱加上引號。

## <a name="see-also"></a>另請參閱

[建立註冊機構腳本](../atl/creating-registrar-scripts.md)
