---
title: BSCMAKE 錯誤 BK1509 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1509
dev_langs:
- C++
helpviewer_keywords:
- BK1509
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 091fab63737c7ee1b3b85753a354bb7214cfa411
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025239"
---
# <a name="bscmake-error-bk1509"></a>BSCMAKE 錯誤 BK1509

堆積空間不足

BSCMAKE 已用盡記憶體，包括虛擬記憶體。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 請釋放一些磁碟空間。

1. 增加分頁檔大小。

1. 增加 Windows 交換檔的大小。

1. 減少使用 /Ei BSCMAKE 需要的記憶體，或以排除一些 /Es 輸入檔或消除巨集主體/e m。