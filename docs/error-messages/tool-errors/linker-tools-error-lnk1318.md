---
title: 連結器工具錯誤 LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: cce2c03783039a62b5cb6f60ecf8d76b23589483
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446697"
---
# <a name="linker-tools-error-lnk1318"></a>連結器工具錯誤 LNK1318

> 未預期的 PDB 錯誤;*原因*[*詳細資料*]

連結器在開啟、讀取或寫入 PDB 檔案時，發生未預期的錯誤。

針對 PDB 檔案中的罕見問題，會產生這個錯誤訊息。 *原因*和*詳細資料*代表失敗發生時，連結器可用的資訊。 這可能不太實用，因為處理 PDB 檔案時的常見錯誤會有個別、更具資訊性的錯誤訊息。

由於錯誤的來源並不常見，因此只有一般的建議可用來解決此問題：

- 在您的組建目錄中執行乾淨的作業，然後執行解決方案的完整組建。

- 重新開機您的電腦，或檢查 mspdbsrv.exe 進程的偏離或無回應，並在 TaskManager 中將其終止。

- 關閉專案目錄中的防毒程式檢查。

- 如果使用[/mp](../../build/reference/mp-build-with-multiple-processes.md)搭配 MSBuild 或另一個平行組建進程，請使用[/Zf](../../build/reference/zf.md)編譯器選項。

- 嘗試使用64位裝載工具組來建立。

- 如有需要，序列化連結以減輕平行連結問題。 如果某個連結實例啟動 mspdbsrv.exe，就會導致此錯誤，並在使用它的另一個連結實例完成之前關閉。 此修正的缺點是，您的專案組建可能需要更長的時間才能完成。
