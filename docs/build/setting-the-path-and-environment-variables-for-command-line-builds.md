---
title: 設定指令列產生的路徑與環境變數
ms.custom: conceptual
ms.date: 07/24/2019
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
ms.openlocfilehash: aeafe806e5d29b89c243586974814aa7cfc16d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335591"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>設定指令列產生的路徑與環境變數

Microsoft C++ (MSVC) 命令列生成工具需要為安裝和生成配置自定義多個環境變數。 當 Visual Studio 安裝程式安裝 C++工作負荷時,它會創建自訂的命令檔或批處理檔,以設置所需的環境變數。 然後,安裝程式使用這些命令檔為 Windows Start 功能表創建快捷方式以打開開發人員命令提示視窗。 這些快捷方式為特定生成配置設置環境變數。 當您想要使用命令列工具時,可以運行這些快捷方式之一,也可以打開一個普通的命令提示視窗,然後運行其中一個自定義命令檔來自行設置生成配置環境。 關於詳細資訊,請參閱[使用命令列 中的 MSVC 工具集](building-on-the-command-line.md)。 要使用具有簡單命令提示的命令檔,請參閱標題為[「開發人員命令檔位置](building-on-the-command-line.md#developer_command_file_locations)」的部分。

MSVC 命令列工具使用 PATH、TMP、INCLUDE、LIB 和 LIBPATH 環境變數,還使用特定於已安裝的工具、平臺和 SDK 的其他環境變數。 即使是簡單的 Visual Studio 安裝也可能設置 20 個或更多環境變數。 由於這些環境變數的值特定於您的安裝和生成配置的選擇,並且可以通過產品更新或升級進行更改,因此強烈建議您使用開發人員命令提示快捷方式或自定義命令檔之一來設置它們,而不是自己在 Windows 環境中設置它們。

要查看由開發人員命令提示快捷方式設置的環境變數,可以使用 SET 命令。 打開一個普通的命令提示視窗,並捕獲基線的 SET 命令的輸出。 打開開發人員命令提示視窗並捕獲 SET 命令的輸出進行比較。 差異工具(如內置於 Visual Studio IDE 中的工具)可用於比較環境變數並查看開發人員命令提示符設置的內容。 有關編譯器和連結器使用的特定環境變數的資訊,請參閱[CL 環境變數](reference/cl-environment-variables.md)。

> [!NOTE]
> 多個命令列工具或工具選項可能需要管理員許可權。 如果您在使用權限問題時遇到權限問題,我們建議您使用 **「以管理員身份執行」** 選項打開開發人員命令提示視窗。 在 Windows 10 上, 右鍵按下以開啟命令提示視窗的快捷選單,然後選擇 **「更多**」**以管理員身份執行**。

## <a name="see-also"></a>另請參閱

[從命令列使用 MSVC 工具組](building-on-the-command-line.md)<br/>
[MSVC 連結器參考](reference/linking.md)<br/>
[MSVC 連結器選項](reference/linker-options.md)<br/>
[MSVC 編譯器參考](reference/compiling-a-c-cpp-program.md)<br/>
[MSVC 編譯器選項](reference/compiler-options.md)
