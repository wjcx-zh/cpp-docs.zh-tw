---
title: BSCMAKE 錯誤 BK1509
ms.date: 11/04/2016
f1_keywords:
- BK1509
helpviewer_keywords:
- BK1509
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
ms.openlocfilehash: 384f202ea3eb969da2ce3a3b82209c383009c62e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475448"
---
# <a name="bscmake-error-bk1509"></a>BSCMAKE 錯誤 BK1509

堆積空間不足

BSCMAKE 已用盡記憶體，包括虛擬記憶體。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 請釋放一些磁碟空間。

1. 增加分頁檔大小。

1. 增加 Windows 交換檔的大小。

1. 減少使用 /Ei BSCMAKE 需要的記憶體，或以排除一些 /Es 輸入檔或消除巨集主體/e m。