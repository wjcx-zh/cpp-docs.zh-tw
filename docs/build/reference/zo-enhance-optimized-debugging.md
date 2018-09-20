---
title: -Zo （增強最佳化偵錯） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- -Zo
- /Zo
dev_langs:
- C++
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b40f7b4fff1d6df6f5fb818e090ce687f12a7b4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412783"
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo (增強最佳化的偵錯)

在非偵錯組建中產生適用於最佳化程式碼的增強型偵錯資訊。

## <a name="syntax"></a>語法

```cpp
/Zo[-]
```

## <a name="remarks"></a>備註

**/Zo**編譯器參數會產生最佳化的程式碼的增強型偵錯資訊。 最佳化可能會將暫存器用於區域變數、重新排列程式碼、向量化迴圈和內嵌函式呼叫。 這些最佳化可能會混淆原始程式碼與已編譯的目的碼之間的關係。 **/Zo**參數會指示編譯器產生的區域變數和內嵌函式的其他偵錯資訊。 使用它來查看中的變數**自動變數**，**區域變數**，並**監看式**windows 時逐步執行最佳化 Visual Studio 偵錯工具中的程式碼。 它也能在 WinDBG 偵錯工具中啟用堆疊追蹤以顯示內嵌函式。 偵錯已停用最佳化的組建 ([/Od](../../build/reference/od-disable-debug.md)) 不需要額外的偵錯資訊，產生 **/Zo**指定。 使用 **/Zo**切換至偵錯已開啟最佳化的發行組態。 如需最佳化參數的詳細資訊，請參閱[/O 選項 （最佳化程式碼）](../../build/reference/o-options-optimize-code.md)。 **/Zo**當您指定偵錯資訊時，將會啟用在 Visual Studio 中預設的選項 **/Zi**或是 **/z7**。 指定 **/Zo-** 明確停用此編譯器選項。

**/Zo**交換器可從 Visual Studio 2013 Update 3 開始，它會取代先前未記載 **/d2Zi+** 切換。

### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定 /Zo 編譯器選項

1. 開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性**， **C/c + +** 資料夾。

1. 選取 **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括`/Zo`，然後選擇**確定**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[/O 選項 (最佳化程式碼)](../../build/reference/o-options-optimize-code.md)<br/>
[/Z7、/Zi、/ZI (偵錯資訊格式)](../../build/reference/z7-zi-zi-debug-information-format.md)<br/>
[編輯後繼續](/visualstudio/debugger/edit-and-continue)