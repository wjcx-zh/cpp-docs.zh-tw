---
title: /Zc:threadSafeInit （安全執行緒本機靜態初始設定） |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 438ce5ba783f646e9c8e61d9b82999ea936532b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc:threadSafeInit （安全執行緒本機靜態初始設定）

**/Zc:threadSafeInit**編譯器選項會告訴編譯器初始化靜態區域變數 （函式範圍） 變數中以執行緒安全的方式，不必手動同步處理。 只有初始化是安全執行緒。 使用及修改由多個執行緒的靜態區域變數仍必須是以手動方式同步處理。 此選項可從 Visual Studio 2015 開始。 根據預設，Visual Studio 會啟用此選項。

## <a name="syntax"></a>語法

> **/Zc:threadSafeInit**[**-**]

## <a name="remarks"></a>備註

C + + 11 標準，在區塊範圍變數具有靜態或執行緒儲存期必須是零初始化進行任何其他初始設定之前。 初始化發生於控制項第一次通過變數的宣告。 如果在初始化期間擲回例外狀況，變數會被視為未初始化，而且初始化會重試的下一個時間控制會傳遞透過宣告。 如果控制項進入與初始設定，同時執行區塊時初始化完成同時宣告。 如果控制項重新進入宣告以遞迴方式在初始化期間，則行為是未定義。 根據預設，Visual Studio 啟動 Visual Studio 2015 中實作這個標準行為。 這種行為可能會藉由設定明確指定 **/Zc:threadSafeInit**編譯器選項。

**/Zc:threadSafeInit**編譯器選項預設為開啟。 [/ 寬鬆-](permissive-standards-conformance.md)選項不會影響 **/Zc:threadSafeInit**。

安全執行緒初始化靜態區域變數依賴實作通用的 C 執行階段程式庫 (UCRT) 中的程式碼。 若要避免採用相依性，UCRT 或保留在 Visual Studio 2015 之前的 Visual Studio 版本的非安全執行緒初始化行為，請使用 **/zc: threadsafeinit-** 選項。 如果您知道該執行緒安全，就不需要，請使用此選項來產生稍微較小、 更快速的程式碼周圍的靜態區域宣告。

安全執行緒的靜態區域變數內部使用執行緒區域儲存區 (TLS) 來提供有效率的方式執行時已經初始化靜態。 這項功能的實作會依賴 Windows 作業系統支援函式，在 Windows Vista 和更新版本的作業系統。 Windows XP、 Windows Server 2003 和較舊的作業系統沒有這項支援，因此不會發生效率優點。 這些作業系統上載入的 TLS 區段的數目上也有較低的限制。 超過 TLS 區段限制可能會導致損毀。 如果這是您的程式碼，尤其是在必須在較舊的作業系統執行的程式碼中的問題使用 **/zc: threadsafeinit-** 停用安全執行緒的初始化程式碼。

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 從**組態**下拉式功能表中，選擇 **所有組態**。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/Zc:threadSafeInit**或 **/zc: threadsafeinit-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (一致性)](../../build/reference/zc-conformance.md)<br/>
