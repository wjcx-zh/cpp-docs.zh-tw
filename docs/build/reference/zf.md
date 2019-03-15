---
title: /Zf （PDB 產生速度加快）
ms.date: 03/29/2018
f1_keywords:
- /Zf
helpviewer_keywords:
- /Zf
- -Zf
ms.openlocfilehash: bed37a189e3eb1eb7b55dbdee1f81f360eafa721
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814042"
---
# <a name="zf-faster-pdb-generation"></a>/Zf （PDB 產生速度加快）

最小化 mspdbsrv.exe RPC 呼叫，以啟用更快速的平行組建的 PDB 產生。

## <a name="syntax"></a>語法

> **/Zf**

## <a name="remarks"></a>備註

**/Zf**使用時，選項會啟用更快產生 PDB 檔的編譯器支援[/MP （使用多個處理序建置）](mp-build-with-multiple-processes.md)選項，或當建置系統 (例如[MSBuild](/visualstudio/msbuild/msbuild-reference)或是[CMake](../cmake-projects-in-visual-studio.md)) 可能會多個 cl.exe 在同時執行編譯器處理序。 此選項會導致編譯器前端延遲類型索引的產生 PDB 檔案中的每個類型記錄到結束的編譯，然後要求它們全都放在單一的 RPC 呼叫到 mspdbsrv.exe，而不是 RPC 要求每一筆記錄。 這可以減少 RPC 負載 mspdbsrv.exe 程序，在多個 cl.exe 編譯器處理序同時執行的所在的環境中，大幅改善建置輸送量。

因為 **/Zf**選項僅適用於的 PDB 產生，它需要[/Zi](z7-zi-zi-debug-information-format.md)或是[/ZI](z7-zi-zi-debug-information-format.md)選項。

**/Zf**選項是在 Visual Studio 2017 15.1 版，開始提供，它預設為關閉。 開始在 Visual Studio 2017 15.7 版 Preview 3，此選項預設為開啟時 **/Zi**或是 **/ZI**啟用選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/Zf** ，然後選擇**確定**。

## <a name="see-also"></a>另請參閱

[依字母順序排列的編譯器選項](compiler-options-listed-alphabetically.md)<br/>
[/MP (使用多處理序建置)](mp-build-with-multiple-processes.md)<br/>
