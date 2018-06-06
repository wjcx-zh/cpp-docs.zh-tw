---
title: / DEPENDENTLOADFLAG （設定預設相依負載旗標）
description: /DEPENDENTLOADFLAG 選項設定為使用 LoadLibrary 載入的 Dll 預設旗標
ms.custom: ''
ms.date: 05/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- dependentloadflag
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a171f3c2edbbbf614a986ff78dd2405e734a1d1
ms.sourcegitcommit: d1f576a0f59678edc3d93508cf46485138332178
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753705"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG （設定預設相依負載旗標）

設定預設負載旗標時使用`LoadLibrary`用來載入 Dll。

## <a name="syntax"></a>語法

> **/ DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>引數

|||
|-|-|
*loadflags*|選擇性"C"樣式 16 位元整數值在十進位、 八進位有前置零，或使用含有前置十六進位`0x`，指定要套用到所有的相依負載旗標[LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187)呼叫。 預設值為 0。

## <a name="remarks"></a>備註

此選項的新功能 Visual Studio 2017，且只適用於 Windows 10 RS1 和更新版本上執行的應用程式。 此選項會忽略其他執行應用程式的作業系統。

在支援的作業系統，此選項已變更呼叫的效果`LoadLibrary("dependent.dll")`對等的`LoadLibraryEx("dependent.dll", 0, loadflags)`。 呼叫[LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091)不會受到影響。 此選項不適用於您的應用程式載入的 Dll 以遞迴方式。

這個旗標可以用來防止 DLL 設置攻擊。 例如，如果應用程式使用`LoadLibrary`載入相依的 DLL，攻擊者無法計劃與相同名稱的 DLL 中所使用的搜尋路徑`LoadLibrary`，例如目前的目錄中，這可能會之前先檢查系統目錄是否安全 DLL 搜尋模式停用。 安全的 DLL 搜尋模式更新版本的搜尋順序，會將使用者的目前目錄，並在 Windows XP SP2 和更新版本的預設會啟用。 如需詳細資訊，請參閱[動態連結程式庫搜尋順序](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)。

如果您指定 link 選項`/DEPENDENTLOADFLAG:0xA00`(結合的旗標值`LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`)，則即使在使用者電腦上已停用安全的 DLL 搜尋模式，是限制為受保護的目錄，攻擊者更難以 DLL 搜尋路徑變更。 可用的旗標的詳細資訊及它們的符號和數字值，請參閱*dwFlags*參數描述中的[LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091)。

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 DEPENDENTLOADFLAG 連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入中的選項**其他選項**。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

- [設定連結器選項](setting-linker-options.md)
- [連結器選項](linker-options.md)
- [如何以隱含方式連結到 DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [決定要使用哪一個連結方法](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187)
- [LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091)
- [動態連結程式庫搜尋順序](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)
