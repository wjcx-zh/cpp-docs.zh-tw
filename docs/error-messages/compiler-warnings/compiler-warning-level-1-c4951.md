---
title: 編譯器警告 (層級 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: 73e048aeaa044c35e09539b07d51398829a0fdfd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617853"
---
# <a name="compiler-warning-level-1-c4951"></a>編譯器警告 (層級 1) C4951

> '*函式*' 已經編輯，因為已收集的分析資料，未使用的函式設定檔資料

已將輸入模組中的函式編輯為 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)，因此現在您的設定檔資料無效。 輸入模組在 **/LTCG:PGINSTRUMENT** 之後已重新編譯，且相較於 */LTCG:PGINSTRUMENT*作業當時模組中的控制流程，輸入模組的函式 ( **function** ) 的控制流程不同。

這個警告僅供參考。 若要解決這個警告，請執行 **/LTCG:PGINSTRUMENT**，再取消復原所有測試回合，並執行 **/LTCG:PGOPTIMIZE**。

如果已使用 **/LTCG:PGOPTIMIZE** ，則這個警告會變成錯誤。