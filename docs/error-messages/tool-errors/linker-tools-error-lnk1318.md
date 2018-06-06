---
title: 連結器工具錯誤 LNK1318 |Microsoft 文件
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1318
dev_langs:
- C++
helpviewer_keywords:
- LNK1318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 364c819c6ec2bf6e1195011eced6e6ad1699877b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570687"
---
# <a name="linker-tools-error-lnk1318"></a>連結器工具錯誤 LNK1318

> 未預期的 PDB 錯誤;*導致*'*詳細資料*'

連結器發生未預期的錯誤時開啟、 讀取或寫入 PDB 檔案。

這則錯誤訊息會產生 PDB 檔案中不常發生的問題。 *導致*和*詳細資料*發生失敗時，代表提供的資訊給連結器。 這可能不是非常實用，做為處理 PDB 檔案有不同、 更具資訊性的錯誤訊息時的常見錯誤。

錯誤的來源是很常見，因為沒有一般建議僅可用於解決此問題：

- 在您的組建目錄中執行的清除作業，然後執行 完整建置您的方案。

- 重新啟動電腦，或檢查偏離或無回應 mspdbsrv.exe 處理程序並 TaskManager 中刪除它們。

- 關閉專案目錄中的防毒檢查。

- 使用[/Zf](../../build/reference/zf.md)編譯器選項，如果使用[/MP](../../build/reference/mp-build-with-multiple-processes.md) MSBuild，或另一個平行建置程序。

- 使用 64 位元裝載工具組，請嘗試建置。

- 序列化連結視消除平行連結問題。 如果 mspdbsrv.exe 由一個執行個體的連結，啟動和關機之後才能完成另一個執行個體的連結，可能會造成這個錯誤使用它。 此修正的缺點是您專案的組建可能需要很長的時間才能完成。