---
title: /vd (停用建構替代)
ms.date: 11/04/2016
f1_keywords:
- /vd
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
ms.openlocfilehash: df8891cc71dd5a4cfd417969578c0c1b46ae3be3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223807"
---
# <a name="vd-disable-construction-displacements"></a>/vd (停用建構替代)

## <a name="syntax"></a>語法

```
/vdn
```

## <a name="arguments"></a>引數

**0**<br/>
抑制 vtordisp 的函式/析構函數置換成員。 只有在您確定所有類別的函式和析構函式都呼叫虛擬函式時，才選擇這個選項。

**1**<br/>
可讓您建立隱藏的 vtordisp 函數/析構函式置換成員。 此選項為預設。

**2**<br/>
可讓您在所結構化的物件上使用[Dynamic_cast 運算子](../../cpp/dynamic-cast-operator.md)。 例如，從虛擬基類到衍生類別的 dynamic_cast。

當您具有虛擬函式的虛擬基底時， **/vd2**會新增 vtordisp 欄位。 **/vd1**應該就足夠了。 最常見的情況是，當您的虛擬基底中唯一的虛擬函式為「析構函數」時， **/vd2**是必要的。

## <a name="remarks"></a>備註

這些選項僅適用于使用虛擬基底的 c + + 程式碼。

Visual C++ 在使用虛擬繼承的情況下，會執行 c + + 結構置換支援。 結構置換可解決當虛擬函式在衍生類別中宣告時所建立的問題，在進一步衍生類別的結構期間，會從函式中呼叫。

問題在於， **`this`** 因為對類別的虛擬基底的置換和其衍生類別的置換之間的差異，可能會導致虛擬函式被傳遞不正確的指標。 解決方案為類別的每個虛擬基底提供單一的結構置換調整（稱為 vtordisp 欄位）。

根據預設，每當程式碼定義使用者定義的函數和析構函式，而且也覆寫虛擬基底的虛擬函式時，就會引進 vtordisp 欄位。

這些選項會影響整個原始檔。 您可以使用[vtordisp](../../preprocessor/vtordisp.md) ，依類別逐一隱藏和重新啟用 vtordisp 欄位。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++] **** 資料夾。

1. 按一下 [命令列] **** 屬性頁。

1. 在 [其他選項] **** 方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
