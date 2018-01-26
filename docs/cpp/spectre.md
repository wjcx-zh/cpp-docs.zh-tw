---
title: "spectre |Microsoft 文件"
ms.custom: 
ms.date: 1/23/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
dev_langs: C++
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b515d25d4818cf8b6213a37f3fe78df4f3882a69
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="spectre"></a>spectre

**Microsoft 特定的**

會告知編譯器不要插入函式 Spectre variant 1 推測執行屏障指令。

## <a name="syntax"></a>語法

> **__declspec( spectre(nomitigation) )**  

## <a name="remarks"></a>備註

[/Qspectre](../build/reference/qspectre.md)編譯器選項會導致編譯器插入推測執行屏障指示分析指出 Spectre variant 1 安全性弱點存在。 發出的特定指示取決於處理器。 雖然這些指示應該有的程式碼大小和效能的影響非常小，可能是您的程式碼不會受到這項弱點，而且需要最大效能。

專家分析可能會判斷函式不安全，防止 Spectre variant 1 界限檢查略過缺失。 在此情況下，您可以藉由套用隱藏的函式內的防護程式碼產生`__declspec(spectre(nomitigation))`函式宣告。

> [!CAUTION]
> **/Qspectre**推測執行屏障指令提供重要的安全性保護，不明顯影響效能。 因此，除了在少數函式的效能為重要考量，以及函式已知為安全的情況以外，建議您不要抑制這些檢查。

## <a name="example"></a>範例

下列程式碼示範如何使用`__declspec(spectre(nomitigation))`。

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

**結束 Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)  
[關鍵字](../cpp/keywords-cpp.md)  
[/Qspectre](../build/reference/qspectre.md)  
