---
title: 連結器工具錯誤 LNK1237
ms.date: 11/04/2016
f1_keywords:
- LNK1237
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
ms.openlocfilehash: ae1a397cdcc10cd89fd046a94e78c15dd46dceed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581320"
---
# <a name="linker-tools-error-lnk1237"></a>連結器工具錯誤 LNK1237

程式碼在產生期間，編譯器引入了符號 'symbol' 定義於模組 'module' 以 /GL 編譯的參考

程式碼產生期間，編譯器不應引入稍後將解析成編譯的定義的符號 **/GL**。 `symbol` 是一種是引進，並稍後將解析成定義，以編譯的符號 **/GL**。

如需詳細資訊，請參閱 [/GL (整個程式最佳化)](../../build/reference/gl-whole-program-optimization.md)。

若要解決 LNK1237，無法編譯的符號寬度 **/GL** ，或使用[/INCLUDE （強制符號參考）](../../build/reference/include-force-symbol-references.md)強制符號參考。

## <a name="example"></a>範例

下列範例會產生 LNK1237。 若要解決這個錯誤，未在 LNK1237_a.cpp 陣列進行初始化作業，並新增 **/include: __chkstk**至連結命令。

```
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```