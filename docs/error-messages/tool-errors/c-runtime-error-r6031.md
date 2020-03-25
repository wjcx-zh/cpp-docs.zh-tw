---
title: C 執行階段錯誤 R6031
ms.date: 11/04/2016
f1_keywords:
- R6031
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
ms.openlocfilehash: 4b75b0855f0f0d60304cfe8b7a00b4ce27a8daab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197102"
---
# <a name="c-runtime-error-r6031"></a>C 執行階段錯誤 R6031

嘗試多次初始化 CRT。 這表示您的應用程式中有錯誤。

> [!NOTE]
> 如果您在執行應用程式時遇到此錯誤訊息，則應用程式已關閉，因為它有內部問題。 這可能是應用程式中的錯誤，或應用程式所使用之附加元件或延伸模組中的 bug 所造成。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 使用 [**控制台**] 中的 [**應用程式和功能**] 或 [**程式和功能**] 頁面修復或重新安裝程式。
> - 使用 [**控制台**] 中的 [**應用程式和功能**] 或 [**程式和功能**] 頁面，移除、修復或重新安裝應用程式所使用的任何附加元件或擴充程式。
> - 在 [**控制台**] 中選取 [軟體更新] **Windows Update** 。
> - 檢查應用程式的更新版本。 如果問題持續發生，請洽詢應用程式廠商。

**程式設計人員的資訊**

此診斷表示 MSIL 指令在載入器鎖定期間執行。 如需詳細資訊，請參閱[混合元件的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。
