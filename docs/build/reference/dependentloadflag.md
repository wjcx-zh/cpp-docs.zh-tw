---
title: / DEPENDENTLOADFLAG （設定預設相依載入旗標）
description: /DEPENDENTLOADFLAG 選項會設定預設旗標適用於使用 LoadLibrary 載入的 Dll
ms.date: 05/18/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 94998e06f23a7e70524221d3cb75166b5d3f2c44
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815966"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG （設定預設相依載入旗標）

使用集合的預設負載旗標時`LoadLibrary`用來載入 Dll。

## <a name="syntax"></a>語法

> **/DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>引數

*loadflags*<br/>
選擇性"C"樣式 16 位元整數值以十進位、 八進位以有前置零，或十六進位前置`0x`，指定要套用到所有的相依載入旗標[LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)呼叫。 預設值為 0。

## <a name="remarks"></a>備註

這個選項的新 Visual Studio 2017，並只適用於 Windows 10 RS1 和更新版本上執行的應用程式。 此選項會忽略其他執行應用程式的作業系統。

在支援的作業系統，此選項已變更呼叫的影響`LoadLibrary("dependent.dll")`對等的`LoadLibraryEx("dependent.dll", 0, loadflags)`。 若要呼叫[LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)不會受到影響。 此選項不適用於您的應用程式所載入的 Dll 以遞迴方式。

這個旗標可用來防止設置攻擊的 DLL。 例如，如果應用程式會使用`LoadLibrary`若要載入相依的 DLL，攻擊者可能計劃同名的 DLL 中所使用的搜尋路徑`LoadLibrary`，例如目前的目錄中，這可能之前先檢查系統目錄是否安全的 DLL 搜尋模式停用。 安全的 DLL 搜尋模式會更新版本的搜尋順序，將使用者的目前目錄，並在 Windows XP SP2 和更新版本預設會啟用。 如需詳細資訊，請參閱 <<c0> [ 動態連結程式庫搜尋順序](/windows/desktop/Dlls/dynamic-link-library-search-order)。

如果您指定連結選項`/DEPENDENTLOADFLAG:0xA00`(合併的旗標值`LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`)，則即使在使用者電腦上停用安全的 DLL 搜尋模式，是限制為受保護的目錄，攻擊者更難 DLL 搜尋路徑變更。 如需可用的旗標的詳細資訊和其符號和數字的值，請參閱*dwFlags*中的參數說明[LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)。

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>若要在 Visual Studio 開發環境中設定 DEPENDENTLOADFLAG 連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入中的選項**其他選項**。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
- [將可執行檔連結至 DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [將可執行檔連結至 DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)
- [動態連結程式庫搜尋順序](/windows/desktop/Dlls/dynamic-link-library-search-order)
