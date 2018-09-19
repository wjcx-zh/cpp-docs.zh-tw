---
title: 編譯器錯誤 C3383 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3383
dev_langs:
- C++
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e35aa05dd037c7d8a5dfd9f7e8328f3644b901e8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109388"
---
# <a name="compiler-error-c3383"></a>編譯器錯誤 C3383

/clr:safe 不支援 'operator new'

**/clr:safe** 編譯的輸出檔是可驗證類型安全的檔案，並且不支援指標。

如需詳細資訊，請參閱：

- [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Visual C++ 64 位元移轉時常見的問題](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>範例

下列範例會產生 C3383。

```
// C3383.cpp
// compile with: /clr:safe
int main() {
   char* pCharArray = new char[256];  // C3383
}
```