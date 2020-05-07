---
title: 設定命令列組建的路徑和環境變數
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
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>設定命令列組建的路徑和環境變數

Microsoft c + + （MSVC）命令列組建工具需要數個針對您的安裝和組建設定而自訂的環境變數。 當 Visual Studio 安裝程式安裝 c + + 工作負載時，它會建立自訂的命令檔或批次檔，以設定所需的環境變數。 然後，安裝程式會使用這些命令檔來建立 Windows [開始] 功能表的快捷方式，以開啟 [開發人員命令提示字元] 視窗。 這些快捷方式會設定特定組建設定的環境變數。 當您想要使用命令列工具時，可以執行下列其中一個快捷方式，或者您可以開啟純文字命令提示字元視窗，然後執行其中一個自訂命令檔，自行設定組建環境。 如需詳細資訊，請參閱[從命令列使用 MSVC 工具](building-on-the-command-line.md)組。 若要使用命令檔搭配純文字命令提示字元，請參閱「[開發人員命令檔位置](building-on-the-command-line.md#developer_command_file_locations)」一節。

MSVC 命令列工具會使用 PATH、TMP、INCLUDE、LIB 和 LIBPATH 環境變數，也會使用您已安裝的工具、平臺和 Sdk 特有的其他環境變數。 即使是簡單的 Visual Studio 安裝也可能會設定二十個或更多的環境變數。 因為這些環境變數的值專屬於您的安裝以及您選擇的組建設定，而且可以透過產品更新或升級進行變更，所以強烈建議您使用開發人員命令提示字元快捷方式或其中一個自訂的命令檔來設定它們，而不是自行在 Windows 環境中設定它們。

若要查看開發人員命令提示字元快捷方式所設定的環境變數，您可以使用 SET 命令。 開啟純文字 [命令提示字元] 視窗，並針對基準捕捉 SET 命令的輸出。 開啟 [開發人員命令提示字元] 視窗，並捕捉 SET 命令的輸出以進行比較。 Visual Studio IDE 內建的 diff 工具，可能有助於比較環境變數，並查看開發人員命令提示字元所設定的功能。 如需編譯器和連結器所使用之特定環境變數的詳細資訊，請參閱[CL 環境變數](reference/cl-environment-variables.md)。

> [!NOTE]
> 數個命令列工具或工具選項可能需要系統管理員許可權。 如果您在使用時遇到許可權問題，建議您使用 [以**系統管理員身分執行**] 選項開啟 [開發人員命令提示字元] 視窗。 在 Windows 10 上，以滑鼠右鍵按一下以開啟 [命令提示字元] 視窗的快捷方式功能表，然後選擇 [**更多**]、[**以系統管理員身分執行**]。

## <a name="see-also"></a>請參閱

[從命令列使用 MSVC 工具組](building-on-the-command-line.md)<br/>
[MSVC 連結器參考](reference/linking.md)<br/>
[MSVC 連結器選項](reference/linker-options.md)<br/>
[MSVC 編譯器參考](reference/compiling-a-c-cpp-program.md)<br/>
[MSVC 編譯器選項](reference/compiler-options.md)
