---
title: /Qpar-report (自動平行化工具報告層級)
ms.date: 11/04/2016
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
ms.openlocfilehash: 25732900fa201258331dcb8eee96af9ba97a6def
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818384"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report (自動平行化工具報告層級)

啟用報告功能的編譯器[Auto-parallelizer](../../parallel/auto-parallelization-and-auto-vectorization.md) ，並在編譯期間指定的輸出參考用訊息層級。

## <a name="syntax"></a>語法

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>備註

**/Qpar-report:1**<br/>
輸出已平行化之迴圈的資訊訊息。

**/Qpar-report:2**<br/>
輸出已平行化之迴圈的資訊訊息，並輸出未平行化之迴圈的資訊訊息連同原因碼。

訊息會報告至 stdout。 如果未報告資訊訊息，則可能是程式碼不包含迴圈，或是報告層級並未設定成報告未平行化的迴圈。 如需原因代碼和訊息的詳細資訊，請參閱[向量化工具和平行化工具訊息](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)。

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定 /Qpar 編譯器選項

1. 在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。

1. 在 **屬性頁**對話方塊的  **C/c + +**，選取**命令列**。

1. 在 **其他選項**方塊中，輸入`/Qpar-report:1`或`/Qpar-report:2`。

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>以程式設計方式設定 /Qpar-report 編譯器選項

- 請使用 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> 中的範例程式碼。

## <a name="see-also"></a>另請參閱

[/Q 選項 (低階運算)](q-options-low-level-operations.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)<br/>
[以原生程式碼進行平行程式設計](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)
