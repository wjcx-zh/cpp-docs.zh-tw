---
title: C 執行階段錯誤 R6016
ms.date: 11/04/2016
f1_keywords:
- R6016
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
ms.openlocfilehash: 22bf4b7e8951215d1a013edb29af1ebff7517ffc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197336"
---
# <a name="c-runtime-error-r6016"></a>C 執行階段錯誤 R6016

執行緒資料空間不足

> [!NOTE]
> 如果您在執行應用程式時遇到此錯誤訊息，則應用程式已關閉，因為它有內部記憶體問題。 此錯誤有許多可能的原因，但通常是因為記憶體不足的情況、應用程式中的錯誤，或應用程式所使用之增益集或延伸中的錯誤所造成。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 關閉其他正在執行的應用程式，或重新開機您的電腦以釋放記憶體。
> - 使用 [**控制台**] 中的 [**應用程式和功能**] 或 [**程式和功能**] 頁面修復或重新安裝應用程式。
> - 使用 [**控制台**] 中的 [**應用程式和功能**] 或 [**程式和功能**] 頁面，移除、修復或重新安裝應用程式所使用的增益集或延伸模組。
> - 在 [**控制台**] 中選取 [軟體更新] **Windows Update** 。
> - 檢查應用程式的更新版本。 如果問題持續發生，請洽詢應用程式廠商。

**程式設計人員的資訊**

發生此錯誤的原因是程式未從作業系統收到足夠的記憶體來完成[_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md)或 `_beginthreadex` 呼叫，或是 `_beginthread` 或 `_beginthreadex`尚未初始化執行緒區域儲存區。

當新的執行緒啟動時，程式庫必須為執行緒建立一個內部資料庫。 當使用作業系統提供的記憶體無法展開資料庫時，執行緒就無法啟動，呼叫的處理序也會停止。 當處理序已建立過多執行緒，或是執行緒區域儲存區已用盡時，就會發生這種情形。

我們建議，呼叫 C 執行時間程式庫（CRT）的可執行檔應該使用 `_beginthreadex` 來建立執行緒，而不是 Windows API `CreateThread`。 `_beginthreadex` 會初始化執行緒區域儲存區中許多 CRT 函式所使用的內部靜態儲存區。 如果您使用 `CreateThread` 建立執行緒，則呼叫需要已初始化的內部靜態儲存區的 CRT 函式時，CRT 可能會終止處理序並發出 R6016。
