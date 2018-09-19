---
title: BSCMAKE 錯誤 BK1514 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1514
dev_langs:
- C++
helpviewer_keywords:
- BK1514
ms.assetid: 7c7e2504-a490-44ab-bb1f-47385ee2f4b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20f66c5c48547e92aef00568d5488a6293303be1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094711"
---
# <a name="bscmake-error-bk1514"></a>BSCMAKE 錯誤 BK1514

所有。SBR 檔被截斷，檔名中找不到

指定要更新的.sbr 檔案都屬於原始的瀏覽資訊 (.bsc) 檔。 若要尋找造成此錯誤的.sbr 檔案名稱，請閱讀[BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md)前面的警告。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. .Sbr 或.bsc 指定了錯誤的檔案名稱。

1. .Bsc 檔損毀所需 BSCMAKE 來重建它。