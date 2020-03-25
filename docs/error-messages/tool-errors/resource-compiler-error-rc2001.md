---
title: 資源編譯器錯誤 RC2001
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: 35042687b798b53857becdedba57861bd4f41a05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191715"
---
# <a name="resource-compiler-error-rc2001"></a>資源編譯器錯誤 RC2001

常數中的分行符號

字串常數在第二行繼續，但不含反斜線（ **\\** ）或結尾和左雙引號（ **"** ）。

若要中斷位於原始程式檔中兩行的字串常數，請執行下列其中一項動作：

- 結束具有行接續字元的第一行，也就是反斜線。

- 以雙引號關閉第一行中的字串，然後在下一行以另一個引號開啟字串。

以 \n 結束第一行的程式碼並不足夠，而是在字串常數中嵌入分行符號的逸出序列。
