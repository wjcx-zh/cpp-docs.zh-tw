---
title: 連結器工具警告 LNK4014
ms.date: 11/04/2016
f1_keywords:
- LNK4014
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
ms.openlocfilehash: 5de53abc2342e3ed743f6b4abb871e05606dfc37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194274"
---
# <a name="linker-tools-warning-lnk4014"></a>連結器工具警告 LNK4014

找不到成員物件 "objectname"

LIB 在程式庫中找不到 `objectname`。

**/Remove**和 **/EXTRACT**選項需要要刪除或複製到檔案中的成員物件完整名稱。 完整名稱包含原始物件檔案的路徑。 若要查看程式庫中成員物件的完整名稱，請使用 DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md)或 LIB [/list](../../build/reference/managing-a-library.md)。
