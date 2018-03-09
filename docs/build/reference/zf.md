---
title: "/Zf （產生更快的 PDB） |Microsoft 文件"
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zf
dev_langs:
- C++
helpviewer_keywords:
- /Zf
- -Zf
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7012777643f993c552f79b58a02d4806c0ce4caa
ms.sourcegitcommit: c770a343def04ae77522708387c3f7c470e49969
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="zf-faster-pdb-generation"></a>/Zf （速度 PDB 的產生）

啟用平行組建中的更快產生 PDB mspdbsrv.exe RPC 呼叫將降至最低。

## <a name="syntax"></a>語法

> **/Zf**

## <a name="remarks"></a>備註

**/Zf**選項更快產生 PDB 檔的編譯器支援使用時，啟用[/MP （使用多個處理序建置）](mp-build-with-multiple-processes.md)選項，或當建置系統 (例如， [MSBuild](/visualstudio/msbuild/msbuild-reference)或[CMake](../../ide/cmake-tools-for-visual-cpp.md)) 可能時間內執行多個 cl.exe 編譯器處理程序相同。 此選項會使延遲產生的型別索引 PDB 檔案中每個型別記錄的編譯時，結束之前的編譯器前端然後 mspdbsrv.exe，而非讓 RPC 要求每一筆記錄的單一 RPC 呼叫中的所有要求。 這基本上可以改善建置輸送量藉由減少 mspdbsrv.exe 程序，在多個 cl.exe 編譯器處理序同時執行的所在的環境中的 RPC 負載。

因為**/Zf**選項僅適用於產生 PDB，它需要[/Zi](z7-zi-zi-debug-information-format.md)或[/ZI](z7-zi-zi-debug-information-format.md)選項。

**/Zf**選項從開始使用 Visual Studio 2017 版本 15.1，並預設為關閉。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括**/Zf** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[依字母順序排列的編譯器選項](compiler-options-listed-alphabetically.md)  
[/MP (使用多處理序建置)](mp-build-with-multiple-processes.md)  
