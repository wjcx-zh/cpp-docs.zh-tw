---
title: -QIfist （隱藏 _ftol） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /qifist
dev_langs:
- C++
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b32557507cbe74fc1fde3963a1375318c7ef1e0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448261"
---
# <a name="qifist-suppress-ftol"></a>/QIfist (抑制 _ftol)

已取代。 在必須從浮點類型轉換為整數類型時，抑制對 Helper 函式 `_ftol` 的呼叫。

## <a name="syntax"></a>語法

```
/QIfist
```

## <a name="remarks"></a>備註

> [!NOTE]
>  **/Qifist**僅供以編譯器目標 x86; 這個編譯器選項不適用於以 x64 為目標的編譯器 Arm。

除了從浮點類型轉換成整數類資料類型，`_ftol`函式可確保趨近於零 （截斷），是藉由設定 10 和 11 位元的控制字組的浮點單位 (FPU) 的捨入模式。 這可確保會從浮點類型轉換成整數類資料類型發生 ANSI C 標準 （數字的小數部分會被捨棄） 所述。 使用時 **/QIfist**，這項保證就不再適用。 捨入模式將會是其中四個 Intel 參考手冊所述：

- 四捨五入到最接近 （偶數如果等距）

- 往負無限大方向捨入

- 趨向正無限大捨入

- 趨近於零的捨入

您可以使用[_control87、 _controlfp， \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C 執行階段函式來修改 FPU 捨入行為。 捨入模式的 FPU 預設值是"趨向最接近。 」 使用 **/QIfist**可以改善效能，您的應用程式，但不是沒有風險。 您應該徹底測試您的程式碼所依賴的程式碼以在建置之前，捨入模式的部分 **/QIfist**在生產環境中。

[/arch (x86)](../../build/reference/arch-x86.md)並 **/QIfist**不適用於在相同的編譯模組。

> [!NOTE]
>  **/Qifist**是不作用中預設因為捨入位元也會影響浮點數到浮點數會指向捨入 （發生於每次計算之後），因此當您設定的旗標 （趨近於零） 的 C 樣式捨入，您的浮點數計算可能會不同。 **/Qifist**不應在截斷的小數部分的浮點數的預期行為取決於您的程式碼。 如果您不確定，請不要使用 **/QIfist**。

**/QIfist**選項已被取代，在 Visual Studio 2005 中啟動。 編譯器已對有長足的改進在 float int 轉換速度。 如需已被取代的編譯器選項的清單，請參閱 <<c0>  **已取代及移除的編譯器選項**中[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [命令列]  屬性頁。

1. 在 [其他選項]  方塊中，輸入編譯器選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/Q 選項 (低階運算)](../../build/reference/q-options-low-level-operations.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)