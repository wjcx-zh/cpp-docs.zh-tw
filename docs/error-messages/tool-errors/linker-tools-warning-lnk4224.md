---
title: 連結器工具警告 LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: eb0a019cc80e5218a52697b8bcd5e91b811d04d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465321"
---
# <a name="linker-tools-warning-lnk4224"></a>連結器工具警告 LNK4224

> *選項*不再支援; 已忽略

## <a name="remarks"></a>備註

已指定無效、 已淘汰的連結器選項，並忽略。

例如，如果 /comment 指示詞會出現在可能會發生 LNK4224。 obj/Comment 指示詞已新增透過[註解 （C/c + +）](../../preprocessor/comment-c-cpp.md) pragma，使用已被取代的 exestr 選項。 使用 dumpbin [/all](../../build/reference/all.md) .obj 檔中檢視的連結器指示詞。

可能的話，請修改.obj 檔的來源，並移除 pragma。 如果您忽略此警告，則可能導致編譯使用 **/clr: pure**不會如預期般執行。 **/Clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

## <a name="example"></a>範例

下列範例會產生 LNK4224。

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```