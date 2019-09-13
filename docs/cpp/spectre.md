---
title: spectre
ms.date: 01/23/2018
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
ms.openlocfilehash: 40eee25dec867ae3fce7a6b2d4715f0be81bfe76
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926360"
---
# <a name="spectre"></a>spectre

**Microsoft 專屬**

告訴編譯器不要為函式插入 Spectre variant 1 的推測執行屏障指示。

## <a name="syntax"></a>語法

> **__declspec( spectre(nomitigation) )**

## <a name="remarks"></a>備註

[/Qspectre](../build/reference/qspectre.md)編譯器選項會使編譯器插入推測性執行屏障指示。 它們會插入，其中分析指出有 Spectre variant 1 安全性弱點存在。 所發出的特定指示取決於處理器。 雖然這些指示對程式碼大小或效能應該會有最小的影響，但有時候您的程式碼不會受到弱點的影響，而且需要最大效能。

專家分析可能會判斷函式不會受到 Spectre 變異1界限檢查略過瑕疵的保護。 在這種情況下，您可以將套用`__declspec(spectre(nomitigation))`至函式宣告，以隱藏函式中的風險降低程式碼產生。

> [!CAUTION]
> **/Qspectre**的推測性執行屏障指示提供重要的安全性保護，而且對效能的影響也不明顯。 因此，除了在少數函式的效能為重要考量，以及函式已知為安全的情況以外，建議您不要抑制這些檢查。

## <a name="example"></a>範例

下列程式碼顯示如何使用 `__declspec(spectre(nomitigation))`。

```cpp
// compile with: /c /Qspectre
static __declspec(spectre(nomitigation))
int noSpectreIssues() {
    // No Spectre variant 1 vulnerability here
    // ...
    return 0;
}

int main() {
    noSpectreIssues();
    return 0;
}
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[/Qspectre](../build/reference/qspectre.md)
