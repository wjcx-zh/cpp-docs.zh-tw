---
title: 編譯器警告 (層級 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: 7f7ea7555937069caf5f83c9bf00f0fa980ef020
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175112"
---
# <a name="compiler-warning-level-1-c4794"></a>編譯器警告 (層級 1) C4794

執行緒區域儲存區變數 'variable' 的區段已從 ''section name' 變更為 '.tls$'

您使用了 [#pragma data_seg](../../preprocessor/data-seg.md) ，將 tls 變數放在開頭不是 .tls$ 的區段中。

已定義 *__declspec(thread)* 變數的目的檔中將會有 .tls$ [x](../../cpp/thread.md) 區段。 EXE 或 DLL 中的.tls 區段將會從這些區段產生。

## <a name="example"></a>範例

下列範例會產生 C4794：

```cpp
// C4794.cpp
// compile with: /W1 /c
#pragma data_seg(".someseg")
__declspec(thread) int i;   // C4794

// OK
#pragma data_seg(".tls$9")
__declspec(thread) int j;
```
