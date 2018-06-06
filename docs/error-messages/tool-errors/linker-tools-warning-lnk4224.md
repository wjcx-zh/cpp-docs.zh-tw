---
title: 連結器工具警告 LNK4224 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4224
dev_langs:
- C++
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bdffdf3469cc3a0e5d41b0504b882513d44b63c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703983"
---
# <a name="linker-tools-warning-lnk4224"></a>連結器工具警告 LNK4224

> *選項*不再支援; 已忽略

## <a name="remarks"></a>備註

已指定無效、 過時的連結器選項，並且忽略。

例如，如果 /comment 指示詞會出現在可能會發生 LNK4224。 obj/Comment 指示詞會有透過加入[註解 （C/c + +）](../../preprocessor/comment-c-cpp.md) pragma，使用已被取代的 exestr 選項。 使用 dumpbin [/所有](../../build/reference/all.md).obj 檔中檢視的連結器指示詞。

可能的話，請修改.obj 檔的來源，並移除 pragma。 如果您忽略這個警告，則可能導致編譯與 **/clr: pure**將不會如預期般執行。 **/Clr: pure**編譯器選項已被取代 Visual Studio 2015 中，在 Visual Studio 2017 中支援。

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