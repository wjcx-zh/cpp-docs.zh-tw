---
title: 連結器工具錯誤 LNK1237
ms.date: 11/04/2016
f1_keywords:
- LNK1237
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
ms.openlocfilehash: c56b2eb86c7605fb3330d7b1bb01e3235466ede6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990955"
---
# <a name="linker-tools-error-lnk1237"></a>連結器工具錯誤 LNK1237

在程式碼產生期間，編譯器引進了對以/GL 編譯的模組 ' module ' 中定義的符號 ' symbol ' 的參考

在程式碼產生期間，編譯器不應引進稍後解析為定義的 **/gl**的符號。 `symbol` 是引進的符號，稍後會解析成以 **/gl**編譯的定義。

如需詳細資訊，請參閱 [/GL (整個程式最佳化)](../../build/reference/gl-whole-program-optimization.md)。

若要解析 LNK1237，請勿使用 **/gl**編譯符號，或使用[/INCLUDE （強制符號參考）](../../build/reference/include-force-symbol-references.md)來強制執行符號的參考。

## <a name="example"></a>範例

下列範例會產生 LNK1237。 若要解決這個錯誤，請勿在 LNK1237_a .cpp 中初始化陣列，並將 **/include： __chkstk**新增至 link 命令。

```cpp
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```cpp
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```
