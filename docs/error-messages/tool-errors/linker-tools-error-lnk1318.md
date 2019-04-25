---
title: 連結器工具錯誤 LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: 8ed6489a27d4c0e117f7f18281ff188f40936e0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160987"
---
# <a name="linker-tools-error-lnk1318"></a>連結器工具錯誤 LNK1318

> 未預期的 PDB 錯誤;*會導致*'*詳細資料*'

連結器遇到未預期的錯誤時開啟、 讀取或寫入 PDB 檔案。

此錯誤訊息會產生 PDB 檔案中常見的問題。 *會導致*並*詳細資料*發生失敗時，代表提供的資訊給連結器。 這可能不是非常實用，為處理 PDB 檔案有不同且更具參考性的錯誤訊息時的常見錯誤。

錯誤的來源不常見，因為沒有泛型的建議可用來解決此問題：

- 在您的組建目錄中執行的清除作業，然後執行完整建置您的方案。

- 重新啟動電腦，或檢查偏離或無回應的 mspdbsrv.exe 程序並 TaskManager 中刪除它們。

- 關閉您的專案目錄中的防毒檢查。

- 使用[/Zf](../../build/reference/zf.md)編譯器選項，如果使用[/MP](../../build/reference/mp-build-with-multiple-processes.md) MSBuild 或另一個平行建置程序。

- 嘗試建置使用 64 位元裝載工具組。

- 將序列化連結來減少平行連結問題，如有需要。 可能造成此錯誤，如果 mspdbsrv.exe 由一個執行個體的連結，啟動和關機之後完成連結的另一個執行個體，才能使用它。 此修正的缺點是您專案的組建可能需要很長的時間才能完成。