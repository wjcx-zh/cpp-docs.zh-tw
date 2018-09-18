---
title: 連結器工具警告 LNK4014 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4014
dev_langs:
- C++
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df0a3b6f30733413a0f27c0b8daa07394bb04b07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023107"
---
# <a name="linker-tools-warning-lnk4014"></a>連結器工具警告 LNK4014

找不到成員物件"objectname"

找不到 LIB`objectname`文件庫中。

**/Remove**並 **/擷取**選項都需要刪除或複製到檔案中的成員物件的完整名稱。 完整名稱包含原始的物件檔案的路徑。 若要查看完整的文件庫中的成員物件的名稱，請使用 DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md)或 LIB [/list](../../build/reference/managing-a-library.md)。