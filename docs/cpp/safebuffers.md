---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: 705d3eca67f87e505a147af4984496d3af43dd53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178908"
---
# <a name="safebuffers"></a>safebuffers

**Microsoft 專屬**

告知編譯器不要插入函式的緩衝區滿溢安全性檢查。

## <a name="syntax"></a>語法

```
__declspec( safebuffers )
```

## <a name="remarks"></a>備註

**/Gs**編譯器選項會藉由在堆疊上插入安全性檢查，讓編譯器測試緩衝區溢位。 [/Gs （緩衝區安全性檢查）](../build/reference/gs-buffer-security-check.md)中會說明適用于安全性檢查的資料結構類型。 如需有關緩衝區溢位偵測的詳細資訊，請參閱[MSVC 中的安全性功能](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)。

某位專業人員手動檢閱程式碼或進行外部分析後，可能會判斷函式不會發生緩衝區滿溢。 在這種情況下，您可以將 **__declspec （safebuffers）** 關鍵字套用至函式宣告，以隱藏函式的安全性檢查。

> [!CAUTION]
>  緩衝區安全性檢查提供了重要的安全性保護，且幾乎不會對效能造成影響。 因此，除了在少數函式的效能為重要考量，以及函式已知為安全的情況以外，建議您不要抑制這些檢查。

## <a name="inline-functions"></a>內嵌函式

*主要*函式可以使用[內嵌](inline-functions-cpp.md)關鍵字來插入*次要函數*的複本。 如果 **__declspec （safebuffers）** 關鍵字套用至函式，則會抑制該函數的緩衝區溢位偵測。 不過，內嵌會以下列方式影響 **__declspec （safebuffers）** 關鍵字。

假設已針對這兩個函式指定 **/gs**編譯器選項，但主要函式指定 **__declspec （safebuffers）** 關鍵字。 第二個函式中的資料結構會使其進行安全性檢查，因此函式不會抑制這些檢查。 在此案例中：

- 在次要函式上指定[__forceinline](inline-functions-cpp.md)關鍵字，強制編譯器內嵌該函式，而不論編譯器優化。

- 因為次要函式符合安全性檢查的資格，即使它指定了 **__declspec （safebuffers）** 關鍵字，也會將安全性檢查套用到主要功能。

## <a name="example"></a>範例

下列程式碼顯示如何使用 **__declspec （safebuffers）** 關鍵字。

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

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[inline、__inline、\__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
