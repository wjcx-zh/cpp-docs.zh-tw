---
title: "The application cannot start. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0001"
  - "vs.message.VB_E_IDACANTBOOT"
ms.assetid: ffc123a0-99e1-4e9d-8f6e-34aa357bf98f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The application cannot start.
非預期的錯誤導致 Visual Studio 無法啟動。  發生下列其中一項時，即會出現此錯誤：  
  
-   整合式開發環境 \(IDE\) 無法載入 Msxml3.dll。  
  
-   IDE 無法載入 Mso.dll。  
  
-   IDE 無法載入 DTE.olb。  
  
-   在安裝期間未建立 Visual Studio 的授權金鑰。  
  
-   已開啟指令碼封鎖功能，不允許執行指令碼。  
  
-   .NET Framework 安裝程式 \(Visual Studio 的必要元件\) 無法為 mscorlib.dll 產生有效的原生映像。  
  
-   您的電腦上有 Klez 病毒存在。  
  
 請使用下列其中一個程序更正此錯誤。  
  
> [!WARNING]
>  您必須修改登錄機碼，才能使用其中某些解決方法。  如果您不當使用登錄編輯程式，將可能造成嚴重的問題，而需要重新安裝作業系統。  Microsoft 無法保證您可以解決因不當使用登錄編輯程式而導致的問題。  使用登錄編輯程式的風險須自行承擔。  
  
 IDE 無法載入 Msxml3.dll。  
 2001 年 7 月 Beta 版的 MSXML 4.0 Technology Preview 使電腦進入導致此行為的狀態。  若要修復 Msxml3.dll 登錄，請遵循下列步驟：  
  
### 解除安裝 Msxml4.dll  
  
1.  在 \[**開始**\] 功能表上選擇 \[**執行**\]。  
  
2.  在 \[**開啟**\] 文字方塊中輸入 `regsvr32 /u c:\winnt\system32\msxml4.dll`，然後按一下 \[**確定**\]。  
  
### 下載並安裝 MSXML 的安全性更新  
  
1.  請從 [http:\/\/www.microsoft.com\/windows\/ie\/downloads\/critical\/q317244\/download.asp](http://www.microsoft.com/windows/ie/downloads/critical/q317244/download.asp) 下載您的電腦上安裝的 MSXML 版本所適用的最新安全性更新。  
  
2.  執行安全性更新的 .exe。  
  
### 下載並套用更新的登錄值  
  
1.  請從 [http:\/\/download.microsoft.com\/download\/VisualStudioNET\/fix\/1.0\/WIN98MeXP\/Fixxml4.exe](http://download.microsoft.com/download/VisualStudioNET/fix/1.0/WIN98MeXP/Fixxml4.exe) 下載更新的登錄值。  
  
2.  按兩下 fixxml4.exe，然後將檔案解壓縮。  
  
3.  找出 Fixxml4.reg，然後按兩下該檔案，以更新登錄值。  
  
 IDE 無法載入 Mso.dll。  
 使用下列清單來修正 Mso.dll 的問題。  
  
### Microsoft Office  
  
-   在您的電腦上解除安裝任何 Microsoft Office XP Beta 版本。  
  
-   透過 \[新增\/移除程式\] 來修復 Office XP。  
  
-   在 \[登錄編輯程式\] 中，驗證下列登錄機碼：  
  
     `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0\Path] "MSO"="C:\Program Files\Common Files\Microsoft Shared\Office10\MSO.DLL"`  
  
 IDE 無法載入 DTE.olb。  
 若要更正此錯誤：  
  
### 登錄 Dte.olb  
  
1.  在 \[**開始**\] 功能表上選擇 \[**執行**\]。  
  
2.  在 \[**開啟**\] 文字方塊中輸入 `regsvr32 C:\Program Files\Common Files\Microsoft Shared\MSEnv\DTE.OLB`，然後按一下 \[**確定**\]。  
  
 在安裝期間未建立 Visual Studio 的授權金鑰。  
 如果 Visual Studio 的開頭顯示畫面未包含已安裝的產品清單，且未包含產品安裝人員的相關資訊，表示授權金鑰已遺失。  此外，如果 Visual Studio 未列在 \[新增\/移除程式\] 對話方塊中，表示授權金鑰已遺失。  
  
 若要更正這個問題：  
  
### 建立 Visual Studio 的授權金鑰  
  
-   從電腦中完全移除 Visual Studio，然後重新安裝產品。  
  
 已開啟指令碼封鎖功能，不允許執行指令碼。  
 如果第三方應用程式啟用了指令碼封鎖功能，IDE 將會在出現後消失。  
  
-   若要修正此問題，請確認指令碼封鎖功能正確運作。  
  
 .NET Framework 安裝程式 \(Visual Studio 的必要元件\) 無法為 mscorlib.dll 產生有效的原生映像。  
 如果 Visual Studio 的開頭顯示畫面在短暫出現後隨即消失，表示檔案 Mscorlib.dll 的有效原生映像可能已遺失。  此檔案會在 .NET Framework 安裝期間建立於 \\%windir%\\assembly\\NativeImages1\_v1.0.3705\\mscorlib 目錄中。  
  
 若要更正此問題：  
  
### 建立有效的 Mscorlib.dll 檔  
  
1.  解除安裝 .NET Framework，再加以重新安裝。  
  
 您的電腦上有 Klez 病毒存在。  
 如果您的電腦感染到 Klez 病毒，可能會出現「應用程式無法啟動」錯誤。  建議您更新防毒軟體，再掃描電腦中的病毒。