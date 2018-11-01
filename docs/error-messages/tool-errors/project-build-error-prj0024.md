---
title: 專案建置錯誤 PRJ0024
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: 645b898bdffcc6d7b397c25eb3c41cea25cb361f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589640"
---
# <a name="project-build-error-prj0024"></a>專案建置錯誤 PRJ0024

> Unicode 路徑 '*路徑*' 無法轉譯為使用者 ANSI 字碼頁。

*路徑*是原始的 Unicode 版本的路徑字串。 在情況下會發生此錯誤無法直接轉譯成 ANSI 目前的系統字碼頁的 Unicode 路徑所在。

如果您正在開發的專案使用字碼頁不在您的電腦上的系統上，可能會發生此錯誤。

此錯誤的解決方法是更新的路徑來使用 ANSI 文字，或在電腦上安裝的字碼頁，並將它設定為系統預設值。