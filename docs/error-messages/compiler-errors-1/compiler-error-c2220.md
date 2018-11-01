---
title: 編譯器錯誤 C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: 3ff730c6fea7d2c57c4ec3054fc627cdc6227e2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603407"
---
# <a name="compiler-error-c2220"></a>編譯器錯誤 C2220

將警告視為錯誤-沒有產生目的檔

[/WX](../../build/reference/compiler-option-warning-level.md)會指示編譯器將所有警告視為錯誤。 因為如果發生了錯誤，沒有產生任何目的檔或可執行檔。

此錯誤，才會出現 **/WX**旗標設定，並在編譯期間所發生的警告。 若要更正這個錯誤，您必須排除專案中的每個警告。

### <a name="to-fix-use-one-of-the-following-techniques"></a>若要修正，請使用下列其中一種技術

- 修正在專案中產生警告的問題。

- 在較低的警告層級進行編譯，比方說，使用 **/w3**而不是 **/w4**。

- 使用[警告](../../preprocessor/warning.md)pragma 來停用或隱藏特定警告。

- 不用 **/WX**編譯。