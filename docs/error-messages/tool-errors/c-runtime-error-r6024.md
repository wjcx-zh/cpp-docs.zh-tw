---
title: C 執行階段錯誤 R6024
ms.date: 11/04/2016
f1_keywords:
- R6024
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
ms.openlocfilehash: de89d2e9e2b34f40b906a5dacca4179eade23f7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197193"
---
# <a name="c-runtime-error-r6024"></a>C 執行階段錯誤 R6024

空間不足，無法 _onexit/atexit 資料表

> [!NOTE]
> 如果您在執行應用程式時遇到此錯誤訊息，則應用程式已關閉，因為它有內部記憶體問題。 這個錯誤通常是因為記憶體不足的狀況，或很少是程式中的 bug 或它所使用的視覺C++程式庫損毀所造成。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 關閉其他正在執行的應用程式，或重新開機您的電腦以釋放記憶體。
> - 使用 [**控制台**] 中的 [**應用程式和功能**] 或 [**程式和功能**] 頁面修復或重新安裝程式。
> - 使用 [**控制台**] 中的 [**應用程式和功能**] 或 [**程式和功能**] 頁面，修復或重新安裝C++ Microsoft Visual 可轉散發套件的所有複本。
> - 在 [**控制台**] 中選取 [軟體更新] **Windows Update** 。
> - 檢查應用程式的更新版本。 如果問題持續發生，請洽詢應用程式廠商。

**程式設計人員的資訊**

發生這個錯誤的原因是 `_onexit` 或 `atexit` 函數沒有可用的記憶體。 這個錯誤是因為記憶體不足的狀況所造成。 您可以考慮在應用程式啟動時預先配置緩衝區，以協助儲存使用者資料，並在記憶體不足的情況下執行全新的應用程式結束。
