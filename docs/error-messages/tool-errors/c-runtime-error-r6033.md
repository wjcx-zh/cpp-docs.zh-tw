---
title: C 執行階段錯誤 R6033
ms.date: 11/04/2016
f1_keywords:
- R6033
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
ms.openlocfilehash: 86ac98a2635975b811c7b50020e4d4782675ae4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197013"
---
# <a name="c-runtime-error-r6033"></a>C 執行階段錯誤 R6033

在機器碼初始化期間，嘗試在此元件中使用 MSIL 程式碼。 這表示您的應用程式中有錯誤。 最可能的結果是從原生的函式或 DllMain 呼叫 MSIL 編譯（/clr）函數。

> [!NOTE]
> 如果您在執行應用程式時遇到此錯誤訊息，則應用程式已關閉，因為它有內部問題。 此錯誤可能是應用程式中的 bug，或其所使用之增益集或延伸中的 bug 所造成。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 使用 [**控制台**] 中的 [**應用程式和功能**] 或 [**程式和功能**] 頁面修復或重新安裝程式。
> - 使用 [**控制台**] 中的 [**應用程式和功能**] 或 [**程式和功能**] 頁面，移除、修復或重新安裝任何延伸模組或增益集。
> - 在 [**控制台**] 中選取 [軟體更新] **Windows Update** 。
> - 檢查應用程式的更新版本。 如果問題持續發生，請洽詢應用程式廠商。

**程式設計人員的資訊**

此診斷表示 MSIL 指令在載入器鎖定期間執行。 如果您使用/clr 旗標編譯了C++ native，就可能發生這種情況。 只在包含 managed 程式碼的模組上使用/clr 旗標。 如需詳細資訊，請參閱[混合元件的初始化](../../dotnet/initialization-of-mixed-assemblies.md)。
