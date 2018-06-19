---
title: -fp （指定浮點數行為） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
dev_langs:
- C++
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 520a6e2d675c55e47a0424ab93c6a76d521f2358
ms.sourcegitcommit: 5e932a0e110e80bc241e5f69e3a1a7504bfab1f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2018
ms.locfileid: "34422689"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (指定浮點數行為)

在原始程式碼檔中指定浮點數行為。

## <a name="syntax"></a>語法

> **/fp:**[**精確** | **除了**[**-**] |**快速** | **嚴格**]

### <a name="arguments"></a>引數

#### <a name="precise"></a>精確

預設值 **/fp**是 **/fp： 精確**。

**/Fp： 精確**旗標可停用可以變更浮點計算精確度的最佳化來改善浮點測試相等和不等的一致性。 (為了維持嚴格的 ANSI 一致性，必須保有特定精確度)。根據預設，在程式碼適用於 x86 架構使用 x87 副處理器指令，編譯器會使用副處理器的 80 位元暫存器來存放浮點計算的中繼結果。 這樣可以加快程式的速度並且縮小程式的大小。 不過，由於計算會涉及在記憶體中以小於 80 位元表示的浮點數資料類型，因此帶著額外的精確度位元 (80 位元減去較小浮點類型中的位元數目) 歷經冗長的計算，可能會產生不一致的結果。

與 **/fp： 精確**x86 處理器，編譯器會執行類型的變數的進位`float`指派和轉換 （cast），以及當參數傳遞至函式的正確精確度。 這種捨入方式可保證該資料不保留任何大於其類型容量的數字精確度。 編譯程式 **/fp： 精確**速度較慢且大於不可以是 **/fp： 精確**。 **/fp： 精確**停用內建函式; 常式會改用標準執行階段程式庫。 如需詳細資訊，請參閱 [/Oi (產生內建函式)](../../build/reference/oi-generate-intrinsic-functions.md)。

以啟用下列浮點數行為 **/fp： 精確**:

- 縮減：也就是使用結尾只有一次捨入的複合運算來取代多次運算。

- 不允許對特殊值 (NaN、+infinity、-infinity、+0、-0) 無效的運算式最佳化。 最佳化 x x = > 0 x * 0 = > 0，x-0 = > x、 x + 0 = > x 和 0-x = >-x 會因為各種原因而無效。 (請參閱 IEEE 754 和 C99 標準)。

- 編譯器可正確處理涉及 NaN 的比較。 例如，x ！ = x 會評估為**true**如果`x`是 NaN，和已排序涉及 NaN 的比較會引發例外狀況。

- 運算式評估會遵循 C99 FLT_EVAL_METHOD=2，但有以下例外狀況：當您為 x86 處理器進行設計程式時，由於 FPU 設定為 53 位元精確度，因此這會視為長雙精確度。

- 剛好乘以 1.0 的乘法結果會轉換成使用其他因數， x * y\*1.0 會轉換成 x\*y。 同樣地，x\*1.0\*y 會轉換成 x\*y。

- 剛好除以 1.0 的除法結果會轉換成使用被除數。 x * y/1.0 會轉換成 x\*y。 同樣地，x / 1.0\*y 會轉換成 x\*y。

使用 **/fp： 精確**時[fenv_access](../../preprocessor/fenv-access.md)所在停用最佳化，例如浮點運算式的編譯時期評估。 例如，如果您使用[_control87、 _controlfp、 \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)變更捨入模式，而編譯器會執行浮點計算，您所指定的捨入模式不是作用中除非`fenv_access`是 ON。

**/fp： 精確**取代 **/Op**編譯器選項。

#### <a name="fast"></a>快速

**/Fp: fast**選項在大部分情況下建立最快的程式碼，藉由放寬最佳化浮點運算的規則。 這樣會讓編譯器犧牲準確度和正確性，以最佳化浮點程式碼的速度。 當 **/fp: fast**指定，則編譯器可能會不正確捨入在指派陳述式、 類型轉換或函式呼叫，以及可能不會執行捨入中繼運算式。 編譯器可能會藉由像是遵循關聯和分散規則的方式重新排列運算或執行代數轉換，而不考慮對有限精確度結果的影響。 編譯器可能會將運算和運算元變更為單精確度，而不遵循 C++ 類型提升規則。 一定會啟用浮點點對點特定縮減最佳化 ([fp_contract](../../preprocessor/fp-contract.md)是 ON)。 浮點例外狀況和 FPU 環境存取已停用 (**/fp： 除了-** 隱含和[fenv_access](../../preprocessor/fenv-access.md)是 OFF)。

**/fp: fast**不能與 **/fp: strict**或 **/fp： 精確**。 會使用命令列上指定的最後一個選項。 指定這兩者 **/fp: fast**和 **/fp： 除了**會產生編譯器錯誤。

指定[/Za，/Ze （停用語言擴充功能）](../../build/reference/za-ze-disable-language-extensions.md) （ANSI 相容性） 和 **/fp: fast**可能會造成非預期的行為。 例如，單精確度浮點運算可能不會捨入為單精確度。

#### <a name="except"></a>除了

**/Fp： 除了**選項會啟用可靠的浮點例外狀況模型。 觸發例外狀況之後會立即引發例外狀況。 根據預設，這個選項為關閉狀態。 附加減號至選項 (**/fp： 除了-**) 明確停用。

#### <a name="strict"></a>strict

**/Fp: strict**選項可讓最嚴謹的浮點模型。 **/fp: strict**導致[fp_contract](../../preprocessor/fp-contract.md)是 OFF 和[fenv_access](../../preprocessor/fenv-access.md)是 ON。 **/fp： 除了**隱含的可以藉由明確指定停用 **/fp： 除了-**。 當搭配 **/fp： 除了-**， **/fp: strict**強制執行嚴格浮點語意但不考慮例外事件。

## <a name="remarks"></a>備註

多個 **/fp**相同編譯中，您可以指定選項。

若要控制浮點數行為函式，請參閱[float_control](../../preprocessor/float-control.md) pragma。 這會覆寫 **/fp**編譯器設定。 建議的理想設計做法是儲存並還原本機浮點行為：

```cpp
#pragma float_control(precise, on, push)
// Code that uses /fp:precise mode
#pragma float_control(pop)
```

大部分的浮點最佳化作業的相關 **/fp: strict**， **/fp： 除了**（和及其對應 pragma） 和`fp_contract`pragma 會電腦相關。 **/fp: strict**和 **/fp： 除了**與不相容 **/clr**。

**/fp： 精確**應該可滿足大部分的應用程式的浮點需求。 您可以使用 **/fp： 除了**和 **/fp: strict**，但可能會使效能稍微降低。 如果效能是最重要的請考慮是否使用 **/fp: fast**。

**/fp: strict**， **/fp: fast**，和 **/fp： 精確**精確度 （正確性） 模式。 但一次只能有一個模式生效。 如果兩個 **/fp: strict**和 **/fp： 精確**指定，則編譯器會使用最後處理的那一個。 同時 **/fp: strict**和 **/fp: fast**不指定。

如需詳細資訊，請參閱[Microsoft Visual c + + 浮點最佳化](floating-point-optimization.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 展開**組態屬性** > **C/c + +** > **程式碼產生**屬性頁。

1. 修改**浮點模型**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>。

## <a name="see-also"></a>另請參閱

- [編譯器選項](compiler-options.md)
- [設定編譯器選項](setting-compiler-options.md)
- [Microsoft Visual c + + 的浮動點最佳化](floating-point-optimization.md)