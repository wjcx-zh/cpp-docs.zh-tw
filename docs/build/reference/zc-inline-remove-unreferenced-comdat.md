---
title: '/Zc: inline （移除未參考的 COMDAT） |Microsoft 文件'
ms.custom: ''
ms.date: 03/01/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 067ba5dad4e0751a86835ea56c536a5b7250485d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379584"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (移除未參考的 COMDAT)

移除作為 COMDAT 或僅具有內部連結的未參考函式或資料。 當 **/zc: inline**指定時，編譯器需要使用內嵌資料或內嵌函式的轉譯單位還必須包含資料或函式的定義。

## <a name="syntax"></a>語法

> **/Zc:inline**[**-**]

## <a name="remarks"></a>備註

當 **/zc: inline**指定，則編譯器不會發出符號資訊未參考的 COMDAT 函式或資料，或函式或僅具有內部連結的資料。 此最佳化，可簡化部分連結器在發行組建中所執行之工作或連結器選項[/opt: ref](../../build/reference/opt-optimizations.md)指定。 當編譯器執行此最佳化作業時，可以大幅減小 .obj 檔案的大小，並提高連結器速度。 這個編譯器選項未啟用時已停用最佳化 ([/Od](../../build/reference/od-disable-debug.md)) 或當[/GL （整個程式最佳化）](../../build/reference/gl-whole-program-optimization.md)指定。

根據預設，此選項為關閉 (**/Zc:inline-**)。 [/ 寬鬆-](permissive-standards-conformance.md)選項不會啟用 **/zc: inline**。

如果 **/zc: inline**指定，則編譯器會強制執行的 C + + 11 需求，所有函式宣告`inline`必須在同一個轉譯單位中提供的定義，如果它們使用。 當未指定選項時，Microsoft 編譯器允許非一致宣告的函式會叫用的程式碼`inline`即使沒有定義為可見。 如需詳細資訊，請參閱 3.2 節和 7.1.2 節中的 C++11 標準。 此編譯器選項已引入 Visual Studio 2013 Update 2。

若要使用 **/zc: inline**選項，更新非標準的程式碼。

此範例示範如何使用沒有定義的內嵌函式宣告有不相容仍會編譯及連結時預設 **/Zc:inline-** 選項使用：

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

當 **/zc: inline**啟用時，相同程式碼會導致[LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)錯誤，因為編譯器不會發出非內嵌的程式碼主體`Example::inline_call`針對 example.obj 中。這會導致 `main` 中的非內嵌呼叫，參考未定義的外部符號。

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

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **語言**屬性頁。

1. 修改**移除未參考的程式碼和資料**屬性，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](../../build/reference/zc-conformance.md)<br/>
