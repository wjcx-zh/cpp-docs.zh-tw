---
title: 嚴重錯誤 C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: 13fb8963b33569facf62ccedfe9ce8b7bbbbfdc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428115"
---
# <a name="fatal-error-c1004"></a>嚴重錯誤 C1004

找到未預期的檔案結尾

編譯器會遇到原始程式檔的結尾，而不會解決建構。 程式碼可能會遺失下列項目之一：

- 右大括號

- 右括號

- 結束的註解標記 (* /)

- 分號

若要解決這個錯誤，請檢查下列：

- 預設磁碟機沒有足夠的空間，需要更多關於兩倍的空間為原始程式檔中的暫存檔案。

- `#if`評估為 false 的缺少結尾的指示詞`#endif`指示詞。

- 原始程式檔不以歸位字元和換行字元結尾。

下列範例會產生 C1004:

```
// C1004.cpp
#if TEST
int main() {}
// C1004
```

可能的解決方式：

```
// C1004b.cpp
#if TEST
#endif

int main() {}
```