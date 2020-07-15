---
title: /JMC (Just My Code 偵錯)
ms.date: 08/20/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SupportJustMyCode
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: 7b22a754f9f49564cd7f76c7d1989cd562f70874
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373875"
---
# <a name="jmc-just-my-code-debugging"></a>/JMC (Just My Code 偵錯)

指定 Visual Studio 偵錯工具中原生*Just My Code*的偵錯工具支援。 此選項支援使用者設定，可讓 Visual Studio 不進入系統、架構、程式庫和其他非使用者呼叫，以及在 [呼叫堆疊] 視窗中折迭這些呼叫。 從 Visual Studio 2017 15.8 版開始提供 **/JMC**編譯器選項。

## <a name="syntax"></a>語法

> **/JMC** \[ **-** ]

## <a name="remarks"></a>備註

Visual Studio 的[Just My Code](/visualstudio/debugger/just-my-code)設定會指定 Visual Studio 偵錯工具是否要執行系統、架構、程式庫和其他非使用者呼叫。 **/JMC**編譯器選項可支援在您的原生 c + + 程式碼中進行 Just My Code 的調試。 啟用 **/JMC**時，編譯器會在函數初構中插入 helper 函式的呼叫 `__CheckForDebuggerJustMyCode` 。 Helper 函式提供支援 Visual Studio 偵錯工具 Just My Code 步驟作業的勾點。 若要在 Visual Studio 偵錯工具中啟用 Just My Code，請在功能表列上選擇 [**工具**] [  >  **選項**]，然後在 [**調試**程式]  >  **[一般**] [  >  **啟用 Just My Code**] 中設定選項。

**/JMC**選項需要您的程式碼連結至 C 執行時間程式庫（CRT），以提供 `__CheckForDebuggerJustMyCode` helper 函式。 如果您的專案未連結至 CRT，您可能會看到連結器錯誤**LNK2019：無法解析的外部符號 __CheckForDebuggerJustMyCode**。 若要解決這個錯誤，請連結至 CRT，或停用 **/JMC**選項。

根據預設， **/JMC**編譯器選項為 off。 不過，從 Visual Studio 2017 版15.8 開始，大部分的 Visual Studio 專案範本都會啟用此選項。 若要明確停用此選項，請使用命令列上的 **/JMC-** 選項。 在 Visual Studio 中，開啟 [專案屬性頁] 對話方塊，然後將 [設定**屬性**C/c + + 一般] 屬性頁中的 [**支援 Just My Code 調試**] 屬性變更  >  **C/C++**  >  **General**為 [**否**]。

如需詳細資訊，請參閱[指定是否只在 Visual Studio 中使用 Just My Code 來進行調試](/visualstudio/debugger/just-my-code)程式程式碼，以及 Visual C++ 小組的 Blog 文章[宣佈 c + + Just My Code 逐步執行 Visual Studio](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/)中的[c + + Just My Code](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code) 。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **一般**] 屬性頁。

1. 修改**支援 Just My Code 的調試**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
