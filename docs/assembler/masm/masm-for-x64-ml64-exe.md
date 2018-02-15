---
title: "MASM (ml64.exe) x64 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a42b25b5d86d181bed907a3b437d28f3cbf5e820
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="masm-for-x64-ml64exe"></a>適用於 x64 的 MASM (ml64.exe)

Visual Studio 包含 32 位元和 64 位元裝載的版本 MASM 目標 x64 程式碼。 名為 ml64.exe，這是可接受 x64 組譯工具組譯工具的語言。 當您在 Visual Studio 安裝期間選擇的 c + + 工作負載時，會安裝 MASM 命令列工具。 無法使用個別下載這些工具。 若要下載並安裝 Visual Studio 的複本，請參閱[https://www.visualstudio.com/](https://www.visualstudio.com/)。 如果您不想要安裝 Visual Studio IDE 中，而只想要的命令列工具，請參閱**建置工具的 Visual Studio 2017**選項[Visual Studio 下載](https://www.visualstudio.com/downloads/)頁面。

若要建置使用 MASM 程式碼適用於 x64 目標命令列上，您必須使用適用於 x64 的開發人員命令提示字元設定必要的路徑和其他環境變數的目標。 如需如何開發人員命令提示字元啟動資訊，請參閱[命令列上的建置 C/c + + 程式碼](../../build/building-on-the-command-line.md)。

如需 ml64.exe 命令列選項的資訊，請參閱[ML 和 ML64 命令列參照](../../assembler/masm/ml-and-ml64-command-line-reference.md)。  
  
適用於 x64 或 ARM 為目標不支援內嵌組譯工具或 ASM 關鍵字的使用。 移植您的 x86 程式碼，會使用內嵌組譯工具要 x64 或 ARM，請將您的程式碼轉換成 c + +、 使用編譯器內建函式，或建立組合器語言原始程式檔。 Visual c + + 編譯器支援內建函式可讓您使用特殊函式指示的範例中，特殊權限，位元掃描/測試，連鎖，等等，在做為接近儘可能以跨平台的方式。 如需可用的內建函式的資訊，請參閱[編譯器內建](../../intrinsics/compiler-intrinsics.md)。  

## <a name="add-an-assembler-language-file-to-a-visual-c-project"></a>Visual c + + 專案中加入的組譯工具語言檔案  
  
Visual Studio 專案系統支援使用 c + + 專案中的 MASM 所建置的組譯工具語言檔案。 您可以建立的 x64 組合器語言來源檔，並使用可完全支援 x64 的 MASM 建置成物件檔案。 然後可以將這些目的檔連結至 c + + 程式碼針對 x64 建置目標。 這是一種方式克服 x64 缺乏內嵌組譯工具。  

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-c-project"></a>將組譯工具語言檔案加入至現有的 Visual c + + 專案

1. 選取的專案中**方案總管 中**。 在功能表列上選擇 **專案**，**建置自訂**。

1. 在**Visual c + + 組建自訂檔**對話方塊方塊中，選取核取方塊旁的  **masm(.targets,.props)**。 選擇**確定**儲存您的選擇並關閉對話方塊。

1. 在功能表列上選擇 **專案**，**加入新項目**。 

1. 在**加入新項目**對話方塊中，選取**c + + 檔 (.cpp)**中間窗格內。 在**名稱**編輯控制項中，輸入新的檔案名稱具有**.asm**而不是.cpp 副檔名。 選擇**新增**將檔案加入您的專案，並關閉對話方塊。

您新增的.asm 檔案中建立您的組譯工具語言程式碼。 當您建置方案時，MASM 組合器會叫用來將.asm 檔組合成然後連結至您的專案檔。 若要簡化符號的存取，宣告組譯工具函式做為`extern "C"`在 c + + 程式碼中，而不是使用 c + + 名稱裝飾慣例，在您的組譯工具-語言原始程式檔。
  
## <a name="ml64-specific-directives"></a>ml64 特定指示詞  

您可以使用下列 ml64 特定指示詞程式碼中組譯工具語言來源為 x64 的目標：  
  
-   [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)  
  
-   [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)  
  
-   [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)  
  
-   [.PUSHREG](../../assembler/masm/dot-pushreg.md)  
  
-   [.SAVEREG](../../assembler/masm/dot-savereg.md)  
  
-   [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)  
  
-   [.SETFRAME](../../assembler/masm/dot-setframe.md)  
  
此外， [PROC](../../assembler/masm/proc.md)指示詞已更新 ml64.exe 搭配使用。  
  
## <a name="32-bit-address-mode-address-size-override"></a>32 位元位址模式 （位址大小覆寫）  

如果記憶體運算元包含 32 位元暫存器，MASM 就會發出 0x67 位址大小覆寫。 例如，下列範例會導致發出的位址大小覆寫：  
  
```MASM  
mov rax, QWORD PTR [ecx]  
mov eax, DWORD PTR [ecx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10d+0100h]  
prefetch [eax]  
movnti rax, QWORD PTR [r8d]  
```  
  
MASM 假設如果 32 位元位移出現單獨記憶體運算元，64 位元定址要。 目前沒有與這類運算元定址的 32 位元的支援。  
  
最後，如下列程式碼所示混用內記憶體運算元的暫存器大小會產生錯誤。  
  
```MASM  
mov eax, DWORD PTR [rcx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10+0100h]  
```  
  
## <a name="see-also"></a>請參閱  

[Microsoft 巨集組譯工具參考](../../assembler/masm/microsoft-macro-assembler-reference.md)