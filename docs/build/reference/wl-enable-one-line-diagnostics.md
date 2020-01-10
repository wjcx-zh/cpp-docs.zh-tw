---
title: /WL (啟用一行診斷)
ms.date: 11/04/2016
f1_keywords:
- /wl
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
ms.openlocfilehash: b1ded1cd18eb75ed47b76c1353ad82a7fa497ba9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988573"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL (啟用一行診斷)

將其他資訊附加至錯誤或警告訊息。

## <a name="syntax"></a>語法

```
/WL
```

## <a name="remarks"></a>備註

來自C++編譯器的錯誤和警告訊息後面會接著新行上顯示的其他資訊。 當您從命令列編譯時，可以將額外的資訊行附加至錯誤或警告訊息。 如果您將組建輸出捕獲到記錄檔，然後處理該記錄檔來尋找所有錯誤和警告，這可能是理想的做法。 分號會分隔錯誤或警告訊息與其他行。

並非所有的錯誤和警告訊息都有額外的行資訊。 下列程式碼會產生包含額外行資訊的錯誤;當您使用 **/WL**時，它可讓您測試效果。

```cpp
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] 資料夾。

1. 按一下 [命令列] 屬性頁。

1. 在 [其他選項] 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
