---
title: C 執行階段錯誤 R6033
ms.date: 11/04/2016
f1_keywords:
- R6033
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
ms.openlocfilehash: 39d8a20dacb0cdeb2a767529e9716bd476f406dc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467180"
---
# <a name="c-runtime-error-r6033"></a>C 執行階段錯誤 R6033

嘗試使用從原生程式碼初始化期間的這個組件的 MSIL 程式碼。 這表示您的應用程式中的 bug。 它很可能是呼叫 MSIL 編譯的結果 (/ clr) 從原生的建構函式，或從 DllMain 的函式。

> [!NOTE]
> 如果您遇到這個錯誤訊息時執行應用程式時，應用程式已關閉發生內部問題。 可能造成此錯誤，應用程式中的 bug 或增益集或延伸模組，它會使用中的 bug。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝程式。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**移除，請修復或重新安裝任何延伸模組或增益集。
> - 請檢查**Windows Update**中**控制台**軟體更新。
> - 檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。

**適用於程式設計人員的資訊**

這項診斷表示 MSIL 指示在執行期間載入器鎖定。 如果您使用 /clr 旗標編譯原生 c + +，也可能會發生。 只包含 managed 程式碼的模組上使用 /clr 旗標。 如需詳細資訊，請參閱 <<c0> [ 初始化混合組件](../../dotnet/initialization-of-mixed-assemblies.md)。