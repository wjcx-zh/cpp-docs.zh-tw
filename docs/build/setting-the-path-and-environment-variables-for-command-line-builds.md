---
title: "設定命令列建置的路徑和環境變數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- include
- Lib
- Path
dev_langs:
- C++
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76fa1a14b4fd60f249ab015f6618e386bda7c86f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>設定命令列建置的路徑和環境變數

Visual c + + 命令列建置工具需要您的安裝和組建組態所自訂的數個環境變數。 所安裝的 c + + 工作負載時[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]安裝程式，它會建立自訂的命令檔，或是設定必要的環境變數的批次檔。 安裝程式然後會使用這些命令檔案建立 [開始] 功能表開啟 [開發人員命令提示字元] 視窗的快速鍵。 這些快速鍵設定的環境變數，針對特定建置組態。 當您想要使用命令列工具時，您可以執行其中一個捷徑，或您可以開啟純文字的命令提示字元視窗，然後執行其中一個自訂命令檔案要自行設定組建組態的環境。 如需詳細資訊，請參閱[命令列上建置 C/c + + 程式碼](building-on-the-command-line.md)。  
  
Visual c + + 命令列工具使用的路徑、 TMP、 INCLUDE、 LIB 及 LIBPATH 環境變數，且也使用您已安裝的工具、 平台和 Sdk 的特定其他環境變數。 即使簡單[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]安裝可能會設定 20 個或多個環境變數。 由於這些環境變數的值是針對您的安裝和您所選擇的組建組態，而且可以變更產品更新或升級，我們強烈建議使用開發人員命令提示字元捷徑或其中一個自訂設定，而不是自己設定這些 Windows 環境中的命令檔。 

若要查看哪些環境變數由開發人員命令提示字元捷徑設定，您可以使用 SET 命令。 開啟 [純文字的命令提示字元] 視窗，並擷取基準 SET 命令的輸出。 開啟開發人員命令提示字元視窗，並擷取輸出的 SET 命令進行比較。 差異工具，例如內建於 Visual Studio IDE 可比較的環境變數，並請參閱什麼由開發人員命令提示字元中設定。 編譯器和連結器所使用的特定環境變數的相關資訊，請參閱[CL 環境變數](../build/reference/cl-environment-variables.md)和[LINK 環境變數](../build/reference/link-environment-variables.md)。  
  
> [!NOTE]
>  數個命令列工具或工具選項，可能需要系統管理員權限。 如果您有權限問題，當您使用它們時，我們建議您利用開啟開發人員命令提示字元視窗**系統管理員身分執行**選項。 在 Windows 10 上按一下滑鼠右鍵以開啟 命令提示字元 視窗的捷徑功能表，然後選擇 **詳細**，**系統管理員身分執行**。  
  
## <a name="see-also"></a>請參閱  

[在命令列上建置 C/c + + 程式碼](../build/building-on-the-command-line.md)   
[連結](../build/reference/linking.md)   
[連結器選項](../build/reference/linker-options.md)   
[編譯 C/c + + 程式](../build/reference/compiling-a-c-cpp-program.md)   
[編譯器選項](../build/reference/compiler-options.md)