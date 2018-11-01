---
title: 連結器工具警告 LNK4253
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: d2fd7238a3f57b11b91813bd40b66cb3e9f47202
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628822"
---
# <a name="linker-tools-warning-lnk4253"></a>連結器工具警告 LNK4253

區段 'section1' 尚未合併到 'section2';已合併到 'section3'

連結器偵測到多個衝突的合併要求。 連結器將會忽略其中一個要求。

A **/合併**遇到選項或指示詞和`from`一節已合併到一個不同的區段，因為先前 **/合併**選項或指示詞 （或是因為隱含從合併連結器）。

若要解決 LNK4253，移除其中的合併要求。

當以 x86 為目標機器和 Visual c + +，（ARM、 MIPS、 arm、mips、*sh4 和捲動方塊） 的 Windows CE 目標。CRT 區段現在是唯讀屬性。 如果您的程式碼相依於先前的行為 (。CRT 區段是讀取/寫入），您可以看到非預期的行為。

如需詳細資訊，請參閱：

- [/MERGE (結合區段)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>範例

在下列範例中，連結器會指示要合併`.rdata`區段兩次，但為不同的區段。 下列範例會產生 LNK4253。

```
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```