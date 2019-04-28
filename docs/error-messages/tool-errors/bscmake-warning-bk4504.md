---
title: BSCMAKE 警告 BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 7ffcb7c2e6ae512006ccd29c87b05c53fdfcaef5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279285"
---
# <a name="bscmake-warning-bk4504"></a>BSCMAKE 警告 BK4504

檔案包含太多的參考;忽略進一步的參考，從這個來源

.cpp 檔包含 64,000 個以上的符號參考。 當 BSCMAKE 在檔案中遇到 64,000 個參考，會忽略所有進一步的參考。

若要修正這個問題，您可以將檔案分割成兩個以上的檔案，每一個有少於 64,000 個符號參考，或使用 `#pragma component(browser)` 前置處理器指示詞，限制為特定參考所產生的符號。 如需詳細資訊，請參閱 <<c0> [ 元件](../../preprocessor/component.md)。