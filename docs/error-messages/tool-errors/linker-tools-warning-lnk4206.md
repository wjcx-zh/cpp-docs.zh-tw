---
title: 連結器工具警告 LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: 1758fffb72e183e8a186d115b2b3f3b30c32e047
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193872"
---
# <a name="linker-tools-warning-lnk4206"></a>連結器工具警告 LNK4206

> 找不到先行編譯類型資訊;未連結或覆寫 '*filename*';連結化物件，如同沒有任何調試資訊

連結命令中未指定使用[/yc](../../build/reference/yc-create-precompiled-header-file.md)編譯的*filename*物件檔案，或已覆寫該檔案。

這項警告的常見案例是，使用/Yc 編譯的 .obj 是在程式庫中，而您的程式碼中沒有任何來自該 .obj 的符號參考。  在此情況下，連結器不會使用（或甚至是查看） .obj 檔案。  在這種情況下，您應該重新編譯程式碼，並針對使用[/yu](../../build/reference/yu-use-precompiled-header-file.md)所編譯的物件使用[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 。
