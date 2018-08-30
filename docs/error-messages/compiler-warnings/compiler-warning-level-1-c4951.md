---
title: 編譯器警告 （層級 1） C4951 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e26c4bc176a54f063a3f9bce2faf451a9c0406f0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204231"
---
# <a name="compiler-warning-level-1-c4951"></a>編譯器警告 (層級 1) C4951

> '*函式*' 已經編輯，因為已收集的分析資料，未使用的函式設定檔資料

已將輸入模組中的函式編輯為 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)，因此現在您的設定檔資料無效。 輸入的模組已重新編譯後 **/ltcg: pginstrument**的函式 (*函式*) 的當時模組中的控制流程不同 **/ltcg: pginstrument**作業。

這個警告僅供參考。 若要解決這個警告，請執行 **/LTCG:PGINSTRUMENT**，再取消復原所有測試回合，並執行 **/LTCG:PGOPTIMIZE**。

如果已使用 **/LTCG:PGOPTIMIZE** ，則這個警告會變成錯誤。