---
title: 命令列錯誤 D8027 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8027
dev_langs:
- C++
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8234835d3bb0545c8a72bf35cfb55b2e18bc7da2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070375"
---
# <a name="command-line-error-d8027"></a>命令列錯誤 D8027

無法執行 '元件'

編譯器無法執行指定的編譯器元件或連結器。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 記憶體不足，無法載入元件。 NMAKE 叫用編譯器才會執行外部 makefile 編譯器。

1. 目前的作業系統無法執行的元件。 請確定路徑點到可執行檔適用於您的作業系統。

1. 元件已損毀。 重新複製元件無法安裝磁片，使用安裝程式。

1. 未正確指定的選項。 例如: 

    ```
    cl /B1 file1.c
    ```