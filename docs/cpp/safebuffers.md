---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: bc4736ce233ce026ecab9ef38ac8379466b5a0bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365590"
---
# <a name="safebuffers"></a>safebuffers

**Microsoft 特定的**

告知編譯器不要插入函式的緩衝區滿溢安全性檢查。

## <a name="syntax"></a>語法

```
__declspec( safebuffers )
```

## <a name="remarks"></a>備註

**/GS**編譯器選項通過在堆疊上插入安全檢查,使編譯器測試緩衝區溢出。 符合安全檢查條件的資料結構類型在[/GS(緩衝區安全檢查)中](../build/reference/gs-buffer-security-check.md)描述。 有關緩衝區溢出檢測的詳細資訊,請參閱[MSVC 中的安全功能](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)。

某位專業人員手動檢閱程式碼或進行外部分析後，可能會判斷函式不會發生緩衝區滿溢。 在這種情況下,可以通過將 **__declspec(安全緩衝區)** 關鍵字應用於函數聲明來禁止對函數的安全檢查。

> [!CAUTION]
> 緩衝區安全性檢查提供了重要的安全性保護，且幾乎不會對效能造成影響。 因此，除了在少數函式的效能為重要考量，以及函式已知為安全的情況以外，建議您不要抑制這些檢查。

## <a name="inline-functions"></a>內嵌函式

*主函數*可以使用[內聯](inline-functions-cpp.md)關鍵字插入*輔助函數*的副本。 如果將 **__declspec(安全緩衝區)** 關鍵字應用於函數,則該函數將抑制緩衝區溢出檢測。 但是,內聯以下列方式影響 **__declspec(安全緩衝區)** 關鍵字。

假設為兩個函數指定**了 /GS**編譯器選項,但主函數指定 **__declspec(安全緩衝區)** 關鍵字。 第二個函式中的資料結構會使其進行安全性檢查，因此函式不會抑制這些檢查。 在此案例中：

- 在輔助函數上指定[__forceinline](inline-functions-cpp.md)關鍵字,以強制編譯器內聯該函數,而不考慮編譯器優化。

- 由於輔助函數符合安全檢查條件,因此安全檢查也會應用於主函數,即使它指定**了__declspec(安全緩衝區)** 關鍵字。

## <a name="example"></a>範例

以下代碼演示如何使用 **__declspec(安全緩衝區)** 關鍵字。

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

**結束微軟的**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[內聯、 __inline、_forceinline \_](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
