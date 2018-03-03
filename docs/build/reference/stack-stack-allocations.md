---
title: "堆疊 （堆疊配置） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.StackReserveSize
- VC.Project.VCLinkerTool.StackCommitSize
- /stack
dev_langs:
- C++
helpviewer_keywords:
- STACK linker option
- -STACK linker option
- memory allocation, stack
- /STACK linker option
- stack, setting size
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6b487ff830abd3dfa97a748c81d541cbd9fdd0b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="stack-stack-allocations"></a>/STACK (堆疊配置)
```  
/STACK:reserve[,commit]  
```  
  
## <a name="remarks"></a>備註  
 /STACK 選項會設定堆疊的大小，以位元組為單位。 只有當您建置的.exe 檔時，才使用此選項。  
  
 `reserve`值指定虛擬記憶體中堆疊配置總量。 若是 ARM、x86 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 電腦，預設堆疊大小是 1 MB。  
  
 `commit`受限於作業系統所解譯。 在 Windows RT 中，它是指定一次要配置的實體記憶體數量。 已認可的虛擬記憶體會造成要保留在分頁檔的空間。 當應用程式需要較多的堆疊空間時，較高的 `commit` 值可以節省時間，但會增加記憶體需求且可能增加啟動時間。 若是 ARM、x86 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 電腦，預設 commit 值是 4 KB。  
  
 以十進位數或 C 語言標記法指定 `reserve` 和 `commit` 值。  
  
 若要設定堆疊的大小的另一個方法是使用[STACKSIZE](../../build/reference/stacksize.md)模組定義 (.def) 檔中的陳述式。 **STACKSIZE**覆寫堆疊配置 （/ 堆疊） 選項時如果同時指定這兩者。 您可以使用建置的.exe 檔案之後，變更堆疊大小[EDITBIN](../../build/reference/editbin-reference.md)工具。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**連結器**資料夾。  
  
3.  選取**系統**屬性頁。  
  
4.  修改下列屬性的其中一個：  
  
    -   **堆疊基本配置大小**  
  
    -   **堆疊預留大小**  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> 屬性。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)