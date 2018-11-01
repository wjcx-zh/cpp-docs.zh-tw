---
title: 建立 ATL 登錄器指令碼
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: bc76e41ab0d2cd2d26ef227e6368cb420a8a6401
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480233"
---
# <a name="creating-registrar-scripts"></a>Creating Registrar Scripts

登錄器指令碼會提供資料驅動，而不是 API 驅動，存取系統登錄。 資料驅動的存取是通常更有效率，因為它需要只需要一個或兩行新增至登錄機碼的指令碼中。

[ATL 控制項精靈](../atl/reference/atl-control-wizard.md)自動產生您的 COM 伺服器的登錄器指令碼。 您可以與您的物件相關聯的.rgs 檔中找到此指令碼。

ATL 登錄器指令碼引擎會處理您的登錄器指令碼在執行階段。 ATL 自動叫用伺服器安裝期間的指令碼引擎。

本文章涵蓋登錄器指令碼與相關的下列主題：

- [了解 Backus Nauer Form (BNF) 語法](../atl/understanding-backus-nauer-form-bnf-syntax.md)

- [了解剖析樹狀目錄](../atl/understanding-parse-trees.md)

- [登錄指令碼範例](../atl/registry-scripting-examples.md)

- [使用可置換的參數 (登錄器的前置處理器)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [叫用指令碼](../atl/invoking-scripts.md)

## <a name="see-also"></a>另請參閱

[登錄元件 （登錄器）](../atl/atl-registry-component-registrar.md)

