---
title: 連結器工具警告 LNK4014
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: f67990ed74f500f1b954edcf1d6437f64f93f0d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511701"
---
# <a name="linker-tools-warning-lnk4014"></a>連結器工具警告 LNK4014

找不到成員物件"objectname"

找不到 LIB`objectname`文件庫中。

**/Remove**並 **/擷取**選項都需要刪除或複製到檔案中的成員物件的完整名稱。 完整名稱包含原始的物件檔案的路徑。 若要查看完整的文件庫中的成員物件的名稱，請使用 DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md)或 LIB [/list](../../build/reference/managing-a-library.md)。