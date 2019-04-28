---
title: /STACK (堆疊配置)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.StackReserveSize
- VC.Project.VCLinkerTool.StackCommitSize
- /stack
helpviewer_keywords:
- STACK linker option
- -STACK linker option
- memory allocation, stack
- /STACK linker option
- stack, setting size
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
ms.openlocfilehash: 27de554e1933b2753f641be358461c8d7ff4fffa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317922"
---
# <a name="stack-stack-allocations"></a>/STACK (堆疊配置)

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>備註

/STACK 選項會設定堆疊大小，以位元組為單位。 只在您建置的.exe 檔案時，請使用此選項。

`reserve`值指定虛擬記憶體中堆疊配置總量。 ARM，x86 和 x64 電腦，預設堆疊大小為 1 MB。

`commit` 受限於由作業系統的解譯方式。 在 Windows RT 中，它是指定一次要配置的實體記憶體數量。 已認可的虛擬記憶體會造成要保留在分頁檔的空間。 當應用程式需要較多的堆疊空間時，較高的 `commit` 值可以節省時間，但會增加記憶體需求且可能增加啟動時間。 針對 ARM，x86 和 x64 電腦，預設 commit 值會是 4 KB。

以十進位數或 C 語言標記法指定 `reserve` 和 `commit` 值。

若要設定的堆疊大小的另一個方法是使用[STACKSIZE](stacksize.md)模組定義 (.def) 檔中的陳述式。 **STACKSIZE**覆寫堆疊配置 (/stack) 選項時如果同時指定這兩者。 您可以使用建置的.exe 檔案之後，變更堆疊大小[EDITBIN](editbin-reference.md)工具。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **連結器**資料夾。

1. 選取 **系統**屬性頁。

1. 修改下列屬性之一：

   - **堆疊基本配置大小**

   - **Stack Reserve Size**

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> 屬性。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
