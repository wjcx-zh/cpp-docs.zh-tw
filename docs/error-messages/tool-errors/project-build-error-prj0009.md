---
title: 專案建置錯誤 PRJ0009
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: 963b7c861f9e8ee7105ebdc23afff08c4be46465
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438083"
---
# <a name="project-build-error-prj0009"></a>專案建置錯誤 PRJ0009

建置記錄檔無法開啟進行寫入。

**請確定檔案未開啟另一個處理序，並沒有寫入保護。**

在設定後**建置記錄**屬性設**是**和執行在建置或重建，Visual c + + 無法開啟組建記錄檔以獨佔模式。

檢查**建置記錄**開啟設定**選項**] 對話方塊中 (在**工具**功能表上，按一下 [**選項**命令)，然後選取**VC + + 組建**中**專案**資料夾。 組建檔案稱為 BuildLog.htm，並寫入至中繼目錄 $(IntDir)。

此錯誤的可能原因：

- 您是執行中的 Visual c + + 的兩個處理序，並且想要同時建置的相同專案中都相同的組態。

- 組建記錄檔會鎖定檔案的處理序中開啟。

- 使用者沒有建立檔案的權限。

- 目前的使用者沒有寫入權限 BuildLog.htm 檔案。