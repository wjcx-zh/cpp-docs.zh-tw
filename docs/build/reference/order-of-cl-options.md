---
title: CL 選項的順序
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: e5dd07f52f853b17bf663e2fbad7dbe66a3a1db7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633528"
---
# <a name="order-of-cl-options"></a>CL 選項的順序

選項可以出現在 CL 命令列中，除了 /link 選項，它必須出現在上一次上的任何位置。 編譯器選項中指定的開頭[CL 環境變數](../../build/reference/cl-environment-variables.md)，然後讀取命令列從左到右 — 處理在遇到它們的順序中的命令檔。 每個選項會套用至命令列上的所有檔案。 如果在 CL 發生衝突的選項，它會使用最右邊的選項。

## <a name="see-also"></a>另請參閱

[編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)