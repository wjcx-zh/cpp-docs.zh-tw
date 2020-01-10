---
title: 連結器工具警告 LNK4253
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: c3f45880571e5c06f76d5f063ff993e2f6b2be9b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988095"
---
# <a name="linker-tools-warning-lnk4253"></a>連結器工具警告 LNK4253

區段 ' section1 ' 未合併至 ' section2 ';已合併至 ' section3 '

連結器偵測到多個衝突的合併要求。 連結器會略過其中一個要求。

遇到了 **/merge**選項或指示詞，而且 `from` 區段已經合併到不同的區段，因為先前的 **/merge**選項或指示詞（或是因為連結器的隱含合併）。

若要解決 LNK4253，請移除其中一個合併要求。

以 Visual C++的目標為 x86 電腦和 Windows CE 目標（ARM、MIPS、SH4 和 Thumb）時，。CRT 區段現在是唯讀的。 如果您的程式碼相依于先前的行為（。CRT 區段是讀取/寫入），您可能會看到非預期的行為。

如需詳細資訊，請參閱：

- [/MERGE (結合區段)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>範例

在下列範例中，會指示連結器將 `.rdata` 區段合併兩次，但在不同的區段中。 下列範例會產生 LNK4253。

```cpp
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```
