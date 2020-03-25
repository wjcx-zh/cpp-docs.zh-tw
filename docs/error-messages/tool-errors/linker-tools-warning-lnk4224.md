---
title: 連結器工具警告 LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: 9e52dd533d897e729aba5f2b43ea6c019a024d43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182977"
---
# <a name="linker-tools-warning-lnk4224"></a>連結器工具警告 LNK4224

> 已不再支援*選項*;忽略

## <a name="remarks"></a>備註

指定了不正確過時連結器選項並予以忽略。

例如，如果/comment 指示詞出現在 .obj 中，就會發生 LNK4224。/Comment 指示詞已透過[comment （CC++/）](../../preprocessor/comment-c-cpp.md) pragma 加入，並使用已被取代的 exestr 選項。 使用 dumpbin [/all](../../build/reference/all.md)來查看 .obj 檔案中的連結器指示詞。

可能的話，請修改 .obj 的來源，並移除 pragma。 如果您忽略此警告，則使用 **/clr： pure**編譯的可執行檔可能不會如預期般執行。 **/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

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
