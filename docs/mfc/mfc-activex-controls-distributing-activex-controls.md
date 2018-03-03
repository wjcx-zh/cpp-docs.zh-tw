---
title: "MFC ActiveX 控制項： 散發 ActiveX 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e4ce6602696f733ca3bac03441a58515c57e0dc1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC ActiveX 控制項：散發 ActiveX 控制項
本文將討論與轉散發 ActiveX 控制項相關的幾個問題：  
  
-   [ANSI 或 Unicode 控制版本](#_core_ansi_or_unicode_control_versions)  
  
-   [安裝 ActiveX 控制項和可轉散發 Dll](#_core_installing_activex_controls_and_redistributable_dlls)  
  
-   [註冊控制項](#_core_registering_controls)  
  
##  <a name="_core_ansi_or_unicode_control_versions"></a>ANSI 或 Unicode 控制版本  
 您必須決定是否要出貨控制項，或兩者的 ANSI 或 Unicode 版本。 這項決策根據 ANSI 和 Unicode 字元集中固有的可攜性因素。  
  
 ANSI 控制項，可處理所有 Win32 作業系統，允許各種 Win32 作業系統之間的最大可攜性。 只有 Windows nt （版本 3.51 或更新版本），但不是能在 Windows 95 或 Windows 98，工作 Unicode 控制項。 如果是主要考量，出貨 ANSI 控制項的可攜性。 如果您的控制項將只能在 Windows NT 上執行，您可以送出 Unicode 控制項。 您也可以選擇要出貨兩者，而且已安裝最適合使用者的作業系統版本的應用程式。  
  
##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a>安裝 ActiveX 控制項和可轉散發 Dll  
 安裝程式，您可以提供您的 ActiveX 控制項應該建立特殊的 Windows 目錄的子目錄，並安裝控制項。OCX 檔案。  
  
> [!NOTE]
>  使用 Windows **GetWindowsDirectory**安裝程式中的 API 來取得 Windows 目錄的名稱。 若要從您的公司或產品的名稱衍生子目錄名稱。  
  
 安裝程式必須安裝在 Windows 系統目錄中的必要可轉散發的 DLL 檔案。 如果的任何 Dll 已經存在於使用者的電腦上，安裝程式應該比較您正在安裝的版本。 只有當其版本號碼高於已安裝的檔案，請重新安裝檔案。  
  
 ActiveX 控制項只能用於 OLE 容器應用程式，因為沒有任何需要傳遞完整的 OLE Dll 集與您的控制項。 您可以假設包含的應用程式 （或作業系統本身） 都具有標準 OLE 安裝 Dll。  
  
##  <a name="_core_registering_controls"></a>註冊控制項  
 控制項可以使用之前，必須建立適當的項目，在 Windows 系統註冊資料庫。 某些 ActiveX 控制項容器提供使用者註冊新的控制項的功能表項目，但這項功能可能無法使用所有容器中。 因此，您可能想安裝程式將會在安裝時，註冊控制項。  
  
 如果您想要的話，您可以撰寫安裝程式將改為直接登錄此控制項。  
  
 使用**LoadLibrary** Windows API，以載入控制項 DLL。 接下來，使用**GetProcAddress**取得"DllRegisterServer"函式的位址。 最後，呼叫`DllRegisterServer`函式。 下列程式碼範例示範一個可行的方法，其中`hLib`儲存控制項程式庫的控制代碼和`lpDllEntryPoint`儲存"DllRegisterServer"函式的位址。  
  
 [!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]  
  
 直接註冊控制項的優點是，您不需要叫用及載入不同的處理序 (也就是 「 REGSVR32 」) 來減少安裝時間。 此外，因為註冊是內部處理序，安裝程式來處理錯誤，並發生未預期的情況下，優於外部處理序可以。  
  
> [!NOTE]
>  安裝程式會安裝 ActiveX 控制項之前，應該呼叫**OleInitialize**。 安裝程式完成時，呼叫**OleUnitialize**。 這可確保 OLE 系統 Dll 中註冊的 ActiveX 控制項的適當狀態。  
  
 您應該註冊 MFCx0.DLL。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

