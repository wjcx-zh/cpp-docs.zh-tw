---
title: /DEPENDENTLOADFLAG (設定預設相依負載旗標)
description: /DEPENDENTLOADFLAG 選項會為使用 LoadLibrary 載入的 Dll 設定預設旗標
ms.date: 05/18/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 072fa1103d049c7d5c395ae88d268f3b47e20b4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492946"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (設定預設相依負載旗標)

設定用來載入 dll 時`LoadLibrary`使用的預設載入旗標。

## <a name="syntax"></a>語法

> **/DEPENDENTLOADFLAG**[ **:** _loadflags_]

### <a name="arguments"></a>引數

*loadflags*<br/>
選擇性的 "C" 樣式16位整數值 (十進位)、具有前置零的八進位, 或具有前置`0x`的十六進位, 指定要套用至所有[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)呼叫的相依負載旗標。 預設值為 0。

## <a name="remarks"></a>備註

此選項是 Visual Studio 2017 中的新功能, 僅適用于在 Windows 10 RS1 和更新版本上執行的應用程式。 執行應用程式的其他作業系統會忽略此選項。

在支援的作業系統上, 這個選項的效果是將的呼叫`LoadLibrary("dependent.dll")`變更為對`LoadLibraryEx("dependent.dll", 0, loadflags)`等的。 對[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)的呼叫不會受到影響。 此選項不會以遞迴方式套用至您的應用程式所載入的 Dll。

這個旗標可以用來防止 DLL 植入攻擊。 例如, 如果應用程式使用`LoadLibrary`載入相依的 dll, 攻擊者可能會在`LoadLibrary`使用的搜尋路徑中植入具有相同名稱的 DLL, 例如目前的目錄, 如果安全 DLL 搜尋模式為, 則可能會在系統目錄之前進行檢查。禁止. 安全 DLL 搜尋模式會在後續的搜尋順序中放置使用者目前的目錄, 而且在 Windows XP SP2 和更新版本上預設為啟用。 如需詳細資訊, 請參閱[動態連結程式庫搜尋順序](/windows/win32/Dlls/dynamic-link-library-search-order)。

如果您指定連結選項`/DEPENDENTLOADFLAG:0xA00` (合併旗標`LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`的值), 則即使使用者的電腦上已停用安全 DLL 搜尋模式, DLL 搜尋路徑還是會限制為受保護的目錄, 讓攻擊者更容易更改. 如需可用旗標及其符號和數值的詳細資訊, 請參閱[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)中的*dwFlags*參數描述。

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 DEPENDENTLOADFLAG 連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定] [**屬性** > ] [**連結器** > **命令列**] 屬性頁。

1. 在 [**其他選項**] 中輸入選項。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
- [將可執行檔連結至 DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [將可執行檔連結至 DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [動態連結程式庫搜尋順序](/windows/win32/Dlls/dynamic-link-library-search-order)
