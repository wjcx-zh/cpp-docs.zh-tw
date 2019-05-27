---
title: 建立適用於 ATL 登錄器的指令碼
ms.date: 05/14/2014
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: f32606701ea08736985f0b0dd2ed82712040a049
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707063"
---
# <a name="creating-registrar-scripts"></a>建立登錄器指令碼

登錄器指令碼提供資料驅動 (而非 API 驅動) 的系統登錄存取。 資料驅動的存取通常較有效率，因為它在指令碼中只需要一或兩行，就能將機碼加入至登錄。

[ATL 控制項精靈](../atl/reference/atl-control-wizard.md)會自動為您的 COM 伺服器產生登錄器指令碼。 您可以在與物件相關聯的 .rgs 檔案中找到此指令碼。

ATL 登錄器的指令碼引擎會在執行階段處理您的登錄器指令碼。 ATL 會在伺服器設定期間自動叫用指令碼引擎。

本文涵蓋下列與登錄器指令碼相關的主題：

- [了解巴格斯格式 (BNF) 語法](../atl/understanding-backus-naur-form-bnf-syntax.md)

- [了解剖析樹狀目錄](../atl/understanding-parse-trees.md)

- [登錄指令碼範例](../atl/registry-scripting-examples.md)

- [使用可置換的參數 (登錄器的前置處理器)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [叫用指令碼](../atl/invoking-scripts.md)

## <a name="see-also"></a>另請參閱

[登錄元件 (登錄器)](../atl/atl-registry-component-registrar.md)
