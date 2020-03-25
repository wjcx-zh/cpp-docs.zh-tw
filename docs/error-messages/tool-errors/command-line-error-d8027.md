---
title: 命令列錯誤 D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: 42341507dfc2d3da02639dd28ab1265783452388
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196881"
---
# <a name="command-line-error-d8027"></a>命令列錯誤 D8027

無法執行 ' component '

編譯器無法執行指定的編譯器元件或連結器。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 記憶體不足，無法載入元件。 如果 NMAKE 叫用編譯器，請在 makefile 外執行編譯器。

1. 目前的作業系統無法執行此元件。 請確定路徑指向適用于您作業系統的可執行檔。

1. 元件已損毀。 使用安裝程式，從發佈磁片重新複製元件。

1. 指定了不正確的選項。 例如：

    ```
    cl /B1 file1.c
    ```
