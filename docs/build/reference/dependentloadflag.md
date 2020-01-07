---
title: /DEPENDENTLOADFLAG (設定預設相依負載旗標)
description: /DEPENDENTLOADFLAG 選項會為使用 LoadLibrary 載入的 Dll 設定預設旗標
ms.date: 12/22/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 3a403f22c88ccd3e25ba95c183656ad2ffafd05a
ms.sourcegitcommit: ef34a11cb04511221bf5c7b9f4f55ad91a7a603f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2019
ms.locfileid: "75329994"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (設定預設相依負載旗標)

設定當 `LoadLibrary` 用來載入 Dll 時，所使用的預設載入旗標。

## <a name="syntax"></a>語法

> **/DEPENDENTLOADFLAG**[ __：__ *load_flags*]

### <a name="arguments"></a>Arguments

*load_flags*<br/>
選擇性的 "C" 樣式16位整數值（十進位）、具有前置零的八進位，或具有前置 `0x`的十六進位，指定要套用至所有[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)呼叫的相依負載旗標。 預設值為 0。

## <a name="remarks"></a>備註

此選項是 Visual Studio 2017 中的新功能。 它只適用于在 Windows 10 RS1 和更新版本上執行的應用程式。 執行應用程式的其他作業系統會忽略此選項。

在支援的作業系統上，此選項的效果是將 `LoadLibrary("dependent.dll")` 的呼叫變更為對等的 `LoadLibraryEx("dependent.dll", 0, load_flags)`。 對[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)的呼叫不會受到影響。 此選項不會以遞迴方式套用至您的應用程式所載入的 Dll。

這個旗標可以用來使[DLL 的攻擊](/windows/win32/dlls/dynamic-link-library-security)變得更棘手。 例如，如果應用程式使用 `LoadLibrary` 載入相依的 DLL，攻擊者就可以在 `LoadLibrary`所使用的搜尋路徑中，使用相同名稱來植入 DLL，例如目前的目錄（如果已停用安全 DLL 搜尋模式，則可能會在系統目錄之前檢查）。 安全 DLL 搜尋模式會在後續的搜尋順序中放置使用者目前的目錄，而且在 Windows XP SP2 和更新版本上預設為啟用。 如需詳細資訊，請參閱[動態連結程式庫搜尋順序](/windows/win32/Dlls/dynamic-link-library-search-order)。

如果您指定連結選項 `/DEPENDENTLOADFLAG:0xA00` （結合旗標 `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`的值），則即使使用者的電腦上已停用安全 DLL 搜尋模式，DLL 搜尋路徑還是會限制為應用程式目錄，後面接著%windows%\system32 目錄。 `/DEPENDENTLOADFLAG:0x800` 的選項更嚴格，限制搜尋%windows%\system32 目錄。 受保護的目錄比較難進行，但不是不可能的，可讓攻擊者變更。 如需可用旗標及其符號和數值的詳細資訊，請參閱[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)中的*dwFlags*參數描述。 如需使用各種相依負載旗標時所使用之搜尋順序的詳細資訊，請參閱[使用 LOAD_LIBRARY_SEARCH 旗標的搜尋順序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags)。

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 DEPENDENTLOADFLAG 連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] > **連結器** > [**命令列**] 屬性頁。

1. 在 [**其他選項**] 中輸入選項。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
- [將可執行檔連結至 DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [將可執行檔連結至 DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [動態連結程式庫搜尋順序](/windows/win32/Dlls/dynamic-link-library-search-order)
