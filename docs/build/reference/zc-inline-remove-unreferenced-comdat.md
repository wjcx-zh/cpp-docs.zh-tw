---
title: /Zc:inline (移除未參考的 COMDAT)
ms.date: 09/05/2019
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
ms.openlocfilehash: 290252262254521c024d7b0d6355472199d1f55d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218958"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (移除未參考的 COMDAT)

移除未參考的資料或 Comdat 的函式，或只具有內部連結的函數。 在 **/zc： inline**底下，編譯器會指定具有內嵌資料或函數的轉譯單位也必須包含其定義。

## <a name="syntax"></a>語法

> **/Zc： inline**[ **-** ]

## <a name="remarks"></a>備註

當指定 **/zc： inline**時，編譯器不會針對未參考的 COMDAT 函數或資料發出符號資訊。 或者，適用于僅具有內部連結的資料或函數。 這項優化可簡化連結器在發行組建中所執行的部分工作，或當您指定[/opt： REF](opt-optimizations.md)連結器選項時。 這個編譯器優化可以大幅減少 .obj 檔案大小，並改善連結器速度。 當您停用優化（[/od](od-disable-debug.md)）時，不會啟用編譯器選項。 或者，當您指定[/gl （整個程式優化）](gl-whole-program-optimization.md)時。

根據預設，在命令列組建中，此選項會關閉（**/zc： inline-**）。 [/Permissive-](permissive-standards-conformance.md)選項不會啟用 **/zc： inline**。 在 MSBuild 專案中，選項是由設定**屬性**  >  **C/c + +**  >  **語言**[  >  移除未參考的程式**代碼和資料**] 屬性所設定，預設為 **[是]** 。

如果已指定 **/zc： inline** ，則編譯器會強制執行 c + + 11 需求，而宣告的所有函式 **`inline`** 都必須在相同的轉譯單位中具有可用的定義（如果使用的話）。 未指定選項時，Microsoft 編譯器會允許未符合標準的程式碼叫用已宣告的函式， **`inline`** 即使沒有顯示任何定義也一樣。 如需詳細資訊，請參閱 3.2 節和 7.1.2 節中的 C++11 標準。 此編譯器選項已引入 Visual Studio 2013 Update 2。

若要使用 **/zc： inline**選項，請更新不相容的程式碼。

這個範例會示範當使用預設 **/zc： inline**選項時，不符合標準的內嵌函式宣告在沒有定義的情況下，仍會進行編譯和連結的方式：

```cpp
// example.h
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#pragma once

class Example {
public:
   inline void inline_call(); // declared but not defined inline
   void normal_call();
   Example() {};
};
```

```cpp
// example.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include <stdio.h>
#include "example.h"

void Example::inline_call() {
   printf("inline_call was called.\n");
}

void Example::normal_call() {
   printf("normal_call was called.\n");
   inline_call(); // with /Zc:inline-, inline_call forced into .obj file
}
```

```cpp
// zcinline.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include "example.h"

int main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

當 **/zc： inline**已啟用時，相同的程式碼會造成[LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)錯誤，因為編譯器不會發出範例 .obj 的非內嵌程式碼主體。 `Example::inline_call`這會導致中的非內嵌呼叫 `main` 參考未定義的外部符號。

若要解決這個錯誤，您可以從的宣告中移除 **`inline`** 關鍵字 `Example::inline_call` 、將的定義移 `Example::inline_call` 至標頭檔，或將的實作為 `Example` 主要 .cpp。 下一個範例會將定義移至標頭檔，在那裡，該定義對包括該標頭的任何呼叫程式都可見。

```cpp
// example2.h
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#pragma once
#include <stdio.h>

class Example2 {
public:
   inline void inline_call() {
      printf("inline_call was called.\n");
   }
   void normal_call();
   Example2() {};
};
```

```cpp
// example2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

void Example2::normal_call() {
   printf("normal_call was called.\n");
   inline_call();
}
```

```cpp
// zcinline2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

int main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **語言**] 屬性頁。

1. 修改 [**移除未參考的程式碼和資料**] 屬性，然後選擇 **[確定]**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)<br/>
