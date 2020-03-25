---
title: NMAKE 嚴重錯誤 U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: 9c6b939c97f993e42049677292374377d825d474
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193676"
---
# <a name="nmake-fatal-error-u1051"></a>NMAKE 嚴重錯誤 U1051

記憶體不足

因為 makefile 太大或太複雜，所以 NMAKE 已用盡記憶體，包括虛擬記憶體。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 釋放磁片上的一些空間。

1. 增加 Windows NT 分頁檔案或 Windows 交換檔的大小。

1. 如果只使用部分 makefile，請將 makefile 分割成不同的檔案或使用 **！如果**前置處理指示詞限制 NMAKE 必須處理的數量，則為。 **！IF**指示詞包含 **！若**為，`!IFDEF`， **！IFNDEF**， **！如果**為，則為，否則為 **！否則**`IFDEF`和 **！否則**`IFNDEF`。
