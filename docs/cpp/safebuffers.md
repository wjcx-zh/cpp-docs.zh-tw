---
title: safebuffers |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- safebuffers_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6590a2f210156711066fac241170103cc5a8830
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034352"
---
# <a name="safebuffers"></a>safebuffers

**Microsoft 專屬**

告知編譯器不要插入函式的緩衝區滿溢安全性檢查。

## <a name="syntax"></a>語法

```
__declspec( safebuffers )
```

## <a name="remarks"></a>備註

**/GS**編譯器選項可讓編譯器在堆疊上插入安全性檢查來測試緩衝區滿溢。 進行安全性檢查的資料結構的類型所述[/GS （緩衝區安全性檢查）](../build/reference/gs-buffer-security-check.md)。 如需緩衝區滿溢偵測的詳細資訊，請參閱[MSVC 中的安全性功能](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)。

某位專業人員手動檢閱程式碼或進行外部分析後，可能會判斷函式不會發生緩衝區滿溢。 在此情況下，您可以隱藏函式的安全性檢查，藉由套用 **__declspec （safebuffers)** 函式宣告的關鍵字。

> [!CAUTION]
>  緩衝區安全性檢查提供了重要的安全性保護，且幾乎不會對效能造成影響。 因此，除了在少數函式的效能為重要考量，以及函式已知為安全的情況以外，建議您不要抑制這些檢查。

## <a name="inline-functions"></a>內嵌函式

A*主要函式*可用[內嵌](inline-functions-cpp.md)關鍵字來插入一份*次要函式*。 如果 **__declspec （safebuffers)** 關鍵字是否套用至函式、 緩衝區滿溢偵測會抑製該函式。 不過，內嵌會影響 **__declspec （safebuffers)** 如下的關鍵字。

假設 **/GS**編譯器選項會指定這兩個函式，但主要功能指定了 **__declspec （safebuffers)** 關鍵字。 第二個函式中的資料結構會使其進行安全性檢查，因此函式不會抑制這些檢查。 在此情況下：

- 指定[__forceinline](inline-functions-cpp.md)關鍵字次要的函式，以強制編譯器內嵌該函式，不論編譯器最佳化。

- 由於次要函式是進行安全性檢查，安全性檢查也會套用至主要函式即使它會指定 **__declspec （safebuffers)** 關鍵字。

## <a name="example"></a>範例

下列程式碼示範如何使用 **__declspec （safebuffers)** 關鍵字。

```cpp
// compile with: /c /GS
typedef struct {
    int x[20];
} BUFFER;
static int checkBuffers() {
    BUFFER cb;
    // Use the buffer...
    return 0;
};
static __declspec(safebuffers)
    int noCheckBuffers() {
    BUFFER ncb;
    // Use the buffer...
    return 0;
}
int wmain() {
    checkBuffers();
    noCheckBuffers();
    return 0;
}
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[inline、__inline、\__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)