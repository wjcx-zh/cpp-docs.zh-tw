---
title: BSCMAKE 警告 BK4502 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4502
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4142993b3f4f5bda2b3e4ce322aa26d7beca8584
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056322"
---
# <a name="bscmake-warning-bk4502"></a>BSCMAKE 警告 BK4502

截斷。SBR 檔案 'filename' 不是在檔案名稱

在更新期間指定原本並不是.bsc 檔的一部分的長度為零的.sbr 檔案。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 指定了錯誤的檔案名稱。

1. 刪除的檔案。 (錯誤[BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md)結果。)

1. 檔案已損毀，需要執行完整建置 BSCMAKE。