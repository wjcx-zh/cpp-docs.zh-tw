---
title: MFC ActiveX 控制項：散發 ActiveX 控制項
ms.date: 09/12/2018
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
helpviewer_keywords:
- MFC ActiveX controls [MFC], ANSI or Unicode versions
- RegSvr32.exe
- MFC ActiveX controls [MFC], distributing
- distributing MFC ActiveX controls
- redistributable files, MFC ActiveX controls
- GetSystemDirectory method [MFC]
- registering ActiveX controls
- MSVCRT40.dll
- registry [MFC], registering controls
- LoadLibrary method, registering ActiveX controls
- MFC40U.DLL
- MFC40.DLL
- GetWindowsDirectory method [MFC]
- installing ActiveX controls
- GetProcAddress method, registering ActiveX controls
- MFC ActiveX controls [MFC], installing
- MFC ActiveX controls [MFC], registering
- registering controls
- OLEPRO32.DLL
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
ms.openlocfilehash: 11d647922a4f8097e03e112c0c93c833524c2c4e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618209"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC ActiveX 控制項：散發 ActiveX 控制項

本文討論與轉散發 ActiveX 控制項相關的幾個問題：

- [ANSI 或 Unicode 控制項版本](#_core_ansi_or_unicode_control_versions)

- [安裝 ActiveX 控制項和可轉散發 Dll](#_core_installing_activex_controls_and_redistributable_dlls)

- [註冊控制項](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>ANSI 或 Unicode 控制項版本

您必須決定要傳送 ANSI 或 Unicode 版本的控制項，還是兩者。 這項決定是以 ANSI 和 Unicode 字元集中固有的可攜性因素為基礎。

在所有 Win32 作業系統上運作的 ANSI 控制項，允許各種 Win32 作業系統之間的最大可攜性。 Unicode 控制項僅適用于 Windows NT （3.51 版或更新版本），但不適用於 Windows 95 或 Windows 98。 如果可攜性是您的主要考慮，請寄送 ANSI 控制項。 如果您的控制項只會在 Windows NT 上執行，您可以傳送 Unicode 控制項。 您也可以選擇寄送，並讓您的應用程式安裝最適合使用者作業系統的版本。

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>安裝 ActiveX 控制項和可轉散發 Dll

您以 ActiveX 控制項提供的安裝程式應該建立 Windows 目錄的特殊子目錄並安裝控制項。其中的 OCX 檔案。

> [!NOTE]
> 使用 `GetWindowsDirectory` 安裝程式中的 windows API 來取得 windows 目錄的名稱。 您可能想要從您的公司或產品名稱衍生出子目錄名稱。

安裝程式必須在 Windows 系統目錄中安裝必要的可轉散發 DLL 檔案。 如果使用者的電腦上已有任何 Dll，安裝程式應該將其版本與您要安裝的版本做比較。 只有在檔案的版本號碼高於已安裝的檔案時，才重新安裝檔案。

由於 ActiveX 控制項只能用在 OLE 容器應用程式中，因此不需要使用您的控制項來散發一組完整的 OLE Dll。 您可以假設包含的應用程式（或作業系統本身）已安裝標準的 OLE Dll。

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>註冊控制項

在您可以使用控制項之前，必須在 Windows 註冊資料庫中為其建立適當的專案。 某些 ActiveX 控制項容器會提供功能表項目供使用者註冊新的控制項，但此功能可能無法在所有容器中使用。 因此，您可能會想要讓安裝程式在安裝時註冊控制項。

如果您想要的話，也可以撰寫安裝程式，直接改為註冊控制項。

使用 `LoadLibrary` WINDOWS API 載入控制項 DLL。 接下來，使用 `GetProcAddress` 取得 "DllRegisterServer" 函式的位址。 最後，呼叫函式 `DllRegisterServer` 。 下列程式碼範例示範一個可能的方法，其中 `hLib` 儲存控制項程式庫的控制碼，並 `lpDllEntryPoint` 儲存 "DllRegisterServer" 函式的位址。

[!code-cpp[NVC_MFC_AxCont#16](codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

直接註冊控制項的優點是您不需要叫用並載入個別的進程（也就是 REGSVR32），以縮短安裝時間。 此外，因為註冊是內部程式，所以安裝程式可以處理比外部進程更好的錯誤和無法預期的情況。

> [!NOTE]
> 安裝程式安裝 ActiveX 控制項之前，應該先呼叫 `OleInitialize` 。 當您的安裝程式完成時，請呼叫 `OleUnitialize` 。 這可確保 OLE 系統 Dll 處於適當的狀態，以便註冊 ActiveX 控制項。

您應該註冊 MFCx0。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
