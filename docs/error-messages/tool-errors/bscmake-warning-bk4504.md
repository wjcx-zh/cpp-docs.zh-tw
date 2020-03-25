---
title: BSCMAKE 警告 BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 57858827439ac8cc11e3718d7a484124ae8a6d74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197440"
---
# <a name="bscmake-warning-bk4504"></a>BSCMAKE 警告 BK4504

檔案包含太多參考;忽略此來源的進一步參考

.cpp 檔包含 64,000 個以上的符號參考。 當 BSCMAKE 在檔案中遇到 64,000 個參考，會忽略所有進一步的參考。

若要修正這個問題，您可以將檔案分割成兩個以上的檔案，每一個有少於 64,000 個符號參考，或使用 `#pragma component(browser)` 前置處理器指示詞，限制為特定參考所產生的符號。 如需詳細資訊，請參閱[component](../../preprocessor/component.md)。
