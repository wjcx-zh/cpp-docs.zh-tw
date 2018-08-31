---
title: 專案建置錯誤 PRJ0024 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb539a5f1ee5f1aa5f9d828d93fa6d0dc8690c22
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215594"
---
# <a name="project-build-error-prj0024"></a>專案建置錯誤 PRJ0024

> Unicode 路徑 '*路徑*' 無法轉譯為使用者 ANSI 字碼頁。

*路徑*是原始的 Unicode 版本的路徑字串。 在情況下會發生此錯誤無法直接轉譯成 ANSI 目前的系統字碼頁的 Unicode 路徑所在。

如果您正在開發的專案使用字碼頁不在您的電腦上的系統上，可能會發生此錯誤。

此錯誤的解決方法是更新的路徑來使用 ANSI 文字，或在電腦上安裝的字碼頁，並將它設定為系統預設值。