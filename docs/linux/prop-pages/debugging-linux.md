---
title: 偵錯工具屬性 (Linux C++) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
ms.openlocfilehash: bebee7a2b3bcfd880a538acae35c9616b3b1bd46
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "79446173"
---
# <a name="c-debugging-properties-linux-c"></a>C++ 偵錯工具屬性 (Linux C++)

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range=">=vs-2017"

| 屬性 | 描述 | Choices |
|--|--|--|
| 遠端偵錯電腦 | **Visual Studio 2019 版本 16.1**: 指定要除錯程式的電腦。 可能與 [一般](general-linux.md) 頁面上所指定的遠端組建電腦不同。 您可以使用**工具** > **選項** > **跨平台** > **連接管理員**添加或編輯目標機器連接。 |
| 啟動前命令 | 在偵錯工具開始前於殼層執行的命令，可用來影響偵錯環境。 |
| 程式 | 遠端系統上要進行偵錯之程式的完整路徑。 若保留空白或未變更，則預設為目前的專案輸出。 |
| 程式引數 | 要傳遞到正在偵錯之程式的命令列引數。 |
| 工作目錄 | 遠端應用程式的工作目錄。 預設為使用者主目錄。 |
| 其他偵錯工具命令 | 要讓偵錯工具在開始偵錯之前執行的其他 `gdb` 命令。 |
| 偵錯工具連接埠號碼 | 用來與遠端偵錯工具進行偵錯工具通訊的連接埠號碼。 連接埠號碼不得已經用於本機。 此值必須為正數，且介於 1 到 65535 之間。 如未提供，則會使用可用的連接埠號碼。 |
| 遠端偵錯工具連接埠號碼 | 遠端偵錯工具伺服器 `gdbserver` 在遠端系統上接聽的連接埠號碼。 連接埠號碼不得已經用於遠端系統。 此值必須為正數，且介於 1 到 65535 之間。 如未提供，則會使用 4444 之後的可用連接埠號碼。 |
| 偵錯模式 | 指定偵錯工具與 `gdb` 的互動方式。 在「gdb 模式」** 中，偵錯工具會在遠端系統上將 `gdb` 帶往殼層。 在*gdbserver*`gdb`模式下,在本地`gdbserver`運行並 連接到遠端運行。 | **gdbserver**<br/>**Gdb** |
| 其他符號搜尋路徑 | 偵錯符號的其他搜尋路徑 (solib-search-path)。 |
| 偵錯子處理序 | 指定是否要啟用子處理序的偵錯。 |
| 啟用 Python 美化顯示 | 啟用運算式值的美化顯示。 只有 gdb 偵錯模式中支援。 |
| 視覺效果檔案 | 預設的原生視覺效果檔案 (.natvis)，包含 SLT 類型的視覺效果指示詞。 其他屬於目前解決方案的 .natvis 檔案則會自動載入。 |
| 其他來源檔案路徑對應 | 偵錯工具將 Windows 來源檔案名稱對應至 Linux 來源檔案名稱時，所使用的其他對等路徑。 格式為 "\<windows-path>=\<linux-path>;..."。 將會參考位在 Windows 路徑下的來源檔案名稱，就好像它位在 Linux 路徑下的相同相對位置中一樣。 在本機專案中找到的檔案不需要額外對應。 |

::: moniker-end
