---
title: 適用於 x64 的 MASM (ml64.exe)
ms.date: 08/30/2018
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: d9b550313c8e65e47db70dc81519abce7db95da5
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050208"
---
# <a name="masm-for-x64-ml64exe"></a>適用於 x64 的 MASM (ml64.exe)

Visual Studio 同時包含32位和64位裝載版本的 Microsoft 組合器（MASM），以 x64 程式碼為目標。 命名為 ml64，這是可接受 x64 組合器語言的組合器。 當您在 Visual Studio 安裝期間選擇C++工作負載時，會安裝 MASM 命令列工具。 MASM 工具無法以個別下載的形式提供。 如需有關如何下載及安裝 Visual Studio 複本的指示，請參閱[install Visual Studio](/visualstudio/install/install-visual-studio)。 如果您不想要安裝完整的 Visual Studio IDE，但只想要命令列工具，請下載 Visual Studio 的[組建工具](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)。

若要使用 MASM 在命令列上建立 x64 目標的程式碼，您必須針對 x64 目標使用開發人員命令提示字元，以設定所需的路徑和其他環境變數。 如需如何啟動開發人員命令提示字元的詳細資訊，請參閱在[命令列上建立 C/C++程式碼](../../build/building-on-the-command-line.md)。

如需 ml64 命令列選項的詳細資訊，請參閱[ML 和 Ml64 命令列參考](../../assembler/masm/ml-and-ml64-command-line-reference.md)。

X64 或 ARM 目標不支援內嵌組譯工具或使用 ASM 關鍵字。 若要將使用內嵌組譯工具的 x86 程式碼移植到 x64 或 ARM，您可以C++將程式碼轉換成、使用編譯器內建函式或建立組合語言原始程式檔。 Microsoft C++編譯器支援內建函式，可讓您在盡可能接近跨平臺的情況下，使用特殊功能的指令，例如，許可權、位掃描/測試、連鎖等等。 如需可用內建函式的詳細資訊，請參閱[編譯器內建函式](../../intrinsics/compiler-intrinsics.md)。

## <a name="add-an-assembler-language-file-to-a-visual-studio-c-project"></a>將組合語言檔案加入至 Visual Studio C++專案

Visual Studio 專案系統支援在您C++的專案中使用 MASM 建立的組合語言檔案。 您可以建立 x64 組合器語言原始程式檔，並使用 MASM，將其建立成物件檔案，以完整支援 x64。 然後，您可以將這些物件檔案連結C++至針對 x64 目標所建立的程式碼。 這是克服缺乏 x64 內嵌組合語言的一種方法。

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-studio-c-project"></a>若要將組合語言檔案加入至現有的 Visual Studio C++專案

1. 在 [方案總管] 中選取專案。 在功能表列上，選擇 [**專案**]、[**建立自訂**]。

1. 在 [ **Visual C++ Build 自訂**檔] 對話方塊中，選取 [ **masm （.targets，. .props）** ] 旁的核取方塊。 選擇 **[確定]** 以儲存選取專案並關閉對話方塊。

1. 在功能表列上，選擇 [**專案**]、[**加入新專案**]。

1. 在 [**加入新專案**] 對話方塊中，選取**C++** 中央窗格中的 [檔案（.cpp）]。 在 [**名稱**] 編輯控制項中，輸入副檔名為 **.asm**而不是 .cpp 的新檔案名。 選擇 [**新增**] 將檔案新增至您的專案，並關閉對話方塊。

在您新增的 .asm 檔案中建立組合語言程式語言代碼。 當您建立方案時，會叫用 MASM 組合器，將該 .asm 檔案組合成物件檔案，然後連結至您的專案。 若要讓符號存取變得更容易，請將您的C++組合器函式宣告為原始程式碼C++中的 `extern "C"`，而不是在組合語言來源檔案中使用名稱裝飾慣例。

## <a name="ml64-specific-directives"></a>ml64 特有的指示詞

您可以在以 x64 為目標的組合語言原始程式碼中，使用下列 ml64 特有的指示詞：

- [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)

- [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)

- [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)

- [.PUSHREG](../../assembler/masm/dot-pushreg.md)

- [.SAVEREG](../../assembler/masm/dot-savereg.md)

- [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)

- [.SETFRAME](../../assembler/masm/dot-setframe.md)

此外， [PROC](../../assembler/masm/proc.md)指示詞已更新，可與 ml64 搭配使用。

## <a name="32-bit-address-mode-address-size-override"></a>32位位址模式（位址大小覆寫）

如果記憶體運算元包含32位暫存器，MASM 就會發出0x67 位址大小覆寫。 例如，下列範例會導致發出位址大小覆寫：

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM 假設當32位置換單獨出現為記憶體運算元時，會預期使用64位定址。 目前不支援使用這類運算元的32位定址。

最後，在記憶體運算元內混合暫存器大小，如下列程式碼所示，會產生錯誤。

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>請參閱

[Microsoft 巨集組譯工具參考](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>