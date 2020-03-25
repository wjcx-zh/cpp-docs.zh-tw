---
title: 編譯器錯誤 C2220
ms.date: 11/04/2016
f1_keywords:
- C2220
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
ms.openlocfilehash: c4fdac833e69e748dd29b9cf772c167fc1dbbd00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206657"
---
# <a name="compiler-error-c2220"></a>編譯器錯誤 C2220

將警告視為錯誤處理-未產生任何物件檔案

[/Wx](../../build/reference/compiler-option-warning-level.md)會指示編譯器將所有警告視為錯誤。 因為如果發生了錯誤，沒有產生任何目的檔或可執行檔。

只有在設定了 **/wx**旗標，且在編譯期間發生警告時，才會出現此錯誤。 若要更正這個錯誤，您必須排除專案中的每個警告。

### <a name="to-fix-use-one-of-the-following-techniques"></a>若要修正，請使用下列其中一種技術

- 修正在專案中產生警告的問題。

- 以較低的警告層級編譯-例如，使用 **/W3**而不是 **/W4**。

- 請使用[warning](../../preprocessor/warning.md) pragma 來停用或隱藏特定警告。

- 請勿使用 **/wx**來進行編譯。
