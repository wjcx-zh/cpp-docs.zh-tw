---
title: BSCMAKE 錯誤 BK1506 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1506
dev_langs:
- C++
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26201a894212701cca19ab2192676b37a69e8b57
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088692"
---
# <a name="bscmake-error-bk1506"></a>BSCMAKE 錯誤 BK1506

無法開啟檔案 'filename' [: 原因]

BSCMAKE 無法開啟檔案。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 另一個處理序鎖定的檔案。 如果`reason`說**使用權限被拒**，瀏覽器可能使用此檔案。 關閉 [瀏覽] 視窗，然後重試組建。

1. 磁碟已滿。

1. 硬體錯誤。

1. 指定的輸出檔案具有相同名稱與現有的子目錄。