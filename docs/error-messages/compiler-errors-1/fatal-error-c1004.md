---
title: 嚴重錯誤 C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: 82a1a3e410505be53d4356e46d5521aebb72763c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756964"
---
# <a name="fatal-error-c1004"></a>嚴重錯誤 C1004

找到未預期的檔案結尾

編譯器已到達來源檔案的結尾，但未解析結構。 程式碼可能缺少下列其中一個元素：

- 右大括弧

- 右括弧

- 結尾註解標記（*/）

- 分號

若要解決此錯誤，請檢查下列各項：

- 預設磁片磁碟機的暫存檔案空間不足，需要與原始程式檔的空間大約兩倍。

- 評估為 false 的 `#if` 指示詞缺少結尾的 `#endif` 指示詞。

- 原始程式檔的結尾不是回車和換行。

下列範例會產生 C1004：

```cpp
// C1004.cpp
#if TEST
int main() {}
// C1004
```

可能的解決方案：

```cpp
// C1004b.cpp
#if TEST
#endif

int main() {}
```
