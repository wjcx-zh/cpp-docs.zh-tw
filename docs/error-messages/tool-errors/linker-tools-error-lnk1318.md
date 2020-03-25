---
title: 連結器工具錯誤 LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: a61c11a9cbb25fea6fddc0bf1c5c4c2a7af1cf4f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183575"
---
# <a name="linker-tools-error-lnk1318"></a>連結器工具錯誤 LNK1318

> 未預期的 PDB 錯誤;*原因*[*詳細資料*]

連結器在開啟、讀取或寫入 PDB 檔案時，發生未預期的錯誤。

針對 PDB 檔案中的罕見問題，會產生這個錯誤訊息。 *原因*和*詳細資料*代表失敗發生時，連結器可用的資訊。 這可能不太實用，因為處理 PDB 檔案時的常見錯誤會有個別、更具資訊性的錯誤訊息。

由於錯誤的來源並不常見，因此只有一般的建議可用來解決此問題：

- 在您的組建目錄中執行乾淨的作業，然後執行解決方案的完整組建。

- 重新開機您的電腦，或檢查 mspdbsrv.exe 是否有偏離或停止回應的處理常式，並在 TaskManager 中將其終止。

- 關閉專案目錄中的防毒程式檢查。

- 如果使用[/mp](../../build/reference/mp-build-with-multiple-processes.md)搭配 MSBuild 或另一個平行組建進程，請使用[/Zf](../../build/reference/zf.md)編譯器選項。

- 嘗試使用64位裝載工具組來建立。

- 如有需要，序列化連結以減輕平行連結問題。 這個錯誤可能是因為某個連結實例啟動 mspdbsrv.exe，而在另一個連結實例使用它來完成之前關閉。 此修正的缺點是，您的專案組建可能需要更長的時間才能完成。
