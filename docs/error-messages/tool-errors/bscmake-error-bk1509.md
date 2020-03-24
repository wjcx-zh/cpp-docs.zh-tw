---
title: BSCMAKE 錯誤 BK1509
ms.date: 11/04/2016
f1_keywords:
- BK1509
helpviewer_keywords:
- BK1509
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
ms.openlocfilehash: 04637e13aa49b873117228c8aabd9151e6a6b822
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197675"
---
# <a name="bscmake-error-bk1509"></a>BSCMAKE 錯誤 BK1509

堆積空間不足

BSCMAKE 已用盡記憶體，包括虛擬記憶體。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 釋放一些磁碟空間。

1. 增加交換檔案的大小。

1. 增加 Windows 交換檔的大小。

1. 使用/Ei 或/Es 來減少部分輸入檔或/Em 以消除宏主體，藉此降低記憶體 BSCMAKE 的要求。
