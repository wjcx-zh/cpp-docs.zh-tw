---
title: /Qfast_transcendentals (Force Fast Transcendentals)
ms.date: 11/04/2016
f1_keywords:
- /Qfast_transcendentals
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
ms.openlocfilehash: d96b2c93e9fc8be73ef43f63fc0a6328661df442
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414196"
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Force Fast Transcendentals)

產生先驗函式的內嵌程式碼。

## <a name="syntax"></a>語法

```
/Qfast_transcendentals
```

## <a name="remarks"></a>備註

這個編譯器選項會強制先驗函式轉換成內嵌程式碼，以提升執行速度。 此選項沒有作用，只有在搭配時，才 **/fp： 除了**或是 **/fp： 精確**。 產生先驗函式的內嵌程式碼已下的預設行為 **/fp: fast**。

此選項與不相容 **/fp: strict**。 請參閱[/fp （指定浮點行為）](../../build/reference/fp-specify-floating-point-behavior.md)如需浮點編譯器選項的詳細資訊。

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
