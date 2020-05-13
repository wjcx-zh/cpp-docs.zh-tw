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
ms.openlocfilehash: 1ada1c801b2d9d62f1cc4cd5bf72a2995225b3de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364618"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC ActiveX 控制項：散發 ActiveX 控制項

本文討論了與重新分發 ActiveX 控制項相關的幾個問題:

- [ANSI 或 Unicode 控制版本](#_core_ansi_or_unicode_control_versions)

- [安裝 ActiveX 控制及可再分轉的 DLL](#_core_installing_activex_controls_and_redistributable_dlls)

- [註冊控制項](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX 是一種不應用於新開發的傳統技術。 有關取代 ActiveX 的現代技術的詳細資訊,請參閱[ActiveX 控制件](activex-controls.md)。

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>ANSI 或 Unicode 控制版本

您必須決定是提供控制項的 ANSI 或 Unicode 版本,還是同時發貨。 此決策基於 ANSI 和 Unicode 字元集中固有的可移植性因素。

ANSI 控制項適用於所有 Win32 作業系統,允許在各種 Win32 作業系統之間實現最大的可移植性。 Unicode 控制項僅在 Windows NT(版本 3.51 或更高版本)上工作,但在 Windows 95 或 Windows 98 上不起作用。 如果可移植性是您最關心的問題,請提供 ANSI 控制件。 如果控制項僅在 Windows NT 上運行,則可以提供 Unicode 控制件。 您還可以選擇同時發貨,並讓應用程式安裝最適合使用者操作系統的版本。

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>安裝 ActiveX 控制及可再分轉的 DLL

與 ActiveX 控制件一起提供的安裝程式應建立 Windows 目錄的特殊子目錄並安裝控制項的 。OCX 檔。

> [!NOTE]
> 使用安裝程式中的`GetWindowsDirectory`Windows API 獲取 Windows 目錄的名稱。 您可能希望從公司或產品的名稱派生子目錄名稱。

安裝程式必須在 Windows 系統目錄中安裝必要的可再分發 DLL 檔。 如果用戶的電腦上已存在任何 DLL,安裝程式應將其版本與您正在安裝的版本進行比較。 僅當檔的版本號高於已安裝的檔時,才重新安裝該檔。

由於 ActiveX 控制件只能在 OLE 容器應用程式中使用,因此無需將完整的 OLE DLL 集與控制項一起分發。 可以假定包含的應用程式(或作業系統本身)安裝了標準 OLE DLL。

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>註冊控制項

在使用控制項之前,必須在 Windows 註冊資料庫中為其創建適當的條目。 某些 ActiveX 控件容器為使用者提供了一個功能表項,供使用者註冊新的控制項,但此功能可能並非在所有容器中都可用。 因此,您可能希望安裝程式在安裝控制項時註冊它們。

如果您願意,可以編寫安裝程式以直接註冊控件。

使用`LoadLibrary`Windows API 載入控制項 DLL。 接下來,使用`GetProcAddress`以獲取"DllRegisterServer"功能的位址。 最後,呼叫函數`DllRegisterServer`。 以下代碼範例展示一種可能的方法,`hLib`其中儲存控制項庫的句柄並`lpDllEntryPoint`儲存 DllRegisterServer"函數的位址。

[!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

直接註冊控件的優點是,您不需要調用和載入單獨的進程(即 REGSVR32),從而減少安裝時間。 此外,由於註冊是一個內部過程,安裝程式可以比外部進程更好地處理錯誤和不可預見的情況。

> [!NOTE]
> 安裝程式安裝 ActiveX 控制項之前,它應該呼`OleInitialize`叫 。 安裝程式完成後,呼叫`OleUnitialize`。 這可確保 OLE 系統 DLL 處於註冊 ActiveX 控制件的適當狀態。

您應該註冊 MFCx0.DLL。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
