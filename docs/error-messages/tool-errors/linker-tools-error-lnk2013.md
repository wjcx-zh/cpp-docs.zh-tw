---
title: 連結器工具錯誤 LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 6ad3f40f06e64422b393edb457a0dcf419828b6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194742"
---
# <a name="linker-tools-error-lnk2013"></a>連結器工具錯誤 LNK2013

修復類型修復溢位。 目標 ' symbol name ' 超出範圍

連結器無法將必要的位址或位移放入指定的指令，因為目標符號太遠超出指令的位置。

若要解決這個問題，您可以建立多個映射，或使用[/order](../../build/reference/order-put-functions-in-order.md)選項，讓指示和目標更接近在一起。

當符號名稱是使用者定義的符號（而不是編譯器產生的符號）時，您也可以嘗試下列動作來解決此錯誤：

- 將靜態函數變更為非靜態。

- 將包含靜態函式的程式碼區段重新命名為與呼叫者相同。

使用 `DUMPBIN /SYMBOLS`，以查看函式是否為靜態。
