---
title: "MFC ActiveX 控制項：散發 ActiveX 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetWindowsDirectory"
  - "GetSystemDirectory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "散發 MFC ActiveX 控制項"
  - "GetProcAddress 方法, 註冊 ActiveX 控制項"
  - "GetSystemDirectory 方法"
  - "GetWindowsDirectory 方法"
  - "安裝 ActiveX 控制項"
  - "LoadLibrary 方法, 註冊 ActiveX 控制項"
  - "MFC ActiveX 控制項, ANSI 或 Unicode 版本"
  - "MFC ActiveX 控制項, 散發"
  - "MFC ActiveX 控制項, 安裝"
  - "MFC ActiveX 控制項, 註冊"
  - "MFC40.DLL"
  - "MFC40U.DLL"
  - "MSVCRT40.dll"
  - "OLEPRO32.DLL"
  - "可轉散發檔案, MFC ActiveX 控制項"
  - "註冊 ActiveX 控制項"
  - "註冊控制項"
  - "登錄, 註冊控制項"
  - "RegSvr32.exe"
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：散發 ActiveX 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將討論幾個問題與轉散發 ActiveX 控制項有關聯:  
  
-   [ANSI 或 Unicode 版本控制](#_core_ansi_or_unicode_control_versions)  
  
-   [安裝 ActiveX 控制項和可轉散發 DLL](#_core_installing_activex_controls_and_redistributable_dlls)  
  
-   [註冊控制項](#_core_registering_controls)  
  
    > [!NOTE]
    >  如需轉散發 ActiveX 控制項的詳細資訊，請參閱 [重新分配控制項](../data/ado-rdo/redistributing-controls.md)。  
  
##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI 或 Unicode 版本控制  
 您必須決定要傳輸控制的 ANSI 或 Unicode 版本或兩者。  這個決定根據可攜性因素固有的 ANSI 和 Unicode 字元集。  
  
 ANSI 控制，所有的 Win32 作業系統，可讓您在各種 Win32 作業系統之間的最大可攜性。  Unicode 控制項只在 Windows NT \(3.51 版 \(含\) 以後版本\)，但是，在 Windows 95 或 Windows 98。  如果可攜性就是主要的顧慮，請傳輸 ANSI 控制。  如果控制項在 Windows NT 只執行，您可以傳輸 Unicode 控制。  您也可以選擇傳輸和將應用程式安裝版本最適合使用者的作業系統。  
  
##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> 安裝 ActiveX 控制項和可轉散發 DLL  
 您可以將 ActiveX 控制項的安裝程式應該建立 Windows 目錄中的一個特殊子目錄和安裝在控制項 .OCX 檔案。  
  
> [!NOTE]
>  使用 Windows **GetWindowsDirectory** API 在安裝程式取得 Windows 目錄的名稱。  您可以從您的公司或產品名稱取得子目錄的名稱。  
  
 安裝程式必須安裝在 Windows 系統目錄的必要的可轉散發 DLL 檔案。  如果任何 DLL 已經出現在使用者的電腦上，安裝程式應該其版本與您安裝的版本比較。  其版本號碼高於已經安裝的檔案，請重新安裝檔案。  
  
 由於 ActiveX 控制項在 OLE 容器應用程式只能使用，不需要發出完整設定與控制項的 OLE DLL。  您可以假設，包含的應用程式 \(或作業系統\) 有標準 OLE DLL 安裝。  
  
##  <a name="_core_registering_controls"></a> 註冊控制項  
 在使用之前，控制項必須為它建立適當的項目在 Windows 系統註冊資料庫。  某些 ActiveX 控制項容器為使用者提供一個功能表項目註冊新的控制項，不過，此功能可能無法在所有容器。  因此，，會在安裝時，您可以安裝程式註冊控制項。  
  
 如果您需要，也可以撰寫自己的安裝程式直接註冊控制項。  
  
 使用 **LoadLibrary** Windows API 載入控制項 DLL。  接著，使用 **GetProcAddress** 取得「DllRegisterServer」函式的位址。  最後，呼叫 `DllRegisterServer` 函式。  下列程式碼範例示範了可能的方法，在 `hLib` 控制項程式庫的控制代碼和 `lpDllEntryPoint`存放區「DllRegisterServer」函式的位址。  
  
 [!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/CPP/mfc-activex-controls-distributing-activex-controls_1.cpp)]  
  
 註冊控制項的優點是您不需要叫用和載入個別處理 \(也就是說， REGSVR32\)，以降低安裝時間。  此外，，因為登入是內部處理序，安裝程式會外部處理序可能可以更有效率地管理錯誤和無法預料的情況。  
  
> [!NOTE]
>  在您的安裝程式安裝 ActiveX 控制項之前，它應該呼叫 **OleInitialize**。  當您的安裝程式完成後，請呼叫 **OleUnitialize**。  這可確保這個 OLE 系統 DLL 中登錄的 ActiveX 控制項適當的狀態。  
  
 您必須註冊 MFCx0.DLL。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)