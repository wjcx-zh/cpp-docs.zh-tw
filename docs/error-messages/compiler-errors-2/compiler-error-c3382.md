---
title: 編譯器錯誤 C3382
ms.date: 11/04/2016
f1_keywords:
- C3382
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
ms.openlocfilehash: 419577ddd5b5d7d2d21a91f500070cb190c72117
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760461"
---
# <a name="compiler-error-c3382"></a>編譯器錯誤 C3382

/clr:safe 不支援 'sizeof'

**/clr:safe** 編譯的輸出檔是可驗證類型安全的檔案，而且不支援 sizeof，因為 sizeof 運算子的傳回值是 size_t，其大小視作業系統而異。

如需詳細資訊，請參閱：

- [sizeof 運算子](../../cpp/sizeof-operator.md)

- [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Visual C++ 64 位元移轉時常見的問題](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>範例

下列範例會產生 C3382。

```cpp
// C3382.cpp
// compile with: /clr:safe
int main() {
   sizeof( char );   // C3382
}
```
