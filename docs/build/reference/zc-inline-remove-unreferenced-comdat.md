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
ms.openlocfilehash: f0c0d9a4e5e5f52d239f1a8591006b3d9e369778
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740116"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (移除未參考的 COMDAT)

移除作為 COMDAT 或僅具有內部連結的未參考函式或資料。 當指定 **/zc： inline**時，編譯器會要求使用內嵌資料或內嵌函數的轉譯單位也必須包含資料或函數的定義。

## <a name="syntax"></a>語法

> **/Zc:inline**[ **-** ]

## <a name="remarks"></a>備註

當指定 **/zc： inline**時，編譯器不會針對未參考的 COMDAT 函數或資料，或僅具有內部連結的函數或資料發出符號資訊。 這項優化可簡化發行組建中的連結器所執行的部分工作，或指定連結器選項[/opt： REF](opt-optimizations.md) 。 當編譯器執行此最佳化作業時，可以大幅減小 .obj 檔案的大小，並提高連結器速度。 當優化已停用（[/od](od-disable-debug.md)）或指定了[/Gl （整個程式優化）](gl-whole-program-optimization.md)時，不會啟用此編譯器選項。

根據預設，在命令列組建中，此選項會關閉（ **/zc： inline-** ）。 [/Permissive-](permissive-standards-conformance.md)選項不會啟用 **/zc： inline**。 在 MSBuild 專案中，選項是由設定**屬性** >   > [**C/C++** **語言** > ] [移除未參考的程式**代碼和資料**] 屬性所設定，它會設為 **[是]** 。預設.

如果已指定 **/zc： inline** ，則編譯器會強制執行 c + + 11 需求， `inline`而宣告的所有函式都必須在相同的轉譯單位中具有可用的定義（如果使用的話）。 未指定選項時，Microsoft 編譯器會允許未符合標準的程式碼叫用已宣告`inline`的函式，即使沒有顯示任何定義也一樣。 如需詳細資訊，請參閱 3.2 節和 7.1.2 節中的 C++11 標準。 此編譯器選項已引入 Visual Studio 2013 Update 2。

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

void main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

當 **/zc： inline**已啟用時，相同的程式碼會造成[LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)錯誤，因為編譯器不會發出範例 .obj 的非內嵌程式`Example::inline_call`代碼主體。這會導致 `main` 中的非內嵌呼叫，參考未定義的外部符號。

若要解決此錯誤，您可以從 `inline` 的宣告中，移除 `Example::inline_call` 關鍵字，將 `Example::inline_call` 的定義移至標頭檔，或者將 `Example` 的實作移至 main.cpp。 下一個範例會將定義移至標頭檔，在那裡，該定義對包括該標頭的任何呼叫程式都可見。

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

void main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性** > ] [**C/C++**   > Language] 屬性頁。

1. 修改 [**移除未參考的程式碼和資料**] 屬性，然後選擇 **[確定]** 。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)<br/>
