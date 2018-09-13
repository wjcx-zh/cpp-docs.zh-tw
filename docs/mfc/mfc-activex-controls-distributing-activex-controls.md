---
title: MFC ActiveX 控制項： 散發 ActiveX 控制項 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d400bf09d2fd3484b573112d87735ce0a74d944e
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534894"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC ActiveX 控制項：散發 ActiveX 控制項
這篇文章會討論幾個有關轉散發 ActiveX 控制項問題：  
  
-   [ANSI 或 Unicode 控制版本](#_core_ansi_or_unicode_control_versions)  
  
-   [安裝 ActiveX 控制項和可轉散發 Dll](#_core_installing_activex_controls_and_redistributable_dlls)  
  
-   [註冊控制項](#_core_registering_controls)  


>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。
  
##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI 或 Unicode 控制版本  
 您必須決定是否要寄送該控制項，或兩者的 ANSI 或 Unicode 版本。 這項決策根據 ANSI 和 Unicode 字元集中固有的可攜性因素。  
  
 ANSI 控制項，可在所有的 Win32 作業系統上運作，允許各種 Win32 作業系統之間的最大可攜性。 Unicode 控制項運作，只有 Windows nt （版本 3.51 或更新版本），但不是能在 Windows 95 或 Windows 98。 如果您主要的考量，出貨 ANSI 控制項可攜性。 如果您的控制項將只能在 Windows NT 上執行，您可以將 Unicode 控制項。 您也可以選擇提供兩者，並讓您安裝最適合使用者的作業系統版本的應用程式。  
  
##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> 安裝 ActiveX 控制項和可轉散發 Dll  
 您提供您的 ActiveX 控制項安裝程式應該建立特殊的 Windows 目錄的子目錄，並安裝控制項的。OCX 檔案。  
  
> [!NOTE]
>  使用 Windows`GetWindowsDirectory`安裝程式中的 API 來取得 Windows 目錄的名稱。 若要從您的公司或產品的名稱衍生子目錄的名稱。  
  
 Windows 系統目錄中，安裝程式必須安裝必要的可轉散發 DLL 檔案。 如果所有 Dll 已經存在於使用者的電腦上，安裝程式應該會比較其版本與您要安裝的版本。 只有當其版本號碼高於已安裝的檔案，請重新安裝檔案。  
  
 ActiveX 控制項只能用於 OLE 容器應用程式，因為沒有任何需要傳遞完整的 OLE Dll 與控制。 您可以假設包含的應用程式 （或作業系統本身） 都具有標準 OLE 安裝 Dll。  
  
##  <a name="_core_registering_controls"></a> 註冊控制項  
 控制可用之前，必須建立適當的項目，Windows 註冊資料庫中。 某些 ActiveX 控制項容器提供使用者註冊新的控制項的功能表項目，但這項功能可能無法使用所有容器中。 因此，您可以安裝程式將會在安裝時，註冊控制項。  
  
 如果想要的話，您可以撰寫您的安裝程式，改為直接註冊控制項。  
  
 使用`LoadLibrary`載入控制項 DLL 的 Windows API。 接下來，使用`GetProcAddress`取得 「 DllRegisterServer"函式的位址。 最後，呼叫`DllRegisterServer`函式。 下列程式碼範例示範一個可行的方法，其中`hLib`儲存的控制項程式庫的控制代碼和`lpDllEntryPoint`儲存 「 DllRegisterServer"函式的位址。  
  
 [!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]  
  
 直接註冊控制項的優點是，您不需要叫用，並載入不同的處理序 (也就是 「 REGSVR32 」) 來減少安裝時間。 此外，因為註冊的內部程序，安裝程式可以處理錯誤，而且發生未預期的情況下，優於外部處理序可以。  
  
> [!NOTE]
>  安裝程式會安裝 ActiveX 控制項之前，它應該呼叫`OleInitialize`。 安裝程式完成時，呼叫`OleUnitialize`。 這可確保 OLE 系統 Dll 位於註冊 ActiveX 控制項的適當狀態。  
  
 您應該註冊 MFCx0.DLL。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

