---
title: 適用於 x64 的 MASM (ml64.exe)
ms.date: 08/30/2018
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 0404bff54a08988a72fcb0a0c075a4446bf90f48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596218"
---
# <a name="masm-for-x64-ml64exe"></a>適用於 x64 的 MASM (ml64.exe)

Visual Studio 包含 32 位元和 64 位元裝載的版本的 Microsoft Assembler (MASM) x64 的程式碼。 名為 ml64.exe，這是可接受 x64 組譯工具組譯工具的語言。 當您在 Visual Studio 安裝期間選擇 c + + 工作負載時，會安裝 MASM 命令列工具。 MASM 工具不提供個別下載。 如需如何下載和安裝 Visual Studio 的指示，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。 如果您執行不想要安裝完整的 Visual Studio IDE，但只想要的命令列工具，下載[Build Tools for Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721)。

若要使用 MASM 來建置適用於 x64 的程式碼目標為命令列上，您必須使用適用於 x64 的開發人員命令提示字元設定必要的路徑和其他環境變數的目標。 如需如何開始開發人員命令提示字元，請參閱[命令列上的建置 C/c + + 程式碼](../../build/building-on-the-command-line.md)。

如需 ml64.exe 命令列選項的資訊，請參閱[ML 和 ML64 命令列參考](../../assembler/masm/ml-and-ml64-command-line-reference.md)。

X64 或 ARM 目標不支援內嵌組譯工具或 ASM 關鍵字的使用。 移植您的 x86 程式碼，會使用內嵌組譯工具 x64 或 ARM，您可以將您的程式碼轉換成 c + +、 使用編譯器內建函式，或建立組合器語言原始程式檔。 Visual c + + 編譯器支援內建函式可讓您使用特殊函式的指示，如範例中，特殊權限，位元掃描/測試，連鎖，等等，在為接近盡可能以跨平台的方式。 如需可用的內建函式的資訊，請參閱[編譯器內建](../../intrinsics/compiler-intrinsics.md)。

## <a name="add-an-assembler-language-file-to-a-visual-c-project"></a>Visual c + + 專案中加入的組譯工具語言檔案

Visual Studio 專案系統支援使用 c + + 專案中的 MASM 所建置的組譯工具語言檔案。 您可以建立的 x64 組合器語言來源檔，並使用可完全支援 x64 的 MASM 將它們建置到物件的檔案。 然後可以將這些物件檔案連結在您針對 x64 建置的 c + + 程式碼的目標。 這是一種方式克服 x64 缺乏內嵌組譯工具。

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-c-project"></a>將組譯工具語言檔案加入至現有的 Visual c + + 專案

1. 在 [方案總管] 中選取專案。 在功能表列上選擇 **專案**，**組建自訂**。

1. 在  **Visual c + + 組建自訂檔**對話方塊方塊中，旁邊的核取方塊**masm(.targets,.props)**。 選擇**確定**以儲存您的選擇，並關閉對話方塊。

1. 在功能表列上選擇 **專案**，**加入新項目**。

1. 在 **加入新項目**對話方塊中，選取**c + + 檔 (.cpp)** 在中央窗格中。 在 **名稱**編輯控制項中，輸入新的檔案名稱具有 **.asm**而不是.cpp 的延伸模組。 選擇**新增**檔案加入您的專案，並關閉對話方塊。

在您新增的.asm 檔案組譯工具語言的程式碼。 當您建置方案時，「 MASM 組合器 」 會叫用來將.asm 檔組合成會接著連結至您的專案檔。 若要簡化符號的存取，宣告您的組譯工具函式，做為`extern "C"`c + + 程式碼中，而不是使用 c + + 名稱裝飾慣例，在您的組譯工具-語言原始程式檔。

## <a name="ml64-specific-directives"></a>ml64 特有指示詞

組合器語言程式碼中以 x64 為目標，您可以使用下列的 ml64 特有指示詞：

- [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)

- [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)

- [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)

- [.PUSHREG](../../assembler/masm/dot-pushreg.md)

- [.SAVEREG](../../assembler/masm/dot-savereg.md)

- [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)

- [.SETFRAME](../../assembler/masm/dot-setframe.md)

颾魤 ㄛ [PROC](../../assembler/masm/proc.md)已用於 ml64.exe 更新指示詞。

## <a name="32-bit-address-mode-address-size-override"></a>32 位元的位址模式 （位址大小覆寫）

如果記憶體運算元包含 32 位元暫存器，MASM 就會發出 0x67 位址大小覆寫。 例如，下列範例會造成位址大小覆寫，就會發出：

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM 假設，如果單獨做為記憶體運算元時，出現的 32 位元移動，64 位元位址是。 目前沒有使用這類運算元定址的 32 位元的支援。

最後，混合內記憶體運算元的暫存器大小，如下列程式碼所示，會產生錯誤。

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>另請參閱

[Microsoft 巨集組譯工具參考](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>