---
title: /Qvec-report (自動向量化工具報告層級)
ms.date: 11/04/2016
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
ms.openlocfilehash: 2007e80db0ee0aec362869315767505ec06ab109
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836864"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report (自動向量化工具報告層級)

啟用編譯器 [自動向量化工具](../../parallel/auto-parallelization-and-auto-vectorization.md) 的報告功能，並指定在編譯期間輸出的資訊訊息層級。

## <a name="syntax"></a>語法

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>備註

**/Qvec-report：1**<br/>
輸出向量化之迴圈的參考訊息。

**/Qvec-report：2**<br/>
輸出向量化和 for 迴圈（未向量化）的參考訊息，以及原因代碼。

如需原因代碼和訊息的詳細資訊，請參閱 [向量化工具和平行化工具訊息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定/Qvec-report 編譯器選項

1. 在 **方案總管**中，開啟專案的快捷方式功能表，然後選擇 [ **屬性**]。

1. 在 [ **屬性頁** ] 對話方塊的 [ **C/c + +**] 底下，選取 [ **命令列**]。

1. 在 [ **其他選項** ] 方塊中，輸入 `/Qvec-report:1` 或 `/Qvec-report:2` 。

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>以程式設計方式設定/Qvec-report 編譯器選項

- 請使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的範例程式碼。

## <a name="see-also"></a>另請參閱

[ (低層級作業的/q 選項) ](q-options-low-level-operations.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[Visual Studio 中的機器碼向量化](/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
