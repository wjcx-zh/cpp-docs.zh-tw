---
title: 連結器工具警告 LNK4254 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4254
dev_langs:
- C++
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2ef421cbfa87ecab8a27dfa796eaa4eaacf7b70
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064642"
---
# <a name="linker-tools-warning-lnk4254"></a>連結器工具警告 LNK4254

區段 'section1' （位移） 合併到 'section2' (offset) 有不同的屬性

一個區段的內容已合併到另一個，但兩個區段的屬性會不同。 您的程式可能會產生非預期的結果。 例如，您想要讀取的資料可能現在只能在可寫入區段。

若要解決 LNK4254，修改或移除的合併要求。

當以 x86 為目標機器和 Visual c + +，（ARM、 MIPS、 arm、mips、*sh4 和捲動方塊） 的 Windows CE 目標。CRT 區段是唯讀的。 如果您的程式碼相依於先前的行為 (。CRT 區段是讀取/寫入），您可以看到非預期的行為。

如需詳細資訊，請參閱：

- [/MERGE (結合區段)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>範例

下列範例會產生 LNK4254。

```
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```