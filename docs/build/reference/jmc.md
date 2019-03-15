---
title: / JMC （Just My Code 偵錯）
ms.date: 08/20/2018
f1_keywords:
- /JMC
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: c107ad7107d2a65ed19719933aa127c0557916ce
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808049"
---
# <a name="jmc-just-my-code-debugging"></a>/ JMC （Just My Code 偵錯）

指定編譯器支援原生*Just My Code*在 Visual Studio debugger 中偵錯。 此選項支援允許 Visual Studio 不進入系統、 架構、 程式庫和其他非使用者呼叫，並摺疊這些呼叫，在 [呼叫堆疊] 視窗中的使用者設定。 **/JMC**編譯器選項是從 Visual Studio 2017 版本 15.8 中推出。

## <a name="syntax"></a>語法

> **/JMC**\[**-**]

## <a name="remarks"></a>備註

Visual Studio [Just My Code](/visualstudio/debugger/just-my-code)設定可讓您指定 Visual Studio 偵錯工具是否會進入系統、 架構、 程式庫和其他非使用者呼叫。 **/JMC**編譯器選項可讓支援 Just My Code 偵錯原生的 c + + 程式碼。 當 **/JMC**已啟用，編譯器會插入協助程式函式呼叫`__CheckForDebuggerJustMyCode`，函式初構中。 Helper 函式會提供支援 Visual Studio 偵錯工具 Just My Code 步驟作業的攔截程序。 若要啟用 Just My Code，Visual Studio 偵錯工具，在功能表列上，選擇**工具** > **選項**，然後在中設定選項**偵錯** > **一般** > **啟用 Just My Code**。

**/JMC**選項需要您的程式碼連結至 C 執行階段程式庫 (CRT)，可提供`__CheckForDebuggerJustMyCode`helper 函式。 如果您的專案不會連結到 CRT，您可能會看到連結器錯誤**LNK2019： 無法解析的外部符號 __CheckForDebuggerJustMyCode**。 若要解決這個錯誤，請連結到 CRT，或停用 **/JMC**選項。

根據預設， **/JMC**編譯器選項已關閉。 不過，開始在 Visual Studio 2017 版本 15.8 此選項大部分的 Visual Studio 專案範本中啟用。 若要明確停用此選項，請使用 **/JMC-** 命令列上的選項。 在 Visual Studio 中，開啟 [專案屬性頁] 對話方塊中，並將變更**支援只我的程式碼偵錯**中的屬性**組態屬性** > **C/c + +** > **一般**屬性頁**No**。

如需詳細資訊，請參閱 < [c + + Just My Code](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code)中[指定是否只使用 Just My Code，Visual Studio 中的使用者程式碼偵錯](/visualstudio/debugger/just-my-code)，和 Visual c + + 小組部落格文章[宣布 c + + Just My Code在 Visual Studio 中逐步執行](https://blogs.msdn.microsoft.com/vcblog/2018/06/29/announcing-jmc-stepping-in-visual-studio/)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **一般**屬性頁。

1. 修改**支援只我的程式碼偵錯**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)<br/>
