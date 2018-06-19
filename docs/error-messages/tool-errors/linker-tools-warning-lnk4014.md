---
title: 連結器工具警告 LNK4014 |Microsoft 文件
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
ms.openlocfilehash: 2fb86efbdc70342861a87a233ab687f7564cb48b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300055"
---
# <a name="linker-tools-warning-lnk4014"></a>連結器工具警告 LNK4014
找不到成員物件"objectname"  
  
 找不到 LIB`objectname`文件庫中。  
  
 **/移除**和 **/擷取**選項需要成員物件所要刪除或複製到檔案的完整名稱。 完整名稱包含原始的物件檔案的路徑。 若要查看文件庫中的成員物件的完整名稱，請使用 DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md)或 LIB [/list](../../build/reference/managing-a-library.md)。