---
title: "/SUBSYSTEM (指定子系統) | Microsoft Docs"
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
  - "/subsystem"
  - "VC.Project.VCLinkerTool.SubSystem"
  - "VC.Project.VCLinkerTool.SubSystemVersion"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SUBSYSTEM 連結器選項"
  - "SUBSYSTEM 連結器選項"
  - "-SUBSYSTEM 連結器選項"
  - "通訊端"
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SUBSYSTEM (指定子系統)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|  
            POSIX|WINDOWS)  
            [,major[.minor]]  
```  
  
 BOOT\_APPLICATION  
 在 Windows 開機環境中執行的應用程式。  如需有關開機應用程式的詳細資訊，請參閱 [BCD 相關資訊](http://msdn.microsoft.com/library/windows/desktop/aa362639)。  
  
 CONSOLE  
 Win32 字元模式應用程式。  作業系統會提供主控台應用程式適用的主控台。  如果已為機器碼定義了 `main` 或 `wmain`，並且為 Managed 程式碼定義了 `int main(array<String ^> ^)`，或者您只使用了 `/clr:safe` 來建置應用程式，則 CONSOLE 是預設值。  
  
 可延伸的韌體介面  
 EFI\_\* 子系統。  如需詳細資訊，請參閱 EFI 規格。  如需參考範例，請參閱 Intel 網站說明。  最低及預設的版本是 1.0 版。  
  
 NATIVE  
 Windows NT 核心模式驅動程式。  這個選項通常只在 Windows 系統元件中使用。  如果已指定了 [\/DRIVER:WDM](../../build/reference/driver-windows-nt-kernel-mode-driver.md)，預設值便是 NATIVE。  
  
 POSIX  
 在 Windows NT 中以 POSIX 子系統執行的應用程式。  
  
 WINDOWS  
 應用程式不需要主控台，可能是因為它建立自己的視窗，與使用者進行互動。  如果已定義機器碼的 `WinMain` 或 `wWinMain`，或是已為 Managed 程式碼定義了 `WinMain(HISTANCE *, HINSTANCE *, char *, int)` 或 `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)`，則 WINDOWS 為預設值。  
  
 `Major` 和 `minor` \(選擇性\)  
 指定子系統的最小必要版本。  引數是介於 0 到 65,535 範圍之間的十進位數字。  如需詳細資訊，請參閱「備註」。  版本號碼沒有上限。  
  
## 備註  
 \/SUBSYSTEM 選項可用來指定可執行檔的環境。  
  
 子系統的選擇會影響連結器將選取的進入點符號 \(或進入點函式\)。  
  
 下表列出子系統的選擇性最小和預設的 `major` 和 `minor` 版本號碼。  
  
|子系統|最低|預設|  
|---------|--------|--------|  
|BOOT\_APPLICATION|1.0|1.0|  
|CONSOLE|5.01 \(x86\) 5.02 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|6.00 \(x86 ,[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|  
|WINDOWS|5.01 \(x86\) 5.02 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|6.00 \(x86 ,[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|  
|NATIVE \(包含 DRIVER:WDM\)|1.00 \(x86\) 1.10 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)],ARM\)|1.00 \(x86\) 1.10 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)],ARM\)|  
|NATIVE \(不含 \/DRIVER:WDM\)|4.00 \(x86\) 5.02 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|4.00 \(x86\) 5.02 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|  
|POSIX|1.0|19.90|  
|EFI\_APPLICATION, EFI\_BOOT\_SERVICE\_DRIVER, EFI\_ROM, EFI\_RUNTIME\_DRIVER|1.0|1.0|  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[連結器\] 資料夾。  
  
3.  按一下 \[**系統**\] 屬性頁。  
  
4.  修改 `SubSystem` 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)