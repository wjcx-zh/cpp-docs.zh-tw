---
title: 連結器工具警告 LNK4254
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 8431bd2d89fd5df5cf076ad006ab04006f552c4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988058"
---
# <a name="linker-tools-warning-lnk4254"></a>連結器工具警告 LNK4254

' section1 ' （offset）區段已合併至具有不同屬性的 ' section2 ' （offset）

一個區段的內容已合併至另一個區段，但這兩個區段的屬性不同。 您的程式可能會提供非預期的結果。 例如，您想要唯讀的資料現在可能位於可寫入的區段中。

若要解決 LNK4254，請修改或移除合併要求。

以 Visual C++的目標為 x86 電腦和 Windows CE 目標（ARM、MIPS、SH4 和 Thumb）時，。CRT 區段是唯讀的。 如果您的程式碼相依于先前的行為（。CRT 區段是讀取/寫入），您可能會看到非預期的行為。

如需詳細資訊，請參閱：

- [/MERGE (結合區段)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>範例

下列範例會產生 LNK4254。

```cpp
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```
