---
title: 連結器工具警告 LNK4204 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4204
dev_langs:
- C++
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee6164f20bbf91a8cb0b88d8a1333107f239d3f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136229"
---
# <a name="linker-tools-warning-lnk4204"></a>連結器工具警告 LNK4204

'filename' 遺漏參考模組; 的偵錯資訊如同沒有偵錯資訊般連結物件

.Pdb 檔案有錯誤的簽章。 連結器會繼續連結沒有偵錯資訊的物件。 您可能想要重新編譯物件檔案使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)選項。

如果某些文件庫中的物件參考不存在的檔案，可能會發生 LNK4204。 這種情形時重新建置方案例如物件檔案可能已刪除，因為編譯錯誤，所以不會重建。 請在此情況下，以編譯 **/z7**，或 **/Fd**，以更新物件，表示單一檔案每個程式庫 （也就是沒有預設的.pdb 檔名稱）。  如需詳細資訊，請參閱 [/Fd (程式資料庫檔名)](../../build/reference/fd-program-database-file-name.md)。  請確定每次更新原始檔控制系統中，以程式庫儲存.pdb。