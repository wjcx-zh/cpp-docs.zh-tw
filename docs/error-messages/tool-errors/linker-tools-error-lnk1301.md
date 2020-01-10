---
title: 連結器工具錯誤 LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: fe64eecfbc9fed57c3748afd5804b76d6e4284a4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990933"
---
# <a name="linker-tools-error-lnk1301"></a>連結器工具錯誤 LNK1301

找到 LTCG clr 模組，與/LTCG：參數不相容

以/clr 和/GL 編譯的模組已與/LTCG. 的其中一個特性指引優化（PGO）參數一起傳遞至連結器

/Clr 模組不支援特性指引優化。

如需詳細資訊，請參閱＜＞。

- [/GL (整個程式最佳化)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (連結時間產生程式碼)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)

- [特性指引最佳化](../../build/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>若要改正這項錯誤

1. 請勿使用/clr 進行編譯，或不要以/LTCG. 的其中一個 PGO 參數連結

## <a name="example"></a>範例

下列範例會產生 LNK1301：

```cpp
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```
