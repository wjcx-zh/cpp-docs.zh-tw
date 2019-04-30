---
title: 編譯器錯誤 C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: 8b50221997dcf2fb60ee2b82ed630dd325a38145
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377003"
---
# <a name="compiler-error-c2097"></a>編譯器錯誤 C2097

不合法的初始化

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 初始化變數，使用非常數的值。

1. 簡短的位址與一長串位址來初始化。

1. 初始化本機結構、 等位或陣列進行編譯時是非常數運算式 **/Za**。

1. 包含逗號運算子的運算式進行初始化。

1. 不是常數或符號的運算式進行初始化。