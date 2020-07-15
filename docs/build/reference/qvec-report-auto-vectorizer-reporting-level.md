---
title: /Qvec-report (自動向量化工具報告層級)
ms.date: 11/04/2016
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
ms.openlocfilehash: 260cf89d50110f960eb6f320dccbb4a1d80f65bc
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373810"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report (自動向量化工具報告層級)

啟用編譯器[自動向量化工具](../../parallel/auto-parallelization-and-auto-vectorization.md)的報告功能，並指定在編譯期間輸出的資訊訊息層級。

## <a name="syntax"></a>語法

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>備註

**/Qvec-report：1**<br/>
輸出向量化之迴圈的參考用訊息。

**/Qvec-report：2**<br/>
針對向量化的迴圈以及未向量化的迴圈，連同原因代碼，輸出參考用訊息。

如需原因代碼和訊息的詳細資訊，請參閱[向量化工具和平行化工具訊息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定/Qvec-report 編譯器選項

1. 在**方案總管**中，開啟專案的快捷方式功能表，然後選擇 [**屬性**]。

1. 在 [**屬性頁**] 對話方塊的 [ **C/c + +**] 底下，選取 [**命令列**]。

1. 在 [**其他選項**] 方塊中，輸入 `/Qvec-report:1` 或 `/Qvec-report:2` 。

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>以程式設計方式設定/Qvec-report 編譯器選項

- 請使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的範例程式碼。

## <a name="see-also"></a>另請參閱

[/Q 選項（低層級作業）](q-options-low-level-operations.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[Visual Studio 中的原生程式碼向量化](https://docs.microsoft.com/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
