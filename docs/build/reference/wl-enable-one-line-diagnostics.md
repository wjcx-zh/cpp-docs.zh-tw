---
title: -WL （啟用一行診斷） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /wl
dev_langs:
- C++
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e82a3273673d45d1abf3ac201d7a0f63334cecbb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718662"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (啟用一行診斷)

將其他資訊附加至錯誤或警告訊息。

## <a name="syntax"></a>語法

```
/WL
```

## <a name="remarks"></a>備註

錯誤和警告訊息，從 c + + 編譯器可運用的出現，根據預設，在新行上的其他資訊。 當您從命令列編譯時，其他的一行資訊可以附加至錯誤或警告訊息。 如果您擷取您的組建輸出記錄檔，然後再處理該記錄檔，以找出所有錯誤和警告，這可能不妥當。 分號會分隔錯誤或警告訊息，與其他列。

並非所有錯誤和警告訊息會都有一行額外資訊。 下列程式碼會產生錯誤，有一行額外的資訊。它可讓您測試是否有效，當您使用 **/WL**。

```
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)