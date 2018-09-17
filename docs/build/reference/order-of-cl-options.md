---
title: CL 選項的順序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffe9a440396df14823775db335e52bca6cacdb3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725019"
---
# <a name="order-of-cl-options"></a>CL 選項的順序

選項可以出現在 CL 命令列中，除了 /link 選項，它必須出現在上一次上的任何位置。 編譯器選項中指定的開頭[CL 環境變數](../../build/reference/cl-environment-variables.md)，然後讀取命令列從左到右 — 處理在遇到它們的順序中的命令檔。 每個選項會套用至命令列上的所有檔案。 如果在 CL 發生衝突的選項，它會使用最右邊的選項。

## <a name="see-also"></a>另請參閱

[編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)