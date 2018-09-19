---
title: 資源編譯器嚴重錯誤 RW1022 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1022
dev_langs:
- C++
helpviewer_keywords:
- RW1022
ms.assetid: 6747c8a9-9c9b-4422-b414-0645d22092d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caaefc045a31ca64aa9843927d550ef66285cb2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099838"
---
# <a name="resource-compiler-fatal-error-rw1022"></a>資源編譯器嚴重錯誤 RW1022

**寫入檔案時發生 I/O 錯誤**

資源編譯器無法寫入檔案中。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 磁碟空間不足。 可用空間必須等於至少兩次會建立可執行檔的大小。

1. 磁碟區是唯讀的。

1. 磁區損壞。

1. 共用違規。