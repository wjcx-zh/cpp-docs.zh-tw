---
title: C 執行階段錯誤 R6016
ms.date: 11/04/2016
f1_keywords:
- R6016
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
ms.openlocfilehash: b617e3cf6d48a24b01479ef7ef3fb6ac425b3996
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556939"
---
# <a name="c-runtime-error-r6016"></a>C 執行階段錯誤 R6016

執行緒資料空間不足

> [!NOTE]
> 如果您遇到這個錯誤訊息時執行應用程式時，應用程式已關閉因為它有內部記憶體問題。 有許多原因會造成這個錯誤，但通常增益集或應用程式使用的擴充功能中的 bug 或極低的記憶體不足，應用程式中的 bug 所造成。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 關閉其他正在執行的應用程式或重新啟動電腦以釋出記憶體。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝應用程式。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**移除，請修復或重新安裝增益集或使用應用程式的延伸模組。
> - 請檢查**Windows Update**中**控制台**軟體更新。
> - 檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。

**適用於程式設計人員的資訊**

發生這個錯誤是因為程式未收到足夠的記憶體來完成作業系統[_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md)或是`_beginthreadex`呼叫或尚未初始化本機存放區的執行緒`_beginthread`或`_beginthreadex`。

當新的執行緒啟動時，程式庫必須為執行緒建立一個內部資料庫。 當使用作業系統提供的記憶體無法展開資料庫時，執行緒就無法啟動，呼叫的處理序也會停止。 當處理序已建立過多執行緒，或是執行緒區域儲存區已用盡時，就會發生這種情形。

我們建議您呼叫 C 執行階段程式庫 (CRT) 的可執行檔應該使用`_beginthreadex`執行緒的建立，而不是 Windows API `CreateThread`。 `_beginthreadex` 會初始化執行緒區域儲存區中許多 CRT 函式所使用的內部靜態儲存區。 如果您使用 `CreateThread` 建立執行緒，則呼叫需要已初始化的內部靜態儲存區的 CRT 函式時，CRT 可能會終止處理序並發出 R6016。