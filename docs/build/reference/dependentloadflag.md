---
title: /DEPENDENTLOADFLAG (設定預設相依負載旗標)
description: /DEPENDENTLOADFLAG 選項會針對此模組所載入的 Dll，設定預設的相依載入旗標。
ms.date: 01/22/2020
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 5e31a0d747e7186814cba3ae1c4cf243569d87a8
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725704"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (設定預設相依負載旗標)

::: moniker range="vs-2015"

**/DEPENDENTLOADFLAG**選項需要 Visual Studio 2017 或更新版本。

::: moniker-end

::: moniker range=">=vs-2017"

設定當作業系統解析模組的靜態連結匯入時，所使用的預設載入旗標。

## <a name="syntax"></a>語法

> **/DEPENDENTLOADFLAG**[ __：__ *load_flags*]

### <a name="arguments"></a>Arguments

*load_flags*<br/>
選擇性的整數值，指定解析模組的靜態連結匯入相依性時，要套用的載入旗標。 預設值為 0。 如需支援的旗標值清單，請參閱[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)中的 `LOAD_LIBRARY_SEARCH_*` 專案。

## <a name="remarks"></a>備註

當作業系統解析模組的靜態連結匯入時，它會使用預設的[搜尋順序](/windows/win32/dlls/dynamic-link-library-search-order)。 使用 [ **/DEPENDENTLOADFLAG** ] 選項可指定變更用來解析這些匯入之搜尋路徑的*load_flags*值。 在支援的作業系統上，它會變更靜態匯入解析搜尋順序，類似于使用 `LOAD_LIBRARY_SEARCH` 參數時的[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa) 。 如需*load_flags*所設定之搜尋順序的詳細資訊，請參閱[使用 LOAD_LIBRARY_SEARCH 旗標的搜尋順序](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags)。

這個旗標可以用來讓一個[DLL 植入攻擊](/windows/win32/dlls/dynamic-link-library-security)向量更棘手。 例如，假設有一個應用程式以靜態方式連結 DLL：

- 攻擊者可能會在先前的匯入解析搜尋路徑（例如應用程式目錄）中，使用相同的名稱來植入 DLL。 受保護的目錄比較難進行，但不是不可能的，可讓攻擊者變更。

- 如果應用程式、%windows%\system32 和% windows% 目錄中遺漏 DLL，則匯入解析會落在目前目錄中。 攻擊者可以在那裡植出 DLL。

在這兩種情況下，如果您指定連結選項 `/DEPENDENTLOADFLAG:0x800` （旗標 `LOAD_LIBRARY_SEARCH_SYSTEM32`的值），則模組搜尋路徑會限制為%windows%\system32 目錄。 它提供一些保護，防止其他目錄的攻擊。 如需詳細資訊，請參閱[動態連結程式庫安全性](/windows/win32/dlls/dynamic-link-library-security)。

若要查看任何 DLL 中 **/DEPENDENTLOADFLAG**選項所設定的值，請使用[DUMPBIN](dumpbin-reference.md)命令搭配[/LOADCONFIG](loadconfig.md)選項。

**/DEPENDENTLOADFLAG**選項在 Visual Studio 2017 中是新的。 它只適用于在 Windows 10 RS1 和更新版本上執行的應用程式。 執行應用程式的其他作業系統會忽略此選項。

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定 DEPENDENTLOADFLAG 連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] >**連結器**> [**命令列**] 屬性頁。

1. 在 [**其他選項**] 中輸入選項。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
- [以隱含方式將可執行檔連結至 DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [決定要使用哪一個連結方法](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [動態連結程式庫搜尋順序](/windows/win32/Dlls/dynamic-link-library-search-order)
- [動態連結程式庫安全性](/windows/win32/dlls/dynamic-link-library-security)

::: moniker-end
