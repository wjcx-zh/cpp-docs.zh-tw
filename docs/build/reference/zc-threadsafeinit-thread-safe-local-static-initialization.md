---
title: /Zc:threadSafeInit （安全執行緒本機靜態初始設定）
ms.date: 03/14/2018
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
ms.openlocfilehash: 92a1bfa5ec3bab2814397d51e35e617b7666c706
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808335"
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc:threadSafeInit （安全執行緒本機靜態初始設定）

**/Zc:threadSafeInit**編譯器選項會指示編譯器初始化靜態本機 （函式範圍） 變數的執行緒安全的方式，而不需要手動同步處理。 只初始化具備執行緒安全。 使用及修改多個執行緒的靜態區域變數必須仍是手動同步處理。 此選項可從 Visual Studio 2015 開始。 根據預設，Visual Studio 會啟用此選項。

## <a name="syntax"></a>語法

> **/Zc:threadSafeInit**[**-**]

## <a name="remarks"></a>備註

C + + 11 標準，在區塊範圍變數與靜態或執行緒儲存期必須是零初始化任何其他的初始化發生之前。 初始化發生於控制項第一次通過變數的宣告。 如果在初始化期間擲回例外狀況，變數會被視為未初始化，而且初始設定是重試的下一個時間控制項就會通過宣告。 如果控制項輸入的宣告與初始化時，會在完成初始設定時的並行執行區塊。 如果控制項重新輸入宣告以遞迴方式在初始化期間，則行為是未定義。 根據預設，開始在 Visual Studio 2015 的 Visual Studio 會實作此標準的行為。 此行為可以藉由設定明確指定 **/Zc:threadSafeInit**編譯器選項。

**/Zc:threadSafeInit**編譯器選項預設為開啟。 [/Permissive--](permissive-standards-conformance.md)選項並不會影響 **/Zc:threadSafeInit**。

安全執行緒初始化靜態區域變數依賴通用 C 執行階段程式庫 (UCRT) 中實作的程式碼。 若要避免仰賴 UCRT，或保留版本的 Visual Studio 2015 之前的 Visual Studio 的非安全執行緒初始化行為，請使用 **/zc: threadsafeinit**選項。 如果您知道該執行緒安全則不需要，請使用此選項來產生較小、 更快速的程式碼周圍的靜態區域宣告。

安全執行緒靜態區域變數已初始化靜態時，提供有效率的方式執行，請以在內部使用執行緒區域儲存區 (TLS)。 這項功能的實作會依賴 Windows Vista 和更新版本的作業系統中的 Windows 作業系統支援函式。 Windows XP、 Windows Server 2003 和較舊的作業系統並沒有這項支援，因此不會收到效率優勢。 這些作業系統可載入的 TLS 區段的數目也擁有較低的限制。 超過 TLS 區段的限制可能會導致當機。 如果這是一個問題，在您的程式碼，尤其是必須在舊的作業系統執行的程式碼中使用 **/zc: threadsafeinit**停用安全執行緒初始化程式碼。

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 從**組態**下拉式功能表中，選擇**所有組態**。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/Zc:threadSafeInit**或是 **/zc: threadsafeinit** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)<br/>
[/Zc (一致性)](zc-conformance.md)<br/>
